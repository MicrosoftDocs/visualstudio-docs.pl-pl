---
title: Wewnątrz edytora
description: Dowiedz się więcej o podsystemach i funkcjach edytora. Można rozciągnąć funkcje edytora programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0bd45bb0a47de7283d75c083edc46b6fc38fe7d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105079205"
---
# <a name="inside-the-editor"></a>Wewnątrz edytora

Edytor składa się z kilku różnych podsystemów, które zostały zaprojektowane w celu zachowania niezależnego modelu tekstu edytora od widoku tekstu i interfejsu użytkownika.

W tych sekcjach opisano różne aspekty edytora:

- [Przegląd podsystemów](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Model tekstu](../extensibility/inside-the-editor.md#the-text-model)

- [Widok tekstu](../extensibility/inside-the-editor.md#the-text-view)

W tych sekcjach opisano funkcje edytora:

- [Tagi i klasyfikatory](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Zakończeń](../extensibility/inside-the-editor.md#adornments)

- [Projekcja](../extensibility/inside-the-editor.md#projection)

- [Tworzenie konspektu](../extensibility/inside-the-editor.md#outlining)

- [Powiązania myszy](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operacje edytora](../extensibility/inside-the-editor.md#editor-operations)

- [Technologia](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Przegląd podsystemów

### <a name="text-model-subsystem"></a>Podsystem modelu tekstu

Podsystem modelu tekstu jest odpowiedzialny za reprezentowania tekstu i włączenie jego manipulowania. Podsystem modelu tekstu zawiera <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfejs, który opisuje sekwencję znaków, które mają być wyświetlane przez Edytor. Ten tekst można modyfikować, śledzić i w inny sposób manipulować na wiele sposobów. Model tekstu udostępnia również typy dla następujących aspektów:

- Usługa, która kojarzy tekst z plikami i zarządza odczytami i zapisywaniem ich w systemie plików.

- Usługa różnicowa, która umożliwia znalezienie minimalnych różnic między dwiema sekwencjami obiektów.

- System do opisywania tekstu w buforze pod warunkiem podzbiorów tekstu w innych buforach.

Podsystem modelu tekstu jest bezpłatny pojęcia interfejsu użytkownika. Na przykład nie jest odpowiedzialny za formatowanie tekstu ani układ tekstu i nie ma informacji o zakończeniach wizualizacji, które mogą być skojarzone z tekstem.

Typy publiczne podsystemu modelu tekstowego są zawarte w *Microsoft.VisualStudio.Text.Data.dll* i *Microsoft.VisualStudio.CoreUtility.dll*, które są zależne tylko od .NET Framework biblioteki klas podstawowych i Managed Extensibility Framework (MEF).

### <a name="text-view-subsystem"></a>Podsystem wyświetlania tekstu

Podsystem wyświetlania tekstu jest odpowiedzialny za formatowanie i wyświetlanie tekstu. Typy w tym podsystemie są podzielone na dwie warstwy, w zależności od tego, czy typy polegają na Windows Presentation Foundation (WPF). Najważniejsze typy to <xref:Microsoft.VisualStudio.Text.Editor.ITextView> i <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView> , które kontrolują zestaw wierszy tekstu, które mają być wyświetlane, a także karetkę, zaznaczenie i obiekty służące do wypełniania tekstu przy użyciu elementów interfejsu użytkownika WPF. Ten podsystem zawiera również Marginesy wokół obszaru wyświetlania tekstu. Marginesy te mogą być rozszerzane i mogą zawierać różne rodzaje zawartości i efekty wizualne. Przykładami marginesów są wyświetlanie numerów wierszy i paski przewijania.

Typy publiczne podsystemu widoku tekstu są zawarte w *Microsoft.VisualStudio.Text.UI.dll* i *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Pierwszy zestaw zawiera elementy niezależne od platformy, a drugi zawiera elementy specyficzne dla WPF.

### <a name="classification-subsystem"></a>Podsystem klasyfikacji

Podsystem klasyfikacji jest odpowiedzialny za określanie właściwości czcionki dla tekstu. Klasyfikator dzieli tekst na różne klasy, na przykład "słowo kluczowe" lub "komentarz". Mapa formatu klasyfikacji odnosi się do tych klas do rzeczywistych właściwości czcionki, na przykład "Blue Consolas 10 pt". Te informacje są używane przez widok tekstu podczas formatowania i renderowania tekstu. Tagowanie, które zostało opisane w dalszej części tego tematu, umożliwia skojarzenie danych z zakresem tekstu.

Typy publiczne podsystemu klasyfikacji są zawarte w Microsoft.VisualStudio.Text.Logic.dll i współpracują z wizualnymi aspektami klasyfikacji, które znajdują się w Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Podsystem operacji

Podsystem operacji definiuje zachowanie edytora. Zawiera implementację poleceń edytora programu Visual Studio i systemu cofania.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Bliższe spojrzenie na model tekstu i widok tekstu

### <a name="the-text-model"></a>Model tekstu

Podsystem modelu tekstu składa się z różnych grup typów tekstu. Obejmują one bufor tekstu, migawki tekstu i zakresy tekstu.

#### <a name="text-buffers-and-text-snapshots"></a>Bufory tekstu i migawki tekstu

<xref:Microsoft.VisualStudio.Text.ITextBuffer>Interfejs reprezentuje sekwencję znaków Unicode, które są kodowane przy użyciu UTF-16, czyli kodowania używanego przez `String` typ w .NET Framework. Bufor tekstowy może zostać utrwalony jako dokument systemu plików, ale nie jest to wymagane.

Służy <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> do tworzenia pustego bufora tekstowego lub bufora tekstu, który jest inicjowany z ciągu lub <xref:System.IO.TextReader> . Bufor tekstowy może zostać utrwalony w systemie plików jako <xref:Microsoft.VisualStudio.Text.ITextDocument> .

Dowolny wątek może edytować bufor tekstu, dopóki wątek nie przejmie na własność buforu tekstu przez wywołanie <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A> . Następnie tylko ten wątek może wykonywać edycję.

Bufor tekstowy może przechodzić przez wiele wersji w okresie istnienia. Nowa wersja jest generowana za każdym razem, gdy bufor jest edytowany, a niezmienna <xref:Microsoft.VisualStudio.Text.ITextSnapshot> reprezentuje zawartość tej wersji buforu. Ponieważ migawki tekstu są niezmienne, można uzyskać dostęp do migawki tekstu w dowolnym wątku bez ograniczeń, nawet jeśli bufor tekstu, który reprezentuje, nadal zmienia się.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Migawki tekstu i linie migawek tekstu

Zawartość migawki tekstu można wyświetlić jako sekwencję znaków lub sekwencję wierszy. Liczba znaków i wierszy jest indeksowana począwszy od zera. Pusta migawka tekstowa zawiera zero znaków i jeden pusty wiersz. Linia jest rozdzielana przez dowolną prawidłową sekwencję znaków w wierszu Unicode lub początkową lub końcową buforu. Znaki podziału wiersza są jawnie reprezentowane w migawce tekstowej, a podziały wierszy w migawce tekstowej nie wszystkie muszą być takie same.

> [!NOTE]
> Aby uzyskać więcej informacji na temat znaków podziału wiersza w edytorze programu Visual Studio, zobacz [kodowania i podziały wierszy](../ide/encodings-and-line-breaks.md).

Wiersz tekstu jest reprezentowany przez <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> obiekt, który można uzyskać z migawki tekstu dla określonego numeru wiersza lub dla określonego znaku.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Elementy snapshotpoint, SnapshotSpans i NormalizedSnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> reprezentuje pozycję znaku w migawce. Położenie jest gwarantowane między zerem a długością migawki. <xref:Microsoft.VisualStudio.Text.SnapshotSpan>Reprezentuje zakres tekstu w migawce. Jego położenie końcowe jest gwarantowane między zerem a długością migawki. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection>Składa się z zestawu <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiektów z tej samej migawki.

#### <a name="spans-and-normalizedspancollections"></a>Zakresy i NormalizedSpanCollections

<xref:Microsoft.VisualStudio.Text.Span>Reprezentuje interwał, który można zastosować do zakresu tekstu w migawce tekstu. Położenia migawek są zależne od zera, więc zakresy mogą zaczynać się w dowolnym miejscu, w tym zero. `End`Właściwość zakresu jest równa sumie jego `Start` właściwości i jej `Length` właściwości. Element `Span` nie zawiera znaku, który jest indeksowany przez `End` Właściwość. Na przykład zakres, który ma początek = 5 i długość = 3, ma wartość End = 8 i zawiera znaki w położeniach 5, 6 i 7. Notacją dla tego zakresu jest [5.. 8).

Dwa przedziały przecinają się, jeśli mają jakiekolwiek pozycje wspólne, łącznie z pozycją końcową. W związku z tym, przecięcie [3, 5) i [2, 7) jest [3, 5) i przecięcie [3, 5) i [5, 7) to [5, 5). (Należy zauważyć, że [5, 5) jest pustym zakresem).

Dwa zakresy nakładają się, jeśli mają wspólne stanowiska, z wyjątkiem pozycji końcowej. Pusty zakres nigdy nie pokrywa się z żadnym innym zakresem, a nakładanie się na dwa zakresy nie jest nigdy puste.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> to lista zakresów w kolejności właściwości początkowych zakresów. Na liście, nakładające się lub sąsiadujące zakresy są scalane. Na przykład, z uwzględnieniem zestawu zakresów [5.. 9), [0.. 1), [3.. 6) i [9.. 10), znormalizowana lista zakresów to [0.. 1), [3.. 10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Powiadomienia o zmianach ITextEdit, textversion i text

Zawartość bufora tekstowego można zmienić przy użyciu <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu. Utworzenie takiego obiektu (przy użyciu jednej z `CreateEdit()` metod <xref:Microsoft.VisualStudio.Text.ITextBuffer> ) powoduje uruchomienie transakcji tekstowej, która składa się z edycji tekstu. Każda edycja polega na zastąpieniu pewnego zakresu tekstu w buforze przez ciąg. Współrzędne i zawartość każdej edycji są wyrażane względem migawki bufora, gdy transakcja została uruchomiona. <xref:Microsoft.VisualStudio.Text.ITextEdit>Obiekt dostosowuje współrzędne zmian, na które mają wpływ inne modyfikacje w tej samej transakcji.

Rozważmy na przykład bufor tekstowy, który zawiera ten ciąg:

```
abcdefghij
```

Zastosuj transakcję, która zawiera dwie edycje, jedną edycję zastępującą zakres [2.. 4) przy użyciu znaku `X` i drugiej edycji, która zastępuje zakres w [6.. 9) przy użyciu znaku `Y` . Wynik jest tym buforem:

```
abXefYj
```

Współrzędne dla drugiej edycji zostały obliczone w odniesieniu do zawartości buforu na początku transakcji przed zastosowaniem pierwszej edycji.

Zmiany w buforze są stosowane, gdy <xref:Microsoft.VisualStudio.Text.ITextEdit> obiekt jest zatwierdzany przez wywołanie jego `Apply()` metody. Jeśli istnieje co najmniej jedna niepusta Edycja, zostanie <xref:Microsoft.VisualStudio.Text.ITextVersion> utworzona nowa, <xref:Microsoft.VisualStudio.Text.ITextSnapshot> zostanie utworzona nowa i `Changed` zostanie zgłoszone jedno zdarzenie. Każda wersja tekstowa ma inną migawkę tekstu. Migawka tekstowa reprezentuje pełen stan bufora tekstowego po edycji transakcji, ale wersja tekstowa zawiera opis tylko zmian z jednej migawki do następnej. Ogólnie, migawki tekstu są przeznaczone do użycia raz, a następnie odrzucane, podczas gdy wersje tekstu muszą pozostać aktywne przez jakiś czas.

Wersja tekstowa zawiera <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection> . Ta kolekcja zawiera informacje o zmianach, które w przypadku zastosowania do migawki tworzą następną migawkę. Każda <xref:Microsoft.VisualStudio.Text.ITextChange> w kolekcji zawiera pozycję znaku zmiany, zastąpiony ciąg i ciąg zastępczy. Zastąpiony ciąg jest pusty dla podstawowego wstawiania, a ciąg zamienny jest pusty dla usunięcia podstawowego. Znormalizowana kolekcja jest zawsze `null` dla najnowszej wersji buforu tekstu.

W <xref:Microsoft.VisualStudio.Text.ITextEdit> dowolnym momencie można utworzyć wystąpienie tylko jednego obiektu dla buforu tekstu, a wszystkie edycje tekstu muszą zostać wykonane na wątku, który jest właścicielem buforu tekstowego (Jeśli odmówiono własności). Edycję tekstu można porzucić, wywołując `Cancel` metodę lub `Dispose` metodę.

<xref:Microsoft.VisualStudio.Text.ITextBuffer> zapewnia również `Insert()` `Delete()` `Replace()` metody, które przypominają te Znalezione w <xref:Microsoft.VisualStudio.Text.ITextEdit> interfejsie. Wywołanie tych ma taki sam skutek jak tworzenie <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu, wykonywanie podobnego wywołania, a następnie zastosowanie edycji.

#### <a name="tracking-points-and-tracking-spans"></a>Punkty śledzenia i zakres śledzenia

<xref:Microsoft.VisualStudio.Text.ITrackingPoint>Reprezentuje pozycję znaku w buforze tekstu. Jeśli bufor jest edytowany w sposób, który powoduje zmianę położenia znaku, punkt śledzenia przesuwa się z nim. Na przykład, jeśli punkt śledzenia odnosi się do pozycji 10 w buforze, a pięć znaków jest wstawianych na początku buforu, punkt śledzenia odnosi się do pozycji 15. Jeśli wstawienie odbywa się na dokładnej pozycji wskazywanej przez punkt śledzenia, jego zachowanie jest określane przez jego <xref:Microsoft.VisualStudio.Text.PointTrackingMode> , który może mieć wartość `Positive` lub `Negative` . Jeśli tryb śledzenia jest dodatni, punkt śledzenia odnosi się do tego samego znaku, który jest teraz na końcu wstawiania. Jeśli tryb śledzenia jest ujemny, punkt śledzenia odnosi się do pierwszego wstawionego znaku w pierwotnym położeniu. Jeśli znak w pozycji reprezentowanej przez punkt śledzenia zostanie usunięty, punkt śledzenia przenosi się do pierwszego znaku, który następuje po usunięciu zakresu. Na przykład, jeśli punkt śledzenia odwołuje się do znaku w pozycji 5, a znaki w pozycjach od 3 do 6 są usuwane, punkt śledzenia odwołuje się do znaku na pozycji 3.

<xref:Microsoft.VisualStudio.Text.ITrackingSpan>Reprezentuje zakres znaków zamiast tylko jednego położenia. Jego zachowanie zależy od jego <xref:Microsoft.VisualStudio.Text.SpanTrackingMode> . Jeśli tryb śledzenia zakresu ma wartość [SpanTrackingMode. EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), zakres śledzenia powiększa się, aby uwzględnić tekst wstawiony do jego krawędzi. Jeśli tryb śledzenia zakresu ma wartość [SpanTrackingMode. EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), zakres śledzenia nie uwzględnia tekstu wstawionego na jego krawędzi. Jeśli jednak tryb śledzenia zakresu ma wartość [SpanTrackingMode. z edgepositive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), wstawianie powoduje wypchnięcie bieżącej pozycji do początku, a jeśli tryb śledzenia zakresu jest [SpanTrackingMode. z edgenegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), wypchnięcie bieżącej pozycji do końca.

Możesz uzyskać pozycję punktu śledzenia lub zakres śledzenia dla dowolnej migawki bufora tekstowego, do której należą. Punkty śledzenia i zakresy śledzenia mogą być bezpiecznie przywoływane z dowolnego wątku.

#### <a name="content-types"></a>Typy zawartości

Typy zawartości to mechanizm służący do definiowania różnych rodzajów zawartości. Typ zawartości może być typem pliku, takim jak "text", "Code" lub "Binary" lub typem technologii, takim jak "XML", "VB" lub "c#". Na przykład słowo "Using" jest słowem kluczowym w języku C# i Visual Basic, ale nie w innych językach programowania. W związku z tym definicja tego słowa kluczowego byłaby ograniczona do typów zawartości "c#" i "VB".

Typy zawartości są używane jako filtr dla modułów definiowania układu i innych elementów edytora. Wiele funkcji edytora i punktów rozszerzenia są zdefiniowane dla każdego typu zawartości. Na przykład Kolorowanie tekstu jest inne dla zwykłych plików tekstowych, plików XML i plików kodu źródłowego Visual Basic. Bufory tekstu są zwykle przypisane do typu zawartości podczas ich tworzenia, a typ zawartości bufora tekstowego można zmienić.

Typy zawartości mogą mieć wiele dziedziczenia z innych typów zawartości. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition>Pozwala określić wiele typów podstawowych jako obiekty nadrzędne danego typu zawartości.

Deweloperzy mogą definiować własne typy zawartości i rejestrować je przy użyciu <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService> . Wiele funkcji edytora można zdefiniować w odniesieniu do określonego typu zawartości przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> . Na przykład można zdefiniować marginesy edytora, elementy definiowania i procedury obsługi myszy, aby były stosowane tylko do edytorów, które wyświetlają określone typy zawartości.

### <a name="the-text-view"></a>Widok tekstu

Część widoku wzorca widoku modelu (MVC) definiuje widok tekstu, formatowanie widoku, elementy graficzne, takie jak pasek przewijania, oraz karetkę. Wszystkie elementy prezentacji edytora programu Visual Studio są oparte na platformie WPF.

#### <a name="text-views"></a>Widoki tekstu

<xref:Microsoft.VisualStudio.Text.Editor.ITextView>Interfejs jest reprezentacją widoku tekstu niezależną od platformy. Jest ona używana głównie do wyświetlania dokumentów tekstowych w oknie, ale może być również używana do innych celów, na przykład w etykietce narzędzia.

Widok tekstu odwołuje się do różnych rodzajów buforów tekstu. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A>Właściwość odwołuje się do <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> obiektu, który wskazuje te trzy różne bufory tekstowe: bufor danych, czyli górny bufor poziomu danych, bufor edycji, w którym odbywa się Edycja, i bufor wizualny, który jest buforem, który jest wyświetlany w widoku tekstu.

Tekst jest formatowany w oparciu o klasyfikatory, które są dołączone do bazowego bufora tekstu i jest umieszczony przy użyciu dostawców zakończenia, które są dołączone do samego widoku tekstu.

#### <a name="the-text-view-coordinate-system"></a>System współrzędnych widoku tekstu

System współrzędnych widoku tekstu określa pozycje w widoku tekstu. W tym układzie współrzędnych wartość x 0,0 odpowiada lewej krawędzi wyświetlanego tekstu, a wartość y 0,0 odpowiada górnej krawędzi wyświetlanego tekstu. Współrzędna x rośnie od lewej do prawej, a Współrzędna y zwiększa się od góry do dołu.

Okienka ekranu (część tekstu widocznego w oknie tekstu) nie można przewijać w taki sam sposób, jak w pionie. Okienko ekranu jest przewijane w poziomie, zmieniając jego lewą współrzędną, tak aby poruszać się w odniesieniu do powierzchni rysunku. Okienko ekranu może być jednak przewijane w pionie tylko przez zmianę renderowanego tekstu, co powoduje <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> podniesienie poziomu zdarzenia.

Odległości w układzie współrzędnych odnoszą się do pikseli logicznych. Jeśli powierzchnia renderowania tekstu jest wyświetlana bez przekształcenia skalowania, jedna jednostka w systemie współrzędnych renderowania tekstu odpowiada jeden piksel na ekranie.

#### <a name="margins"></a>Marginesy

<xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin>Interfejs reprezentuje margines i umożliwia kontrolę widoczności marginesu i jego rozmiaru. Istnieją cztery wstępnie zdefiniowane marginesy o nazwie "Top", "Left", "Right" i "Bottom" i są dołączone do górnej, dolnej, lewej lub prawej krawędzi widoku. Marginesy te są kontenerami, w których można umieścić inne marginesy. Interfejs definiuje metody, które zwracają rozmiar marginesu i widoczność marginesu. Marginesy to elementy wizualne, które zawierają dodatkowe informacje o widoku tekstu, do którego są dołączone. Na przykład margines numeru wiersza wyświetla numery wierszy dla widoku tekstu. Margines glifu wyświetla elementy interfejsu użytkownika.

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider>Interfejs obsługuje tworzenie i rozmieszczenie marginesów. Marginesy mogą być uporządkowane w odniesieniu do innych marginesów. Marginesy o wyższym priorytecie znajdują się bliżej widoku tekstu. Na przykład jeśli istnieją dwa lewe marginesy, margines a i margines B, a margines B ma niższy priorytet niż margines A, margines B pojawia się po lewej stronie marginesu A.

#### <a name="the-text-view-host"></a>Host widoku tekstu

<xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Interfejs zawiera widok tekstu i wszelkie sąsiednie dekoracje, które towarzyszą widokowi, na przykład paski przewijania. Host widoku tekstu zawiera również marginesy, które są dołączone do obramowania widoku.

#### <a name="formatted-text"></a>Tekst sformatowany

Tekst wyświetlany w widoku tekstu składa się z <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> obiektów. Każdy wiersz w widoku tekstu odpowiada jednemu wierszowi tekstu w widoku tekstu. Długie wiersze w źródłowym buforze tekstowym mogą być częściowo słonięte (jeśli Zawijanie słów nie jest włączone) lub podzielone na wiele wierszy widoku tekstu. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>Interfejs zawiera metody i właściwości mapowania między współrzędnymi i znakami, a dla definiowania układu, które mogą być skojarzone z wierszem.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> obiekty są tworzone przy użyciu <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfejsu. Jeśli jesteś zainteresowany tylko tekstem, który jest aktualnie wyświetlany w widoku, możesz zignorować Źródło formatowania. Jeśli interesuje Cię format tekstu, który nie jest wyświetlany w widoku (na przykład w celu obsługi wycinania i wklejania tekstu sformatowanego), możesz użyć, <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> Aby sformatować tekst w buforze tekstu.

Widok tekstu jest formatowany pojedynczo <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> .

## <a name="editor-features"></a>Funkcje edytora

Funkcje edytora są zaprojektowane tak, aby definicja funkcji była oddzielona od jej implementacji. Edytor obejmuje następujące funkcje:

- Tagi i klasyfikatory

- Zakończeń

- Projekcja

- Tworzenie konspektu

- Powiązania myszy i klucza

- Operacje i elementy podstawowe

- IntelliSense

### <a name="tags-and-classifiers"></a>Tagi i klasyfikatory

Tagi to znaczniki, które są skojarzone z zakresem tekstu. Mogą być prezentowane na różne sposoby, na przykład za pomocą kolorowania tekstu, podkreśleń, grafiki lub wyskakujących okienek. Klasyfikatory są jednym rodzajem znacznika.

Inne rodzaje tagów służą <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> do wyróżniania tekstu, tworzenia <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> konspektu i <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> błędów kompilacji.

#### <a name="classification-types"></a>Typy klasyfikacji

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationType>Interfejs reprezentuje klasę równoważności, która jest abstrakcyjną kategorią tekstu. Typy klasyfikacji mogą mieć wiele dziedziczeń z innych typów klasyfikacji. Na przykład klasyfikacje języka programowania mogą zawierać słowo kluczowe "Keyword", "Comment" i "identifier", które dziedziczą z "Code". Typy klasyfikacji języka naturalnego mogą zawierać "rzeczownik", "czasownik" i "przymiotnik", który dziedziczy po "języku naturalnym".

#### <a name="classifications"></a>Klasyfikacje

Klasyfikacja jest wystąpieniem określonego typu klasyfikacji, zwykle w odniesieniu do zakresu tekstu. A służy <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> do reprezentowania klasyfikacji. Zakres klasyfikacji może być uważany za etykietę obejmującą konkretny zakres tekstu i informuje system, że ten zakres tekstu jest określonego typu klasyfikacji.

#### <a name="classifiers"></a>Klasyfikatory

<xref:Microsoft.VisualStudio.Text.Classification.IClassifier>Jest mechanizmem, który dzieli tekst na zestaw klasyfikacji. Klasyfikatory muszą być zdefiniowane dla określonych typów zawartości i są tworzone dla określonych buforów tekstu. Klienci muszą implementować <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> uczestnictwo w klasyfikacji tekstu.

#### <a name="classifier-aggregators"></a>Agregatory klasyfikatora

Agregator klasyfikatora jest mechanizmem, który łączy wszystkie klasyfikatory dla jednego buforu tekstowego w tylko jeden zestaw klasyfikacji. Na przykład zarówno klasyfikator C#, jak i klasyfikator języka angielskiego mogą tworzyć klasyfikacje na komentarzu w pliku C#. Weź pod uwagę następujący komentarz:

```
// This method produces a classifier
```

Klasyfikator języka C# może oznaczyć cały zakres jako komentarz, a klasyfikatora w języku angielskim może sklasyfikować "produkuje" jako "czasownik" i "Method" jako "rzeczownik". Agregator tworzy zestaw nienakładających się klasyfikacji, a typ zestawu jest oparty na wszystkich wkładach.

Agregator klasyfikatora jest również klasyfikatorem, ponieważ dzieli tekst na zestaw klasyfikacji. Agregator klasyfikatora gwarantuje również, że nie ma nakładających się klasyfikacji i że klasyfikacje są sortowane. Poszczególne klasyfikatory są bezpłatne do zwrócenia dowolnego zestawu klasyfikacji w dowolnej kolejności i nakładają się w dowolny sposób.

#### <a name="classification-formatting-and-text-coloring"></a>Formatowanie klasyfikacji i kolorowanie tekstu

Formatowanie tekstu to przykład funkcji, która jest oparta na klasyfikacji tekstu. Jest on używany przez warstwę widoku tekstu do określenia sposobu wyświetlania tekstu w aplikacji. Obszar formatowania tekstu zależy od WPF, ale logiczna definicja klasyfikacji nie.

Format klasyfikacji to zestaw właściwości formatowania dla określonego typu klasyfikacji. Te formaty dziedziczą z formatu nadrzędnego typu klasyfikacji.

<xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap>Jest to mapa z typu klasyfikacji do zestawu właściwości formatowania tekstu. Implementacja mapy formatu w edytorze obsługuje wszystkie eksporty formatów klasyfikacji.

### <a name="adornments"></a>Zakończeń

Elementy definiowania układu są efektami graficznymi, które nie są bezpośrednio związane z czcionką i kolorem znaków w widoku tekstu. Na przykład czerwoną podkreśleniem, która jest używana do oznaczania kodu niekompilowanego w wielu językach programowania, jest osadzony podział, a etykietki narzędzi są wyskakujące okienka. Zakończenia są wyprowadzane z <xref:System.Windows.UIElement> i implementowane <xref:Microsoft.VisualStudio.Text.Tagging.ITag> . Dwa wyspecjalizowane typy tagów definiowania układu są <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag> , w przypadku tekstów końcowych, które zajmują ten sam obszar co tekst w widoku, i <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> dla podkreślenia.

Osadzone zakończenia są elementami graficznymi, które stanowią część sformatowanego widoku tekstu. Są one zorganizowane w różnych warstwach Z kolejnością od. Istnieją trzy wbudowane warstwy: tekst, karetka i zaznaczenie. Jednak deweloperzy mogą definiować więcej warstw i umieszczać je w pozostałej kolejności. Trzy rodzaje osadzonych etapów są względami tekstowymi (które przesuwają się, gdy tekst jest przenoszony i są usuwane po usunięciu tekstu), względnych dla widoku, które należy wykonać w przypadku nietekstowych części widoku), a w przypadku regionów z kontrolą właściciela (Deweloper musi zarządzać umieszczaniem).

Wyskakujące okienka są to grafiki, które są wyświetlane w małym oknie powyżej widoku tekstu, na przykład etykietki narzędzi.

### <a name="projection"></a><a name="projection"></a> Stając

Projekcja jest techniką służącą do konstruowania innego rodzaju bufora tekstu, który nie przechowuje tekstu, ale zamiast tego łączy tekst z innych buforów tekstu. Na przykład można użyć buforu projekcji do łączenia tekstu z dwóch innych buforów i przedstawić wynik, tak jakby znajdował się w tylko jednym buforze, lub ukryć części tekstu w jednym buforze. Bufor projekcji może działać jako bufor źródłowy do innego buforu projekcji. Zestaw buforów, które są powiązane przez projekcję, może być skonstruowany w celu ponownego rozmieszczenia tekstu na wiele różnych sposobów. (Taki zestaw jest również znany jako *Graf bufora*). Funkcja konspektowania tekstu programu Visual Studio jest implementowana przy użyciu buforu projekcji w celu ukrycia zwiniętego tekstu, a Edytor programu Visual Studio dla stron ASP.NET używa projekcji do obsługi języków osadzonych, takich jak Visual Basic i C#.

<xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer>Jest tworzony przy użyciu <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService> . Bufor projekcji jest reprezentowany przez uporządkowaną sekwencję <xref:Microsoft.VisualStudio.Text.ITrackingSpan> obiektów, które są znane jako *zakresy źródłowe*. Zawartość tych zakresów jest prezentowana jako sekwencja znaków. Bufory tekstu, z których są rysowane zakresy źródłowe, są nazwane *bufory źródłowe*. Klienci buforu projekcji nie muszą pamiętać, że różnią się od zwykłego buforu tekstu.

Bufor projekcji nasłuchuje zdarzeń zmiany tekstu w buforach źródłowych. Gdy tekst w zakresie źródła ulegnie zmianie, bufor projekcji mapuje zmiany współrzędnych tekstu na własne współrzędne i wywołuje odpowiednie zdarzenia zmiany tekstu. Rozważmy na przykład bufory źródłowe A i B, które mają tę zawartość:

```
A: ABCDE
B: vwxyz
```

Jeśli bufor projekcji P jest tworzony z dwóch zakresów tekstu, jeden, który ma wszystkie bufory A i drugi, który ma wszystkie bufory B, wówczas P ma następującą zawartość:

```
P: ABCDEvwxyz
```

Jeśli podciąg `xy` został usunięty z bufora B, wówczas bufor P zgłasza zdarzenie wskazujące, że znaki w pozycjach 7 i 8 zostały usunięte.

Bufor projekcji można również edytować bezpośrednio. Propaguje zmiany do odpowiednich buforów źródłowych. Na przykład jeśli ciąg zostanie wstawiony do buforu P na pozycji 6 (oryginalna pozycja znaku "v"), wstawienie jest propagowane do bufora B na pozycji 1.

Istnieją ograniczenia dotyczące zakresów źródłowych, które przyczyniają się do buforu projekcji. Zakresy źródłowe nie mogą się nakładać. Lokalizacja w buforze projekcji nie może być mapowana na więcej niż jedną lokalizację w buforze źródłowym, a lokalizacja w buforze źródłowym nie może być mapowana na więcej niż jedną lokalizację w buforze projekcji. W relacji buforu źródłowego nie są dozwolone żadne cykliczne.

Zdarzenia są wywoływane, gdy zestaw buforów źródła dla buforu projekcji ulegnie zmianie i gdy zestaw obejmuje zmiany.
Bufor dla koprocedury jest specjalnym rodzajem buforu projekcji. Jest ona używana głównie do tworzenia konspektów i dla operacji, które rozszerzają i zwijają bloki tekstu. Bufor dla koprocedury jest oparty na tylko jednym buforze źródłowym, a zakresy w buforze dla koprocedury muszą być uporządkowane w taki sam sposób, jak w buforze źródłowym.

#### <a name="the-buffer-graph"></a>Wykres buforu

<xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph>Interfejs umożliwia mapowanie na grafie buforów projekcji. Wszystkie bufory tekstowe i bufory projekcji są zbierane w postaci bezpośredniego wykresu, podobnie jak w przypadku drzewa składni abstrakcyjnej, który jest generowany przez kompilator języka. Wykres jest definiowany przez górny bufor, który może być dowolnym buforem tekstu. Wykres buforu można zmapować z punktu w górnym buforze do punktu w buforze źródłowym lub z zakresu w górnym buforze do zestawu zakresów w buforze źródłowym. Podobnie, można zmapować punkt lub zakres od buforu źródłowego do punktu w górnym buforze. Wykresy buforowe są tworzone przy użyciu <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService> .

#### <a name="events-and-projection-buffers"></a>Bufory zdarzeń i projekcji

Gdy bufor projekcji jest modyfikowany, modyfikacje są wysyłane z buforu projekcji do buforów, które są od niego zależne. Po zmodyfikowaniu wszystkich buforów zdarzenia zmiany buforu są wywoływane, rozpoczynając od najwyższego buforu.

### <a name="outlining"></a>Tworzenie konspektu

Konspekt umożliwia rozwijanie lub zwijanie różnych bloków tekstu w widoku tekstu. Konspekt jest definiowany jako rodzaj <xref:Microsoft.VisualStudio.Text.Tagging.ITag> , w taki sam sposób jak zdefiniowano definicje. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> to tag definiujący region tekstu, który może być rozwinięty lub zwinięty. Aby użyć konspektu, należy zaimportować program w <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> celu uzyskania <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager> . Menedżer konspektu wylicza, zwija i rozwija różne bloki, które są reprezentowane jako <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> obiekty, i odpowiednio wywołuje zdarzenia.

### <a name="mouse-bindings"></a>Powiązania myszy

Powiązania myszy łączą ruchy myszy z innymi poleceniami. Powiązania myszy są definiowane przy użyciu <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider> , a kluczowe powiązania są zdefiniowane przy użyciu <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider> . <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost>Powoduje automatyczne utworzenie wystąpienia wszystkich powiązań i połączenie ich ze zdarzeniami myszy w widoku.

<xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor>Interfejs zawiera programy obsługi zdarzeń wykonywane wstępnie i proces po procesie dla różnych zdarzeń myszy. Aby obsłużyć jedno ze zdarzeń, można zastąpić niektóre metody w <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase> .

### <a name="editor-operations"></a>Operacje edytora

Operacje edytora mogą służyć do automatyzowania interakcji z edytorem, do obsługi skryptów lub innych celów. Można zaimportować <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> do operacji w celu uzyskania dostępu na danym <xref:Microsoft.VisualStudio.Text.Editor.ITextView> . Możesz następnie użyć tych obiektów do modyfikacji zaznaczenia, przewinąć widok lub przenieść karetkę do różnych części widoku.

### <a name="intellisense"></a>IntelliSense

Technologia IntelliSense obsługuje uzupełnianie instrukcji, pomoc w sygnaturach (znane także jako informacje o parametrach), szybkie informacje i żarówki.

Uzupełnianie instrukcji zawiera listę podręcznych potencjalnych uzupełniania dla nazw metod, elementów XML i innych elementów kodowania lub znaczników. Ogólnie rzecz biorąc, gest użytkownika wywołuje sesję ukończenia. Sesja wyświetla listę potencjalnych popełnień, a użytkownik może wybrać jedną lub odrzucić listę. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker>Jest odpowiedzialny za tworzenie i wyzwalanie <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession> . <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource>Oblicza <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> elementy ukończenia dla sesji.

## <a name="see-also"></a>Zobacz też

- [Punkty rozszerzenia usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Importy edytora](../extensibility/editor-imports.md)
