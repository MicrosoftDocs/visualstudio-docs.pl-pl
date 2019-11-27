---
title: Tworzenie interfejsu użytkownika przy użyciu projektanta XAML
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 879d8457a0f5fd4bf63a2d69a4f3f026ce4c6fe1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74294665"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant XAML w programie Visual Studio udostępnia interfejs graficzny, aby ułatwić projektowanie XAML aplikacje Windows Store, Windows Phone, WPF i Silverlight. Możesz tworzyć interfejsy użytkownika dla aplikacji, przeciągając kontrolki z **przybornika** i ustawiając właściwości w oknie **Właściwości** . Można również edytować XAML bezpośrednio w widoku XAML.

 Aby uzyskać zaawansowane zadania projektowania XAML, takie jak animacje i zachowania, zobacz [Tworzenie interfejsu użytkownika przy użyciu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>Obszar roboczy Projektanta XAML
 Obszar roboczy w Projektancie XAML składa się z kilku elementów interfejsu wizualnego. Obejmują one edytora XAML w obszarze kompozycji urządzenia okna, okno konspektu dokumentu i okna właściwości. Aby otworzyć projektant XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksplorator rozwiązań** i wybierz polecenie **Projektant widoków**.

## <a name="authoring-views"></a>Tworzenie widoków
 Projektant XAML udostępnia widok XAML i zsynchronizowany widok projektu aplikacji renderowanego kodu znaczników XAML. Gdy plik XAML jest otwarty w programie Visual Studio, można przełączać się między widok Projekt i widokiem XAML przy użyciu kart **projektowanie** i **XAML** . Możesz użyć przycisku **Zamień okienka** , aby przełączyć okno wyświetlane na górze: obszar kompozycji lub Edytor XAML.

 W widok Projekt okno z *obszarem roboczym* jest oknem aktywnym i można go użyć jako podstawowej powierzchni roboczej. Służy on do wizualnie projektować strony w aplikacji przez dodanie lub rysowania elementów i ich modyfikowania. Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md). Ta ilustracja przedstawia obszaru kompozycji w widoku Projekt.

 ![widok Projekt projektant XAML](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Te funkcje są dostępne w obszarze roboczym:

 **Linii wyrównania** Linii wyrównania są *granicami wyrównania* , które są wyświetlane w postaci czerwonych kresek, aby pokazać, kiedy są wyrównane krawędzie formantów, lub gdy są wyrównane linie bazowe tekstu. Granice wyrównania są wyświetlane tylko wtedy, gdy jest włączone **przyciąganie do linii wyrównania** .

 **Szyny siatki** `Grid` szyny są używane do zarządzania wierszami i kolumnami w panelu [siatki](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) . Można tworzyć i usuwać wiersze i kolumny, a można dostosować ich względne szerokości i wysokości. Szyny siatki pionowej, która pojawia się po lewej stronie obszaru roboczego, jest używany dla wierszy i linii poziomej, która pojawia się u góry, jest używany dla kolumn.

 Moduły **definiowania układu siatki** `Grid` moduł definiowania układu pojawia się jako Trójkąt, który ma linię pionową lub poziomą dołączoną do niej na `Grid` szynie. Gdy przeciągniesz moduł definiowania `Grid`, Szerokość lub wysokość sąsiadujących kolumn lub wierszy są aktualizowane podczas przesuwania myszy.

 Moduły definiowania układu `Grid` są używane do sterowania szerokością i wysokością wierszy i kolumn `Grid`. Możesz dodać nową kolumnę lub wiersz, klikając kolejno `Grid`. Gdy dodasz nowy wiersz lub wiersz kolumny dla panelu `Grid`, który ma dwie lub więcej kolumn lub wierszy, wyświetlany jest minipasek narzędzi poza szyną, która umożliwia jawne Ustawianie szerokości i wysokości. Minipasek narzędzi umożliwia ustawianie opcji ustalania rozmiarów `Grid` wierszy i kolumn.

 **Uchwyty zmiany rozmiaru** Uchwyty zmiany rozmiaru są wyświetlane w wybranych kontrolkach i umożliwiają zmianę rozmiaru kontrolki. Podczas zmiany rozmiaru kontrolki wartości szerokości i wysokości wyświetlane są zwykle ułatwiające rozmiar kontrolki. Aby uzyskać więcej informacji na temat manipulowania kontrolkami w widok Projekt, zobacz [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md).

 **Marginesy** Marginesy reprezentują ilość miejsca stałego między krawędzią kontrolki a krawędzią jej kontenera. Marginesy kontrolki można ustawić przy użyciu właściwości [marginesu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) w obszarze **Układ** w okno właściwości.

 Moduły **definiowania układu marginesu** Za pomocą modułów definiowania marginesów można zmienić marginesy elementu względem jego kontenera układu. Gdy marginesu jest otwarty, margines nie jest ustawiona, a moduł definiowania układu marginesu zawiera przerwany łańcuch. Margines nie jest ustawiony, elementy pozostają w miejscu, o przy zmianie rozmiaru kontener układu w czasie wykonywania. Po zamknięciu marginesu marginesu Wyświetla nieprzerwany łańcuch, a elementy zostaną przeniesione z marginesem jako kontener układu zmiany rozmiaru w czasie wykonywania (margines pozostaje stały).

 **Uchwyty elementu** Można zmodyfikować element przy użyciu uchwytów elementu, które pojawiają się w obszarze kompozycji po przesunięciu wskaźnika myszy nad rogi niebieskiego pola otaczającego element. Uchwyty te umożliwiają obracanie, zmieniać rozmiar, przerzucić, Przenieś lub Dodaj promienia narożnika do elementu. Symbol uchwytu elementu zależy od funkcji, a następnie zmienia się w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwyty elementu, upewnij się, że element jest wybrany.

 W widoku Projekt obszaru kompozycji dodatkowe polecenia są dostępne w lewej dolnej części ekranu, jak pokazano poniżej:

 ![Polecenia widok Projekt](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Te polecenia są dostępne w tym narzędzi:

 **Powiększenie** Powiększenie umożliwia zmianę rozmiaru powierzchni projektowej. Możesz powiększyć od 12,5% do 800% lub wybrać opcje, takie jak **Dopasuj do zaznaczenia** i **Dopasuj do wszystkich**.

 **Pokaż/Ukryj siatkę przyciągania** Wyświetla lub ukrywa siatkę przyciągania pokazującą linie siatki. Linie siatki są używane, gdy jest włączone **przyciąganie do linii siatki** lub **przyciąganie do linii wyrównania** .

 **Włącz/Wyłącz przyciąganie do linii siatki** Jeśli **przyciąganie do linii siatki** jest włączone po przeciągnięciu elementu w obszarze kompozycji, element ma być wyrównany do najbliższych poziomych i pionowych linii siatki.

 **Włącz/Wyłącz przyciąganie do linii wyrównania** Linii wyrównania ułatwiają wyrównywanie formantów względem siebie. Jeśli **przyciąganie do linii wyrównania** jest włączone, gdy przeciągasz kontrolkę względem innych kontrolek, pojawiają się granice wyrównania, gdy krawędzie i tekst niektórych kontrolek są wyrównane w poziomie lub w pionie. Granicy wyrównania jest wyświetlana jako linia kreskowana czerwony.

 W widoku XAML okno zawierające edytora XAML jest aktywnym oknem, a Edytor XAML to podstawowe narzędzie autorskie. Extensible Application Markup Language (XAML) zapewnia słownictwa deklaratywne, oparty na formacie XML do określania interfejsu użytkownika aplikacji. Widok XAML zawiera, IntelliSense, automatycznego formatowania, wyróżnianie składni i nawigacji tagu. Ta ilustracja przedstawia widok XAML:

 ![Widok XAML](../designers/media/xaml-editor.png "xaml_editor")

 **Pasek widoku dzielonego** Pasek Widok podzielony pojawia się u góry widoku XAML, gdy Edytor XAML znajduje się w dolnym oknie. Wyświetl pasek podziału umożliwia sterowanie względne rozmiary widoku projektu i widok XAML. Można również wymienić lokalizacje widoków (za pomocą przycisku **Zamień okienka** ), określić, czy widoki są ułożone w poziomie, czy w pionie, i zwijać każdy widok.

 **Powiększenie znaczników** Powiększenie znaczników umożliwia rozmiar widoku XAML. Możesz powiększyć z 20% do 400%.

## <a name="device-window"></a>Okno urządzenia
 Okno urządzenia w programie XAML Designer umożliwia symulowanie w czasie projektowania, różnych widoków, ekranów i wyświetlić opcje projektu Windows Store lub Windows Phone. Okno urządzenia jest dostępne w menu **projekt** podczas pracy w Projektant XAML. Poniżej przedstawiono wygląda następująco:

 ![Okno urządzenia](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Oto opcje dostępne w oknie urządzenia:

 **Wyświetl** Określa różne rozmiary i rozdzielczości dla aplikacji.

 **Orientacja** Określa różne orientacje dla aplikacji: **pozioma** lub **pionowa**.

 **Krawędź** Określa różne wyrównania krawędzi dla **aplikacji: w** **lewo**, w **prawo**lub **Brak**.

 **Duży kontrast** Wyświetl podgląd aplikacji na podstawie wybranego ustawienia kontrastu. To ustawienie, gdy jest ustawiona na wartość inną niż **Domyślna**, spowoduje zastąpienie właściwości `RequestedTheme` ustawionej w pliku App. XAML.

 **Przesłoń skalowanie** Włącza i wyłącza emulację skalowania dokumentu na powierzchni projektowej. Dzięki temu można zwiększyć procent skalowania przez jeden składnik. Zaznacz pole wyboru, aby włączyć emulacji. Na przykład jeśli Twoje procent skalowania wynosi 100%, dokumentu w powierzchni projektowej skalowane wraz ze 140%. Ta opcja jest wyłączona, jeśli bieżąca wartość skalowania jest 180.

 **Minimalna szerokość** Określa ustawienie minimalnej szerokości. Minimalna szerokość można zmienić w pliku App.xaml.

 **Motyw** Określa motyw aplikacji. Na przykład może przełączać się między ciemnoszary i motyw jasny.

 **Pokaż Chrome** Włącza i wyłącza symulowaną ramkę tabletu wokół aplikacji w widok Projekt. Zaznacz pole wyboru, aby wyświetlić ramki.

 **Przytnij do ekranu** Określa tryb wyświetlania. Zaznacz pole wyboru, kiedy należy przyciąć rozmiar dokumentu do rozmiaru ekranu.

## <a name="document-outline-window"></a>Okno konspektu dokumentu
 Okno konspektu dokumentu w Projektancie XAML pomaga wykonywać następujące zadania:

- Wyświetlanie hierarchicznej struktury wszystkich elementów w obszarze kompozycji.

- Wybierz elementy, dzięki czemu możesz modyfikować je (przeniesienie ich wokół w hierarchii, zmodyfikuj je w obszarze kompozycji, ustawiać ich właściwości w oknie dialogowym właściwości i tak dalej). Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md)

- Tworzenie i modyfikowanie szablonów elementów będących kontrolkami.

- Użyj menu kontekstowego dla wybranych elementów. Tego samego menu jest również dostępny dla wybranych elementów w obszarze kompozycji.

  Aby wyświetlić okno Konspekt dokumentu, na pasku menu wybierz **Widok**, **inne okna**, **Konspekt dokumentu**.

  ![Okno konspektu dokumentu](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Oto opcje dostępne w oknie konspekt dokumentu:

  **Konspekt dokumentu** Widok główny w oknie Konspekt dokumentu zawiera hierarchię dokumentu w strukturze drzewa. Hierarchiczny charakter konspekt dokumentu można użyć, aby zbadać dokument na różnych poziomach szczegółowości i blokowanie i ukrywanie elementów, pojedynczo lub w grupach.

  **Pokaż/Ukryj** Wyświetla lub ukrywa elementy obszaru roboczego odpowiadające elementom w konspekcie dokumentu. Użyj przycisków **Pokaż/Ukryj** , aby wyświetlić symbol oka, gdy jest wyświetlany, lub naciśnij klawisze CTRL + H, aby ukryć elementy, a następnie klawisze Shift + Ctrl + H, aby je wyświetlić.

  **Zablokuj/Odblokuj** Blokuje lub odblokowuje elementy obszaru roboczego odpowiadające elementom w konspekcie dokumentu. Nie można zmodyfikować zablokowanych elementów. Użyj przycisków **blokowania/odblokowywania** , które wyświetlają symbol kłódki po zablokowaniu, lub naciśnij kombinację klawiszy Ctrl + L, aby zablokować elementy i Shift + Ctrl + L, aby je odblokować.

  **Zwróć zakres do pageRoot** Opcja w górnej części okna konspektu dokumentu, która wyświetla symbol strzałki w górę, zwraca Konspekt dokumentu do poprzedniego zakresu. Zakresu działa ma zastosowanie tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości
 W oknie właściwości służy do ustawiania wartości właściwości kontrolek. Poniżej przedstawiono wygląda następująco:

 ![okno Właściwości](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Istnieją różne opcje w górnej części okna właściwości. Nazwę aktualnie zaznaczonego elementu można zmienić przy użyciu pola **Nazwa** . W lewym górnym rogu istnieje ikona reprezentująca obecnie wybranego elementu. Aby rozmieścić właściwości według kategorii lub alfabetycznie, kliknij pozycję **Kategoria**, **Nazwa**lub **Źródło** na liście **Rozmieść według** . Aby wyświetlić listę zdarzeń dla kontrolki, kliknij przycisk **zdarzenia** , który wyświetla Symbol błyskawicy. Aby wyszukać właściwość, Zacznij od wpisania nazwy właściwości w polu **Właściwości wyszukiwania** . Okno właściwości wyświetla właściwości, spełniających kryteria wyszukiwania. Niektóre właściwości umożliwiają ustawianie zaawansowanych właściwości, wybierając przycisk strzałki w dół. Aby uzyskać więcej informacji na temat używania właściwości i obsługi zdarzeń, zobacz [Szybki Start: Dodawanie kontrolek i obsługa zdarzeń](https://go.microsoft.com/fwlink/?LinkID=247983)

 Po prawej stronie każdej wartości właściwości jest *znacznik właściwości* , który jest wyświetlany jako symbol pola. Wygląd znacznika właściwość wskazuje, czy powiązanie danych lub zasób stosowany do właściwości. Na przykład symbol białe pola wskazuje wartość domyślną, symbol czarne pole zwykle wskazuje, że zastosowano zasobu lokalnego i pole pomarańczowy zwykle wskazuje, że zastosowano powiązanie danych. Po kliknięciu znacznik właściwości, przejdź do definicji stylu, otworzyć Konstruktor powiązań danych lub otworzyć selektor zasobów.

## <a name="see-also"></a>Zobacz też
 [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md) [sposób tworzenia i stosowania](../designers/how-to-create-and-apply-a-resource.md) [przewodnika po zasobach: powiązanie z danymi w Projektant XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
