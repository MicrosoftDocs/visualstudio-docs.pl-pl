---
title: Projektant XAML — omówienie
description: Dowiedz się więcej o interfejsie użytkownika obszaru roboczego i funkcjach projektant XAML platformie Blend for Visual Studio udostępnia interfejs wizualny ułatwiający projektowanie aplikacji opartych na języku XAML.
ms.date: 03/03/2020
ms.topic: conceptual
ms.custom: contperf-fy21q4; SEO-VS-2020
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.DocumentOutline
- Blend.Start.Dev12
ms.devlang: CSharp
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 3d5584380b78bba05f1596a99aa2298789df018f
ms.sourcegitcommit: 3e1ff87fba290f9e60fb4049d011bb8661255d58
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2021
ms.locfileid: "107879359"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML

Interfejs projektant XAML w Visual Studio i Blend for Visual Studio udostępnia interfejs wizualny ułatwiający projektowanie aplikacji opartych na języku XAML, takich jak WPF i UWP. Interfejsy użytkownika dla aplikacji można tworzyć, przeciągając kontrolki z okna przybornika (okno Elementy Blend for Visual Studio) i ustawiając właściwości w okno Właściwości. Możesz również edytować kod XAML bezpośrednio w widoku XAML.

W przypadku zaawansowanych użytkowników można nawet [dostosować projektant XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin.Forms nie obsługuje projektanta XAML. Aby wyświetlić interfejsy użytkownika języka XAML platformy Xamarin.Forms i edytować je, gdy aplikacja jest uruchomiona, użyj Przeładowywanie kodu XAML na gorąco dla platformy Xamarin.Forms. Aby uzyskać więcej informacji, zobacz [stronę Przeładowywanie kodu XAML na gorąco dla platformy Xamarin.Forms (wersja zapoznawcza).](/xamarin/xamarin-forms/xaml/hot-reload/)

## <a name="xaml-designer-workspace"></a>projektant XAML roboczy

Obszar roboczy w projektant XAML składa się z kilku elementów interfejsu wizualnego. Obejmują one *obszar kompozycji* (czyli powierzchnię projektową wizualizacji), edytor XAML, okno konspektu dokumentu (Obiekty i oś czasu okno Blend for Visual Studio) i okno Właściwości. Aby otworzyć projektant XAML, kliknij prawym przyciskiem myszy plik XAML w Eksplorator rozwiązań **i** wybierz **Projektant widoków**.

projektant XAML widok XAML i zsynchronizowany widok Projekt renderowanych znaczników XAML aplikacji. Po otwarciu pliku XAML w Visual Studio lub Blend for Visual Studio można przełączać się między widok Projekt i widokiem XAML przy użyciu kart Projektowanie **i** **XAML.** Możesz użyć przycisku **Zamień** okienka Przycisk Zamień okienka w projektant XAML, aby przełączyć okno wyświetlane u góry: obszar kompozycji lub ![ ](media/swap-panes.PNG) edytor XAML.

### <a name="design-view"></a>widok Projekt

W widok Projekt okno zawierające obszar kompozycji jest aktywnym oknem i można go użyć jako podstawowej powierzchni roboczej. Umożliwia wizualne projektowanie strony w aplikacji przez dodawanie, rysowanie lub modyfikowanie elementów. Aby uzyskać więcej informacji, zobacz [Praca z elementami w projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md). Na tej ilustracji przedstawiono obszar kompozycji w widok Projekt.

![widok Projekt projektant XAML](media/xaml-artboard.png)

Te funkcje są dostępne w tablicy kompozycji:

**Snaplines**

Linie przyciągania *to granice* wyrównania, które są wyświetlane jako linie kreskowane czerwoną kreską, gdy krawędzie kontrolek są wyrównane lub gdy linie bazowe tekstu są wyrównane. Granice wyrównania są wyświetlane tylko **wtedy, gdy jest włączone przyciąganie do linii** przyciągania.

**Szyny siatki**

Szyny siatki służą do zarządzania wierszami i kolumnami w [panelu Siatki.](xref:Windows.UI.Xaml.Controls.Grid) Można tworzyć i usuwać wiersze i kolumny oraz dostosowywać ich względne szerokości i wysokości. Pionowa szyna Grid wyświetlana po lewej stronie artboardu jest używana dla wierszy, a pozioma linia, która pojawia się u góry, jest używana dla kolumn.

**Definiowanie układów siatki**

Definiowanie układu siatki jest wyświetlane jako trójkąt, który ma do niego dołączona pionowa lub pozioma linia na szynie siatki. Podczas przeciągania układu siatki szerokość lub wysokość sąsiednich kolumn lub wierszy są aktualizowane podczas przesuwania myszy.

Definiowanie układów siatki służy do kontrolowania szerokości i wysokości wierszy i kolumn siatki. Możesz dodać nową kolumnę lub wiersz, klikając szyny siatki. Po dodaniu nowego wiersza lub linii kolumny dla panelu siatki, który ma co najmniej dwie kolumny lub wiersze, mini pasek narzędzi jest wyświetlany poza szyną, co umożliwia jawne ustawienie szerokości i wysokości. Mini pasek narzędzi umożliwia ustawianie opcji rozmiaru dla wierszy i kolumn siatki.

![Definiowanie układu siatki w projektant XAML](media/grid-adorner.png)

**Zmienianie rozmiaru uchwytów**

Uchwyty zmiany rozmiaru są wyświetlane na wybranych kontrolkach i umożliwiają zmianę rozmiaru kontrolki. Podczas zmiany rozmiaru kontrolki zwykle wyświetlane są wartości szerokości i wysokości, które ułatwiają jej rozmiar. Aby uzyskać więcej informacji na temat manipulowania kontrolkami w **widoku Projekt,** zobacz [Praca z elementami w projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Marginesy**

Marginesy reprezentują stałą ilość miejsca między krawędzią kontrolki a krawędzią jej kontenera. Marginesy kontrolki można ustawić przy użyciu właściwości [Margines](xref:Windows.UI.Xaml.FrameworkElement.Margin) w obszarze **Układ** w **oknie** Właściwości.

**Definiowanie układów marginesów**

Użyj funkcji definiowania układu marginesów, aby zmienić marginesy elementu względem jego kontenera układu. Gdy definiowanie układu marginesu jest otwarte, margines nie jest ustawiony, a definiowanie układu marginesu wyświetla przerwany łańcuch. Gdy margines nie jest ustawiony, elementy pozostają na miejscu, gdy rozmiar kontenera układu jest zmieniany w czasie uruchamiania. Po zamknięciu definiowania układu marginesu, definiowanie układu marginesu wyświetla odłączony łańcuch, a elementy są przesuwane z marginesem, gdy rozmiar kontenera układu jest zmieniany w czasie uruchamiania (margines pozostaje stały).

**Dojścia elementów**

Element można zmodyfikować przy użyciu uchwytów elementów, które pojawiają się na tablicy kompozycji, gdy przesuwasz wskaźnik na narożniki niebieskiego pola otaczającego element. Te uchwyty umożliwiają obracanie, zmienianie rozmiaru, przerzucanie, przenoszenie lub dodawanie promienia narożnika do elementu. Symbol uchwytu elementu zależy od funkcji i zmian w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwytów elementu, upewnij się, że element jest zaznaczony.

W **widoku** Projekt dodatkowe polecenia obszaru kompozycji są dostępne w lewym dolnym obszarze okna, jak pokazano poniżej:

![widok Projekt polecenia](media/xaml-design-view-controls.png)

Te polecenia są dostępne na tym pasku narzędzi:

**Powiększenie**

Funkcja Zoom umożliwia rozmiar powierzchni projektowej. Możesz powiększyć z 12,5% do 800% lub wybrać opcje, takie jak Dopasuj **zaznaczenie** i **Dopasuj wszystko.**

**Pokaż/Ukryj siatkę przyciągania**

Wyświetla lub ukrywa siatkę przyciągania, która pokazuje linie siatki. Linie siatki są używane w przypadku włączenia przyciągania do linii **siatki** lub **przyciągania do linii przyciągania.**

**Włączanie/wyłączanie przyciągania do linii siatki**

Jeśli **jest włączone przyciąganie** do linii siatki, element ma tendencję do wyrównywania z najbliższymi poziomymi i pionowymi liniami siatki podczas przeciągania do tablicy kompozycji.

**Przełączanie tła obszarów kompozycji**

Przełącza się między jasnym i ciemnym tłem.

**Włączanie/wyłączanie przyciągania do linii przyciągania**

Linie przyciągania ułatwiają wyrównywanie kontrolek względem siebie. Jeśli **przyciąganie** do linii przyciągania jest włączone, podczas przeciągania kontrolki względem innych kontrolek granice wyrównania są wyświetlane, gdy krawędzie i tekst niektórych kontrolek są wyrównane w poziomie lub w pionie. Granica wyrównania jest wyświetlana jako linia przerywana w kolorze czerwonym.

**Wyłączanie kodu projektu**

Wyłącza [kod projektu](debugging-or-disabling-project-code-in-xaml-designer.md), na przykład niestandardowe kontrolki i konwertery wartości, a następnie ponownie ładuje projektanta.

### <a name="xaml-view"></a>Widok XAML

W **widoku XAML** okno zawierające edytor XAML jest aktywnym oknem, a edytor XAML jest podstawowym narzędziem do tworzenia. Język Extensible Application Markup Language (XAML) udostępnia deklaratywne, oparte na języku XML słownictwo do określania interfejsu użytkownika aplikacji. Widok XAML obejmuje funkcję IntelliSense, automatyczne formatowanie, wyróżnianie składni i nawigację po tagach. Na poniższej ilustracji przedstawiono widok XAML z otwartym menu IntelliSense:

![Widok XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Okno Konspekt dokumentu w Visual Studio jest podobne do [Obiekty i oś czasu w Blend for Visual Studio.](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) Konspekt dokumentu ułatwia wykonywanie tych zadań:

- Wyświetl hierarchiczną strukturę wszystkich elementów w tablicy kompozycji.

- Wybierz elementy, aby można było je modyfikować. Można na przykład poruszać się po hierarchii lub ustawiać ich właściwości w okno Właściwości. Aby uzyskać więcej informacji, zobacz [Praca z elementami w projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Tworzenie i modyfikowanie szablonów dla elementów, które są kontrolkami.

- [Tworzenie animacji](animate-objects-in-xaml-designer.md) (tylko Blend for Visual Studio).

Aby wyświetlić okno Konspekt dokumentu w Visual Studio, na pasku menu wybierz pozycję **Wyświetl**  >  **inne konspekt** dokumentu  >  **systemu** Windows.
Aby wyświetlić okno Obiekty i oś czasu w Blend for Visual Studio, na pasku menu wybierz pozycję **Wyświetl**  >  **konspekt dokumentu.**

![Okno Konspekt dokumentu w Visual Studio](media/document-outline-window.png)

Główny widok w oknie Konspekt/Obiekty i oś czasu dokument zawiera hierarchię dokumentu w strukturze drzewa. Hierarchiczny charakter konspektu dokumentu umożliwia badanie dokumentu na różnych poziomach szczegółowości oraz blokowanie i ukrywanie elementów w grupach lub w grupach. Następujące opcje są dostępne w oknie Konspekt/Obiekty i oś czasu dokumentu:

**Pokaż/ukryj**

Wyświetla lub ukrywa elementy obszarów kompozycji. Pojawia się jako symbol oka, gdy jest wyświetlany. Możesz również nacisnąć klawisz **Ctrl** + **H,** aby ukryć element, i **shift** + **Ctrl** + **H,** aby go pokazać.

**Blokowanie/odblokowywanie**

Blokuje lub odblokowuje elementy obszarów kompozycji. Zablokowanych elementów nie można modyfikować. Pojawia się jako symbol kłódki po zablokowaniu. Możesz również nacisnąć klawisz **Ctrl** + **L,** aby zablokować element, i **klawisze Shift** + **Ctrl** + **L,** aby go odblokować.

**Zwracanie zakresu do pageRoot**

Opcja w górnej części okna Konspekt/Obiekty i oś czasu dokumentu, w którym jest symbol strzałki w górę, przechodzi do poprzedniego zakresu. Określanie zakresu ma zastosowanie tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości

Okno **Właściwości** umożliwia ustawienie wartości właściwości dla kontrolek. Oto jak wygląda:

![Okno właściwości](media/xaml-designer-properties-window.png)

W górnej części okna Właściwości są dostępne **różne** opcje:

- Zmień nazwę aktualnie wybranego elementu w **polu** Nazwa.
- W lewym górnym rogu znajduje się ikona reprezentująca aktualnie wybrany element.
- Aby rozmieścić właściwości według kategorii lub alfabetycznie, kliknij pozycję **Kategoria,** **Nazwa** **lub** Źródło na liście **Rozmieść** według.
- Aby wyświetlić listę zdarzeń dla kontrolki, kliknij przycisk **Zdarzenia,** który jest wyświetlany jako symbol pioruna.
- Aby wyszukać właściwość, zacznij wpisywać nazwę właściwości w polu wyszukiwania. W **oknie** Właściwości zostaną wyświetlone właściwości, które pasują do wyszukiwania podczas wpisywania.

Niektóre właściwości umożliwiają ustawianie właściwości zaawansowanych przez wybranie przycisku strzałki w dół.

Po prawej stronie każdej wartości właściwości znajduje się *znacznik właściwości,* który jest wyświetlany jako symbol pola. Wygląd znacznika właściwości wskazuje, czy do właściwości zastosowano powiązanie danych, czy zasób. Na przykład symbol białej skrzynki wskazuje wartość domyślną, symbol czarnej skrzynki zwykle wskazuje, że zastosowano zasób lokalny, a pomarańczowe pole zwykle wskazuje, że zostało zastosowane powiązanie danych. Po kliknięciu znacznika właściwości możesz przejść do definicji stylu, otworzyć konstruktor powiązania danych lub otworzyć s wyboru zasobów.

Aby uzyskać więcej informacji na temat używania właściwości i obsługi zdarzeń, zobacz [Wprowadzenie do kontrolek i wzorców](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Zobacz też

- [Praca z elementami w projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Tworzenie i stosowanie zasobów](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Przewodnik: wiązanie z danymi w projektancie XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
