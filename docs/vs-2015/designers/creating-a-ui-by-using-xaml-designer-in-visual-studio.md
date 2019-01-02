---
title: Tworzenie interfejsu użytkownika przy użyciu projektanta XAML
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.XamlDesigner
- VS.DevicePanel
- VS.XamlEditor
- VS.DocumentOutline
ms.assetid: c54969a7-d75a-4a35-9b37-af7a596a7c24
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3bd82bd99901ba0b8df400e3780b17d1baadab0c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53837293"
---
# <a name="creating-a-ui-by-using-xaml-designer-in-visual-studio"></a>Tworzenie interfejsu użytkownika przy użyciu projektanta XAML w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Projektant XAML w programie Visual Studio udostępnia interfejs graficzny, aby ułatwić projektowanie XAML aplikacje Windows Store, Windows Phone, WPF i Silverlight. Można utworzyć interfejsów użytkownika dla aplikacji poprzez przeciąganie kontrolek z **przybornika** i ustawianie właściwości w **właściwości** okna. Można również edytować XAML bezpośrednio w widoku XAML.

 Aby uzyskać zaawansowane zadania projektowania XAML, takich jak animacjom i zachowaniom, zobacz [Tworzenie interfejsu użytkownika przy użyciu programu Blend for Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md).

## <a name="xaml-designer-workspace"></a>Obszar roboczy Projektanta XAML
 Obszar roboczy w Projektancie XAML składa się z kilku elementów interfejsu wizualnego. Obejmują one edytora XAML w obszarze kompozycji urządzenia okna, okno konspektu dokumentu i okna właściwości. Aby otworzyć projektanta XAML, kliknij prawym przyciskiem myszy plik XAML w **Eksploratora rozwiązań** i wybierz polecenie **Projektant widoków**.

## <a name="authoring-views"></a>Tworzenie widoków
 Projektant XAML udostępnia widok XAML i zsynchronizowany widok projektu aplikacji renderowanego kodu znaczników XAML. Plik XAML jest otwarty w programie Visual Studio, można przełączać się między widoku projektu i widok XAML przy użyciu **projektowania** i **XAML** karty. Możesz użyć **Zamień okienka** przycisk, aby zmienić okno, które pojawia się na wierzchu: obszar roboczy lub edytora XAML.

 W widoku Projekt zawierający okna *obszaru kompozycji* jest aktywnym oknem i służy jako powierzchnia podstawowego. Służy on do wizualnie projektować strony w aplikacji przez dodanie lub rysowania elementów i ich modyfikowania. Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md). Ta ilustracja przedstawia obszaru kompozycji w widoku Projekt.

 ![Widok projektanta XAML projektu](../designers/media/xaml-editor-design-view.png "xaml_editor_design_view")

 Te funkcje są dostępne w obszarze roboczym:

 **Linii przyciągania** linii przyciągania są *granice wyrównanie* , są wyświetlane jako linia przerywana red wierszy do wyświetlenia po wyrównania krawędzi kontrolki lub kiedy są wyrównane linii bazowych tekstu. Wyrównanie granice są wyświetlane tylko wtedy, gdy **przyciąganie do linii wyrównania** jest włączona.

 **Siatka rails** `Grid` rails są używane do zarządzania, wierszy i kolumn w [siatki](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.grid.aspx) panelu. Można tworzyć i usuwać wiersze i kolumny, a można dostosować ich względne szerokości i wysokości. Szyny siatki pionowej, która pojawia się po lewej stronie obszaru roboczego, jest używany dla wierszy i linii poziomej, która pojawia się u góry, jest używany dla kolumn.

 **Moduły definiowania układu siatki** A `Grid` moduł definiowania układu kodu jest wyświetlany jako trójkąt z linią pionową lub poziomą dołączony do niego `Grid` szyny. Podczas przeciągania `Grid` moduł definiowania układu kodu, szerokości lub wysokości przyległe kolumny lub wiersze aktualizacji podczas przesuwania myszy.

 `Grid` Moduły definiowania układu są używane do kontrolowania, szerokość i wysokość `Grid`firmy wierszy i kolumn. Można dodać nowej kolumny lub wiersza, klikając przycisk w `Grid` platformy rails. Po dodaniu nowego wiersza lub kolumny wiersza dla `Grid` poza szyny, który umożliwia ustawianie szerokości i wysokości jawnie zostanie wyświetlony panel, zawierający co najmniej dwie kolumny lub wiersze, mini narzędzi. Mini narzędzi pozwala ustawić opcje ustalania rozmiaru `Grid` wierszy i kolumn.

 **Uchwyty zmiany rozmiaru** uchwytami zmiany rozmiaru pojawiają się w zaznaczonych kontrolek oraz pozwalające użytkownikowi na zmienianie rozmiaru formantów. Podczas zmiany rozmiaru kontrolki wartości szerokości i wysokości wyświetlane są zwykle ułatwiające rozmiar kontrolki. Aby uzyskać więcej informacji na temat manipulowanie kontrolami w widoku projektu, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md).

 **Marginesy** marginesy reprezentują ilość stały odstęp między krawędzią formantu a krawędzią jej kontenera. Można ustawić marginesy kontrolki przy użyciu [margines](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.frameworkelement.margin.aspx) właściwości pod **układ** w oknie dialogowym właściwości.

 **Moduły definiowania układu marginesu** moduły definiowania układu marginesu można użyć, aby zmienić margines elementu względem jego kontener układu. Gdy marginesu jest otwarty, margines nie jest ustawiona, a moduł definiowania układu marginesu zawiera przerwany łańcuch. Margines nie jest ustawiony, elementy pozostają w miejscu, o przy zmianie rozmiaru kontener układu w czasie wykonywania. Po zamknięciu marginesu marginesu Wyświetla nieprzerwany łańcuch, a elementy zostaną przeniesione z marginesem jako kontener układu zmiany rozmiaru w czasie wykonywania (margines pozostaje stały).

 **Obsługuje element** można zmodyfikować elementu za pomocą uchwytów elementów, które pojawiają się w obszarze kompozycji podczas przesuwania wskaźnika nad narożnikami niebieski prostokąt otaczający element. Uchwyty te umożliwiają obracanie, zmieniać rozmiar, przerzucić, Przenieś lub Dodaj promienia narożnika do elementu. Symbol uchwytu elementu zależy od funkcji, a następnie zmienia się w zależności od dokładnej lokalizacji wskaźnika. Jeśli nie widzisz uchwyty elementu, upewnij się, że element jest wybrany.

 W widoku Projekt obszaru kompozycji dodatkowe polecenia są dostępne w lewej dolnej części ekranu, jak pokazano poniżej:

 ![Projektowanie poleceń widoku](../designers/media/xaml-editor-design-controls.png "xaml_editor_design_controls")

 Te polecenia są dostępne w tym narzędzi:

 **Powiększenie** powiększenia pozwala na rozmiar powierzchni projektowej. Powiększenie z % 12,5 800% lub wybrać opcje takie jak **Dopasuj do wyboru** i **Dopasuj do wszystkich**.

 **Pokaż/Ukryj siatkę przyciągania** Wyświetla lub ukrywa przyciągania siatki, który pokazuje linie siatki. Linie siatki są używane podczas albo **przyciąganie do linii siatki** lub **przyciąganie do linii wyrównania** jest włączona.

 **Włączanie/wyłączanie przyciągania do siatki** Jeśli **przyciąganie do linii siatki** jest włączona, podczas przeciągania elementu w obszarze kompozycji, element zwykle przy najbliższej poziome i pionowe linie siatki.

 **Włącz/wyłącz przyciąganie do linii wyrównania** linii przyciągania ułatwiają wyrównywanie formantów względem siebie nawzajem. Jeśli **przyciąganie do linii wyrównania** jest włączona, podczas przeciągania kontroli względem innych kontrolek wyrównanie granice są wyświetlane, gdy krawędzie i tekst niektóre kontrolki są wyrównane w poziomie lub pionie. Granicy wyrównania jest wyświetlana jako linia kreskowana czerwony.

 W widoku XAML okno zawierające edytora XAML jest aktywnym oknem, a Edytor XAML to podstawowe narzędzie autorskie. Extensible Application Markup Language (XAML) zapewnia słownictwa deklaratywne, oparty na formacie XML do określania interfejsu użytkownika aplikacji. Widok XAML zawiera, IntelliSense, automatycznego formatowania, wyróżnianie składni i nawigacji tagu. Ta ilustracja przedstawia widok XAML:

 ![Widok XAML](../designers/media/xaml-editor.png "xaml_editor")

 **Wyświetl podziału** pasek podziału w widoku jest wyświetlany w górnej części widoku XAML, gdy Edytor XAML znajduje się w dolnym oknie. Wyświetl pasek podziału umożliwia sterowanie względne rozmiary widoku projektu i widok XAML. Mogą również wymieniać lokalizacje widoki (przy użyciu **Zamień okienka** przycisku), a następnie określ, czy widoków ułożone poziomo lub pionowo i zwinąć którymś z widoków.

 **Powiększenie znaczników** powiększenia znaczników umożliwia utworzenie widoku XAML rozmiar. Możesz powiększyć z 20% do 400%.

## <a name="device-window"></a>Okno urządzenia
 Okno urządzenia w programie XAML Designer umożliwia symulowanie w czasie projektowania, różnych widoków, ekranów i wyświetlić opcje projektu Windows Store lub Windows Phone. Okno urządzenia jest dostępna w **projektowania** menu podczas pracy w Projektancie XAML. Poniżej przedstawiono wygląda następująco:

 ![Okno urządzenia](../designers/media/xaml-editor-device-panel.png "xaml_editor_device_panel")

 Oto opcje dostępne w oknie urządzenia:

 **Wyświetlanie** określa rozmiarów ekranów i rozwiązań dla aplikacji.

 **Orientacja** określa różnych orientacji aplikacji: **Orientacja pozioma** lub **pionowa**.

 **Krawędź** Określa wyrównanie krawędzi różnych aplikacji: **Zarówno**, **po lewej stronie**, **po prawej stronie**, lub **Brak**.

 **Duży kontrast** Wyświetl podgląd aplikacji, w oparciu o wybrane ustawienie kontrastu. To ustawienie, gdy wartość do wartości innej niż **domyślne**, spowoduje zastąpienie `RequestedTheme` właściwość w pliku App.xaml.

 **Zastąp skalowanie** włącza i wyłącza emulacji skalowania w obrębie na powierzchnię projektową dokumentu. Dzięki temu można zwiększyć procent skalowania przez jeden składnik. Zaznacz pole wyboru, aby włączyć emulacji. Na przykład jeśli Twoje procent skalowania wynosi 100%, dokumentu w powierzchni projektowej skalowane wraz ze 140%. Ta opcja jest wyłączona, jeśli bieżąca wartość skalowania jest 180.

 **Minimalna szerokość** określa ustawienie minimalnej szerokości. Minimalna szerokość można zmienić w pliku App.xaml.

 **Motyw** określa układu aplikacji. Na przykład może przełączać się między ciemnoszary i motyw jasny.

 **Pokaż chrome** włącza i wyłącza ramki symulowane tablet wokół aplikacji w widoku Projekt. Zaznacz pole wyboru, aby wyświetlić ramki.

 **Przytnij do ekranu** Określa tryb wyświetlania. Zaznacz pole wyboru, kiedy należy przyciąć rozmiar dokumentu do rozmiaru ekranu.

## <a name="document-outline-window"></a>Okno konspektu dokumentu
 Okno konspektu dokumentu w Projektancie XAML pomaga wykonywać następujące zadania:

- Wyświetlanie hierarchicznej struktury wszystkich elementów w obszarze kompozycji.

- Wybierz elementy, dzięki czemu możesz modyfikować je (przeniesienie ich wokół w hierarchii, zmodyfikuj je w obszarze kompozycji, ustawiać ich właściwości w oknie dialogowym właściwości i tak dalej). Aby uzyskać więcej informacji, zobacz [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md)

- Tworzenie i modyfikowanie szablonów elementów będących kontrolkami.

- Użyj menu kontekstowego dla wybranych elementów. Tego samego menu jest również dostępny dla wybranych elementów w obszarze kompozycji.

  Aby wyświetlić okno konspektu dokumentu, na pasku menu wybierz **widoku**, **Windows inne**, **konspekt dokumentu**.

  ![Okno konspektu dokumentu](../designers/media/xaml-editor-doc-outline.png "xaml_editor_doc_outline")

  Oto opcje dostępne w oknie konspekt dokumentu:

  **Konspekt dokumentu** Widok główny okno konspektu dokumentu Wyświetla hierarchię dokumentu w strukturze drzewa. Hierarchiczny charakter konspekt dokumentu można użyć, aby zbadać dokument na różnych poziomach szczegółowości i blokowanie i ukrywanie elementów, pojedynczo lub w grupach.

  **Pokaż/Ukryj** Wyświetla lub ukrywa elementy obszaru kompozycji, które odpowiadają elementom konspekt dokumentu. Użyj **Pokaż/Ukryj** przycisków, które wyświetlanie symboli oka po pokazano lub naciśnij klawisze CTRL + H, aby ukryć elementy i SHIFT + klawisze CTRL + H, aby je wyświetlić.

  **Zablokuj/Odblokuj** blokuje albo odblokowuje elementy obszaru kompozycji, które odpowiadają elementom konspekt dokumentu. Nie można zmodyfikować zablokowanych elementów. Użyj **Zablokuj/Odblokuj** przycisków, które zawierają kłódka symboli, gdy zablokowany lub naciśnij klawisze CTRL + L, elementy blokady i SHIFT + klawisze CTRL + L, aby je odblokować.

  **Zwróć zakres do pageRoot** u góry okna konspekt dokumentu, który znajduje się symbol strzałki, opcję Zwraca konspekt dokumentu do poprzedniego zakresu. Zakresu działa ma zastosowanie tylko wtedy, gdy jesteś w zakresie stylu lub szablonu.

## <a name="properties-window"></a>Okno właściwości
 W oknie właściwości służy do ustawiania wartości właściwości kontrolek. Poniżej przedstawiono wygląda następująco:

 ![Okno właściwości](../designers/media/xaml-editor-prop-window.png "xaml_editor_prop_window")

 Istnieją różne opcje w górnej części okna właściwości. Nazwa aktualnie wybranego elementu można zmienić za pomocą **nazwa** pole. W lewym górnym rogu istnieje ikona reprezentująca obecnie wybranego elementu. Aby ustawić właściwości według kategorii lub alfabetycznie, kliknij przycisk **kategorii**, **nazwa**, lub **źródła** w **Rozmieść według** listy. Aby wyświetlić listę zdarzeń dla formantu, kliknij **zdarzenia** przycisk, który jest wyświetlany symbol bolt pod kątem obsługi. Aby wyszukać właściwość, rozpocznij wpisywanie nazwy właściwości w **wyszukującą** pole. Okno właściwości wyświetla właściwości, spełniających kryteria wyszukiwania. Niektóre właściwości umożliwiają ustawianie zaawansowanych właściwości, wybierając przycisk strzałki w dół. Aby uzyskać więcej informacji na temat używania właściwości i obsługa zdarzeń, zobacz [Szybki Start: dodawanie formantów i obsługa zdarzeń](http://go.microsoft.com/fwlink/?LinkID=247983)

 Po prawej stronie każdej właściwości jest wartość *znacznik właściwości* wyświetlany jako symbol pola. Wygląd znacznika właściwość wskazuje, czy powiązanie danych lub zasób stosowany do właściwości. Na przykład symbol białe pola wskazuje wartość domyślną, symbol czarne pole zwykle wskazuje, że zastosowano zasobu lokalnego i pole pomarańczowy zwykle wskazuje, że zastosowano powiązanie danych. Po kliknięciu znacznik właściwości, przejdź do definicji stylu, otworzyć Konstruktor powiązań danych lub otworzyć selektor zasobów.

## <a name="see-also"></a>Zobacz też
 [Praca z elementami w Projektancie XAML](../designers/working-with-elements-in-xaml-designer.md) [sposób tworzenia i stosowanie zasobów](../designers/how-to-create-and-apply-a-resource.md) [instruktażu: Powiązanie z danymi w Projektancie XAML](../designers/walkthrough-binding-to-data-in-xaml-designer.md)
