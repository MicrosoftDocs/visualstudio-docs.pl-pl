---
title: Projektant wstążki
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- Designer_Microsoft.VisualStudio.Tools.Office.Ribbon.Design.RibbonDesigner
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom Ribbon, about Ribbon Designer
- controls [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], controls
- customizing the Ribbon, about Ribbon Designer
- Ribbon [Office development in Visual Studio], visual designer
- customizing the Ribbon
- custom Ribbon
- designers [Office development in Visual Studio], Ribbon
- Ribbon [Office development in Visual Studio], customizing
- Ribbon [Office development in Visual Studio], common tasks
- Ribbon Designer [Office development in Visual Studio]
- read-only properties
- Ribbon [Office development in Visual Studio], shortcut keys
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7179de49f80bee847077a7f247cc11dee855be80
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928870"
---
# <a name="ribbon-designer"></a>Projektant wstążki
  Projektant wstążki jest wizualną kanwą. Za pomocą projektanta wstążki można dodać niestandardowe karty, grupy i formanty do Wstążki aplikacji pakietu Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Aby otworzyć projektanta wstążki, Dodaj **Wstążka (Projektant graficzny)** elementu do projektu. Można następnie użyć narzędzia do projektowania dla następujących zadań:

-   [Zaprojektuj układ wstążki](#DesigningRibbonLayout)

-   [Obsługa zdarzeń i ustawianie właściwości formantu](#HandleEventsSetProperties)

-   [Dodawanie formantów do widoku Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
>  Istnieją pewne zadania, których nie można wykonać przy użyciu projektanta wstążki. Aby uzyskać więcej informacji na temat tych zadań i jak można je wykonać, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).

 ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Używać projektanta wstążki w celu dostosowania wstążki w programie Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Dodaj element wstążki (Projektant graficzny) do projektu
 Aby używać projektanta wstążki, Dodaj nowy **Wstążka (Projektant graficzny)** elementu do projektu. Aby uzyskać więcej informacji, zobacz [jak: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Po dodaniu nowego **Wstążka (Projektant graficzny)** elementu programu Visual Studio automatycznie dodaje następujące pliki do projektu:

- Plik kodu wstążki. Ten plik ma nazwę określoną dla **Wstążka (Projektant graficzny)** pozycja **Dodaj nowy element** okno dialogowe. Dodaj kod do obsługi zdarzeń wstążki do tego pliku.

- Plik kodu projektanta wstążki. Ten plik zawiera kod generowany przez projektanta wstążki i nie należy bezpośrednio edytować.

- Plik zasobów. Ten plik zawiera wartości właściwości każdego formantu na Wstążce.

  Jeśli masz już **Wstążka (Projektant graficzny)** elementu z innego projektu, można ponownie użyć go w bieżącym projekcie za pomocą **Dodaj istniejący element** okno dialogowe.

##  <a name="DesigningRibbonLayout"></a> Projektowanie wstążki
 Istnieją trzy sposoby otwierania projektanta wstążki:

- W **Eksploratora rozwiązań**, kliknij dwukrotnie plik kodu wstążki.

- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy plik kodu wstążki, a następnie kliknij przycisk **Projektant widoków**.

- W **Eksploratora rozwiązań**, wybierz plik kodu wstążki, a następnie kliknij przycisk **projektanta** na **widoku** menu.

  Projektant wstążki zawiera domyślną kartę i grupę. Przy użyciu projektanta wstążki można usunąć obowiązujące tabulatory i grupę. Aby usunąć grupę domyślną, kliknij prawym przyciskiem myszy **grupa1**, a następnie kliknij przycisk **Usuń**. Aby usunąć kartę domyślną, kliknij prawym przyciskiem myszy pusty obszar powierzchni projektu, a następnie kliknij przycisk **Usuń kartę Wstążki**.

  Można również dodać niestandardowe karty, grupy i formanty do projektanta wstążki. Możesz znaleźć te kontrolki w **przybornika**w **formanty wstążki Office** grupy. Istnieją trzy sposoby dodawania formantów z **formanty wstążki Office** grupy do projektanta wstążki:

- Przeciągnięcie formantu do odpowiedniego obszaru na projektancie wstążki.

- Kliknij formant, a następnie kliknij odpowiedni obszar w Projektancie wstążki.

- Wybierz odpowiedni obszar w projektancie, a następnie kliknij dwukrotnie formant w **przybornika**.

### <a name="ribbon-design-workflow"></a>Przepływ pracy projektowania wstążki
 Wykonaj te proste kroki, aby zaprojektować układ wstążki:

1. [Dodaj kartę niestandardową do wstążki](#AddTabToRibbon).

2. [Dodawanie grup do karty](#AddGroupsToTab).

3. [Dodawanie formantów do grup](#AddControlsToGroups).

   Formanty mogą być zrzucane tylko na grupy; Nie można przeciągać formantu bezpośrednio na kartę czy do wstążki. Grupy mogą być upuszczane tylko na kartach. grupy nie można przeciągnąć bezpośrednio na Wstążkę.

   Rozmieść formanty przeciągając je na właściwe pozycje. Można ustawić właściwości kontrolki przy użyciu **właściwości** okna.

   Nie można przeciągać formantów z jednej karty do innej na Wstążce. Jeśli chcesz przenieść formant do innej karty, należy użyć **Wytnij** polecenie, aby usunąć formant z jednej karty, a następnie wkleić formant na inną kartę. Jeśli wytniesz formant i wkleisz go, program obsługi zdarzeń przestanie działać. Można ponownie połączyć program obsługi zdarzeń w **właściwości** okna. Aby uzyskać więcej informacji, zobacz [okno właściwości](../ide/reference/properties-window.md).

###  <a name="AddTabToRibbon"></a> Dodaj niestandardowe karty do wstążki
 Istnieją trzy sposoby dodania niestandardowej karty do wstążki:

- Dodaj kartę z **przybornika**.

- Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij przycisk **Dodaj kartę Wstążki**.

- Otwórz **Edotor kolekcji zakładek**, a następnie kliknij przycisk **Dodaj**.

   Aby otworzyć **Edotor kolekcji zakładek**w **właściwości** wybierz **karty** właściwości, a następnie kliknij przycisk wielokropka ![przenośnych ASP.NET Elipsa projektanta](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET").

  Po dodaniu karty, można dodać grupy zawierające formanty.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Usuwanie niestandardowych kart ze Wstążki
 Istnieją trzy sposoby usuwania karty niestandardowej ze Wstążki:

-   Kliknij prawym przyciskiem myszy projektanta, a następnie kliknij przycisk **Usuń kartę Wstążki**.

-   W **polecenia** okienku **właściwości** okna, kliknij przycisk **Usuń kartę Wstążki**.

-   Otwórz **Edotor kolekcji zakładek**, wybierz kartę, a następnie kliknij przycisk **Usuń**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Zmiana położenia zakładki na Wstążce
 Możesz zmienić kolejność niestandardowych kart na Wstążce. Można także określić położenie niestandardowych kart przed lub po wbudowanej karcie na Wstążce. Aby uzyskać więcej informacji, zobacz [jak: Zmiana położenia zakładki na wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Dostosowywanie wbudowane karty na Wstążce
 Wbudowana karty to karta, która jest już na Wstążce aplikacji Microsoft Office. Na przykład **danych** karty to karta wbudowana w programie Excel.

 Grupy i formanty można dodać do wbudowanej karty. Domyślnie grupa niestandardowa pojawia się jako ostatnia grupę na karcie wbudowanej, ale można go przenieść przed lub za dowolną grupę wbudowaną znajdującą na karcie.

 Nie można usunąć wbudowanych grup.

 Aby uzyskać szczegółowe informacje na temat sposobu dostosowywania karty wbudowanej, zobacz [jak: Dostosowywanie wbudowanej karty](../vsto/how-to-customize-a-built-in-tab.md).

###  <a name="AddGroupsToTab"></a> Dodawanie grup do karty
 Grupy logicznie organizują formanty na Wstążce. Dodawanie grup do kart. Dodaj wszystkie inne formanty do grupy.

###  <a name="AddControlsToGroups"></a> Dodawanie formantów do grup
 Dodaj jeden lub kilka formantów do grupy. W poniższej tabeli opisano każdy formant.

|Formant|Opis|
|-------------|-----------------|
|**Box**|Kontener, który organizuje formanty w grupie. Możesz dodać dowolną kontrolkę, do pola z wyjątkiem separatora, grupy lub karty. Pole może mieć poziomej lub pionowej.|
|**Przycisk**|Przycisk, który uruchamia akcję. Można dodać przycisk do grupy, grupy przycisków, listy rozwijanej, galerii, menu lub przycisku podziału.|
|**Grupa przycisków**|Grupa, która zawiera jeden lub więcej przycisków, przyciski przełączników, menu, przyciski dzielone i galerie. Grupa przycisków można dodać do grupy lub menu.|
|**CheckBox**|Pole zaznaczane lub odznaczane, aby włączyć lub wyłączyć opcję.|
|**ComboBox**|Pole edycji z dołączonym polem listy. Użytkownikom można wpisać lub wybrać żądaną pozycję. Pola są wyświetlane bieżące zaznaczenie. Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> właściwości, aby dodawać i usuwać elementy w czasie wykonywania przed lub po załadowaniu wstążki do aplikacji pakietu Office.|
|**Lista rozwijana**|Lista elementów, które użytkownik może wybrać. Użytkownik nie może wpisać nowej pozycji na liście rozwijanej.<br /><br /> Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> właściwości, aby dodać elementy do listy. Można dodawać i usuwać elementy w czasie wykonywania.<br /><br /> Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> właściwości, aby dodać przyciski do listy. Nie można jednak dodawać i usuwać przycisków w czasie wykonywania po załadowaniu wstążki do aplikacji pakietu Office.|
|**Pole edycji**|Pole, w którym użytkownik może wpisać tekst.|
|**Galeria**|Menu przedstawiające tablicę lub wykres wyborów wizualnych, z których użytkownicy mogą wybrać. Można kontrolować układ zaznaczeń w menu. Użyj <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A> i <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> właściwości, aby określić liczbę wierszy i kolumn, które będą wyświetlane elementy i przyciski galerii.|
|**Etykieta**|Tekst, który służy do określania formantów na Wstążce.|
|**Menu**|Listy rozwijanej, która może zawierać dowolny z następujących formantów:<br /><br /> — Przycisk<br />— Pole<br />— Galeria<br />— Menu<br />-Przycisk podziału<br />-Przycisk przełączania<br />-Separatora<br /><br /> Aby dodać formant do menu w Projektancie wstążki, kliknij strzałkę w dół w menu aby odsłonić powierzchnię projektową menu. Następnie można przeciągać formanty wstążki z **przybornika** na menu. Aby rozmieścić formanty, przeciągnij je do żądanych pozycji.<br /><br /> Aby dodać formanty do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po załadowaniu wstążki do aplikacji pakietu Office, należy ustawić <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> właściwości **true** przed załadowaniem wstążki. Aby dowiedzieć się, jak to zrobić, zobacz [model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md).|
|**Separator**|Cienki słupek używany do oddzielania elementów listy. Po dodaniu do grupy pasek jest pionowy. Po dodaniu do menu pasek jest poziomy.|
|**Przycisk podziału**|Przycisk z dołączonym menu. Przycisk podziału może zawierać żadnego z następujących formantów:<br /><br /> — Przycisk<br />— Pole<br />— Galeria<br />— Menu<br />-Przycisk podziału<br />-Przycisk przełączania<br />-Separatora<br /><br /> Podobnie jak menu przycisk podziału ma swoją własną powierzchnię projektową. Jednak w przeciwieństwie do menu, można tylko aktualizować elementy w przycisku podziału przed załadowaniem wstążki do aplikacji pakietu Office. Aby uzyskać informacje o sposobie aktualizowania elementów w przycisku podziału, zobacz [model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Pojawiający się przycisk jest wciśnięty lub nie.|

##  <a name="HandleEventsSetProperties"></a> Obsługa zdarzeń i ustawianie właściwości
 Projektant wstążki umożliwia ustawianie właściwości formantu w czasie projektowania za pomocą **właściwości** okna. Ponadto Wstążka udostępnia model silnie typizowany obiekt, który służy do pobierania i ustawiania właściwości formantów wstążki w czasie wykonywania.

 Możesz kliknąć dwukrotnie dowolny kontroler na elemencie projektanta aby otworzyć program obsługi zdarzeń dla zdarzenia domyślne formantu. Programy obsługi zdarzeń dla wszystkich innych zdarzeń formantów można utworzyć za pomocą **właściwości** okna.

 Zdarzenia i właściwości wstążki znajdują się w <xref:Microsoft.Office.Tools.Ribbon> przestrzeni nazw. **Wstążka (Projektant graficzny)** elementu automatycznie dodaje odwołanie do tego zestawu w projekcie i wstawia odpowiednią **przy użyciu** lub **Importy** instrukcji na górze pliku kodu wstążki.

 Aby uzyskać informacje na temat obsługi zdarzeń Wstążki i ustawiania właściwości formantów wstążki w czasie wykonywania, zobacz [model obiektu Wstążka ― omówienie](../vsto/ribbon-object-model-overview.md).

##  <a name="CustomizingMicrosoftOfficeButton"></a> Dostosowywanie widoku Backstage
 Można użyć projektanta wstążki, aby dodać formanty do menu otwieranego po kliknięciu **pliku** kartę. To menu jest nazywane widokiem Backstage.

 Nie możesz umieścić formantów przed ani po wbudowanych formantach przy użyciu projektanta wstążki. Wbudowany formant jest formant, który już występuje w widoku Backstage. Jeśli chcesz umieścić formanty przed lub po formantach wbudowanych, należy użyć składni XML wstążki. Aby uzyskać więcej informacji na temat **wstążki (XML)**, zobacz [kodu XML wstążki](../vsto/ribbon-xml.md). Aby uzyskać więcej informacji na temat dostosowywania widoku Backstage, zobacz [wprowadzenie do widoku widoku Backstage programu Office 2010 dla programistów](http://go.microsoft.com/fwlink/?LinkId=182189) i [dostosować widok widoku Backstage programu Office 2010 dla programistów](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Aby uzyskać informacje o sposobie dodawania formantów do widoku Backstage, zobacz [jak: Dodawanie formantów do widoku Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

##  <a name="Accessibility"></a> Dostępność w Projektancie wstążki
 Skróty klawiaturowe umożliwia przenoszenie formantów w Projektancie wstążki. Niektóre skróty klawiaturowe mają zastosowanie do wszystkich formantów, a niektóre są stosowane wyłącznie do formantów, które mają menu.

 W poniższej tabeli przedstawiono skróty klawiaturowe, które mają zastosowanie do wszystkich formantów.

|Akcja|Skrót klawiaturowy|
|------------|-----------------------|
|Przenieś formant przed poprzedni formant na liście.|**CTRL**+**się**<br /><br /> **CTRL**+**po lewej stronie**|
|Przenieś formant po następnym formancie na liście.|**CTRL**+**w dół**<br /><br /> **CTRL**+**po prawej stronie**|
|Przenieś zaznaczenie z jednego formantu do drugiego w tej samej grupie. Dla panelu listy rozwijanej przechodzenie między formantem nadrzędnym a kontrolki w panelu listy rozwijanej.|**W górę**<br /><br /> **W dół**|
|Iteracja FO przodu przez wszystkie formanty.|**Karta**|
|Iteruj do tyłu przez wszystkie formanty.|**SHIFT**+**kartę**|
|Usuń zaznaczony formant lub zestaw formantów.|**Delete**|
|Kopiuj wybrane formanty.|**CTRL**+**C**|
|Wytnij wybrane formanty.|**CTRL**+**X**|
|Wklej formanty ze Schowka.|**CTRL**+**V**|
|Wybierz **przybornika**.|**CTRL**+**Alt**+**X**|
|Wybierz składnik nadrzędny.|**ESC**|

 Skróty klawiaturowe, które mają zastosowanie tylko do Menu pakietu Microsoft Office, <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, i <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> są wyświetlane w poniższej tabeli.

|Akcja|Skrót klawiaturowy|
|------------|-----------------------|
|Wybierz formant nadrzędny, jeśli jest otwarty panel listy rozwijanej i jest zaznaczony na panelu listy rozwijanej kontrolki.|**po lewej stronie**|
|Zamknij panel listy rozwijanej, jeśli jest otwarty panel listy rozwijanej, a formant nadrzędny wybrany.|**po lewej stronie**|
|Otwórz panel listy rozwijanej.|**po prawej stronie**|
|Wybierz pierwszy formant na panelu listy rozwijanej, jeśli jest otwarty panel listy rozwijanej.|**po prawej stronie**|
|Zamknij panel listy rozwijanej.|**ESC**|

## <a name="see-also"></a>Zobacz także

- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie kart niestandardowych za pomocą projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Instrukcje: Eksportowanie wstążki z projektanta wstążki do XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
