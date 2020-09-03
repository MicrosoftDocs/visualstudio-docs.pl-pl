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
ms.openlocfilehash: d230d9a4719e1757820de87b60bcc7566a785f99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844017"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant XAML w programie Visual Studio udostępnia interfejs wizualny ułatwiający projektowanie aplikacji do sklepu Windows, Windows Phone, WPF i Silverlight w języku XAML. Możesz tworzyć interfejsy użytkownika dla aplikacji, przeciągając kontrolki z **przybornika** i ustawiając właściwości w oknie **Właściwości** . Możesz również edytować XAML bezpośrednio w widoku XAML.

 Aby uzyskać zaawansowane zadania projektowania XAML, takie jak animacje i zachowania, zobacz [Tworzenie interfejsu użytkownika przy użyciu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>projektant XAML obszar roboczy
 Obszar roboczy w projektant XAML składa się z kilku elementów interfejsu wizualizacji. Obejmują one obszar kompozycji, Edytor XAML, okno urządzenia, okno konspektu dokumentu i okno Właściwości. Aby otworzyć projektant XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksplorator rozwiązań** i wybierz polecenie **Projektant widoków**.

## <a name="authoring-views"></a>Widoki autorstwa
 Projektant XAML udostępnia widok XAML i zsynchronizowaną widok Projekt renderowanego znacznika języka XAML aplikacji. Gdy plik XAML jest otwarty w programie Visual Studio, można przełączać się między widok Projekt i widokiem XAML przy użyciu kart **projektowanie** i **XAML** . Możesz użyć przycisku **Zamień okienka** , aby przełączyć okno wyświetlane na górze: obszar kompozycji lub Edytor XAML.

 W widok Projekt okno z *obszarem roboczym* jest oknem aktywnym i można go użyć jako podstawowej powierzchni roboczej. Można jej użyć do wizualnego projektowania strony w aplikacji przez dodawanie lub rysowanie elementów, a następnie poprzez ich modyfikowanie. Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md). Na tej ilustracji przedstawiono obszar kompozycji w widok Projekt.

 ![widok Projekt projektant XAML](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Te funkcje są dostępne w obszarze kompozycji:

 **Linii wyrównania** Linii wyrównania są *granicami wyrównania* , które są wyświetlane w postaci czerwonych kresek, aby pokazać, kiedy są wyrównane krawędzie formantów, lub gdy są wyrównane linie bazowe tekstu. Granice wyrównania są wyświetlane tylko wtedy, gdy jest włączone **przyciąganie do linii wyrównania** .

 **Szyny siatki** `Grid` szyny służą do zarządzania wierszami i kolumnami w panelu [siatki](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) . Można tworzyć i usuwać wiersze i kolumny oraz zmieniać ich względne szerokości i wysokości. Kolejka siatki pionowej, która pojawia się po lewej stronie obszaru kompozycji, jest używana w przypadku wierszy, a linia pozioma, która pojawia się u góry, jest używana na potrzeby kolumn.

 Moduły **definiowania układu siatki** Moduł `Grid` definiowania układu jest wyświetlany jako Trójkąt, który ma linię pionową lub poziomą dołączoną do niej na `Grid` szynie. Gdy przeciągniesz moduł `Grid` definiowania układu, Szerokość lub wysokość sąsiadujących kolumn lub wierszy są aktualizowane podczas przesuwania myszy.

 `Grid` Moduły definiowania układu służą do sterowania szerokością i wysokością `Grid` wierszy i kolumn. Aby dodać nową kolumnę lub wiersz, kliknij `Grid` kolejno pozycje szyny. Gdy dodasz nowy wiersz lub wiersz kolumny dla `Grid` panelu, który ma dwie lub więcej kolumn lub wierszy, wyświetlany jest minipasek narzędzi poza szyną, która umożliwia jawne ustawienie szerokości i wysokości. Minipasek narzędzi umożliwia ustawianie opcji ustalania rozmiarów dla `Grid` wierszy i kolumn.

 **Uchwyty zmiany rozmiaru** Uchwyty zmiany rozmiaru są wyświetlane w wybranych kontrolkach i umożliwiają zmianę rozmiaru kontrolki. Zmiana rozmiaru kontrolki powoduje, że wartości szerokości i wysokości są zwykle wyświetlane w celu ułatwienia rozmiaru formantu. Aby uzyskać więcej informacji na temat manipulowania kontrolkami w widok Projekt, zobacz [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md).

 **Marginesy** Marginesy reprezentują ilość miejsca stałego między krawędzią kontrolki a krawędzią jej kontenera. Marginesy kontrolki można ustawić przy użyciu właściwości [marginesu](https://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) w obszarze **Układ** w okno właściwości.

 Moduły **definiowania układu marginesu** Za pomocą modułów definiowania marginesów można zmienić marginesy elementu względem jego kontenera układu. Gdy jest otwarty moduł definiowania układu marginesu, margines nie jest ustawiony, a moduł definiowania układu marginesu wyświetla przerwany łańcuch. Gdy margines nie jest ustawiony, elementy pozostaną w miejscu, gdy rozmiar kontenera układu zostanie zmieniony w czasie wykonywania. Gdy moduł definiowania układu marginesu jest zamknięty, moduł definiowania układu marginesu wyświetla nieprzerwany łańcuch, a elementy będą przenoszone wraz z marginesem, gdy rozmiar kontenera układów zostanie zmieniony w czasie wykonywania (margines pozostaje ustalony).

 **Uchwyty elementu** Można zmodyfikować element przy użyciu uchwytów elementu, które pojawiają się w obszarze kompozycji po przesunięciu wskaźnika myszy nad rogi niebieskiego pola otaczającego element. Te uchwyty umożliwiają obracanie, zmienianie rozmiaru, przerzucanie, przenoszenie i dodawanie do elementu promienia narożnika. Symbol uchwytu elementu zależy od funkcji i zmienia się w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwytów elementu, upewnij się, że element jest zaznaczony.

 W widok Projekt dodatkowe polecenia obszaru roboczego są dostępne w dolnym lewym obszarze ekranu, jak pokazano poniżej:

 ![Polecenia widok Projekt](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Te polecenia są dostępne na tym pasku narzędzi:

 **Powiększenie** Powiększenie umożliwia zmianę rozmiaru powierzchni projektowej. Możesz powiększyć od 12,5% do 800% lub wybrać opcje, takie jak **Dopasuj do zaznaczenia** i **Dopasuj do wszystkich**.

 **Pokaż/Ukryj siatkę przyciągania** Wyświetla lub ukrywa siatkę przyciągania pokazującą linie siatki. Linie siatki są używane, gdy jest włączone **przyciąganie do linii siatki** lub **przyciąganie do linii wyrównania** .

 **Włącz/Wyłącz przyciąganie do linii siatki** Jeśli **przyciąganie do linii siatki** jest włączone po przeciągnięciu elementu w obszarze kompozycji, element ma być wyrównany do najbliższych poziomych i pionowych linii siatki.

 **Włącz/Wyłącz przyciąganie do linii wyrównania** Linii wyrównania ułatwiają wyrównywanie formantów względem siebie. Jeśli **przyciąganie do linii wyrównania** jest włączone, gdy przeciągasz kontrolkę względem innych kontrolek, pojawiają się granice wyrównania, gdy krawędzie i tekst niektórych kontrolek są wyrównane w poziomie lub w pionie. Granica wyrównania pojawia się jako linia czerwona.

 W widoku XAML okno zawierające Edytor XAML jest aktywnym oknem, a Edytor XAML jest głównym narzędziem do tworzenia. Extensible Application Markup Language (XAML) zawiera deklaratywne słownictwo oparte na języku XML do określania interfejsu użytkownika aplikacji. Widok XAML zawiera funkcje IntelliSense, automatyczne formatowanie, wyróżnianie składni i nawigowanie po tagach. Na tej ilustracji przedstawiono widok XAML:

 ![Widok XAML](../designers/media/xaml-editor.png "xaml_editor")

 **Pasek widoku dzielonego** Pasek Widok podzielony pojawia się u góry widoku XAML, gdy Edytor XAML znajduje się w dolnym oknie. Pasek Widok podzielony pozwala kontrolować względne rozmiary widok Projekt i widoku XAML. Można również wymienić lokalizacje widoków (za pomocą przycisku **Zamień okienka** ), określić, czy widoki są ułożone w poziomie, czy w pionie, i zwijać każdy widok.

 **Powiększenie znaczników** Powiększenie znaczników umożliwia rozmiar widoku XAML. Możesz powiększyć od 20% do 400%.

## <a name="device-window"></a>Okno urządzenia
 Okno urządzenia w projektant XAML umożliwia symulowanie w czasie projektowania różnych widoków, wyświetlanie i wyświetlanie opcji dla Sklepu Windows lub projektu Windows Phone. Okno urządzenia jest dostępne w menu **projekt** podczas pracy w Projektant XAML. Oto jak wygląda:

 ![Okno urządzenia](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Dostępne są następujące opcje w oknie urządzenia:

 **Wyświetl** Określa różne rozmiary i rozdzielczości dla aplikacji.

 **Orientacja** Określa różne orientacje dla aplikacji: **pozioma** lub **pionowa**.

 **Krawędź** Określa różne wyrównania krawędzi dla **aplikacji: w** **lewo**, w **prawo**lub **Brak**.

 **Duży kontrast** Wyświetl podgląd aplikacji na podstawie wybranego ustawienia kontrastu. To ustawienie ustawiające wartość inną niż **Domyślna**spowoduje zastąpienie `RequestedTheme` Właściwości ustawionej w pliku App. XAML.

 **Przesłoń skalowanie** Włącza i wyłącza emulację skalowania dokumentu na powierzchni projektowej. Pozwala to zwiększyć procent skalowania według jednego czynnika. Zaznacz to pole wyboru, aby włączyć emulację. Na przykład jeśli wartość procentowa skalowania wynosi 100%, dokument na powierzchni projektowej będzie skalowany w górę do 140%. Ta opcja jest wyłączona, jeśli bieżąca wartość procentowa skalowania to 180.

 **Minimalna szerokość** Określa ustawienie minimalnej szerokości. Szerokość minimalna można zmienić w pliku App. XAML.

 **Motyw** Określa motyw aplikacji. Można na przykład zmienić motyw ciemny i jasny.

 **Pokaż Chrome** Włącza i wyłącza symulowaną ramkę tabletu wokół aplikacji w widok Projekt. Zaznacz pole wyboru, aby wyświetlić ramkę.

 **Przytnij do ekranu** Określa tryb wyświetlania. Zaznacz pole wyboru, aby wyciąć rozmiar dokumentu do rozmiaru ekranu.

## <a name="document-outline-window"></a>Okno konspektu dokumentu
 Okno Konspekt dokumentu w projektant XAML ułatwia wykonywanie następujących zadań:

- Wyświetl hierarchiczną strukturę wszystkich elementów w obszarze kompozycji.

- Wybierz elementy, aby można je było modyfikować (przenosić je w hierarchii, modyfikować je w obszarze kompozycji, ustawiać ich właściwości w okno Właściwości itd.). Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md)

- Tworzenie i modyfikowanie szablonów dla elementów, które są kontrolkami.

- Użyj menu kontekstowego dla wybranych elementów. To samo menu jest również dostępne dla wybranych elementów w obszarze kompozycji.

  Aby wyświetlić okno Konspekt dokumentu, na pasku menu wybierz **Widok**, **inne okna**, **Konspekt dokumentu**.

  ![Okno konspektu dokumentu](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Są to opcje dostępne w oknie Konspekt dokumentu:

  **Konspekt dokumentu** Widok główny w oknie Konspekt dokumentu zawiera hierarchię dokumentu w strukturze drzewa. Możesz użyć hierarchicznego charakteru konspektu dokumentu, aby przeanalizować dokument na różnych poziomach szczegółowości i zablokować i ukryć elementy pojedynczo lub w grupach.

  **Pokaż/Ukryj** Wyświetla lub ukrywa elementy obszaru roboczego odpowiadające elementom w konspekcie dokumentu. Użyj przycisków **Pokaż/Ukryj** , aby wyświetlić symbol oka, gdy jest wyświetlany, lub naciśnij klawisze CTRL + H, aby ukryć elementy, a następnie klawisze Shift + Ctrl + H, aby je wyświetlić.

  **Zablokuj/Odblokuj** Blokuje lub odblokowuje elementy obszaru roboczego odpowiadające elementom w konspekcie dokumentu. Nie można modyfikować zablokowanych elementów. Użyj przycisków **blokowania/odblokowywania** , które wyświetlają symbol kłódki po zablokowaniu, lub naciśnij kombinację klawiszy Ctrl + L, aby zablokować elementy i Shift + Ctrl + L, aby je odblokować.

  **Zwróć zakres do pageRoot** Opcja w górnej części okna konspektu dokumentu, która wyświetla symbol strzałki w górę, zwraca Konspekt dokumentu do poprzedniego zakresu. Określanie zakresu jest stosowane tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości
 Okno Właściwości umożliwia ustawianie wartości właściwości w kontrolkach. Oto jak wygląda:

 ![Okno właściwości](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Dostępne są różne opcje w górnej części okno Właściwości. Nazwę aktualnie zaznaczonego elementu można zmienić przy użyciu pola **Nazwa** . W lewym górnym rogu znajduje się ikona reprezentująca aktualnie wybrany element. Aby rozmieścić właściwości według kategorii lub alfabetycznie, kliknij pozycję **Kategoria**, **Nazwa**lub **Źródło** na liście **Rozmieść według** . Aby wyświetlić listę zdarzeń dla kontrolki, kliknij przycisk **zdarzenia** , który wyświetla Symbol błyskawicy. Aby wyszukać właściwość, Zacznij od wpisania nazwy właściwości w polu **Właściwości wyszukiwania** . Okno Właściwości wyświetla właściwości, które pasują do wyszukiwania podczas wpisywania. Niektóre właściwości pozwalają ustawić zaawansowane właściwości, wybierając przycisk strzałki w dół. Aby uzyskać więcej informacji na temat używania właściwości i obsługi zdarzeń, zobacz [Szybki Start: Dodawanie kontrolek i obsługa zdarzeń](https://msdn.microsoft.com/library/windows/apps/xaml/hh465336.aspx)

 Po prawej stronie każdej wartości właściwości jest *znacznik właściwości* , który jest wyświetlany jako symbol pola. Wygląd znacznika właściwości wskazuje, czy istnieje powiązanie danych lub zasób zastosowany do właściwości. Na przykład symbol białego znaku wskazuje wartość domyślną, symbol czarnego pudełka zwykle wskazuje, że zastosowano zasób lokalny, a pomarańczowe pole zazwyczaj wskazuje, że zostało zastosowane powiązanie danych. Po kliknięciu znacznika właściwości można przejść do definicji stylu, otworzyć konstruktora powiązań danych lub otworzyć selektor zasobów.

## <a name="see-also"></a>Zobacz też
 [Praca z elementami w Projektant XAML](../designers/working-with-elements-in-xaml-designer.md) [sposób tworzenia i stosowania](../designers/how-to-create-and-apply-a-resource.md) [przewodnika po zasobach: powiązanie z danymi w Projektant XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
