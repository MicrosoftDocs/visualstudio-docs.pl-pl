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
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 31a31e413ecd39b7d15f8ea3cd0417c2493463ca
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649620"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML

Projektant XAML w programie Visual Studio i Blend dla programu Visual Studio udostępnia interfejs wizualny ułatwiające projektowanie aplikacji opartych na języku XAML, takich jak WPF i platformy uniwersalnej systemu Windows. Interfejsy użytkownika dla aplikacji można tworzyć, przeciągając kontrolki z okna Przybornik (okno Zasoby w programie Blend for Visual Studio) i ustawiając właściwości w oknie Właściwości. Można również edytować XAML bezpośrednio w widoku XAML.

Dla zaawansowanych użytkowników można nawet [dostosować projektanta XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin.Forms nie obsługuje projektanta XAML. Aby wyświetlić interfejsy API Xamarin.Forms XAML i edytować je, gdy aplikacja jest uruchomiona, użyj funkcji XAML Hot Reload for Xamarin.Forms. Aby uzyskać więcej informacji, zobacz [stronę XAML Hot Reload for Xamarin.Forms (Preview).](/xamarin/xamarin-forms/xaml/hot-reload/)

## <a name="xaml-designer-workspace"></a>Obszar roboczy projektanta XAML

Obszar roboczy w projektancie XAML składa się z kilku elementów interfejsu wizualnego. Należą do nich *obszar roboczy* (który jest powierzchnią projektu wizualnego), edytor XAML, okno Konspekt dokumentu (obiekty i okno osi czasu w programie Blend for Visual Studio) i okno Właściwości. Aby otworzyć Projektanta XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksploratorze rozwiązań** i wybierz polecenie **Wyświetl projektanta**.

XAML Designer udostępnia widok XAML i zsynchronizowany widok projektu renderowanych znaczników XAML aplikacji. Po otwarciu pliku XAML w programie Visual Studio lub Blend for Visual Studio można przełączać się między widokiem Projektu i widokiem XAML przy użyciu kart **Projektowanie** i **XAML.** Przycisk **Zamień okienka** można użyć przycisku ![Zamień okienka w projektancie XAML,](media/swap-panes.PNG) aby przełączyć okno, które jest wyświetlane na górze: obszar roboczy lub edytor XAML.

### <a name="design-view"></a>Widok projektu

W widoku Projekt okno zawierające obszar roboczy jest aktywnym oknem i można go używać jako podstawowej powierzchni roboczej. Można go używać do wizualnego projektowania strony w aplikacji, dodając, rysując lub modyfikując elementy. Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Na tej ilustracji przedstawiono obszar roboczy w widoku Projekt.

![Widok projektu projektanta XAML](media/xaml-artboard.png)

Te funkcje są dostępne w pokładzie:

**Snaplines**

Snaplines są *granicami wyrównania,* które są wyświetlane jako linie z czerwoną kreską, aby pokazać, kiedy krawędzie formantów są wyrównane lub gdy linie bazowe tekstu są wyrównane. Granice wyrównania są wyświetlane tylko wtedy, gdy **przyciąganie do linii przyciągania** jest włączone.

**Szyny siatkowe**

Szyny siatki służą do zarządzania wierszami i kolumnami w panelu [Siatka.](xref:Windows.UI.Xaml.Controls.Grid) Można tworzyć i usuwać wiersze i kolumny, a także dostosowywać ich względne szerokości i wysokości. Pionowa szyna siatki, która pojawia się po lewej stronie obszaru roboczego, jest używana dla wierszy, a linia pozioma, która pojawia się u góry, jest używana dla kolumn.

**Adornery siatki**

A Grid adorner pojawia się jako trójkąt, który ma pionową lub poziomą linię przymocowaną do niego na szynie Siatki. Podczas przeciągania adorner siatki, szerokości lub wysokości sąsiednich kolumn lub wierszy aktualizacji podczas przenoszenia myszy.

Adorners siatki są używane do kontrolowania szerokości i wysokości grid wierszy i kolumn. Nową kolumnę lub wiersz można dodać, klikając siatkę na szynach. Po dodaniu nowej linii wiersza lub kolumny dla panelu Siatka, który ma dwie lub więcej kolumn lub wierszy, poza szyną pojawia się mini-pasek narzędzi, który umożliwia jawne ustawienie szerokości i wysokości. Minipasek narzędzi umożliwia ustawienie opcji zmiany rozmiaru dla wierszy i kolumn siatki.

![Adorner siatki w projektancie XAML](media/grid-adorner.png)

**Uchwyty zmienić rozmiar**

Uchwyty o rozmiarze rozmiaru są wyświetlane na wybranych formantach i umożliwiają zmienić rozmiar formantu. Po zmienić rozmiar formantu, szerokość i wysokość wartości zazwyczaj pojawiają się, aby ułatwić rozmiar formantu. Aby uzyskać więcej informacji na temat manipulowania formantami w widoku **Projekt,** zobacz [Praca z elementami w Projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Marginesy**

Marginesy reprezentują ilość stałej przestrzeni między krawędzią formantu a krawędzią jego kontenera. Marginesy formantu można ustawić za pomocą [właściwości Margines](xref:Windows.UI.Xaml.FrameworkElement.Margin) w obszarze **Układ** w oknie **Właściwości.**

**Adornery marży**

Użyj symboli marginesów, aby zmienić marginesy elementu względem jego kontenera układu. Gdy adorner marginesu jest otwarty, margines nie jest ustawiony, a margines adorner wyświetla przerwany łańcuch. Gdy margines nie jest ustawiony, elementy pozostają w miejscu, gdy kontener układu jest zmieniany w czasie wykonywania. Gdy adorner marginesu jest zamknięty, adorner marginesu wyświetla nieprzerwany łańcuch, a elementy przenieść z marginesem, jak kontener układu jest zmieniany w czasie wykonywania (margines pozostaje stały).

**Uchwyty elementu**

Element można zmodyfikować za pomocą uchwytów elementu, które pojawiają się w obszarze roboczym podczas przesuwania wskaźnika nad narożnikami niebieskiego pola otaczającego element. Uchwyty te umożliwiają obracanie, zmienianie rozmiaru, przerzucanie, przesuwanie lub dodawanie promienia naroża do elementu. Symbol uchwytu elementu różni się w zależności od funkcji i zmienia się w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwytów elementu, upewnij się, że element jest zaznaczony.

W widoku **Projekt** dodatkowe polecenia obszaru roboczego są dostępne w lewym dolnym obszarze okna, jak pokazano poniżej:

![Polecenia widoku projektu](media/xaml-design-view-controls.png)

Te polecenia są dostępne na tym pasku narzędzi:

**Zoom**

Zoom umożliwia powiększenie powierzchni projektowej. Możesz powiększyć od 12,5% do 800% lub wybrać opcje, takie jak **Dopasuj wybór** i **Dopasuj wszystkie**.

**Pokaż/Ukryj siatkę przyciągania**

Wyświetla lub ukrywa siatkę przyciągania, która pokazuje linie siatki. Linie siatki są używane po **włączeniu przyciągania do linii siatki** lub **przyciągania do linii przyciągania**.

**Włączanie/wyłączanie przyciągania do linii siatki**

Jeśli **przyciąganie do linii siatki** jest włączone, element ma tendencję do wyrównania z najbliższymi poziomymi i pionowymi liniami siatki podczas przeciągania go na obszar roboczy.

**Przełączanie tła obszaru roboczego**

Przełącza między jasnym i ciemnym tłem.

**Włączanie/wyłączanie przyciągania do przyciągania**

Snaplines pomagają wyrównać formanty względem siebie. Jeśli **przyciąganie do linii przyciągania** jest włączone, podczas przeciągania formantu względem innych formantów, granice wyrównania są wyświetlane, gdy krawędzie i tekst niektórych formantów są wyrównane w poziomie lub w pionie. Granica wyrównania jest wyświetlana jako linia o czerwonej kreski.

**Wyłączanie kodu projektu**

Wyłącza [kod projektu](debugging-or-disabling-project-code-in-xaml-designer.md), na przykład formantów niestandardowych i konwerterów wartości i ponownie ładuje projektanta.

### <a name="xaml-view"></a>Widok XAML

W widoku **XAML** okno zawierające edytor XAML jest aktywnym oknem, a edytor XAML jest podstawowym narzędziem do tworzenia. Język XAML (Extensible Application Markup Language) zawiera deklaratywne słownictwo oparte na języku XML do określania interfejsu użytkownika aplikacji. Widok XAML zawiera intellisense, automatyczne formatowanie, wyróżnianie składni i nawigację znaczników. Na poniższej ilustracji przedstawiono widok XAML z otwartym menu IntelliSense:

![Widok XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno Konspekt dokumentu

Okno Konspekt dokumentu w programie Visual Studio jest podobne do [okna Obiekty i oś czasu](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) w programie Blend for Visual Studio. Konspekt dokumentu ułatwia wykonywanie następujących zadań:

- Służy do wyświetlania struktury hierarchicznej wszystkich elementów w obszarze roboczym.

- Wybierz elementy, aby można je było modyfikować. Na przykład można przenieść je w hierarchii lub ustawić ich właściwości w oknie Właściwości. Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Tworzenie i modyfikowanie szablonów dla elementów, które są formantami.

- [Tworzenie animacji](animate-objects-in-xaml-designer.md) (tylko w programie Visual Studio).

Aby wyświetlić okno Konspekt dokumentu w programie Visual Studio, na pasku menu wybierz pozycję **Wyświetl** > inny**konspekt dokumentu****systemu Windows** > .
Aby wyświetlić okno Obiekty i oś czasu w programie Blend for Visual Studio, na pasku menu wybierz pozycję **Wyświetl** > **konspekt dokumentu**.

![Okno Konspekt dokumentu w programie Visual Studio](media/document-outline-window.png)

Widok główny w oknie Konspekt/Obiekty dokumentu i oś czasu wyświetla hierarchię dokumentu w strukturze drzewa. Hierarchicznego charakteru konspektu dokumentu można użyć do zbadania dokumentu na różnych poziomach szczegółowości oraz do blokowania i ukrywania elementów pojedynczo lub w grupach. W oknie Konspekt/Obiekty dokumentu i oś czasu dostępne są następujące opcje:

**Pokaż/ukryj**

Wyświetla lub ukrywa elementy obszaru roboczego. Pojawia się jako symbol oka, gdy jest wyświetlany. Można również nacisnąć **klawisze Ctrl H,**+**H** aby ukryć element, a **następnie klawisze Shift**+**Ctrl**+**H,** aby go wyświetlić.

**Zablokuj/odblokuj**

Blokuje lub odblokowuje elementy obszaru roboczego. Zablokowanych elementów nie można modyfikować. Pojawia się jako symbol kłódki po zablokowaniu. Można również nacisnąć **klawisze Ctrl**+**L,** aby zablokować element, a **następnie klawisze Shift**+**Ctrl**+**L,** aby go odblokować.

**Zwracanie zakresu do pageRoot**

Opcja w górnej części okna Konspekt/Obiekty dokumentu i oś czasu, która pokazuje symbol strzałki w górę, przechodzi do poprzedniego zakresu. Określanie zakresu ma zastosowanie tylko wtedy, gdy znajdujesz się w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości

Okno **Właściwości** umożliwia ustawienie wartości właściwości na formanty. Oto jak to wygląda:

![Okno właściwości](media/xaml-designer-properties-window.png)

W górnej części okna **Właściwości** znajdują się różne opcje:

- Zmień nazwę aktualnie zaznaczonego elementu w polu **Nazwa.**
- W lewym górnym rogu znajduje się ikona reprezentująca aktualnie zaznaczony element.
- Aby rozmieścić właściwości według kategorii lub alfabetycznie, kliknij pozycję **Kategoria**, **Nazwa**lub **Źródło** na liście **Rozmieść według.**
- Aby wyświetlić listę zdarzeń formantu, kliknij przycisk **Zdarzenia,** który jest wyświetlany jako symbol błyskawicy.
- Aby wyszukać właściwość, zacznij wpisywać nazwę właściwości w polu wyszukiwania. Okno **Właściwości** wyświetla właściwości, które pasują do wyszukiwania podczas pisania.

Niektóre właściwości umożliwiają ustawienie właściwości zaawansowanych przez wybranie przycisku strzałki w dół.

Po prawej stronie każdej wartości właściwości znajduje się *znacznik właściwości,* który pojawia się jako symbol pola. Wygląd znacznika właściwości wskazuje, czy istnieje powiązanie danych lub zasób zastosowany do właściwości. Na przykład biały symbol pola wskazuje wartość domyślną, symbol czarnego pola zazwyczaj wskazuje, że zastosowano zasób lokalny, a pomarańczowe pole zazwyczaj wskazuje, że zastosowano powiązanie danych. Po kliknięciu znacznika właściwości można przejść do definicji stylu, otworzyć konstruktora wiązania danych lub otworzyć selektor zasobów.

Aby uzyskać więcej informacji na temat używania właściwości i obsługi zdarzeń, zobacz [Wprowadzenie do formantów i wzorców](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Zobacz też

- [Praca z elementami w projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Tworzenie i stosowanie zasobów](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Przewodnik: wiązanie z danymi w projektancie XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
