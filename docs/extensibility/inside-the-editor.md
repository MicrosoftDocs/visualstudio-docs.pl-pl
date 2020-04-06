---
title: Wewnątrz edytora
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bba0b5192df53b6ec837b0030c7b236bf8e08dea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710328"
---
# <a name="inside-the-editor"></a>Wewnątrz edytora

Edytor składa się z kilku różnych podsystemów, które mają na celu oddzielenie modelu tekstu edytora od widoku tekstu i interfejsu użytkownika.

W tych sekcjach opisano różne aspekty edytora:

- [Przegląd podsystemów](../extensibility/inside-the-editor.md#overview-of-the-subsystems)

- [Model tekstu](../extensibility/inside-the-editor.md#the-text-model)

- [Widok tekstu](../extensibility/inside-the-editor.md#the-text-view)

W tych sekcjach opisano funkcje edytora:

- [Tagi i klasyfikatory](../extensibility/inside-the-editor.md#tags-and-classifiers)

- [Ozdoby](../extensibility/inside-the-editor.md#adornments)

- [Projekcja](../extensibility/inside-the-editor.md#projection)

- [Tworzenie konspektu](../extensibility/inside-the-editor.md#outlining)

- [Wiązania myszy](../extensibility/inside-the-editor.md#mouse-bindings)

- [Operacje edytora](../extensibility/inside-the-editor.md#editor-operations)

- [IntelliSense](../extensibility/inside-the-editor.md#intellisense)

## <a name="overview-of-the-subsystems"></a>Przegląd podsystemów

### <a name="text-model-subsystem"></a>Podsystem modelu tekstu

Podsystem modelu tekstu jest odpowiedzialny za reprezentowanie tekstu i włączanie jego manipulacji. Podsystem modelu tekstu <xref:Microsoft.VisualStudio.Text.ITextBuffer> zawiera interfejs, który opisuje sekwencję znaków, które mają być wyświetlane przez edytor. Ten tekst może być modyfikowany, śledzony i w inny sposób manipulowany na wiele sposobów. Model tekstu zawiera również typy dla następujących aspektów:

- Usługa kojarzy tekst z plikami i zarządza odczytywaniem i zapisywaniem ich w systemie plików.

- Usługa różnicowania, która znajduje minimalne różnice między dwiema sekwencjami obiektów.

- System opisujący tekst w buforze pod względem podzbiorów tekstu w innych buforach.

Podsystem modelu tekstu jest wolny od pojęć interfejsu użytkownika(UI). Na przykład nie jest odpowiedzialny za formatowanie tekstu lub układ tekstu i nie ma znajomości ozdób wizualnych, które mogą być skojarzone z tekstem.

Publiczne typy podsystemu modelu tekstu są zawarte w *plikach Microsoft.VisualStudio.Text.Data.dll* i *Microsoft.VisualStudio.CoreUtility.dll*, które zależą tylko od biblioteki klas podstawowych programu .NET Framework i zarządzanej struktury rozszerzalności (MEF).

### <a name="text-view-subsystem"></a>Podsystem widoku tekstu

Podsystem widoku tekstu jest odpowiedzialny za formatowanie i wyświetlanie tekstu. Typy w tym podsystemie są podzielone na dwie warstwy, w zależności od tego, czy typy zależą od programu Windows Presentation Foundation (WPF). Najważniejsze typy <xref:Microsoft.VisualStudio.Text.Editor.ITextView> są <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>i , które kontrolują zestaw wierszy tekstu, które mają być wyświetlane, a także cieszy, zaznaczenie i urządzenia do ozdabiania tekstu przy użyciu elementów interfejsu użytkownika WPF. Ten podsystem zapewnia również marginesy wokół obszaru wyświetlania tekstu. Te marginesy mogą być rozszerzone i mogą zawierać różne rodzaje zawartości i efekty wizualne. Przykładami marginesów są wyświetlacze numerów linii i paski przewijania.

Publiczne typy podsystemu widoku tekstu są zawarte w plikach *Microsoft.VisualStudio.Text.UI.dll* i *Microsoft.VisualStudio.Text.UI.Wpf.dll*. Pierwszy zestaw zawiera elementy niezależne od platformy, a drugi zawiera elementy specyficzne dla WPF.

### <a name="classification-subsystem"></a>Podsystem klasyfikacji

Podsystem klasyfikacji jest odpowiedzialny za określanie właściwości czcionki dla tekstu. Klasyfikator dzieli tekst na różne klasy, na przykład "słowo kluczowe" lub "komentarz". Mapa formatu klasyfikacji odnosi się do tych klas do rzeczywistych właściwości czcionki, na przykład "Blue Consolas 10 pt". Te informacje są używane przez widok tekstu podczas formatowania i renderowania tekstu. Tagowanie, które jest opisane bardziej szczegółowo w dalszej części tego tematu, umożliwia dane, które mają być skojarzone z zakresami tekstu.

Publiczne typy podsystemu klasyfikacji są zawarte w pliku Microsoft.VisualStudio.Text.Logic.dll i współdziałają z wizualnymi aspektami klasyfikacji, które są zawarte w pliku Microsoft.VisualStudio.Text.UI.Wpf.dll.

### <a name="operations-subsystem"></a>Podsystem operacji

Podsystem operacji definiuje zachowanie edytora. Zapewnia implementację dla poleceń edytora visual studio i systemu cofania.

## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Bliższe spojrzenie na model tekstu i widok tekstu

### <a name="the-text-model"></a>Model tekstu

Podsystem modelu tekstu składa się z różnych grup typów tekstu. Należą do nich bufor tekstu, migawki tekstu i zakresy tekstu.

#### <a name="text-buffers-and-text-snapshots"></a>Bufory tekstu i migawki tekstu

Interfejs <xref:Microsoft.VisualStudio.Text.ITextBuffer> reprezentuje sekwencję znaków Unicode, które są kodowane przy użyciu UTF-16, `String` który jest kodowanie używane przez typ w .NET Framework. Bufor tekstu może być utrwalony jako dokument systemu plików, ale nie jest to wymagane.

Służy <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> do tworzenia pustego buforu tekstowego lub buforu tekstu, <xref:System.IO.TextReader>który jest inicjowany z ciągu lub z . Bufor tekstu można utrwalić w <xref:Microsoft.VisualStudio.Text.ITextDocument>systemie plików jako plik .

Każdy wątek może edytować bufor tekstu, dopóki <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>wątek nie przejmie na własność buforu tekstowego, wywołując program . Po tym tylko ten wątek może wykonywać zmiany.

Bufor tekstu można przejść przez wiele wersji w okresie jego istnienia. Nowa wersja jest generowana za każdym razem, gdy <xref:Microsoft.VisualStudio.Text.ITextSnapshot> bufor jest edytowany, a niezmienne reprezentuje zawartość tej wersji buforu. Ponieważ migawki tekstu są niezmienne, można uzyskać dostęp do migawki tekstu w dowolnym wątku, bez ograniczeń, nawet jeśli bufor tekstu, który reprezentuje, nadal się zmienia.

#### <a name="text-snapshots-and-text-snapshot-lines"></a>Migawki tekstu i wiersze migawki tekstu

Zawartość migawki tekstowej można wyświetlić jako sekwencję znaków lub jako sekwencję wierszy. Znaki i wiersze są indeksowane od zera. Migawka pustego tekstu zawiera zero znaków i jeden pusty wiersz. Wiersz jest rozdzielany przez dowolną prawidłową sekwencję znaków podziału wiersza Unicode lub przez początek lub koniec buforu. Znaki podziału wiersza są jawnie reprezentowane w migawce tekstu, a podziały wierszy w migawce tekstu nie muszą być takie same.

> [!NOTE]
> Aby uzyskać więcej informacji na temat znaków podziału wiersza w edytorze programu Visual Studio, zobacz [Kodowanie i podziały wierszy](../ide/encodings-and-line-breaks.md).

Wiersz tekstu jest reprezentowany <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> przez obiekt, który można uzyskać z migawki tekstu dla określonego numeru wiersza lub dla określonej pozycji znaku.

#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>SnapshotPoints, SnapshotSpans i NormalizedSnapshotSpanCollections

A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> reprezentuje położenie znaku w migawce. Pozycja jest gwarantowana leży między zero i długość migawki. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> reprezentuje zakres tekstu w migawce. Jego pozycja end jest gwarantowane leżeć między zero i długość migawki. Składa <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> się z <xref:Microsoft.VisualStudio.Text.SnapshotSpan> zestawu obiektów z tej samej migawki.

#### <a name="spans-and-normalizedspancollections"></a>Przęsła i znormalizowaneSpanKollections

A <xref:Microsoft.VisualStudio.Text.Span> reprezentuje interwał, który można zastosować do zakresu tekstu w migawce tekstu. Pozycje migawki są oparte na wartościach zerowych, więc zakresy można rozpocząć w dowolnej pozycji, w tym zero. Właściwość `End` zakresu jest równa sumie jego `Start` własności `Length` i jej właściwości. A `Span` nie zawiera znaku, który jest `End` indeksowany przez właściwość. Na przykład zakres, który ma Start = 5 i Length = 3 ma End = 8 i zawiera znaki w pozycjach 5, 6 i 7. Notacja dla tego zakresu jest [5..8).

Dwa przęsła przecinają się, jeśli mają wspólne pozycje, w tym pozycję Koniec. Dlatego przecięcie [3, 5) i [2, 7) wynosi [3, 5), a przecięcie [3, 5) i [5, 7) wynosi [5, 5). (Zwróć uwagę, że [5, 5) jest pustym rozpiętością).

Dwa zakresy nakładają się, jeśli mają wspólne pozycje, z wyjątkiem pozycji Koniec. Puste rozpiętość nigdy nie nakłada się na inne rozpiętości, a nakładanie się dwóch zakresów nigdy nie jest puste.

A <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> to lista zakresów w kolejności start właściwości zakresów. Na liście nakładające się lub przylegające zakresy są scalane. Na przykład, biorąc pod uwagę zestaw zakresów [5..9), [0..1), [3..6) i [9..10), znormalizowana lista zakresów to [0..1), [3..10).

#### <a name="itextedit-textversion-and-text-change-notifications"></a>Powiadomienia o zmianie tekstu ITextEdit, TextVersion i tekst

Zawartość buforu tekstu można zmienić <xref:Microsoft.VisualStudio.Text.ITextEdit> za pomocą obiektu. Tworzenie takiego obiektu (przy użyciu `CreateEdit()` jednej <xref:Microsoft.VisualStudio.Text.ITextBuffer>z metod ) rozpoczyna transakcję tekstową, która składa się z edycji tekstu. Każda edycja jest zastąpienie niektórych zakres tekstu w buforze przez ciąg. Współrzędne i zawartość każdej edycji są wyrażane względem migawki buforu podczas rozpoczęcia transakcji. Obiekt <xref:Microsoft.VisualStudio.Text.ITextEdit> dostosowuje współrzędne zmian, na które mają wpływ inne zmiany w tej samej transakcji.

Rozważmy na przykład bufor tekstowy zawierający ten ciąg:

```
abcdefghij
```

Zastosuj transakcję, która zawiera dwie edycje, jedną edycję, która zastępuje zakres w `X` [2..4) za pomocą znaku, a drugą `Y`edycję, która zastępuje zakres w [6..9) za pomocą znaku . Wynikiem jest ten bufor:

```
abXefYj
```

Współrzędne dla drugiej edycji zostały obliczone w odniesieniu do zawartości buforu na początku transakcji, przed zastosowaniem pierwszej edycji.

Zmiany w buforze są <xref:Microsoft.VisualStudio.Text.ITextEdit> skuteczne, gdy obiekt `Apply()` jest zatwierdzany przez wywołanie jego metody. Jeśli była co najmniej jedna niepusta edycja, tworzona jest nowa, <xref:Microsoft.VisualStudio.Text.ITextVersion> tworzona jest nowa <xref:Microsoft.VisualStudio.Text.ITextSnapshot> i wywoływane jest jedno `Changed` zdarzenie. Każda wersja tekstu ma inną migawkę tekstu. Migawka tekstu reprezentuje pełny stan buforu tekstu po transakcji edycji, ale wersja tekstowa opisuje tylko zmiany z jednej migawki do następnej. Ogólnie rzecz biorąc migawki tekstu są przeznaczone do użycia raz, a następnie odrzucone, podczas gdy wersje tekstu muszą pozostać aktywne przez pewien czas.

Wersja tekstowa <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>zawiera plik . W tej kolekcji opisano zmiany, które po zastosowaniu do migawki, produkcji kolejnych migawki. Każdy <xref:Microsoft.VisualStudio.Text.ITextChange> w kolekcji zawiera położenie znaku zmiany, zastąpiony ciąg i ciąg zastępczy. Zastąpiony ciąg jest pusty dla wstawiania podstawowego, a ciąg zastępczy jest pusty dla usunięcia podstawowego. Znormalizowana `null` kolekcja jest zawsze dla najnowszej wersji buforu tekstu.

Tylko <xref:Microsoft.VisualStudio.Text.ITextEdit> jeden obiekt można utworzyć wystąpienia dla buforu tekstu w dowolnym momencie, a wszystkie zmiany tekstu muszą być wykonywane w wątku, który jest właścicielem buforu tekstu (jeśli własność została odebrana). Edycji tekstu można porzucić, `Cancel` wywołując `Dispose` jego metody lub jej metody.

<xref:Microsoft.VisualStudio.Text.ITextBuffer>zapewnia `Insert()`również `Delete()`, `Replace()` i metody, które <xref:Microsoft.VisualStudio.Text.ITextEdit> przypominają te znalezione na interfejsie. Wywołanie tych ma taki sam <xref:Microsoft.VisualStudio.Text.ITextEdit> efekt jak tworzenie obiektu, wykonywanie podobnych wywołań, a następnie stosowanie edycji.

#### <a name="tracking-points-and-tracking-spans"></a>Punkty śledzenia i zakresy śledzenia

Reprezentuje <xref:Microsoft.VisualStudio.Text.ITrackingPoint> położenie znaku w buforze tekstu. Jeśli bufor jest edytowany w sposób, który powoduje przesunięcie położenia znaku, punkt śledzenia przesuwa się wraz z nim. Na przykład jeśli punkt śledzenia odwołuje się do pozycji 10 w buforze, a pięć znaków są wstawiane na początku buforu, punkt śledzenia następnie odnosi się do pozycji 15. Jeśli wstawienie odbywa się dokładnie w pozycji oznaczonej przez punkt <xref:Microsoft.VisualStudio.Text.PointTrackingMode>śledzenia, jego zachowanie `Positive` `Negative`jest określane przez jego , który może być albo lub . Jeśli tryb śledzenia jest dodatni, punkt śledzenia odnosi się do tego samego znaku, który znajduje się teraz na końcu wstawiania. Jeśli tryb śledzenia jest ujemny, punkt śledzenia odnosi się do pierwszego wstawionego znaku w pozycji oryginalnej. Jeśli znak w pozycji reprezentowany przez punkt śledzenia zostanie usunięty, punkt śledzenia zostanie przesunięty do pierwszego znaku, który następuje po usuniętym zakresie. Na przykład jeśli punkt śledzenia odwołuje się do znaku w pozycji 5, a znaki w pozycjach od 3 do 6 zostaną usunięte, punkt śledzenia odnosi się do znaku w pozycji 3.

Reprezentuje <xref:Microsoft.VisualStudio.Text.ITrackingSpan> zakres znaków zamiast tylko jednej pozycji. Jego zachowanie zależy <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>od jego . Jeśli tryb śledzenia zakresu jest [SpanTrackingMode.EdgeInclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeInclusive), zakres śledzenia rośnie do włączenia tekstu wstawionego na jego krawędziach. Jeśli tryb śledzenia zakresu jest [SpanTrackingMode.EdgeExclusive](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeExclusive), zakres śledzenia nie zawiera tekst wstawiony na jego krawędziach. Jednak jeśli tryb śledzenia zakresu jest [SpanTrackingMode.EdgePozytywny](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgePositive), wstawiania wypycha bieżącą pozycję w kierunku startu, a jeśli tryb śledzenia zakresu jest [SpanTrackingMode.EdgeNegative](xref:Microsoft.VisualStudio.Text.SpanTrackingMode.EdgeNegative), wstawianie wypycha bieżącą pozycję pod koniec.

Można uzyskać położenie punktu śledzenia lub zakres zakresu śledzenia dla dowolnej migawki buforu tekstu, do którego należą. Punkty śledzenia i zakresy śledzenia mogą być bezpiecznie odwoływane z dowolnego wątku.

#### <a name="content-types"></a>Typy zawartości

Typy zawartości są mechanizmem definiowania różnych rodzajów zawartości. Typem zawartości może być typ pliku, taki jak "text", "code" lub "binary" lub typu technologii, takiego jak "xml", "vb" lub "c#". Na przykład słowo "przy użyciu" jest słowem kluczowym w języku C# i Visual Basic, ale nie w innych językach programowania. W związku z tym definicja tego słowa kluczowego będzie ograniczona do typów zawartości "c#" i "vb".

Typy zawartości są używane jako filtr ozdób i innych elementów edytora. Wiele funkcji edytora i punktów rozszerzeń jest zdefiniowanych dla typu zawartości. Na przykład kolorowanie tekstu różni się w przypadku plików tekstowych, plików XML i plików kodu źródłowego języka Visual Basic. Bufory tekstu są zazwyczaj przypisywane typ zawartości podczas ich tworzenia i typ zawartości buforu tekstu można zmienić.

Typy zawartości mogą dziedziczyć wiele z innych typów zawartości. Umożliwia <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> określenie wielu typów podstawowych jako elementów podstawowych danego typu zawartości.

Deweloperzy mogą definiować własne typy <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>zawartości i rejestrować je za pomocą programu . Wiele funkcji edytora można zdefiniować w odniesieniu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>do określonego typu zawartości za pomocą pliku . Na przykład marginesy edytora, ozdoby i programy obsługi myszy można zdefiniować tak, aby były stosowane tylko do edytorów, które wyświetlają określone typy zawartości.

### <a name="the-text-view"></a>Widok tekstu

Część widoku wzorca kontrolera widoku modelu (MVC) definiuje widok tekstu, formatowanie widoku, elementy graficzne, takie jak pasek przewijania i cieszkę. Wszystkie elementy prezentacji edytora visual studio są oparte na WPF.

#### <a name="text-views"></a>Widoki tekstu

Interfejs <xref:Microsoft.VisualStudio.Text.Editor.ITextView> jest niezależną od platformy reprezentacją widoku tekstowego. Służy głównie do wyświetlania dokumentów tekstowych w oknie, ale może być również używany do innych celów, na przykład w etykietce narzędzia.

Widok tekstu odwołuje się do różnych rodzajów buforów tekstu. Właściwość <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> odnosi się <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> do obiektu, który wskazuje te trzy różne bufory tekstu: bufor danych, który jest najwyższym buforem na poziomie danych, bufor edycji, w którym odbywa się edycja, i bufor wizualny, który jest buforem wyświetlanym w widoku tekstowym.

Tekst jest formatowany na podstawie klasyfikatorów, które są dołączone do buforu tekstu źródłowego i jest ozdobiony przy użyciu dostawców ozdabień, które są dołączone do samego widoku tekstu.

#### <a name="the-text-view-coordinate-system"></a>Układ współrzędnych widoku tekstu

Układ współrzędnych widoku tekstu określa pozycje w widoku tekstowym. W tym układzie współrzędnych wartość x 0,0 odpowiada lewej krawędzi wyświetlanego tekstu, a wartość y 0,0 odpowiada górnej krawędzi wyświetlanego tekstu. Współrzędna x zwiększa się od lewej do prawej, a współrzędna y wzrasta od góry do dołu.

Rzutnia (część tekstu widocznego w oknie tekstowym) nie może być przewijana w taki sam sposób w poziomie, jak jest przewijana w pionie. Rzutnia jest przewijana w poziomie, zmieniając jej lewą współrzędną tak, aby poruszała się względem powierzchni rysunku. Jednak rzutnia można przewijać tylko w pionie, zmieniając <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> renderowany tekst, co powoduje, że zdarzenie ma zostać podniesione.

Odległości w układzie współrzędnych odpowiadają pikselom logicznym. Jeśli powierzchnia renderowania tekstu jest wyświetlana bez przekształcenia skalowania, jedna jednostka w układzie współrzędnych renderowania tekstu odpowiada jednemu pikselowi na ekranie.

#### <a name="margins"></a>Marginesy

Interfejs <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> reprezentuje margines i umożliwia kontrolę widoczności marginesu i jego wielkości. Istnieją cztery wstępnie zdefiniowane marginesy, które mają nazwy "Góra", "Lewy", "Prawy" i "Dolny" i są dołączone do górnej, dolnej, lewej lub prawej krawędzi widoku. Te marginesy są kontenerami, w których można umieścić inne marginesy. Interfejs definiuje metody, które zwracają rozmiar marginesu i widoczność marginesu. Marginesy są elementami wizualnymi, które dostarczają dodatkowych informacji o widoku tekstu, do którego są dołączone. Na przykład margines liczby wierszy wyświetla numery wierszy dla widoku tekstu. Margines glifów wyświetla elementy interfejsu użytkownika.

Interfejs <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> obsługuje tworzenie i umieszczanie marginesów. Marże można zamówić w odniesieniu do innych marginesów. Marginesy o wyższym priorytecie znajdują się bliżej widoku tekstu. Na przykład, jeśli istnieją dwa lewe marginesy, margines A i margines B, a margines B ma niższy priorytet niż margines A, margines B pojawia się po lewej stronie marginesu A.

#### <a name="the-text-view-host"></a>Host widoku tekstu

Interfejs <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> zawiera widok tekstowy i wszelkie towarzyszące dekoracje, które towarzyszą widokowi, na przykład paski przewijania. Host widoku tekstu zawiera również marginesy, które są dołączone do obramowania widoku.

#### <a name="formatted-text"></a>Sformatowany tekst

Tekst wyświetlany w widoku tekstowym składa <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> się z obiektów. Każdy wiersz widoku tekstu odpowiada jednemu wierszowi tekstu w widoku tekstu. Długie wiersze w buforze tekstu źródłowego mogą być częściowo zasłonięte (jeśli zawijanie wyrazów nie jest włączone) lub podzielone na wiele wierszy widoku tekstu. Interfejs <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> zawiera metody i właściwości mapowania między współrzędnymi i znakami oraz ozdób, które mogą być skojarzone z wierszem.

<xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine>obiekty są tworzone <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> za pomocą interfejsu. Jeśli jesteś zaniepokojony tylko tekstem, który jest aktualnie wyświetlany w widoku, możesz zignorować źródło formatowania. Jeśli interesuje Cię format tekstu, który nie jest wyświetlany w widoku (na przykład do obsługi wytnienia i wklejania tekstu sformatowanego), można użyć <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> do formatowania tekstu w buforze tekstowym.

Widok tekstu formatuje <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> po jednym na raz.

## <a name="editor-features"></a>Funkcje edytora

Funkcje edytora są zaprojektowane tak, aby definicja funkcji była oddzielona od jej implementacji. Edytor zawiera następujące funkcje:

- Tagi i klasyfikatory

- Ozdoby

- Projekcja

- Tworzenie konspektu

- Wiązania myszy i klawiszy

- Operacje i prymitywy

- IntelliSense

### <a name="tags-and-classifiers"></a>Tagi i klasyfikatory

Znaczniki są znacznikami, które są skojarzone z zakresem tekstu. Można je prezentować na różne sposoby, na przykład za pomocą kolorowania tekstu, podkreśleń, grafiki lub wyskakujących okienków. Klasyfikatory są jednym rodzajem tagu.

Inne rodzaje tagów <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> są do <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> wyróżniania tekstu, <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> do tworzenia nakreślenia i dla błędów kompilacji.

#### <a name="classification-types"></a>Typy klasyfikacji

Interfejs <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> reprezentuje klasę równoważności, która jest abstrakcyjną kategorią tekstu. Typy klasyfikacji mogą dziedziczyć wiele z innych typów klasyfikacji. Na przykład klasyfikacje języków programowania mogą zawierać "słowo kluczowe", "komentarz" i "identyfikator", które wszystkie dziedziczą po "kod". Typy klasyfikacji języka naturalnego mogą obejmować "rzeczownik", "czasownik" i "przymiotnik", które dziedziczą po "języku naturalnym".

#### <a name="classifications"></a>Klasyfikacje

Klasyfikacja jest wystąpieniem określonego typu klasyfikacji, zazwyczaj w zakresie tekstu. A <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> jest używany do reprezentowania klasyfikacji. Zakres klasyfikacji można traktować jako etykietę, która obejmuje określony zakres tekstu i informuje system, że ten zakres tekstu jest określonego typu klasyfikacji.

#### <a name="classifiers"></a>Klasyfikatorów

Jest <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> mechanizmem, który dzieli tekst na zestaw klasyfikacji. Klasyfikatory muszą być zdefiniowane dla określonych typów zawartości i wystąpienia dla określonych buforów tekstu. Klienci muszą <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> zaimplementować, aby uczestniczyć w klasyfikacji tekstu.

#### <a name="classifier-aggregators"></a>Agregatory klasyfikatorów

Agregator klasyfikatora to mechanizm, który łączy wszystkie klasyfikatory dla jednego buforu tekstu w tylko jeden zestaw klasyfikacji. Na przykład klasyfikator języka C# i klasyfikator języka angielskiego można utworzyć klasyfikacje za kątem komentarza w pliku Języka C#. Rozważmy ten komentarz:

```
// This method produces a classifier
```

Klasyfikator języka C# może oznaczać cały zakres jako komentarz, a klasyfikator języka angielskiego może klasyfikować "produkuje" jako "zlecenie" i "metoda" jako "rzeczownik". Agregator tworzy zestaw nienakładających się klasyfikacji, a typ zestawu jest oparty na wszystkich wkładach.

Agregator klasyfikatora jest również klasyfikatorem, ponieważ dzieli tekst na zestaw klasyfikacji. Agregator klasyfikatora zapewnia również, że nie ma nakładających się klasyfikacji i że klasyfikacje są sortowane. Poszczególne klasyfikatory mogą zwracać dowolny zestaw klasyfikacji w dowolnej kolejności i nakładające się w jakikolwiek sposób.

#### <a name="classification-formatting-and-text-coloring"></a>Formatowanie klasyfikacji i kolorowanie tekstu

Formatowanie tekstu jest przykładem operacji opartej na klasyfikacji tekstu. Jest on używany przez warstwę widoku tekstu do określenia wyświetlania tekstu w aplikacji. Obszar formatowania tekstu zależy od WPF, ale logiczna definicja klasyfikacji nie.

Format klasyfikacji to zestaw właściwości formatowania dla określonego typu klasyfikacji. Te formaty dziedziczą z formatu nadrzędnego typu klasyfikacji.

An <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> jest mapą od typu klasyfikacji do zestawu właściwości formatowania tekstu. Implementacja mapy formatu w edytorze obsługuje wszystkie eksporty formatów klasyfikacji.

### <a name="adornments"></a>Ozdoby

Ozdoby to efekty graficzne, które nie są bezpośrednio związane z czcionką i kolorem znaków w widoku tekstowym. Na przykład czerwony squiggle podkreślenie, który jest używany do oznaczania nie kompilowania kodu w wielu językach programowania jest osadzone ozdoby i etykietki narzędzi są wyskakujące ozdoby. Ozdoby pochodzą z <xref:System.Windows.UIElement> i implementują <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Dwa wyspecjalizowane typy znacznika <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>ozdoby to , dla ozdób, które zajmują taką <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>samą przestrzeń jak tekst w widoku, oraz , dla podkreślenia fali.

Osadzone ozdoby to grafika stanowiąca część sformatowanego widoku tekstu. Są one zorganizowane w różnych warstwach z zamówieniem. Istnieją trzy wbudowane warstwy, w następujący sposób: tekst, cieszka i zaznaczenie. Jednak deweloperzy mogą zdefiniować więcej warstw i umieścić je w kolejności względem siebie. Trzy rodzaje osadzonych ozdób są ozdoby względne tekstu (które są przenoszone, gdy tekst przenosi i są usuwane po usunięciu tekstu), ozdoby względne widoku (które mają do czynienia z nietekstowymi częściami widoku) i kontrolowane przez właściciela ozdoby (deweloper musi zarządzać ich położeniem).

Ozdoby wyskakujące to grafika, która pojawia się w małym oknie nad widokiem tekstu, na przykład etykietki narzędzi.

### <a name="projection"></a><a name="projection"></a>Projekcji

Projekcja jest techniką konstruowania innego rodzaju buforu tekstu, który w rzeczywistości nie przechowuje tekstu, ale zamiast tego łączy tekst z innych buforów tekstu. Na przykład bufor projekcji może służyć do łączenia tekstu z dwóch innych buforów i przedstawić wynik tak, jakby był w jednym buforze lub do ukrycia części tekstu w jednym buforze. Bufor projekcji może działać jako bufor źródłowy do innego buforu projekcji. Zestaw buforów, które są powiązane przez projekcji mogą być skonstruowane w celu zmiany rozmieszczenia tekstu na wiele różnych sposobów. (Taki zestaw jest również znany jako *wykres buforu*.) Funkcja tworzenia kreślenia tekstu programu Visual Studio jest implementowana przy użyciu buforu rzutowania, aby ukryć zwinięty tekst, a edytor Visual Studio dla stron ASP.NET używa projekcji do obsługi języków osadzonych, takich jak Visual Basic i C#.

An <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> jest tworzony <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>przy użyciu programu . Bufor projekcji jest reprezentowany przez <xref:Microsoft.VisualStudio.Text.ITrackingSpan> uporządkowaną sekwencję obiektów, które są znane jako *zakresy źródłowe*. Zawartość tych zakresów są przedstawiane jako sekwencja znaków. Bufory tekstowe, z których są rysowane zakresy źródłowe, są nazywane *buforami źródłowymi*. Klienci buforu projekcji nie muszą być świadomi, że różni się on od zwykłego buforu tekstu.

Bufor projekcji nasłuchuje zdarzeń zmiany tekstu w buforach źródłowych. Gdy tekst w zakresie źródłowym zmienia się, bufor projekcji mapuje zmienione współrzędne tekstu na własne współrzędne i wywołuje odpowiednie zdarzenia zmiany tekstu. Rozważmy na przykład bufory źródłowe A i B, które mają te treści:

```
A: ABCDE
B: vwxyz
```

Jeśli bufor projekcji P jest utworzony z dwóch zakresów tekstu, jeden, który ma cały bufor A, a drugi, który ma cały bufor B, a następnie P ma następującą zawartość:

```
P: ABCDEvwxyz
```

Jeśli podciąg `xy` zostanie usunięty z bufora B, a następnie bufor P wywołuje zdarzenie, które wskazuje, że znaki w pozycjach 7 i 8 zostały usunięte.

Bufor projekcji można również edytować bezpośrednio. Propaguje zmiany do odpowiednich buforów źródłowych. Na przykład jeśli ciąg zostanie wstawiony do buforu P w pozycji 6 (oryginalna pozycja znaku "v"), wstawienie jest propagowane do buforu B w pozycji 1.

Istnieją ograniczenia dotyczące zakresów źródłowych, które przyczyniają się do buforu projekcji. Zakresy źródłowe nie mogą się nakładać; lokalizacja w buforze projekcji nie może mapować do więcej niż jednej lokalizacji w dowolnym buforze źródłowym, a lokalizacja w buforze źródłowym nie może być mapowana do więcej niż jednej lokalizacji w buforze projekcji. W relacji buforu źródłowego nie są dozwolone żadne cykliczności.

Zdarzenia są wywoływane, gdy zmienia się zestaw buforów źródłowych dla buforu projekcji i gdy zmienia się zestaw źródeł.
Bufor elision jest specjalnym rodzajem bufora projekcji. Jest on używany głównie do konspektów i operacji, które rozwijają i zwijają bloki tekstu. Bufor elision opiera się tylko na jednym buforze źródłowym, a zakresy w buforze elision muszą być uporządkowane tak samo, jak są one uporządkowane w buforze źródłowym.

#### <a name="the-buffer-graph"></a>Wykres buforu

Interfejs <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> umożliwia mapowanie na wykresie buforów projekcji. Wszystkie bufory tekstu i bufory projekcji są zbierane w ukierunkowanym wykresie acyklicznym, podobnie jak abstrakcyjne drzewo składni, które jest tworzone przez kompilator języka. Wykres jest zdefiniowany przez górny bufor, który może być dowolnym buforem tekstowym. Wykres buforu można mapować z punktu w górnym buforze do punktu w buforze źródłowym lub z zakresu w górnym buforze do zestawu zakresów w buforze źródłowym. Podobnie można mapować punkt lub zakres z buforu źródłowego do punktu w górnym buforze. Wykresy buforu są tworzone <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>przy użyciu pliku .

#### <a name="events-and-projection-buffers"></a>Zdarzenia i bufory projekcji

Po zmodyfikowaniu buforu projekcji modyfikacje są wysyłane z buforu projekcji do buforów, które są od niego zależne. Po zmodyfikowaniu wszystkich buforów zdarzenia zmiany buforu są wywoływane, począwszy od najgłębszego buforu.

### <a name="outlining"></a>Tworzenie konspektu

Konspekt to możliwość rozwijania lub zwijania różnych bloków tekstu w widoku tekstowym. Nakreślenie jest definiowane <xref:Microsoft.VisualStudio.Text.Tagging.ITag>jako rodzaj , w taki sam sposób, jak ozdoby są zdefiniowane. A <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> to znacznik definiujący region tekstu, który można rozwinąć lub zwinąć. Aby użyć zwymiarze, <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> należy <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>zaimportować, aby uzyskać plik . Menedżer konsytów wylicza, zwija i rozwija różne bloki, które są reprezentowane jako <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> obiekty i odpowiednio wywołuje zdarzenia.

### <a name="mouse-bindings"></a>Wiązania myszy

Wiązania myszy łączą ruchy myszy z różnymi poleceniami. Powiązania myszy są definiowane <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>za pomocą programu , a <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>powiązania klawiszy są definiowane za pomocą pliku . Automatycznie <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> tworzenie wystąpienia wszystkich powiązań i łączy je ze zdarzeniami myszy w widoku.

Interfejs <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> zawiera programy obsługi zdarzeń przed procesem i po procesie dla różnych zdarzeń myszy. Aby obsłużyć jedno ze zdarzeń, można <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>zastąpić niektóre metody w pliku .

### <a name="editor-operations"></a>Operacje edytora

Operacje edytora mogą służyć do automatyzacji interakcji z edytorem, do skryptów lub innych celów. Operacje dostępu <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> można zaimportować <xref:Microsoft.VisualStudio.Text.Editor.ITextView>w danym pliku . Następnie można użyć tych obiektów, aby zmodyfikować zaznaczenie, przewinąć widok lub przenieść dasznik do różnych części widoku.

### <a name="intellisense"></a>IntelliSense

IntelliSense obsługuje uzupełnianie instrukcji, pomoc dotyczącą podpisu (znane również jako informacje o parametrach), szybkie informacje i żarówki.

Uzupełnianie instrukcji zawiera listy podręczne potencjalnych uzupełnień dla nazw metod, elementów XML i innych elementów kodowania lub znaczników. Ogólnie rzecz biorąc gest użytkownika wywołuje sesję zakończenia. Sesja wyświetla listę potencjalnych uzupełnień, a użytkownik może wybrać jedną lub odrzucić listę. Jest <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> odpowiedzialny za tworzenie i <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>wyzwalanie . Oblicza <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> elementy ukończenia sesji.

## <a name="see-also"></a>Zobacz też

- [Punkty rozszerzeń usługi językowej i edytora](../extensibility/language-service-and-editor-extension-points.md)
- [Importowanie edytora](../extensibility/editor-imports.md)
