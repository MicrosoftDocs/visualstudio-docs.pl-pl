---
title: Tworzenie interfejsów uIs za pomocą Visual Studio projektant XAML
description: Dowiedz się więcej o interfejsie użytkownika obszaru roboczego i funkcjach projektant XAML platformie Blend for Visual Studio udostępnia interfejs wizualny ułatwiający projektowanie aplikacji opartych na języku XAML.
ms.date: 03/03/2020
ms.topic: conceptual
ms.custom: contperf-fy21q4, SEO-VS-2020
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
ms.openlocfilehash: ef7d94acbb558ef2a8a3c557051e6dea16be916c
ms.sourcegitcommit: 809fff25b7701882c899c639eeb6da38ad4fb88a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2021
ms.locfileid: "112550691"
---
# <a name="create-a-ui-by-using-xaml-designer"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML

Interfejs projektant XAML w Visual Studio i Blend for Visual Studio udostępnia interfejs wizualny ułatwiający projektowanie aplikacji opartych na języku XAML, takich jak WPF i UWP. Interfejsy użytkownika dla aplikacji można tworzyć, przeciągając kontrolki z okna Przybornik (okno Elementy Blend for Visual Studio) i ustawiając właściwości w okno Właściwości. Język XAML można również edytować bezpośrednio w widoku XAML.

W przypadku użytkowników zaawansowanych można nawet [dostosować projektant XAML](https://github.com/microsoft/xaml-designer-extensibility/blob/master/documents/xaml-designer-extensibility-migration.md).

> [!NOTE]
> Xamarin.Forms nie obsługuje projektanta XAML. Aby wyświetlić interfejsy użytkownika języka XAML platformy Xamarin.Forms i edytować je, gdy aplikacja jest uruchomiona, użyj Przeładowywanie kodu XAML na gorąco dla platformy Xamarin.Forms. Aby uzyskać więcej informacji, zobacz [stronę Przeładowywanie kodu XAML na gorąco platformy Xamarin.Forms (wersja zapoznawcza).](/xamarin/xamarin-forms/xaml/hot-reload/)

## <a name="xaml-designer-workspace"></a>projektant XAML obszaru roboczego

Obszar roboczy w projektant XAML składa się z kilku elementów interfejsu wizualnego. Obejmują one *obszar kompozycji* (czyli powierzchnię projektową wizualizacji), edytor XAML, okno konspektu dokumentu (Obiekty i oś czasu okno Blend for Visual Studio) i okno Właściwości. Aby otworzyć projektant XAML, kliknij prawym przyciskiem myszy plik XAML w Eksplorator rozwiązań **i** wybierz **Projektant widoków**.

projektant XAML udostępnia widok XAML i zsynchronizowany widok Projekt renderowanych znaczników XAML aplikacji. Po otwarciu pliku XAML w Visual Studio lub Blend for Visual Studio można przełączać się między widok Projekt i widokiem XAML przy użyciu kart Projektowanie **i** **XAML.** Możesz użyć przycisku **Zamień** okienka Przycisk Zamień okienka w projektant XAML, aby przełączyć okno wyświetlane u góry: obszar kompozycji lub ![ edytor ](media/swap-panes.PNG) XAML.

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

Uchwyty zmiany rozmiaru są wyświetlane na wybranych kontrolkach i umożliwiają zmianę rozmiaru kontrolki. Podczas zmiany rozmiaru kontrolki zwykle wyświetlane są wartości szerokości i wysokości, które ułatwiają jej rozmiar. Aby uzyskać więcej informacji na temat manipulowania kontrolkami w **widoku projektu,** zobacz [Praca z elementami w projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

**Marginesy**

Marginesy reprezentują stałą przestrzeń między krawędzią kontrolki a krawędzią jej kontenera. Marginesy kontrolki można ustawić przy użyciu właściwości [Margines](xref:Windows.UI.Xaml.FrameworkElement.Margin) w obszarze **Układ** w **oknie** Właściwości.

**Definiowanie układów marginesów**

Użyj funkcji definiowania układu marginesów, aby zmienić marginesy elementu względem jego kontenera układu. Gdy definiowanie układu marginesu jest otwarte, margines nie jest ustawiany, a definiowanie układu marginesu wyświetla przerwany łańcuch. Gdy margines nie jest ustawiony, elementy pozostają na miejscu, gdy rozmiar kontenera układu jest zmieniany w czasie uruchamiania. Gdy definiowanie układu marginesu jest zamknięte, definiowanie układu marginesu wyświetla nieprzerwany łańcuch, a elementy są przesuwane z marginesem, ponieważ rozmiar kontenera układu jest zmieniany w czasie uruchamiania (margines pozostaje stały).

**Uchwyty elementów**

Element można zmodyfikować przy użyciu uchwytów elementów, które pojawiają się na tablicy kompozycji podczas przesuwania wskaźnika na narożniki niebieskiego pola otaczającego element. Te uchwyty umożliwiają obracanie, zmienianie rozmiaru, przerzucanie, przenoszenie lub dodawanie promienia rogu do elementu. Symbol uchwytu elementu różni się w zależności od funkcji i zmienia się w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwytów elementu, upewnij się, że element został wybrany.

W **widoku** Projekt dodatkowe polecenia obszaru kompozycji są dostępne w lewym dolnym obszarze okna, jak pokazano poniżej:

![widok Projekt polecenia](media/xaml-design-view-controls.png)

Te polecenia są dostępne na tym pasku narzędzi:

**Powiększenie**

Funkcja Zoom umożliwia rozmiar powierzchni projektowej. Możesz powiększyć z 12,5% do 800% lub wybrać opcje, takie jak **Dopasuj wybór** i **Dopasuj wszystko.**

**Pokaż/ukryj siatkę przyciągania**

Wyświetla lub ukrywa siatkę przyciągania, która pokazuje linie siatki. Linie siatki są używane w przypadku włączenia przyciągania do linii **siatki** lub **przyciągania do linii przyciągania.**

**Włączanie/wyłączanie przyciągania do linii siatki**

Jeśli **jest włączone przyciąganie** do linii siatki, element ma tendencję do wyrównywania z najbliższymi poziomymi i pionowymi liniami siatki podczas przeciągania do tablicy kompozycji.

**Przełączanie tła obszarów kompozycji**

Przełącza się między jasnym i ciemnym tłem.

**Włączanie/wyłączanie przyciągania do linii przyciągania**

Linie przyciągania ułatwiają wyrównywanie kontrolek względem siebie. Jeśli **przyciąganie** do linii przyciągania jest włączone, podczas przeciągania kontrolki względem innych kontrolek granice wyrównania są wyświetlane, gdy krawędzie i tekst niektórych kontrolek są wyrównane w poziomie lub w pionie. Granica wyrównania jest wyświetlana jako linia przerywana w kolorze czerwonym.

**Wyłączanie kodu projektu**

Wyłącza [kod projektu](debugging-or-disabling-project-code-in-xaml-designer.md), na przykład niestandardowe kontrolki i konwertery wartości, a także ponownie ładuje projektanta.

### <a name="xaml-view"></a>Widok XAML

W **widoku XAML** okno zawierające edytor XAML jest aktywnym oknem, a edytor XAML jest podstawowym narzędziem do tworzenia. Język Extensible Application Markup Language (XAML) udostępnia deklaratywne, oparte na języku XML słownictwo do określania interfejsu użytkownika aplikacji. Widok XAML obejmuje funkcję IntelliSense, automatyczne formatowanie, wyróżnianie składni i nawigację po tagach. Na poniższej ilustracji przedstawiono widok XAML z otwartym menu IntelliSense:

![Widok XAML](media/xaml-editor.png)

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Okno Konspekt dokumentu w Visual Studio jest podobne do [Obiekty i oś czasu w Blend for Visual Studio.](creating-a-ui-by-using-blend-for-visual-studio.md#objects-and-timeline-window) Konspekt dokumentu ułatwia wykonywanie tych zadań:

- Wyświetl hierarchiczną strukturę wszystkich elementów w tablicy kompozycji.

- Wybierz elementy, aby można je było modyfikować. Można na przykład poruszać się po hierarchii lub ustawiać ich właściwości w okno Właściwości. Aby uzyskać więcej informacji, zobacz [Praca z elementami w projektant XAML](../xaml-tools/working-with-elements-in-xaml-designer.md).

- Tworzenie i modyfikowanie szablonów dla elementów, które są kontrolkami.

- [Tworzenie animacji](animate-objects-in-xaml-designer.md) (tylko Blend for Visual Studio).

Aby wyświetlić okno Konspekt dokumentu Visual Studio, na pasku menu wybierz pozycję **Wyświetl**  >  **inne konspekt** dokumentu  >  **systemu** Windows.
Aby wyświetlić okno Obiekty i oś czasu w Blend for Visual Studio, na pasku menu wybierz pozycję **Wyświetl**  >  **konspekt dokumentu.**

![Okno Konspekt dokumentu w Visual Studio](media/document-outline-window.png)

Główny widok w oknie Konspekt/Obiekty i oś czasu dokumentu wyświetla hierarchię dokumentu w strukturze drzewa. Można użyć hierarchicznego charakteru konspektu dokumentu, aby zbadać dokument na różnych poziomach szczegółowości oraz zablokować i ukryć elementy w grupach lub w grupach. Następujące opcje są dostępne w oknie Konspekt/Obiekty i oś czasu dokumentu:

**Pokaż/ukryj**

Wyświetla lub ukrywa elementy obszarów kompozycji. Pojawia się jako symbol oka, gdy jest wyświetlany. Możesz również nacisnąć klawisz **Ctrl** + **H,** aby ukryć element, i **klawisze Shift** + **Ctrl** + **H,** aby go pokazać.

**Blokowanie/odblokowywanie**

Blokuje lub odblokowuje elementy obszarów kompozycji. Zablokowanych elementów nie można modyfikować. Pojawia się jako symbol kłódki po zablokowaniu. Możesz również nacisnąć klawisz **Ctrl** + **L,** aby zablokować element, i **nacisnąć klawisz** + **Ctrl** + **L,** aby go odblokować.

**Zwracanie zakresu do pageRoot**

Opcja w górnej części okna Konspekt/Obiekty i oś czasu dokumentu, w której jest symbol strzałki w górę, przechodzi do poprzedniego zakresu. Określanie zakresu ma zastosowanie tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości

Okno **Właściwości** umożliwia ustawienie wartości właściwości w kontrolkach. Oto jak wygląda:

![Okno właściwości](media/xaml-designer-properties-window.png)

W górnej części okna Właściwości dostępne są **różne** opcje:

- Zmień nazwę aktualnie wybranego elementu w **polu** Nazwa.
- W lewym górnym rogu znajduje się ikona reprezentująca aktualnie wybrany element.
- Aby rozmieścić właściwości według kategorii lub alfabetycznie, kliknij pozycję **Kategoria,** **Nazwa** lub **Źródło** na liście **Rozmieść według.**
- Aby wyświetlić listę zdarzeń dla kontrolki, kliknij przycisk **Zdarzenia,** który jest wyświetlany jako symbol pioruna.
- Aby wyszukać właściwość, zacznij wpisywać nazwę właściwości w polu wyszukiwania. W **oknie** Właściwości zostaną wyświetlone właściwości, które pasują do wyszukiwania podczas wpisywania.

Niektóre właściwości umożliwiają ustawianie właściwości zaawansowanych przez wybranie przycisku strzałki w dół.

Po prawej stronie każdej wartości właściwości znajduje się znacznik *właściwości,* który jest wyświetlany jako symbol pola. Wygląd znacznika właściwości wskazuje, czy do właściwości zastosowano powiązanie danych, czy zasób. Na przykład symbol białej skrzynki wskazuje wartość domyślną, symbol czarnej skrzynki zazwyczaj oznacza, że zastosowano zasób lokalny, a pomarańczowe pole zwykle wskazuje, że zastosowano powiązanie danych. Po kliknięciu znacznika właściwości możesz przejść do definicji stylu, otworzyć konstruktora powiązań danych lub otworzyć s wyboru zasobów.

Aby uzyskać więcej informacji na temat używania właściwości i obsługi zdarzeń, zobacz [Wprowadzenie do kontrolek i wzorców](/windows/uwp/design/controls-and-patterns/controls-and-events-intro).

## <a name="see-also"></a>Zobacz też

- [Praca z elementami w projektancie XAML](../xaml-tools/working-with-elements-in-xaml-designer.md)
- [Tworzenie i stosowanie zasobów](../xaml-tools/how-to-create-and-apply-a-resource.md)
- [Przewodnik: wiązanie z danymi w projektancie XAML](../xaml-tools/walkthrough-binding-to-data-in-xaml-designer.md)
