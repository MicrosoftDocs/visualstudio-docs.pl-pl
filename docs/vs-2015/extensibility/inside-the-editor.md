---
title: Wewnątrz edytora | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - architecture
ms.assetid: 822cbb8d-7ab4-40ee-bd12-44016ebcce81
caps.latest.revision: 32
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddca5ab4b0d7dc6aa43f3db8c641ad5fc9e583b2
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735188"
---
# <a name="inside-the-editor"></a>Wewnątrz edytora
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Edytor składa się z liczbą różne podsystemy, które pozwalają zapobiec edytora tekstu modelu oddzielne widoku tekstu i interfejsu użytkownika.  
  
 W tych sekcjach opisano różne aspekty Edytor:  
  
- [Omówienie podsystemów](../extensibility/inside-the-editor.md#overview)  
  
- [Model tekstu](../extensibility/inside-the-editor.md#textmodel)  
  
- [Widok tekstu](../extensibility/inside-the-editor.md#textview)  
  
  W tych sekcjach opisano funkcje edytora:  
  
- [Znaczniki i klasyfikatorów](../extensibility/inside-the-editor.md#tagsandclassifiers)  
  
- [Zakończeń](../extensibility/inside-the-editor.md#adornments)  
  
- [Projekcja](../extensibility/inside-the-editor.md#projection)  
  
- [Obramowanie](../extensibility/inside-the-editor.md#outlining)  
  
- [Powiązania myszy](../extensibility/inside-the-editor.md#mousebindings)  
  
- [Operacje edytora](../extensibility/inside-the-editor.md#editoroperations)  
  
- [Funkcja IntelliSense](../extensibility/inside-the-editor.md#intellisense)  
  
##  <a name="overview"></a> Omówienie podsystemów  
  
### <a name="text-model-subsystem"></a>Podsystem modelu tekstu  
 Podsystem modelu tekstu jest odpowiedzialny za reprezentowania tekstu i włączając jego manipulacji. Podsystem modelu tekst zawiera <xref:Microsoft.VisualStudio.Text.ITextBuffer> interfejs, który opisuje sekwencji znaków, który ma być wyświetlana przez edytor. Ten tekst można modyfikować, śledzone i inny sposób modyfikować na wiele sposobów. Model tekst zawiera także typy następujące aspekty:  
  
- Usługa, która kojarzy tekstu z plików i zarządza odczytywania i zapisywania ich w systemie plików.  
  
- Różnicowe usługa, która umożliwia znalezienie minimalny różnice między dwoma sekwencjami obiektów.  
  
- System do opisywania tekstu w buforze pod względem podzbiorem tekstu w innych buforów.  
  
  Podsystem modelu tekstu jest bezpłatny pojęcia dotyczące interfejsu użytkownika. Na przykład nie jest odpowiedzialny za formatowania tekstu lub układu tekstu, a następnie go nie zna visual zakończeń, które mogą być skojarzone z tekstem.  
  
  Typy publiczne podsystemu modelu tekstu są zawarte w Microsoft.VisualStudio.Text.Data.dll i Microsoft.VisualStudio.CoreUtilitiy.dll, które być zależne tylko od biblioteki klasy bazowej programu .NET Framework i Managed Extensibility Framework (MEF).  
  
### <a name="text-view-subsystem"></a>Podsystem widoku tekstu  
 Podsystem widoku tekstu jest odpowiedzialny za formatowania i wyświetlania tekstu. Typy w tym podsystemu są podzielone na dwie warstwy, w zależności od tego, czy typy polegają na Windows Presentation Foundation (WPF). Najważniejsze typy są <xref:Microsoft.VisualStudio.Text.Editor.ITextView> i <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextView>, które kontrolują zestaw wierszy tekstu, które mają być wyświetlane i również karetki, wybór i urządzenia adorning tekst przy użyciu elementów interfejsu użytkownika WPF. Podsystem ten znajdują się również obszar wyświetlania marginesy wokół tekstu. Marginesy te można rozszerzyć i może zawierać różne rodzaje efekty zawartości i visual. Przykłady marginesy wiersza numer Wyświetla i pasków przewijania.  
  
 Typy publiczne podsystemu widoku tekstu są zawarte w Microsoft.VisualStudio.Text.UI.dll i Microsoft.VisualStudio.Text.UI.Wpf.dll. Pierwszy zestaw zawiera elementy niezależne od platformy, a drugi zawiera elementy specyficzne dla programu WPF.  
  
### <a name="classification-subsystem"></a>Podsystem klasyfikacji  
 Podsystem klasyfikacji jest odpowiedzialny za sprawdzenie właściwości czcionki dla tekstu. Klasyfikator dzieli tekst na różnych klas, na przykład, "słowo kluczowe" lub "comment". Mapa formatu klasyfikacji dotyczy tych klas właściwości czcionki rzeczywiste, na przykład "niebieski Consolas 10 (czas pacyficzny)". Te informacje są używane w widoku tekstu, gdy formatuje i powoduje wyświetlenie tekstu. Tagowanie, który jest opisany bardziej szczegółowo w dalszej części tego tematu, umożliwia danych ma zostać skojarzony z zakresami tekstu.  
  
 Typy publiczne podsystemu klasyfikacji są zawarte w Microsoft.VisualStudio.Text.Logic.dll i interakcji z visual aspekty klasyfikacji, które są zawarte w Microsoft.VisualStudio.Text.UI.Wpf.dll.  
  
### <a name="operations-subsystem"></a>Podsystem działania  
 Podsystem działania definiuje zachowanie edytora. Udostępnia implementację dla poleceń edytora programu Visual Studio i systemie cofania.  
  
## <a name="a-closer-look-at-the-text-model-and-the-text-view"></a>Bliższe spojrzenie na modelu tekstu i widoku tekstu  
  
###  <a name="textmodel"></a> Model tekstu  
 Podsystem modelu tekstu składa się z różnych grup z typów tekstu. Obejmują one bufor tekstowy, migawek tekstu i zakresy tekstu.  
  
#### <a name="text-buffers-and-text-snapshots"></a>Bufory tekstu i migawek tekstu  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> Interfejs reprezentuje sekwencję znaków Unicode, które są zakodowane przy użyciu UTF-16, czyli kodowanie używane przez `String` typ w .NET Framework. Bufor tekstowy może być utrwalony jako dokument systemu plików, ale nie jest to wymagane.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBufferFactoryService> Służy do tworzenia buforu pusty tekst lub bufor tekstowy, który jest inicjowany z ciągu lub <xref:System.IO.TextReader>. Bufor tekstowy mogą zostać utrwalone w systemie plików jako <xref:Microsoft.VisualStudio.Text.ITextDocument>.  
  
 Bufor tekstowy mogą być edytowane w żadnym z wątków, aż wątek przejmuje na własność buforu tekstowego, wywołując <xref:Microsoft.VisualStudio.Text.ITextBuffer.TakeThreadOwnership%2A>. Po tym tylko tym wątku można dokonać edycji.  
  
 Bufor tekstowy może przejść przez wiele wersji jego okres istnienia. Nowa wersja jest generowana za każdym razem, gdy edytowany jest buforu, a niezmienne <xref:Microsoft.VisualStudio.Text.ITextSnapshot> reprezentuje zawartość tej wersji buforu. Ponieważ migawek tekstu są niezmienne, są dostępne migawki tekst na żadnym z wątków, bez ograniczeń, nawet wtedy, gdy bufor tekstowy, który reprezentuje podlega zmianom.  
  
#### <a name="text-snapshots-and-text-snapshot-lines"></a>Migawek tekstu i wierszy migawek tekstu  
 Zawartość migawki tekstu można wyświetlić jako sekwencja znaków lub sekwencja wierszy. Znaki i wiersze są indeksowane zarówno, począwszy od zera. Migawka pusty tekst zawiera zero znaków i jeden pusty wiersz. Wiersz jest rozdzielany przez dowolne prawidłowe sekwencje znaków Unicode podział wiersza lub początek lub koniec buforu. Znaki końca wiersza są jawnie reprezentowane w migawce tekstu i podziały wierszy w migawce tekst nie wszystkie muszą być takie same.  
  
> [!NOTE]
>  Aby uzyskać więcej informacji na temat znaki podziału wiersza w edytorze programu Visual Studio, zobacz [kodowania i podziały wierszy](../ide/encodings-and-line-breaks.md).  
  
 Wiersz tekstu jest reprezentowany przez <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> obiektu, który można uzyskać z migawki tekst, numeru wiersza określonego lub stanowiska określonego znaku.  
  
#### <a name="snapshotpoints-snapshotspans-and-normalizedsnapshotspancollections"></a>Elementy Snapshotpoint SnapshotSpans i NormalizedSnapshotSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.SnapshotPoint> odpowiada pozycji znaku w migawce. Pozycja jest gwarantowane przypadać między zero a długość migawki. A <xref:Microsoft.VisualStudio.Text.SnapshotSpan> reprezentuje fragment tekstu w migawce. Jego pozycja końcowa jest gwarantowane przypadać między zero a długość migawki. <xref:Microsoft.VisualStudio.Text.NormalizedSnapshotSpanCollection> Składa się z szeregu <xref:Microsoft.VisualStudio.Text.SnapshotSpan> obiekty z tym samym migawki.  
  
#### <a name="spans-and-normalizedspancollections"></a>Zakresy i NormalizedSpanCollections  
 A <xref:Microsoft.VisualStudio.Text.Span> reprezentuje interwału, który można zastosować do tekstu w migawce tekstu. Pozycje migawki, są liczony od zera, więc zakresy można uruchomić w dowolnym miejscu, w tym zero. `End` Właściwość zakresu jest równy sumie jego `Start` właściwości i jego `Length` właściwości. A `Span` nie zawiera znaku, która jest indeksowana przy `End` właściwości. Na przykład zakres zawierający Start = 5, a długość = 3 ma End = 8, i zawiera znaki w pozycji 5, 6 i 7. Ten zakres jest 5..8).  
  
 Dwa zakresy intersect, jeśli mają one żadnych pozycji w tym pozycja końcowa. W związku z tym, część wspólną [3, 5) i [2, 7) jest [3, 5) i część wspólną [3, 5) i [5, 7) jest [5, 5). (Zwróć uwagę, że [5, 5) jest pusty zakres.)  
  
 Dwa zakresy nakładają się, jeśli mają one pozycji, z wyjątkiem pozycja końcowa. Pusty zakres nigdy nie nakłada się inne zakres i nakładanie się dwa zakresy nigdy nie jest pusty.  
  
 Element <xref:Microsoft.VisualStudio.Text.NormalizedSpanCollection> znajduje się lista zakresy według właściwości rozpoczęcia zakresów. Na liście zachodzącymi na siebie lub zakresy są scalane. Na przykład, biorąc pod uwagę zestaw zakresy [5..9), [0..1), [3..6), i [9..10), znormalizowana listy zakresów jest [0..1), [3..10).  
  
#### <a name="itextedit-textversion-and-text-change-notifications"></a>ITextEdit, TextVersion i powiadomień o zmianie tekstu  
 Zawartość buforu tekstowego można zmienić za pomocą <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu. Utworzenie takiego obiektu (przy użyciu jednej z `CreateEdit()` metody <xref:Microsoft.VisualStudio.Text.ITextBuffer>) rozpoczyna się transakcji tekst, który składa się z tekstowych. Każdy edytowanie zastępuje niektóre zakres tekstu w buforze przez ciąg. Współrzędne i zawartości każdej edycji są wyrażone względem migawki buforu, gdy transakcja została uruchomiona. <xref:Microsoft.VisualStudio.Text.ITextEdit> Obiektu dostosowuje współrzędne edycje, których dotyczy innych zmian w tej samej transakcji.  
  
 Na przykład należy wziąć pod uwagę bufor tekstowy, który zawiera ten ciąg:  
  
```  
abcdefghij  
```  
  
 Stosowanie transakcji, który zawiera dwie zmiany, jedna Edycja zastępujący zakresu w [2..4) za pomocą znaku `X` i drugiej edycji, zastępujący zakres na [6..9) za pomocą znaku `Y`. Wynik jest tego buforu:  
  
```  
abXefYj  
```  
  
 Współrzędne do drugiej edycji zostały obliczone względem zawartości buforu na początku transakcji, przed zastosowaniem pierwsza edycja.  
  
 Zmiany w buforze wprowadzone podczas <xref:Microsoft.VisualStudio.Text.ITextEdit> stawia obiektu przez wywołanie jego `Apply()` metody. Jeśli wystąpił co najmniej jeden niepusty edycji, nowy <xref:Microsoft.VisualStudio.Text.ITextVersion> jest tworzony nowy <xref:Microsoft.VisualStudio.Text.ITextSnapshot> zostanie utworzony i jeden `Changed` zdarzenie jest wywoływane. Każda wersja tekst ma inny tekst migawki. Migawka tekst reprezentuje pełną stan buforu tekstowego po edycji transakcji, ale to tekstowa wersja kwestii opisano tylko zmiany z jedną migawkę do następnego. Ogólnie rzecz biorąc migawek tekstu są przeznaczone do jednorazowego użytku i następnie zostaje odrzucone, natomiast wersjach tekstu musi pozostać aktywne przez pewien czas.  
  
 Zawiera to tekstowa wersja kwestii <xref:Microsoft.VisualStudio.Text.INormalizedTextChangeCollection>. Ta kolekcja zawiera opis zmian, po zastosowaniu do migawki, dadzą kolejne migawki. Każdy <xref:Microsoft.VisualStudio.Text.ITextChange> w kolekcji zawiera pozycji znaku zmian, zamienianym ciągu i w ciągu zamiennym. Zamienianym ciągu jest pusta dla podstawowych wstawiania, a ciąg zastępujący jest pusta dla podstawowych usunięcia. Znormalizowana kolekcji jest zawsze `null` dla najbardziej aktualną wersję bufor tekstowy.  
  
 Tylko jeden <xref:Microsoft.VisualStudio.Text.ITextEdit> obiekt może być utworzone dla bufora tekstowego w dowolnym momencie, a wszystkie zmiany tekstu, należy wykonać w wątku, który jest właścicielem bufor tekstowy (jeśli została odebrana własność). Zmiana w tekście porzucone, wywołując jego `Cancel` metody lub jej `Dispose` metody.  
  
 <xref:Microsoft.VisualStudio.Text.ITextBuffer> udostępnia również `Insert()`, `Delete()`, i `Replace()` metody, które przypominają te znalezione na <xref:Microsoft.VisualStudio.Text.ITextEdit> interfejsu. Wywoływanie tych działa tak samo jak podczas tworzenia <xref:Microsoft.VisualStudio.Text.ITextEdit> obiektu, podobne wywołania, a następnie zastosowanie edycji.  
  
#### <a name="tracking-points-and-tracking-spans"></a>Punkty śledzenia i śledzenie zakresy  
 <xref:Microsoft.VisualStudio.Text.ITrackingPoint> Odpowiada pozycji znaku w buforze tekstu. W przypadku modyfikacji buforu w sposób, który powoduje, że położenie znaku, aby przesunąć punkt śledzenia przenosi się z nim. Na przykład jeśli punkt śledzenia, który odwołuje się do pozycji 10 w buforze, a następnie dodaje się pięć znaków od początku buforu, punkt śledzenia następnie odnosi się do pozycji 15. W przypadku wstawiania w dokładnie określonym położeniu wskazywane przez punkt śledzenia, jego zachowanie zależy od jego <xref:Microsoft.VisualStudio.Text.PointTrackingMode>, który może być `Positive` lub `Negative`. Jeśli tryb śledzenia jest dodatnia, punkt śledzenia, który odwołuje się do takiego samego znaku, która jest teraz na końcu wstawiania; Jeśli tryb śledzenia jest ujemna, punkt śledzenia odnosi się do pierwszego znaku wstawiony w oryginalnym położeniu. Jeśli znak na pozycji, która jest reprezentowana przez punkt śledzenia zostanie usunięty, punkt śledzenia przenosi do pierwszego znaku, który następuje po usuniętego zakresu. Na przykład jeśli punkt śledzenia, który odwołuje się do znaku w pozycji 5 i zostaną usunięte znaki w pozycjach 3 – 6, punkt śledzenia odnosi się do znaku na pozycji 3.  
  
 <xref:Microsoft.VisualStudio.Text.ITrackingSpan> Przedstawia szeroką gamę znaków, a nie tylko jedną pozycję. Jego zachowanie zależy od jego <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>. Jeśli tryb zakresu śledzenia <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, zakres śledzenia rozszerza się, aby dołączyć tekst wstawiony w jego krawędzi; Jeśli tryb zakresu śledzenia <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, zakres śledzenia zawierają tekst wstawiony na jego krawędzi. Jednak jeśli tryb zakresu śledzenia <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, wstawiania wypychanie bieżącej pozycji do początku i, jeśli tryb zakresu śledzenia <xref:Microsoft.VisualStudio.Text.SpanTrackingMode>, wstawiania wypychanie bieżącej pozycji do końca.  
  
 Wszystkie migawki buforu tekstowego, do których one należą, możesz uzyskać położenie punktu śledzenia lub zakresu zakres śledzenia. Punkty śledzenia i śledzenie zakresy mogą bezpiecznie odwoływać się z żadnym z wątków.  
  
#### <a name="content-types"></a>Typy zawartości  
 Typy zawartości to mechanizm służący do definiowania różnych typów zawartości. Typ zawartości może być typu pliku, takie jak "text", "code" lub "binary" lub typ technologii, np. "xml", "vb" lub "c#". Na przykład wyraz "using" jest słowem kluczowym w językach C# i Visual Basic, ale nie w innych językach programowania. W związku z tym definicja tego słowa kluczowego będzie ograniczona do typów zawartości "c#" i "vb".  
  
 Typy zawartości są używane jako filtr dla zakończeń i innych elementów w edytorze. Wiele funkcji edytora i punktów rozszerzeń, które są zdefiniowane dla typu zawartości; na przykład tekst kolorowanie różni się plikami ze zwykłym tekstem, pliki XML i pliki kodu źródłowego języka Visual Basic. Bufory tekstu ogólnie są przypisywane typu zawartości, są one tworzone, gdy typ zawartości buforu tekstowego można zmienić.  
  
 Typy zawartości wielu — dziedziczenie z innych typów zawartości. <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> Pozwala określić wiele typów podstawowych jako nadrzędne danego typu zawartości.  
  
 Deweloperzy mogą definiować własne typy zawartości i zarejestruj je przy użyciu <xref:Microsoft.VisualStudio.Utilities.IContentTypeRegistryService>. Wiele funkcji w edytorze można zdefiniować w odniesieniu do określonego typu zawartości przy użyciu <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute>. Na przykład marginesy edytora, zakończeń i obsługi myszy można zdefiniować tak, aby dotyczyły tylko do edytory, które wyświetlają określone typy zawartości.  
  
###  <a name="textview"></a> Widok tekstu  
 Part widok wzorca model view controller (MVC) definiuje widoku tekstu formatowanie widok, elementów graficznych, takich jak pasek przewijania i karetki. Wszystkie elementy prezentacji w edytorze programu Visual Studio są oparte na WPF.  
  
#### <a name="text-views"></a>Widoki tekstowe  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextView> Interfejs jest niezależny od platformy reprezentacja widoku tekstu. Jest używana głównie w celu wyświetlenia dokumentów tekstowych w oknie, ale może również służyć do innych celów, na przykład w etykietce narzędzia.  
  
 Widok tekstu odwołuje się do różnych rodzajów buforów tekstu. <xref:Microsoft.VisualStudio.Text.Editor.ITextView.TextViewModel%2A> Właściwość odwołuje się do <xref:Microsoft.VisualStudio.Text.Editor.ITextViewModel> obiektu, który wskazuje na tych trzech buforów inny tekst: bufor danych, który jest najważniejsze bufora poziom danych, bufor edycji, w którym Edycja występuje i visual bufora, który jest buforu, który jest wyświetlane w widoku tekstu.  
  
 Tekst jest sformatowany w oparciu o klasyfikatorów, które są dołączone do podstawowej bufor tekstowy i jest powiązany za pomocą dostawców zakończeń, które są dołączone do samego widoku tekstu.  
  
#### <a name="the-text-view-coordinate-system"></a>System współrzędnych widoku tekstu  
 System współrzędnych widoku tekstu określa pozycje w widoku tekstu. W tym układzie współrzędnych x wartość 0.0 odnosi się do lewej krawędzi tekstu wyświetlanego, a wartość y 0.0 odnosi się do górnej krawędzi tekst jest wyświetlany. Współrzędna x zwiększa od lewej do prawej, a współrzędna y zwiększa od góry do dołu.  
  
 Okienko ekranu (część tekstu widoczne w oknie tekstowym) nie mogą być przewijane w taki sam sposób w poziomie zgodnie z jest przewijane w pionie. Okienko ekranu jest przewijane w poziomie, zmieniając jego lewą współrzędną, tak aby przemieszczał się w odniesieniu do powierzchni do rysowania. Jednak okienko ekranu może być przewijana pionowo zmieniając renderowanego tekstu, co powoduje, że <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged> zdarzenia.  
  
 Odległość w układzie współrzędnych odpowiadają logiczne pikseli. Po wyświetleniu powierzchnię renderowania tekstu bez skalowania przekształcenia jednej jednostki w układzie współrzędnych renderowanie tekstu odnosi się do jednego piksela na ekranie.  
  
#### <a name="margins"></a>Marginesy  
 <xref:Microsoft.VisualStudio.Text.Editor.ITextViewMargin> Interfejs reprezentuje margines i umożliwia kontrolowanie widoczności marginesu oraz jego rozmiaru. Istnieją cztery marginesy wstępnie zdefiniowanych, które są nazywane "Top", "Po lewej", "Right" i "Dolnej" i są dołączone do góry, dolnemu, lewemu lub prawej krawędzi widoku. Marginesy te są kontenery, w których można umieścić inne marginesy. Interfejs definiuje metody zwracające rozmiar marginesu i widoczność margines. Marginesy są elementy wizualne, które zapewniają dodatkowe informacje na temat widoku tekstu, do której są dołączone. Na przykład margines numer wiersza Wyświetla numery wierszy w widoku tekstu. Na marginesie symbol Wyświetla elementy interfejsu użytkownika.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewMarginProvider> Interfejs obsługuje tworzenie i umieszczania marginesy. Marginesy może zostać określona w odniesieniu do innych marginesy. Marginesy o wyższym priorytecie są znajduje się bliżej do widoku tekstu. Na przykład jeśli istnieją dwa marginesy po lewej stronie, A i B margines margines B ma niższy priorytet niż marginesu, marża B pojawi się do lewego marginesu A.  
  
#### <a name="the-text-view-host"></a>Host widoku tekstu  
 <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Interfejs zawiera widok tekstu i stykających dekoracje, dołączone do widoku, na przykład paski przewijania. Host widoku tekstu zawiera także marginesy, które są dołączone do obramowania widoku.  
  
#### <a name="formatted-text"></a>Tekst sformatowany  
 Tekst, który jest wyświetlany w widoku tekstu składa się z <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> obiektów. Każdy wiersz w widoku tekstu odnosi się do jednego wiersza tekstu w widoku tekstu. Długie wiersze w buforze tekstu podstawowego można być częściowo zasłonięte (Jeśli nie włączono zawijanie wyrazów) lub podzielić na wiele wierszy w widoku tekstu. <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> Interfejs zawiera metody i właściwości dla mapowania między współrzędnych i znaki i zakończeń, które mogą być skojarzone z wiersza.  
  
 <xref:Microsoft.VisualStudio.Text.Formatting.ITextViewLine> obiekty są tworzone za pomocą <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> interfejsu. Jeśli po prostu zajmującym się tekst, który jest aktualnie wyświetlany w widoku, możesz zignorować źródło formatowania. Jeśli interesuje Cię w formacie tekstu, który nie jest wyświetlane w widoku (na przykład do obsługi Wytnij tekst sformatowany i wkleić), możesz użyć <xref:Microsoft.VisualStudio.Text.Formatting.IFormattedLineSource> formatowania tekstu w buforze tekstu.  
  
 Widok tekstu Formatuje jedną <xref:Microsoft.VisualStudio.Text.ITextSnapshotLine> w danym momencie.  
  
## <a name="editor-features"></a>Funkcje edytora  
 Funkcje edytora zaprojektowano tak, aby definicji funkcji jest oddzielony od implementacji. Edytor zawiera następujące funkcje:  
  
-   Znaczniki i klasyfikatorów  
  
-   Zakończeń  
  
-   Rzut  
  
-   Tworzenie konspektu  
  
-   Mysz i klucz powiązania  
  
-   Operacje i w nim elementów podstawowych  
  
-   IntelliSense  
  
###  <a name="tagsandclassifiers"></a> Znaczniki i klasyfikatorów  
 Tagi są znaczniki, które są skojarzone z tekstu. Mogły być wyświetlane na różne sposoby, na przykład za pomocą kolorowania tekstu, podkreślenia, grafiki lub wyskakujących okienek. Klasyfikatorów są jednego rodzaju tagu.  
  
 Inne rodzaje znaczniki są <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag> wyróżnianie tekstu, <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> tworzenia konspektów, i <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag> błędy kompilacji.  
  
#### <a name="classification-types"></a>Typy klasyfikacji  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationType> Interfejs reprezentuje klasę równoważności, który jest abstrakcyjny kategorii tekstu. Typy klasyfikacji wielu — dziedziczenie z innych typów klasyfikacji. Na przykład klasyfikacji języka programowania może zawierać "— słowo kluczowe", "comment" i "identyfikator", które dziedziczą z "code". Język naturalny typy klasyfikacji mogą obejmować "rzeczownik", "verb" i "przymiotnik", które dziedziczą z "języka naturalnego".  
  
#### <a name="classifications"></a>Klasyfikacje  
 Klasyfikacji jest wystąpieniem typu określonej klasyfikacji, zwykle za pośrednictwem zakres tekstu. Element <xref:Microsoft.VisualStudio.Text.Classification.ClassificationSpan> jest używana do reprezentowania klasyfikacji. Zakres klasyfikacji można traktować jako etykietę, która obejmuje określoną zakres tekstu i informuje system, który ten zakres tekstu jest typu określonej klasyfikacji.  
  
#### <a name="classifiers"></a>Klasyfikatorów  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> To mechanizm, który dzieli tekst na zbiór klasyfikacji. Klasyfikatorów musi być zdefiniowany dla określonych typów zawartości i wystąpienia dla buforów określonym tekstem. Klienci muszą implementować <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> do wzięcia udziału w klasyfikacji tekstu.  
  
#### <a name="classifier-aggregators"></a>Klasyfikator agregatorów  
 Agregator Klasyfikator to mechanizm, który łączy wszystkie klasyfikatorów buforu tekstowego tylko jeden zestaw klasyfikacji. Na przykład klasyfikatora C# i klasyfikatora języka angielskiego utworzyć klasyfikacje za pośrednictwem komentarz w pliku C#. Należy wziąć pod uwagę ten komentarz:  
  
```  
// This method produces a classifier  
```  
  
 Klasyfikator C# może oznaczyć całego zakresu jako komentarz i klasyfikatora języka angielskiego może sklasyfikować "generuje" jako "czasownik" i "method" jako "rzeczownik". Agregator tworzy zbiór nienakładających klasyfikacje, a typ zestawu opiera się na wszystkie współtworzone elementy.  
  
 Agregatora klasyfikatora jest również klasyfikatora, ponieważ przerywa tekstu do zestawu z klasyfikacji. Agregator klasyfikatora gwarantuje również, że nie istnieją żadne nakładających się klasyfikacje i sortowania klasyfikacje. Poszczególne klasyfikatorów są bezpłatne do zwrócenia dowolny zbiór klasyfikacje, w dowolnej kolejności i nakładających się w dowolny sposób.  
  
#### <a name="classification-formatting-and-text-coloring"></a>Kolorowanie tekstu i formatowania klasyfikacji  
 Formatowanie tekstu jest przykładem funkcja, która jest oparta na klasyfikacji tekstu. Jest używana przez warstwę widoku tekstu do określenia sposobu wyświetlania tekstu w aplikacji. Obszar formatowania tekstu jest zależny od WPF, ale logiczne definicja klasyfikacji nie jest.  
  
 Format klasyfikacji to zbiór właściwości dla typu określonej klasyfikacji formatowania. Te formaty dziedziczą z formatu elementu nadrzędnego typu klasyfikacji.  
  
 <xref:Microsoft.VisualStudio.Text.Classification.IClassificationFormatMap> Mapowanie z typu klasyfikacji do zestawu właściwości formatowania tekstu. Implementacja Mapa formatu w edytorze obsługuje wszystkich eksporty formatów klasyfikacji.  
  
###  <a name="adornments"></a> Zakończeń  
 Zakończeń są efekty graficzne, które nie są bezpośrednio związane z czcionek i kolorów, znaków w widoku tekstu. Na przykład podkreślenie czerwona fala, który służy do oznaczania — kompilowanie kodu w wielu językach programowania jest osadzony zakończeń i etykietki narzędzi są wyskakujące zakończeń. Zakończeń są uzyskiwane z <xref:System.Windows.UIElement> i zaimplementować <xref:Microsoft.VisualStudio.Text.Tagging.ITag>. Istnieją dwa typy specjalne tag zakończeń <xref:Microsoft.VisualStudio.Text.Tagging.SpaceNegotiatingAdornmentTag>, dla skojarzenia, które zajmują się tą samą przestrzenią jako tekst w widoku i <xref:Microsoft.VisualStudio.Text.Tagging.ErrorTag>, dla podkreślenia wężyk.  
  
 Osadzony zakończeń są grafiki, które stanowią część widoku tekstu sformatowanego. Są zorganizowane w różnych warstwach porządku osi Z. Istnieją trzy warstwy wbudowane, w następujący sposób: tekst, karetki i zaznaczenia. Jednakże deweloperzy mogą zdefiniować większej liczbie warstw i umieść je w kolejności, w odniesieniu do siebie nawzajem. Trzy rodzaje zakończeń osadzone są zakończeń tekstu powiązane z wątkiem, (które przeniesienie, gdy tekst i są usuwane po usunięciu tekst), zakończeń Wyświetl powiązane z wątkiem, (które mają na celu innymi niż tekstowe części widoku) i kontrolowane przez właściciela zakończeń ( Deweloper musi zarządzać ich umieszczania).  
  
 Wyskakujące zakończeń są grafiki, które są wyświetlane w małym oknie powyżej widoku tekstu, na przykład etykietek narzędzi.  
  
###  <a name="projection"></a> Projekcja  
 Projekcja jest techniką tworzenia inny rodzaj buforu tekstu, który nie przechowuje tekst, ale zamiast tego łączy tekstu z innych buforów tekstu. Na przykład buforu projekcji można połączyć tekst z dwóch innych buforów i przedstawi wynik, tak jak w przypadku w buforze tylko jeden lub ukrycia fragmenty tekstu w buforze jeden. Bufor projekcji może działać jako bufor źródłowy do innego buforu projekcji. Zbiór buforów, które są powiązane przez projekcję można skonstruować tak, aby zmienić tekst na wiele różnych sposobów. (Taki zestaw jest również nazywany *wykres buforu*.) Funkcję tworzenia konspektów tekstu Visual Studio jest implementowany przy użyciu buforu projekcji ukryć zwinięty tekst i Edytor programu Visual Studio dla stron ASP.NET używa projekcji o obsłudze języków osadzone, takie jak Visual Basic i C#.  
  
 <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBuffer> Jest tworzona przy użyciu <xref:Microsoft.VisualStudio.Text.Projection.IProjectionBufferFactoryService>. Bufor projekcji jest reprezentowany przez uporządkowana sekwencja <xref:Microsoft.VisualStudio.Text.ITrackingSpan> obiektów, które są znane jako *źródła zakresy*. Zawartość tych zakresów są uporządkowane jako sekwencja znaków. Bufory tekstu, z których są rysowane zakresy źródłowych są nazywane *źródła buforów*. Klienci buforu projekcji nie muszą wiedzieć, że różni się od buforu zwykły tekst.  
  
 Bufor projekcji nasłuchuje zdarzeń zmiany tekstu w bufory źródła. W przypadku tekstu w źródle obejmują zmiany, buforu projekcji mapuje współrzędne zmieniony tekst do jego własnej współrzędnych i wywołuje zdarzenia odpowiednie zmiany tekstu. Na przykład należy wziąć pod uwagę bufory źródła A i B, które mają następującą zawartość:  
  
```  
A: ABCDE  
B: vwxyz  
```  
  
 Jeśli bufor projekcji P jest tworzony na podstawie dwa zakresy tekstu, taki, który zawiera wszystkie buforu i innych zawierający wszystkie buforu B, P ma następującą zawartość:  
  
```  
P: ABCDEvwxyz  
```  
  
 Jeśli podciąg `xy` są usuwane z buforu B, a następnie buforu P wywołuje zdarzenie, które wskazuje, że zostały usunięte znaki w pozycjach 7 i 8.  
  
 Bufor projekcji można także bezpośrednio edytować. Propaguje on zmiany do buforów odpowiedniego źródła. Na przykład jeśli ciąg jest wstawiany do buforu P na pozycji 6 (początkowe położenie znaków "v"), wstawianie jest propagowany do buforu B na pozycji 1.  
  
 Ma ograniczeń dotyczących zakresów źródła, które przyczyniają się do buforu projekcji. Zakresy źródła nie może nakładać się na; lokalizację w buforze projekcji nie można zamapować na więcej niż jedną lokalizację w buforze dowolnego źródła i lokalizację w bufor źródłowy nie można zamapować na więcej niż jedną lokalizację w buforze projekcji. Circularities nie są dozwolone w relacji bufor źródłowy.  
  
 Zdarzenia są wywoływane, gdy zestaw źródłowy buforuje zmian buforu projekcji i zestaw źródłowy obejmuje zmiany.  
  
 Bufor pominięcia jest specjalny rodzaj rzutowania buforu. Służy przede wszystkim dla konspekt i operacji, które rozwijać i zwijać bloków tekstu. Bufor pominięcia opiera się na tylko jeden bufor źródłowy i zakresy w buforze pominięcia muszą być uporządkowane takie same jak są one uporządkowane w buforze źródłowym.  
  
##### <a name="the-buffer-graph"></a>Na wykresie buforu  
 <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraph> Interfejs umożliwia mapowanie między wykres buforów projekcji. Wszystkie bufory tekstu i bufory projekcji są zbierane w skierowanym grafie acyklicznym, podobnie jak drzewo abstrakcyjnej składni, który jest produkowany przez kompilator języka. Wykres jest definiowany przez najważniejszych buforu, który może być dowolnym bufor tekstowy. Na wykresie buforu można mapować z punktem w górnym buforu do punktu w bufor źródłowy lub zakres w buforze najważniejsze zestaw zakresów bufor źródłowy. Podobnie możesz zmapować punkt lub równy od bufor źródłowy do punktu w górnym buforu. Wykresy buforu są tworzone za pomocą <xref:Microsoft.VisualStudio.Text.Projection.IBufferGraphFactoryService>.  
  
##### <a name="events-and-projection-buffers"></a>Zdarzenia i bufory projekcji  
 Po zmodyfikowaniu buforu projekcji, zmiany są wysyłane z buforu projekcji do buforów, które od niego zależne. Po zmodyfikowaniu wszystkie bufory bufora zmiany zdarzenia są wywoływane, począwszy od najgłębiej zagnieżdżoną buforu.  
  
###  <a name="outlining"></a> Tworzenie konspektu  
 Konspekt jest możliwość rozwijać i zwijać różne bloki tekstu w widoku tekstu. Konspekt jest zdefiniowany jako rodzajem elementu <xref:Microsoft.VisualStudio.Text.Tagging.ITag>, w taki sam sposób, jak zdefiniowano zakończeń. Element <xref:Microsoft.VisualStudio.Text.Tagging.OutliningRegionTag> jest znacznikiem, który definiuje region tekstu, który można rozwijać i zwijać. Aby użyć konspektu, należy zaimportować <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManagerService> można pobrać <xref:Microsoft.VisualStudio.Text.Outlining.IOutliningManager>. Menedżer konspektu wylicza zwija i rozwija różne bloki, które są reprezentowane jako <xref:Microsoft.VisualStudio.Text.Outlining.ICollapsible> obiektów i w związku z tym wywołuje zdarzenia.  
  
###  <a name="mousebindings"></a> Powiązania myszy  
 Powiązania myszy połączyć różne polecenia ruchów myszy. Powiązania myszy są zdefiniowane przy użyciu <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessorProvider>, i klawiszy są definiowane za pomocą <xref:Microsoft.VisualStudio.Text.Editor.IKeyProcessorProvider>. <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewHost> Automatycznie tworzy wszystkie powiązania i łączy je z zdarzeń myszy w widoku.  
  
 <xref:Microsoft.VisualStudio.Text.Editor.IMouseProcessor> Interfejs zawiera procedury obsługi zdarzeń przetwarzania wstępnego i po przetwarzaniu dla zdarzeń myszy. Obsługiwać jednego ze zdarzeń, możesz zastąpić niektóre metody w <xref:Microsoft.VisualStudio.Text.Editor.MouseProcessorBase>.  
  
###  <a name="editoroperations"></a> Operacje edytora  
 Przestała może służyć do automatyzowania interakcji z edytora, skryptów lub w innych celach. Możesz zaimportować <xref:Microsoft.VisualStudio.Text.Operations.IEditorOperationsFactoryService> do dostępu do operacji w danym <xref:Microsoft.VisualStudio.Text.Editor.ITextView>. Te obiekty służy następnie do modyfikowania zaznaczenia, przewiń w widoku lub Przesuń karetkę do różnych części widoku.  
  
###  <a name="intellisense"></a> Funkcja IntelliSense  
 Technologia IntelliSense obsługuje uzupełniania instrukcji, pomocy dotyczącej sygnatur (nazywane również informacje o parametrach), szybkie informacje i żarówki.  
  
 Dokańczanie instrukcji zawiera wyskakującego listę potencjalnych uzupełnienia dla nazwy metod, elementy XML i innych elementów kodu lub języka znaczników. Ogólnie rzecz biorąc gestu użytkownika wywołuje sesja kończenia. Sesja Wyświetla listę potencjalnych ukończenia, a użytkownik może wybrać jedną lub Odrzuć listy. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionBroker> Jest odpowiedzialny za tworzenie i wyzwalanie <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSession>. <xref:Microsoft.VisualStudio.Language.Intellisense.ICompletionSource> Oblicza <xref:Microsoft.VisualStudio.Language.Intellisense.CompletionSet> elementów uzupełniania dla sesji.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi językowej i edytora punkty rozszerzenia](../extensibility/language-service-and-editor-extension-points.md)   
 [Importy edytora](../extensibility/editor-imports.md)

