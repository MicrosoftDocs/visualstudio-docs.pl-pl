---
title: Projektant XAML — omówienie
ms.date: 03/03/2020
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: f8579a4e8088dc0fc6e7403da7f0371e46f2c928
ms.sourcegitcommit: e359b93c93c6ca316c0d8b86c2b6e566171fd1ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2020
ms.locfileid: "87507966"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML

Projektant XAML w programie Visual Studio i Blend for Visual Studio udostępnia interfejs wizualny ułatwiający projektowanie aplikacji opartych na języku XAML, takich jak WPF i platformy UWP. Możesz tworzyć interfejsy użytkownika dla aplikacji, przeciągając kontrolki z okna przybornika (okna elementów zawartości w Blend for Visual Studio) i ustawiając właściwości w okno Właściwości. Możesz również edytować XAML bezpośrednio w widoku XAML.

Użytkownicy zaawansowani mogą nawet [dostosowywać Projektant XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Program Xamarin. Forms nie obsługuje projektanta XAML. Aby wyświetlić zestaw narzędzi Xamarin. Forms w języku XAML interfejsów użytkownika i edytować je, gdy aplikacja jest uruchomiona, Użyj usługi XAML Hot reload for Xamarin. Forms. Aby uzyskać więcej informacji, zobacz stronę [Hot reload for Xamarin. Forms (wersja zapoznawcza)](/xamarin/xamarin-forms/xaml/hot-reload/) .

## <a name="xaml-designer-workspace"></a>projektant XAML obszar roboczy

Obszar roboczy w projektant XAML składa się z kilku elementów interfejsu wizualizacji. Obejmują one *obszar kompozycji* (czyli powierzchnię projektowania wizualizacji), Edytor XAML, okno konspektu dokumentu (Obiekty i oś czasu okno Blend for Visual Studio) i okno właściwości. Aby otworzyć projektant XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksplorator rozwiązań** i wybierz polecenie **Projektant widoków**.

Projektant XAML udostępnia widok XAML i zsynchronizowaną widok Projekt renderowanego znacznika języka XAML aplikacji. Gdy plik XAML jest otwarty w programie Visual Studio lub Blend for Visual Studio, można przełączać się między widok Projekt i widokiem XAML przy użyciu kart **projektowanie** i **XAML** . Możesz użyć przycisku wymiany **okienek przycisk Zamień** ![ okienka w Projektant XAML ](media/swap-panes.PNG) , aby przełączyć, które okno pojawia się na górze: obszar kompozycji lub Edytor XAML.

### <a name="design-view"></a>widok Projekt

W widok Projekt okno z obszarem roboczym jest oknem aktywnym i można go użyć jako podstawowej powierzchni roboczej. Można jej użyć do wizualnego projektowania strony w aplikacji przez dodawanie, rysowanie lub modyfikowanie elementów. Aby uzyskać więcej informacji, zobacz [Work with elementy w Projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Na tej ilustracji przedstawiono obszar kompozycji w widok Projekt.

![widok Projekt projektant XAML](media/xaml-artboard.png)

Te funkcje są dostępne w obszarze kompozycji:

**Linii wyrównania**

Linii wyrównania są *granicami wyrównania* , które są wyświetlane jako czerwone linie kreskowane, aby pokazać, gdy krawędzie formantów są wyrównane lub gdy linie bazowe tekstu są wyrównane. Granice wyrównania są wyświetlane tylko wtedy, gdy jest włączone **przyciąganie do linii wyrównania** .

**Szyny siatki**

Szyny siatki są używane do zarządzania wierszami i kolumnami w panelu [siatki](xref:Windows.UI.Xaml.Controls.Grid) . Można tworzyć i usuwać wiersze i kolumny oraz zmieniać ich względne szerokości i wysokości. Kolejka siatki pionowej, która pojawia się po lewej stronie obszaru kompozycji, jest używana w przypadku wierszy, a linia pozioma, która pojawia się u góry, jest używana na potrzeby kolumn.

**Moduły definiowania układu siatki**

Moduł definiowania układu siatki pojawia się jako Trójkąt, który ma linię pionową lub poziomą dołączoną do niej na szynze siatki. Gdy przeciągniesz moduł definiowania układu siatki, Szerokość lub wysokość sąsiadujących kolumn lub wierszy są aktualizowane podczas przesuwania myszy.

Moduły definiowania układu siatki służą do sterowania szerokością i wysokością wierszy i kolumn siatki. Możesz dodać nową kolumnę lub wiersz, klikając kolejno szyny siatki. Po dodaniu nowego wiersza lub wiersza kolumny dla panelu siatki, który ma dwie lub więcej kolumn lub wierszy, wyświetlany jest minipasek narzędzi poza szyną, która umożliwia jawne ustawienie szerokości i wysokości. Minipasek narzędzi umożliwia ustawianie opcji ustalania rozmiarów dla wierszy i kolumn siatki.

![Moduł definiowania układu siatki w projektant XAML](media/grid-adorner.png)

**Uchwyty zmiany rozmiaru**

Uchwyty zmiany rozmiaru są wyświetlane w wybranych kontrolkach i umożliwiają zmianę rozmiaru kontrolki. Zmiana rozmiaru kontrolki powoduje, że wartości szerokości i wysokości są zwykle wyświetlane w celu ułatwienia rozmiaru formantu. Aby uzyskać więcej informacji na temat manipulowania kontrolkami w widoku **projektu** , zobacz [Work with elementy in Projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Marginesy**

Marginesy reprezentują ilość miejsca stałego między krawędzią kontrolki a krawędzią jej kontenera. Marginesy kontrolki można ustawić przy użyciu właściwości [marginesu](xref:Windows.UI.Xaml.FrameworkElement.Margin) w obszarze **Układ** w oknie **Właściwości** .

**Moduły definiowania układu marginesu**

Aby zmienić marginesy elementu względem jego kontenera układu, użyj modułu definiowania marginesów. Gdy jest otwarty moduł definiowania układu marginesu, margines nie jest ustawiony, a moduł definiowania układu marginesu wyświetla przerwany łańcuch. Gdy margines nie jest ustawiony, elementy pozostają w miejscu, gdy rozmiar kontenera układu zostanie zmieniony w czasie wykonywania. Gdy moduł definiowania układu marginesu jest zamknięty, moduł definiowania układu marginesu wyświetla nieprzerwany łańcuch i elementy są przenoszone wraz z marginesem, gdy rozmiar kontenera układów jest zmieniany w czasie wykonywania (margines pozostaje ustalony).

**Uchwyty elementu**

Można zmodyfikować element przy użyciu uchwytów elementu, które pojawiają się w obszarze kompozycji po przesunięciu wskaźnika myszy nad rogi niebieskiego pola otaczającego element. Te uchwyty umożliwiają obracanie, zmienianie rozmiaru, przerzucanie, przenoszenie i dodawanie do elementu promienia narożnika. Symbol uchwytu elementu zależy od funkcji i zmian w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwytów elementu, upewnij się, że element jest zaznaczony.

W widoku **projekt** w lewym dolnym rogu okna są dostępne dodatkowe polecenia obszaru roboczego, jak pokazano poniżej:

![Polecenia widok Projekt](media/xaml-design-view-controls.png)

Te polecenia są dostępne na tym pasku narzędzi:

**Powiększenie**

Powiększenie umożliwia zmianę rozmiaru powierzchni projektowej. Możesz powiększyć od 12,5% do 800% lub wybrać opcje takie jak **Dopasuj zaznaczenie** i **Dopasuj wszystko**.

**Pokaż/Ukryj siatkę przyciągania**

Wyświetla lub ukrywa siatkę przyciągania pokazującą linie siatki. Linie siatki są używane po włączeniu **przyciągania do linii siatki** lub **przyciągania do linii wyrównania**.

**Włącz/Wyłącz przyciąganie do linii siatki**

Jeśli **przyciąganie do linii siatki** jest włączone, element jest wyrównany do najbliższej poziomej i pionowej linii siatki, gdy przeciągniesz ją na obszar kompozycji.

**Przełącz tło obszaru kompozycji**

Przełącza między jasnym i ciemnym tłem.

**Włącz/Wyłącz przyciąganie do linii wyrównania**

Linii wyrównania ułatwiają wyrównywanie formantów względem siebie. Jeśli **przyciąganie do linii wyrównania** jest włączone, gdy przeciągasz kontrolkę względem innych kontrolek, pojawiają się granice wyrównania, gdy krawędzie i tekst niektórych kontrolek są wyrównane w poziomie lub w pionie. Granica wyrównania pojawia się jako linia czerwona.

**Wyłącz kod projektu**

Wyłącza [kod projektu](debugging-or-disabling-project-code-in-xaml-designer.md), na przykład formanty niestandardowe i konwertery wartości, i ponownie ładuje projektanta.

### <a name="xaml-view"></a>Widok XAML

W widoku **XAML** okno zawierające Edytor XAML jest aktywnym oknem, a Edytor XAML jest głównym narzędziem do tworzenia. Extensible Application Markup Language (XAML) zawiera deklaratywne słownictwo oparte na języku XML do określania interfejsu użytkownika aplikacji. Widok XAML zawiera funkcje IntelliSense, automatyczne formatowanie, wyróżnianie składni i nawigowanie po tagach. Na poniższej ilustracji przedstawiono widok XAML z otwartym menu IntelliSense:

![Widok XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Okno konspektu dokumentu w programie Visual Studio jest podobne do [okna obiekty i oś czasu](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) w Blend for Visual Studio. Konspekt dokumentu ułatwia wykonywanie następujących zadań:

- Wyświetl hierarchiczną strukturę wszystkich elementów w obszarze kompozycji.

- Wybierz elementy, aby można je było modyfikować. Można na przykład przenieść je w hierarchii lub ustawić ich właściwości w okno Właściwości. Aby uzyskać więcej informacji, zobacz [Work with elementy w Projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Tworzenie i modyfikowanie szablonów dla elementów, które są kontrolkami.

- [Twórz animacje](animate-objects-in-xaml-designer.md) (tylko Blend for Visual Studio).

Aby wyświetlić okno Konspekt dokumentu w programie Visual Studio, na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Konspekt dokumentu**systemu Windows.
Aby wyświetlić okno obiekty i oś czasu w Blend for Visual Studio, na pasku menu wybierz pozycję **Wyświetl**  >  **Konspekt dokumentu**.

![Okno konspektu dokumentu w programie Visual Studio](media/document-outline-window.png)

Widok główny w oknie Konspekt dokumentu/Obiekty i oś czasu Wyświetla hierarchię dokumentu w strukturze drzewa. Można użyć hierarchicznego charakteru konspektu dokumentu do sprawdzenia dokumentu na różnych poziomach szczegółowości i zablokowania i ukrycia elementów pojedynczo lub w grupach. W oknie Konspekt dokumentu/Obiekty i oś czasu dostępne są następujące opcje:

**Pokaż/Ukryj**

Wyświetla lub ukrywa elementy obszaru roboczego. Pojawia się jako symbol oka, gdy jest wyświetlany. Możesz również nacisnąć klawisz **Ctrl** + **h** , aby ukryć element i **przesunąć** + **Ctrl** + **h** w celu wyświetlenia go.

**Zablokuj/Odblokuj**

Blokuje lub odblokowuje elementy obszaru roboczego. Nie można modyfikować zablokowanych elementów. Pojawia się jako symbol kłódki po zablokowaniu. Możesz również nacisnąć klawisz **Ctrl** + **l** , aby zablokować element i **przesunąć** + **Ctrl** + **l** , aby go odblokować.

**Zwróć zakres do pageRoot**

Opcja w górnej części okna Konspekt dokumentu/Obiekty i oś czasu, która pokazuje symbol strzałki w górę, przenosi do poprzedniego zakresu. Określanie zakresu jest stosowane tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości

Okno **Właściwości** umożliwia ustawianie wartości właściwości w kontrolkach. Oto jak wygląda:

![Okno właściwości](media/xaml-designer-properties-window.png)

Dostępne są różne opcje w górnej części okna **Właściwości** :

- Zmień nazwę aktualnie wybranego elementu w polu **Nazwa** .
- W lewym górnym rogu znajduje się ikona reprezentująca aktualnie wybrany element.
- Aby rozmieścić właściwości według kategorii lub alfabetycznie, kliknij pozycję **Kategoria**, **Nazwa**lub **Źródło** na liście **Rozmieść według** .
- Aby wyświetlić listę zdarzeń dla kontrolki, kliknij przycisk **zdarzenia** , który jest wyświetlany jako Symbol błyskawicy.
- Aby wyszukać właściwość, Zacznij od wpisania nazwy właściwości w polu wyszukiwania. Okno **Właściwości** wyświetla właściwości, które pasują do wyszukiwania podczas wpisywania.

Niektóre właściwości pozwalają ustawić zaawansowane właściwości, wybierając przycisk strzałki w dół.

Po prawej stronie każdej wartości właściwości jest *znacznik właściwości* , który jest wyświetlany jako symbol pola. Wygląd znacznika właściwości wskazuje, czy istnieje powiązanie danych lub zasób zastosowany do właściwości. Na przykład symbol białego znaku wskazuje wartość domyślną, symbol czarnego pudełka zwykle wskazuje, że zastosowano zasób lokalny, a pomarańczowe pole zazwyczaj wskazuje, że zostało zastosowane powiązanie danych. Po kliknięciu znacznika właściwości można przejść do definicji stylu, otworzyć konstruktora powiązań danych lub otworzyć selektor zasobów.

Aby uzyskać więcej informacji o używaniu właściwości i obsługi zdarzeń, zobacz [wprowadzenie do formantów i wzorców](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Zobacz także

- [Praca z elementami w projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Tworzenie i stosowanie zasobów](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Przewodnik: wiązanie z danymi w projektancie XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
