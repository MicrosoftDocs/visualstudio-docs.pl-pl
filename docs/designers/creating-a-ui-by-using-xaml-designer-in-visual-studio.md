---
title: Przegląd projektant XAML
ms.date: 07/31/2019
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
- Blend.Start.Dev12
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d0d3e6e09eaad4b8c902b6d6c6ec4d20637a6cc9
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822069"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML

Projektant XAML w programie Visual Studio i Blend for Visual Studio udostępnia interfejs wizualny ułatwiający projektowanie aplikacji opartych na języku XAML, takich jak WPF, platformy UWP i Xamarin. Forms. Możesz tworzyć interfejsy użytkownika dla aplikacji, przeciągając kontrolki z okna przybornika (okna elementów zawartości w Blend for Visual Studio) i ustawiając właściwości w okno Właściwości. Można również edytować XAML bezpośrednio w widoku XAML.

Użytkownicy zaawansowani mogą nawet [dostosowywać Projektant XAML](../extensibility/xaml-designer-extensibility-migration.md).

## <a name="xaml-designer-workspace"></a>Obszar roboczy Projektanta XAML

Obszar roboczy w Projektancie XAML składa się z kilku elementów interfejsu wizualnego. Obejmują one *obszar kompozycji* (czyli powierzchnię projektowania wizualizacji), Edytor XAML, okno konspektu dokumentu (Obiekty i oś czasu okno Blend for Visual Studio) i okno właściwości. Aby otworzyć projektanta XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksploratora rozwiązań** i wybierz polecenie **Projektant widoków**.

Projektant XAML udostępnia widok XAML i zsynchronizowany widok projektu aplikacji renderowanego kodu znaczników XAML. Gdy plik XAML jest otwarty w programie Visual Studio lub Blend for Visual Studio, można przełączać się między widok Projekt i widokiem XAML przy użyciu kart **projektowanie** i **XAML** . Możesz użyć przycisku wymiany okienek przycisk ![Zamień okienka w Projektant XAML](media/swap-panes.PNG) , aby przełączyć, które okno pojawia się na górze: obszar kompozycji lub Edytor XAML.

### <a name="design-view"></a>widok Projekt

W widok Projekt okno z obszarem roboczym jest oknem aktywnym i można go użyć jako podstawowej powierzchni roboczej. Można jej użyć do wizualnego projektowania strony w aplikacji przez dodawanie, rysowanie lub modyfikowanie elementów. Aby uzyskać więcej informacji, zobacz [Work with elementy w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md). Ta ilustracja przedstawia obszaru kompozycji w widoku Projekt.

![widok Projekt projektant XAML](../designers/media/xaml-artboard.png)

Te funkcje są dostępne w obszarze roboczym:

**Linii wyrównania**

Linii wyrównania są *granicami wyrównania* , które są wyświetlane jako czerwone linie kreskowane, aby pokazać, gdy krawędzie formantów są wyrównane lub gdy linie bazowe tekstu są wyrównane. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona.

**Szyny siatki**

Szyny siatki są używane do zarządzania wierszami i kolumnami w panelu [siatki](xref:Windows.UI.Xaml.Controls.Grid) . Można tworzyć i usuwać wiersze i kolumny, a można dostosować ich względne szerokości i wysokości. Szyny siatki pionowej, która pojawia się po lewej stronie obszaru roboczego, jest używany dla wierszy i linii poziomej, która pojawia się u góry, jest używany dla kolumn.

**Moduły definiowania układu siatki**

Moduł definiowania układu siatki pojawia się jako Trójkąt, który ma linię pionową lub poziomą dołączoną do niej na szynze siatki. Gdy przeciągniesz moduł definiowania układu siatki, Szerokość lub wysokość sąsiadujących kolumn lub wierszy są aktualizowane podczas przesuwania myszy.

Moduły definiowania układu siatki służą do sterowania szerokością i wysokością wierszy i kolumn siatki. Możesz dodać nową kolumnę lub wiersz, klikając kolejno szyny siatki. Po dodaniu nowego wiersza lub wiersza kolumny dla panelu siatki, który ma dwie lub więcej kolumn lub wierszy, wyświetlany jest minipasek narzędzi poza szyną, która umożliwia jawne ustawienie szerokości i wysokości. Minipasek narzędzi umożliwia ustawianie opcji ustalania rozmiarów dla wierszy i kolumn siatki.

![Moduł definiowania układu siatki w projektant XAML](media/grid-adorner.png)

**Uchwyty zmiany rozmiaru**

Uchwyty zmiany rozmiaru są wyświetlane w wybranych kontrolkach i umożliwiają zmianę rozmiaru kontrolki. Podczas zmiany rozmiaru kontrolki wartości szerokości i wysokości wyświetlane są zwykle ułatwiające rozmiar kontrolki. Aby uzyskać więcej informacji na temat manipulowania kontrolkami w widoku **projektu** , zobacz [Work with elementy in Projektant XAML](../designers/working-with-elements-in-xaml-designer.md).

**Marginesy**

Marginesy reprezentują ilość miejsca stałego między krawędzią kontrolki a krawędzią jej kontenera. Marginesy kontrolki można ustawić przy użyciu właściwości marginesu [](xref:Windows.UI.Xaml.FrameworkElement.Margin) w obszarze **Układ** w oknie **Właściwości** .

**Moduły definiowania układu marginesu**

Aby zmienić marginesy elementu względem jego kontenera układu, użyj modułu definiowania marginesów. Gdy marginesu jest otwarty, margines nie jest ustawiona, a moduł definiowania układu marginesu zawiera przerwany łańcuch. Gdy margines nie jest ustawiony, elementy pozostają w miejscu, gdy rozmiar kontenera układu zostanie zmieniony w czasie wykonywania. Gdy moduł definiowania układu marginesu jest zamknięty, moduł definiowania układu marginesu wyświetla nieprzerwany łańcuch i elementy są przenoszone wraz z marginesem, gdy rozmiar kontenera układów jest zmieniany w czasie wykonywania (margines pozostaje ustalony).

**Uchwyty elementu**

Można zmodyfikować element przy użyciu uchwytów elementu, które pojawiają się w obszarze kompozycji po przesunięciu wskaźnika myszy nad rogi niebieskiego pola otaczającego element. Uchwyty te umożliwiają obracanie, zmieniać rozmiar, przerzucić, Przenieś lub Dodaj promienia narożnika do elementu. Symbol uchwytu elementu zależy od funkcji i zmian w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwyty elementu, upewnij się, że element jest wybrany.

W widoku **projekt** w lewym dolnym rogu okna są dostępne dodatkowe polecenia obszaru roboczego, jak pokazano poniżej:

![Polecenia widok Projekt](../designers/media/xaml-design-view-controls.png)

Te polecenia są dostępne w tym narzędzi:

**Zoom**

Powiększenie umożliwia zmianę rozmiaru powierzchni projektowej. Możesz powiększyć od 12,5% do 800% lub wybrać opcje takie jak **Dopasuj zaznaczenie** i **Dopasuj wszystko**.

**Pokaż/Ukryj siatkę przyciągania**

Wyświetla lub ukrywa siatkę przyciągania pokazującą linie siatki. Linie siatki są używane po włączeniu przyciągania **do linii siatki** lub przyciągania **do linii wyrównania**.

**Włącz/Wyłącz przyciąganie do linii siatki**

Jeśli **przyciąganie do linii siatki** jest włączone, gdy przeciągasz element w obszarze kompozycji, element jest zgodny z najbardziej poziomymi i pionowymi liniami siatki.

**Przełącz tło obszaru kompozycji**

Przełącza między jasnym i ciemnym tłem.

**Włącz/Wyłącz przyciąganie do linii wyrównania**

Linii wyrównania ułatwiają wyrównywanie formantów względem siebie. Jeśli **przyciąganie do linii wyrównania** jest włączona, podczas przeciągania kontroli względem innych kontrolek wyrównanie granice są wyświetlane, gdy krawędzie i tekst niektóre kontrolki są wyrównane w poziomie lub pionie. Granicy wyrównania jest wyświetlana jako linia kreskowana czerwony.

**Wyłącz kod projektu**

Wyłącza [kod projektu](debugging-or-disabling-project-code-in-xaml-designer.md), na przykład formanty niestandardowe i konwertery wartości, i ponownie ładuje projektanta.

### <a name="xaml-view"></a>Widok XAML

W widoku **XAML** okno zawierające Edytor XAML jest aktywnym oknem, a Edytor XAML jest głównym narzędziem do tworzenia. Extensible Application Markup Language (XAML) zapewnia słownictwa deklaratywne, oparty na formacie XML do określania interfejsu użytkownika aplikacji. Widok XAML zawiera, IntelliSense, automatycznego formatowania, wyróżnianie składni i nawigacji tagu. Na poniższej ilustracji przedstawiono widok XAML z otwartym menu IntelliSense:

![Widok XAML](../designers/media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Okno konspektu dokumentu w programie Visual Studio jest podobne do [okna obiekty i oś czasu](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) w Blend for Visual Studio. Konspekt dokumentu ułatwia wykonywanie następujących zadań:

- Wyświetlanie hierarchicznej struktury wszystkich elementów w obszarze kompozycji.

- Wybierz elementy, aby można je było modyfikować (na przykład przenieść je w hierarchii lub ustawić ich właściwości w okno Właściwości). Aby uzyskać więcej informacji, zobacz [Work with elementy w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md).

- Tworzenie i modyfikowanie szablonów elementów będących kontrolkami.

- [Tworzenie animacji](animate-objects-in-xaml-designer.md) (Tylko Blend for Visual Studio).

Aby wyświetlić okno Konspekt dokumentu w programie Visual Studio, na pasku menu wybierz pozycję **Wyświetl** > inne**Konspekt dokumentu** **systemu Windows** > .
Aby wyświetlić okno obiekty i oś czasu w Blend for Visual Studio, na pasku menu wybierz pozycję **Wyświetl** > **Konspekt dokumentu**.

![Okno konspektu dokumentu w programie Visual Studio](../designers/media/document-outline-window.png)

Widok główny w oknie Konspekt dokumentu/Obiekty i oś czasu Wyświetla hierarchię dokumentu w strukturze drzewa. Można użyć hierarchicznego charakteru konspektu dokumentu do sprawdzenia dokumentu na różnych poziomach szczegółowości i zablokowania i ukrycia elementów pojedynczo lub w grupach. Są to opcje dostępne w oknie Konspekt dokumentu/Obiekty i oś czasu:

**Pokaż/Ukryj**

Wyświetla lub ukrywa elementy obszaru roboczego. Pojawia się jako symbol oka, gdy jest wyświetlany. Możesz również nacisnąć klawisz **Ctrl**+**h** , aby ukryć element i **przesunąć**+**Ctrl**+**h** w celu wyświetlenia go.

**Lock/unlock**

Blokuje lub odblokowuje elementy obszaru roboczego. Nie można modyfikować zablokowanych elementów. Pojawia się jako symbol kłódki po zablokowaniu. Możesz również nacisnąć klawisz **Ctrl**+**l** , aby zablokować element i **przesunąć**+**Ctrl**+**l** , aby go odblokować.

**Zwróć zakres do pageRoot**

Opcja w górnej części okna Konspekt dokumentu/Obiekty i oś czasu, która pokazuje symbol strzałki w górę, przenosi do poprzedniego zakresu. Zakresu działa ma zastosowanie tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości

Okno **Właściwości** umożliwia ustawianie wartości właściwości w kontrolkach. Poniżej przedstawiono wygląda następująco:

![Okno właściwości](../designers/media/xaml-designer-properties-window.png)

Dostępne są różne opcje w górnej części okna **Właściwości** :

- Zmień nazwę aktualnie wybranego elementu w polu **Nazwa** .
- W lewym górnym rogu istnieje ikona reprezentująca obecnie wybranego elementu.
- Aby ustawić właściwości według kategorii lub alfabetycznie, kliknij przycisk **kategorii**, **nazwa**, lub **źródła** w **Rozmieść według** listy.
- Aby wyświetlić listę zdarzeń dla kontrolki, kliknij przycisk **zdarzenia** , który jest wyświetlany jako Symbol błyskawicy.
- Aby wyszukać właściwość, Zacznij od wpisania nazwy właściwości w polu wyszukiwania. Okno **Właściwości** wyświetla właściwości, które pasują do wyszukiwania podczas wpisywania.

Niektóre właściwości umożliwiają ustawianie zaawansowanych właściwości, wybierając przycisk strzałki w dół.

Po prawej stronie każdej właściwości jest wartość *znacznik właściwości* wyświetlany jako symbol pola. Wygląd znacznika właściwość wskazuje, czy powiązanie danych lub zasób stosowany do właściwości. Na przykład symbol białe pola wskazuje wartość domyślną, symbol czarne pole zwykle wskazuje, że zastosowano zasobu lokalnego i pole pomarańczowy zwykle wskazuje, że zastosowano powiązanie danych. Po kliknięciu znacznik właściwości, przejdź do definicji stylu, otworzyć Konstruktor powiązań danych lub otworzyć selektor zasobów.

Aby uzyskać więcej informacji o używaniu właściwości i obsługi zdarzeń, zobacz [wprowadzenie do formantów i wzorców](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Zobacz także

- [Praca z elementami w projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)
- [Tworzenie i stosowanie zasobów](../designers/how-to-create-and-apply-a-resource.md)
- [Przewodnik: Powiąż z danymi w projektant XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)