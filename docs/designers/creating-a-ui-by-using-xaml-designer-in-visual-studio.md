---
title: Tworzenie interfejsu użytkownika przy użyciu projektanta XAML
ms.date: 03/28/2019
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- uwp
ms.openlocfilehash: 3cd26f35111fc2e79290b30e7ae488b268e558d0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62899430"
---
# <a name="create-a-ui-by-using-xaml-designer-in-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio

Projektant XAML w programie Visual Studio udostępnia interfejs graficzny, aby ułatwić projektowanie oparte na XAML Windows i aplikacje sieci Web. Można utworzyć interfejsów użytkownika dla aplikacji poprzez przeciąganie kontrolek z **przybornika** i ustawianie właściwości w **właściwości** okna. Można również edytować XAML bezpośrednio w widoku XAML.

Aby uzyskać zaawansowane zadania projektowania XAML, takich jak animacjom i zachowaniom, zobacz [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md). Zobacz też [projektowanie XAML w programie Visual Studio i Blend for Visual Studio](../designers/designing-xaml-in-visual-studio.md) w celu porównania narzędzia.

## <a name="xaml-designer-workspace"></a>Obszar roboczy Projektanta XAML

Obszar roboczy w Projektancie XAML składa się z kilku elementów interfejsu wizualnego. Należą do nich **obszaru kompozycji**, **edytora XAML**, **urządzenia** oknie **konspekt dokumentu** oknie i **właściwości**  okna. Aby otworzyć projektanta XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksploratora rozwiązań** i wybierz polecenie **Projektant widoków**.

## <a name="authoring-views"></a>Tworzenie widoków

Projektant XAML udostępnia widok XAML i zsynchronizowany widok projektu aplikacji renderowanego kodu znaczników XAML. Plik XAML jest otwarty w programie Visual Studio, można przełączać się między widoku projektu i widok XAML przy użyciu **projektowania** i **XAML** karty. Możesz użyć **Zamień okienka** przycisk, aby zmienić okno, które pojawia się na wierzchu: obszar roboczy lub edytora XAML.

W widoku Projekt zawierający okna *obszaru kompozycji* jest aktywnym oknem i służy jako powierzchnia podstawowego. Służy on do wizualnie projektować strony w aplikacji przez dodanie lub rysowania elementów i ich modyfikowania. Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md). Ta ilustracja przedstawia obszaru kompozycji w widoku Projekt.

![Widok projektu w Projektancie XAML](../designers/media/xaml_editor_design_view.png)

Te funkcje są dostępne w obszarze roboczym:

**Linii przyciągania**

Są liniami przyciągania *granice wyrównanie* , są wyświetlane jako linia przerywana red wierszy do wyświetlenia po wyrównania krawędzi kontrolki lub kiedy są wyrównane linii bazowych tekstu. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona.

**Rails siatki**

`Grid` Rails są używane do zarządzania, wierszy i kolumn w [siatki](/uwp/api/Windows.UI.Xaml.Controls.Grid) panelu. Można tworzyć i usuwać wiersze i kolumny, a można dostosować ich względne szerokości i wysokości. Szyny siatki pionowej, która pojawia się po lewej stronie obszaru roboczego, jest używany dla wierszy i linii poziomej, która pojawia się u góry, jest używany dla kolumn.

**Moduły definiowania układu siatki**

Moduł definiowania układu siatki jest wyświetlana jako trójkąt z linią pionową lub poziomą podłączone do niego na szynie siatki. Podczas przeciągania moduł definiowania układu siatki szerokości lub wysokości przyległe kolumny lub wiersze aktualizacji podczas przesuwania myszy.

Moduły definiowania układu siatki są używane do kontrolowania, szerokość i wysokość wierszy i kolumn siatki. Klikając przycisk w rails siatki, można dodać nowej kolumny lub wiersza. Po dodaniu nowego wiersza lub kolumny wiersza dla panelu siatki, która ma dwa lub więcej kolumn lub wierszy mini narzędzi pojawia się poza szyny, który umożliwia ustawianie szerokości i wysokości jawnie. Mini narzędzi można ustawić opcje zmiany rozmiaru siatki wierszy i kolumn.

**Uchwyty zmiany rozmiaru**

Zmień rozmiar obsługuje pojawiają się w zaznaczonych kontrolek oraz pozwalające użytkownikowi na zmienianie rozmiaru formantów. Podczas zmiany rozmiaru kontrolki wartości szerokości i wysokości wyświetlane są zwykle ułatwiające rozmiar kontrolki. Aby uzyskać więcej informacji na temat manipulowanie kontrolami w **projektowania** wyświetlić, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md).

**Marginesy**

Marginesy reprezentuje ilość stały odstęp między krawędzią formantu a krawędzią jej kontenera. Można ustawić marginesy kontrolki przy użyciu [margines](/uwp/api/windows.ui.xaml.frameworkelement.margin) właściwości pod **układ** w oknie dialogowym właściwości.

**Moduły definiowania układu marginesu**

Moduły definiowania układu marginesu można użyć, aby zmienić margines elementu względem jego kontener układu. Gdy marginesu jest otwarty, margines nie jest ustawiona, a moduł definiowania układu marginesu zawiera przerwany łańcuch. Gdy margines nie jest ustawiona, elementy pozostają przy zmianie rozmiaru kontener układu w czasie wykonywania. Po zamknięciu marginesu marginesu Wyświetla nieprzerwany łańcuch, a elementy przeniesione z marginesem jako kontener układu zmiany rozmiaru w czasie wykonywania (margines pozostaje stały).

**Obsługuje element**

Element można modyfikować za pomocą uchwytów elementów, które pojawiają się w obszarze kompozycji podczas przesuwania wskaźnika nad narożnikami niebieski prostokąt otaczający element. Uchwyty te umożliwiają obracanie, zmieniać rozmiar, przerzucić, Przenieś lub Dodaj promienia narożnika do elementu. Symbol uchwytu elementu zależy od funkcji, a następnie zmienia się w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwyty elementu, upewnij się, że element jest wybrany.

W **projektowania** widoku dodatkowe obszar roboczy polecenia są dostępne w obszarze lewej dolnej części ekranu, jak pokazano poniżej:

![Polecenia w widoku projektu](../designers/media/xaml_editor_design_controls.png)

Te polecenia są dostępne w tym narzędzi:

**Zoom**

Powiększenie umożliwia rozmiar powierzchni projektowej. Powiększenie z % 12,5 800% lub wybrać opcje takie jak **Dopasuj do wyboru** i **Dopasuj do wszystkich**.

**Pokaż/Ukryj siatkę przyciągania**

Wyświetla lub ukrywa przyciągania siatki, który pokazuje linie siatki. Linie siatki są używane, gdy zostanie włączone **przyciąganie do linii siatki** lub **przyciąganie do linii wyrównania**.

**Włącz/wyłącz przyciąganie do linii siatki**

Jeśli **przyciąganie do linii siatki** jest włączona, podczas przeciągania elementu w obszarze kompozycji, element zwykle przy najbliższej poziome i pionowe linie siatki.

**Włącz/wyłącz przyciąganie do linii wyrównania**

Linii przyciągania ułatwiają wyrównywanie formantów względem siebie nawzajem. Jeśli **przyciąganie do linii wyrównania** jest włączona, podczas przeciągania kontroli względem innych kontrolek wyrównanie granice są wyświetlane, gdy krawędzie i tekst niektóre kontrolki są wyrównane w poziomie lub pionie. Granicy wyrównania jest wyświetlana jako linia kreskowana czerwony.

W **XAML** widoku okna zawierającego edytora XAML jest aktywnym oknem, a Edytor XAML to podstawowe narzędzie autorskie. Extensible Application Markup Language (XAML) zapewnia słownictwa deklaratywne, oparty na formacie XML do określania interfejsu użytkownika aplikacji. Widok XAML zawiera, IntelliSense, automatycznego formatowania, wyróżnianie składni i nawigacji tagu. Ta ilustracja przedstawia widok XAML:

![Widok XAML](../designers/media/xaml_editor.png)

**Wyświetl podziału**

Pasek podziału widok wyświetlany u góry widoku XAML, gdy Edytor XAML znajduje się w dolnym oknie. Wyświetl pasek podziału umożliwia sterowanie względne rozmiary **projektowania** widoku i **XAML** widoku. Mogą również wymieniać lokalizacje widoki (przy użyciu **Zamień okienka** przycisku), a następnie określ, czy widoków ułożone poziomo lub pionowo i zwinąć którymś z widoków.

**Powiększenie znaczników**

Powiększenie znaczników umożliwia rozmiar **XAML** widoku. Możesz powiększyć z 20% do 400%.

## <a name="document-outline-window"></a>Okno konspektu dokumentu

Okno konspektu dokumentu w Projektancie XAML jest podobne do **obiekty i oś czasu** okna w programie Blend for Visual Studio. **Konspekt dokumentu** umożliwia wykonywanie następujących zadań:

- Wyświetlanie hierarchicznej struktury wszystkich elementów w obszarze kompozycji.

- Wybierz elementy, dzięki czemu możesz modyfikować je (przeniesienie ich wokół w hierarchii, zmodyfikuj je w obszarze kompozycji, ustawiać ich właściwości w oknie dialogowym właściwości i tak dalej). Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)

- Tworzenie i modyfikowanie szablonów elementów będących kontrolkami.

- Dla wybranych elementów, należy użyć menu kontekstowego (menu kontekstowe). Tego samego menu jest również dostępny dla wybranych elementów w obszarze kompozycji.

Aby wyświetlić **konspekt dokumentu** okna, na pasku menu wybierz **widoku** > **Windows inne** > **konspekt dokumentu**.

![Okno konspektu dokumentu w programie Visual Studio](../designers/media/document-outline-window.png)

Są to opcje dostępne w **konspekt dokumentu** okna:

**Konspekt dokumentu**

Widok główny w **konspekt dokumentu** okno wyświetla hierarchię dokumentu w strukturze drzewa. Hierarchiczny charakter konspekt dokumentu można użyć, aby zbadać dokument na różnych poziomach szczegółowości i blokowanie i ukrywanie elementów, pojedynczo lub w grupach.

**Pokaż/Ukryj**

Wyświetla lub ukrywa elementy obszaru kompozycji, które odpowiadają elementom konspekt dokumentu. Użyj **Pokaż/Ukryj** przycisków, które wyświetlić symbol oka po pokazano, lub naciśnij klawisz **Ctrl**+**H** do ukrywania elementów i **Shift** + **Ctrl**+**H** umożliwiający ich wyświetlenie.

**Lock/unlock**

Blokuje albo odblokowuje elementy obszaru kompozycji, które odpowiadają elementom konspekt dokumentu. Nie można zmodyfikować zablokowanych elementów. Użyj **Zablokuj/Odblokuj** przyciski wyświetlania symbolu kłódki, gdy zablokowany, lub naciśnij klawisz **Ctrl**+**L** elementy blokady i **Shift** + **Ctrl**+**L** je odblokować.

**Zwróć zakres do pageRoot**

Opcja w górnej części **konspekt dokumentu** okno, które znajduje się symbol strzałki, zwraca konspekt dokumentu do poprzedniego zakresu. Zakresu działa ma zastosowanie tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości

**Właściwości** okno służy do ustawiania wartości właściwości kontrolek. Poniżej przedstawiono wygląda następująco:

![Okno właściwości](../designers/media/xaml-designer-properties-window.png)

Istnieją różne opcje w górnej części **właściwości** okna. Nazwa aktualnie wybranego elementu można zmienić za pomocą **nazwa** pole. W lewym górnym rogu istnieje ikona reprezentująca obecnie wybranego elementu. Aby ustawić właściwości według kategorii lub alfabetycznie, kliknij przycisk **kategorii**, **nazwa**, lub **źródła** w **Rozmieść według** listy. Aby wyświetlić listę zdarzeń dla formantu, kliknij **zdarzenia** przycisk, który jest wyświetlany symbol bolt pod kątem obsługi.

Aby wyszukać właściwość, rozpocznij wpisywanie nazwy właściwości w polu wyszukiwania. **Właściwości** oknie zostaną wyświetlone właściwości, spełniających kryteria wyszukiwania. Niektóre właściwości umożliwiają ustawianie zaawansowanych właściwości, wybierając przycisk strzałki w dół.

Aby uzyskać więcej informacji na temat używania właściwości i obsługa zdarzeń, zobacz [wprowadzenie do kontrolek i wzorce](/windows/uwp/design/controls-and-patterns/controls-and-events-intro)

Po prawej stronie każdej właściwości jest wartość *znacznik właściwości* wyświetlany jako symbol pola. Wygląd znacznika właściwość wskazuje, czy powiązanie danych lub zasób stosowany do właściwości. Na przykład symbol białe pola wskazuje wartość domyślną, symbol czarne pole zwykle wskazuje, że zastosowano zasobu lokalnego i pole pomarańczowy zwykle wskazuje, że zastosowano powiązanie danych. Po kliknięciu znacznik właściwości, przejdź do definicji stylu, otworzyć Konstruktor powiązań danych lub otworzyć selektor zasobów.

## <a name="see-also"></a>Zobacz także

- [Praca z elementami w projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)
- [Tworzenie i stosowanie zasobów](../designers/how-to-create-and-apply-a-resource.md)
- [Przewodnik: wiązanie z danymi w projektancie XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)