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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f417c077d2280b951f0d101d79876c01cb33789d
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71256028"
---
# <a name="ribbon-designer"></a>Projektant wstążki
  Projektant wstążki jest kanwą projektu wizualizacji. Użyj projektanta wstążki, aby dodać niestandardowe karty, grupy i kontrolki do wstążki aplikacji Microsoft Office.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

 Aby otworzyć projektanta wstążki, Dodaj element **wstążka (projektant graficzny)** do projektu. Następnie można użyć narzędzi projektowych dla następujących zadań:

- [Projektowanie układu wstążki](#DesigningRibbonLayout)

- [Obsługa zdarzeń i Ustawianie właściwości kontrolki](#HandleEventsSetProperties)

- [Dodawanie formantów do widoku Backstage](#CustomizingMicrosoftOfficeButton)

> [!NOTE]
> Istnieją pewne zadania, których nie można osiągnąć przy użyciu projektanta wstążki. Więcej informacji o tych zadaniach i sposobach ich wykonywania można znaleźć w temacie [Omówienie wstążki](../vsto/ribbon-overview.md).

 ![link do wideo](../vsto/media/playvideo.gif "link do wideo") Aby zapoznać się z pokrewną [prezentacją wideo, zobacz Jak mogę: Korzystanie z projektanta wstążki w celu dostosowania wstążki w programie Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130312).

## <a name="add-a-ribbon-visual-designer-item-to-a-project"></a>Dodaj Wstążkę (Visual Designer) do projektu
 Aby użyć projektanta wstążki, Dodaj nowy element **wstążki (projektant graficzny)** do projektu. Aby uzyskać więcej informacji, zobacz [jak: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md).

 Po dodaniu nowego elementu **wstążki (projektant graficzny)** program Visual Studio automatycznie dodaje do projektu następujące pliki:

- Plik kodu wstążki. Ten plik ma nazwę określoną dla elementu **wstążki (projektant graficzny)** w oknie dialogowym **Dodaj nowy element** . Dodaj kod obsługujący zdarzenia wstążki do tego pliku.

- Plik kodu projektanta wstążki. Ten plik zawiera kod wygenerowany przez projektanta wstążki i nie powinien być edytowany bezpośrednio.

- Plik zasobów. Ten plik zawiera wartości właściwości poszczególnych kontrolek na Wstążce.

  Jeśli masz już element **wstążki (projektant graficzny)** z innego projektu, możesz użyć go ponownie w bieżącym projekcie przy użyciu okna dialogowego **Dodaj istniejący element** .

## <a name="DesigningRibbonLayout"></a>Projektowanie wstążki
 Istnieją trzy sposoby otwierania projektanta wstążki:

- W **Eksplorator rozwiązań**kliknij dwukrotnie plik kodu wstążki.

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik kodu wstążki, a następnie kliknij pozycję **Projektant widoków**.

- W **Eksplorator rozwiązań**wybierz plik kodu wstążki, a następnie kliknij pozycję **Projektant** w menu **Widok** .

  Projektant wstążki zawiera domyślną kartę i grupę. Możesz usunąć domyślną kartę i grupę z projektanta wstążki. Aby usunąć grupę domyślną, kliknij prawym przyciskiem myszy pozycję **grupa1**, a następnie kliknij polecenie **Usuń**. Aby usunąć kartę domyślną, kliknij prawym przyciskiem myszy pusty obszar na powierzchni projektowej, a następnie kliknij polecenie **Usuń kartę wstążki**.

  Do projektanta wstążki można także dodawać niestandardowe karty, grupy i formanty. Te kontrolki można znaleźć w **przyborniku**, w grupie **formanty wstążki pakietu Office** . Istnieją trzy sposoby dodawania formantów z grupy **kontrolek wstążki pakietu Office** do projektanta wstążki:

- Przeciągnij formant do odpowiedniego obszaru w Projektancie wstążki.

- Kliknij kontrolkę, a następnie kliknij odpowiedni obszar w Projektancie wstążki.

- Wybierz odpowiedni obszar w projektancie, a następnie kliknij dwukrotnie formant w **przyborniku**.

### <a name="ribbon-design-workflow"></a>Przepływ pracy projektowania wstążki
 Wykonaj następujące podstawowe kroki, aby zaprojektować układ wstążki:

1. [Dodaj kartę niestandardową do wstążki](#AddTabToRibbon).

2. [Dodaj grupy do karty](#AddGroupsToTab).

3. [Dodaj formanty do grup](#AddControlsToGroups).

   Formanty mogą być porzucane tylko w grupach; nie można przeciągnąć kontrolki bezpośrednio na kartę lub na Wstążkę. Grupy mogą być porzucane tylko na kartach; nie można przeciągnąć grupy bezpośrednio na Wstążkę.

   Rozmieść kontrolki, przeciągając je do odpowiednich pozycji. Właściwości kontrolki można ustawić przy użyciu okna **Właściwości** .

   Nie można przeciągać formantów z jednej karty na drugą na Wstążce. Jeśli chcesz przenieść formant na inną kartę, musisz użyć polecenia **Wytnij** , aby usunąć formant z jednej karty, a następnie wkleić formant na innej karcie. Jeśli wytniesz kontrolkę i wkleisz ją, program obsługi zdarzeń przestanie działać. Można ponownie połączyć procedurę obsługi zdarzeń w oknie **Właściwości** . Aby uzyskać więcej informacji, zobacz [okno właściwości](../ide/reference/properties-window.md).

### <a name="AddTabToRibbon"></a>Dodawanie kart niestandardowych do wstążki
 Istnieją trzy sposoby dodawania niestandardowej karty do wstążki:

- Dodaj kartę z **przybornika**.

- Kliknij prawym przyciskiem myszy projektanta wstążki, a następnie kliknij polecenie **Dodaj kartę wstążki**.

- Otwórz **Edytor kolekcji kart**, a następnie kliknij przycisk **Dodaj**.

   Aby otworzyć **Edytor kolekcji kart**, w oknie **Właściwości** wybierz właściwość **tabulatory** , a następnie kliknij przycisk wielokropka ![ASP.net Mobile Designer Elipsa](../sharepoint/media/mwellipsis.gif "ASP.net Mobile Designer Elipsa").

  Po dodaniu karty można dodać grupy zawierające kontrolki.

#### <a name="remove-custom-tabs-from-the-ribbon"></a>Usuwanie kart niestandardowych ze wstążki
 Istnieją trzy sposoby usunięcia niestandardowej karty z wstążki:

- Kliknij prawym przyciskiem myszy projektanta, a następnie kliknij polecenie **Usuń kartę wstążki**.

- W okienku **polecenia** okna **Właściwości** kliknij polecenie **Usuń kartę wstążki**.

- Otwórz **Edytor kolekcji kart**, wybierz kartę, a następnie kliknij przycisk **Usuń**.

#### <a name="change-the-position-of-a-tab-on-the-ribbon"></a>Zmiana pozycji karty na Wstążce
 Można zmienić kolejność kart niestandardowych na Wstążce. Możesz również umieścić karty niestandardowe przed lub po karcie wbudowanej na Wstążce. Aby uzyskać więcej informacji, zobacz [jak: Zmień pozycję karty na Wstążce](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

#### <a name="customize-built-in-tabs-on-the-ribbon"></a>Dostosuj wbudowane karty na Wstążce
 Karta wbudowana to karta, która znajduje się już na Wstążce aplikacji Microsoft Office. Na przykład karta **dane** jest wbudowaną kartą w programie Excel.

 Do wbudowanej karty można dodać grupy i kontrolki. Domyślnie grupa niestandardowa jest wyświetlana jako Ostatnia Grupa na wbudowanej karcie, chociaż można ją przenieść przed lub po dowolna Grupa wbudowana na karcie.

 Nie można usunąć wbudowanych grup.

 Aby uzyskać szczegółowe informacje na temat dostosowywania wbudowanej karty, zobacz [How to: Dostosuj kartę](../vsto/how-to-customize-a-built-in-tab.md)wbudowaną.

### <a name="AddGroupsToTab"></a>Dodawanie grup do karty
 Grupy logicznie organizują kontrolki na Wstążce. Dodaj grupy do kart. Dodaj wszystkie inne kontrolki do grupy.

### <a name="AddControlsToGroups"></a>Dodawanie formantów do grup
 Dodaj co najmniej jedną kontrolkę do grupy. W poniższej tabeli opisano każdy formant.

|formant|Opis|
|-------------|-----------------|
|**Box**|Kontener, który organizuje kontrolki w grupie. Możesz dodać dowolny formant do pola, z wyjątkiem separatora, grupy lub karty. Pole może być w poziomie lub w pionie.|
|**Przycisk**|Przycisk, który uruchamia akcję. Możesz dodać przycisk do grupy, grupy przycisków, listy rozwijanej, galerii, menu lub przycisku podziału.|
|**ButtonGroup**|Grupa zawierająca jeden lub więcej przycisków, przycisków przełączników, menu, przycisków podzielonych i galerii. Grupę przycisków można dodać do grupy lub menu.|
|**CheckBox**|Pole, które jest zaznaczone lub wyczyszczone, aby włączyć lub wyłączyć opcję.|
|**ComboBox**|Pole edycji z dołączonym polem listy. Użytkownicy mogą wpisać lub wybrać opcję. W polu jest wyświetlany bieżący wybór. <xref:Microsoft.Office.Tools.Ribbon.RibbonComboBox.Items%2A> Użyj właściwości, aby dodawać i usuwać elementy w czasie wykonywania przed lub po załadowaniu wstążki do aplikacji pakietu Office.|
|**Przyjmij**|Lista elementów, które użytkownik może wybrać. Użytkownik nie może wpisać nowego elementu na liście rozwijanej.<br /><br /> Użyj właściwości <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Items%2A> , aby dodać elementy do listy. Można dodawać i usuwać elementy w czasie wykonywania.<br /><br /> Użyj właściwości <xref:Microsoft.Office.Tools.Ribbon.RibbonDropDown.Buttons%2A> , aby dodać przyciski do listy. Nie można jednak dodawać i usuwać przycisków w czasie wykonywania po załadowaniu wstążki do aplikacji pakietu Office.|
|**EditBox**|Pole, w którym użytkownik może wpisać tekst.|
|**Galeria**|Menu, które przedstawia tablicę lub siatkę opcji wizualizacji, z których użytkownicy mogą wybrać. Można kontrolować układ wybranych opcji w menu. Użyj właściwości <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.RowCount%2A> i, aby określić liczbę wierszy i kolumn, w których będą wyświetlane elementy i przyciski galerii. <xref:Microsoft.Office.Tools.Ribbon.RibbonGallery.ColumnCount%2A>|
|**Etykieta**|Tekst, którego można użyć do identyfikacji formantów na Wstążce.|
|**Menu**|Lista rozwijana, która może zawierać dowolne z następujących kontrolek:<br /><br /> -Przycisk<br />— Pole wyboru<br />— Galeria<br />— Menu<br />-Split — przycisk<br />-Przycisk przełączania<br />-Separator<br /><br /> Aby dodać kontrolkę do menu w Projektancie wstążki, kliknij strzałkę w dół w menu, aby uwidocznić powierzchnię projektu menu. Następnie można przeciągać formanty wstążki z **przybornika** do menu. Aby rozmieścić formanty, przeciągnij je do żądanych pozycji.<br /><br /> Aby dodać formanty do <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu> po załadowaniu wstążki do aplikacji pakietu Office, należy <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu.Dynamic%2A> ustawić właściwość na **wartość true** przed załadowaniem Wstążki. Aby uzyskać informacje o tym, jak to zrobić, zobacz [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md).|
|**Separator**|Cienki pasek używany do rozdzielania elementów na liście. Po dodaniu do grupy pasek jest pionowy. Po dodaniu do menu pasek jest poziomy.|
|**SplitButton**|Przycisk z dołączonym menu. Przycisk podziału może zawierać dowolne z następujących kontrolek:<br /><br /> -Przycisk<br />— Pole wyboru<br />— Galeria<br />— Menu<br />-Split — przycisk<br />-Przycisk przełączania<br />-Separator<br /><br /> Podobnie jak w przypadku menu, przycisk podziału ma własną powierzchnię projektu. Jednak w przeciwieństwie do menu można aktualizować tylko elementy w przycisku podziału przed załadowaniem Wstążki do aplikacji pakietu Office. Aby uzyskać informacje o sposobach aktualizowania elementów w przycisku podziału, zobacz [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md).|
|**ToggleButton**|Przycisk, który pojawia się po naciśnięciu lub nienaciśnięciu.|

## <a name="HandleEventsSetProperties"></a>Obsługa zdarzeń i Ustawianie właściwości
 Projektant wstążki umożliwia ustawianie właściwości kontrolek w czasie projektowania przy użyciu okna **Właściwości** . Ponadto wstążka uwidacznia model obiektów o jednoznacznie określonym typie, którego można użyć do pobierania i ustawiania właściwości kontrolek wstążki w czasie wykonywania.

 Możesz kliknąć dwukrotnie dowolny formant w projektancie, aby otworzyć program obsługi zdarzeń dla domyślnego zdarzenia formantu. Programy obsługi zdarzeń można utworzyć dla wszystkich innych zdarzeń kontroli przy użyciu okna **Właściwości** .

 Zdarzenia wstążki i właściwości znajdują się w <xref:Microsoft.Office.Tools.Ribbon> przestrzeni nazw. Element **wstążka (projektant graficzny)** automatycznie dodaje odwołanie do tego zestawu w projekcie i wstawia odpowiednią instrukcję **using** lub **Imports** w górnej części pliku kodu wstążki.

 Aby uzyskać informacje na temat obsługi zdarzeń wstążki i ustawiania właściwości formantów wstążki w czasie wykonywania, zobacz [Omówienie modelu obiektów wstążki](../vsto/ribbon-object-model-overview.md).

## <a name="CustomizingMicrosoftOfficeButton"></a>Dostosuj widok Backstage
 Za pomocą projektanta wstążki można dodać kontrolki do menu, które otwiera się po kliknięciu karty **plik** . To menu jest nazywane widokiem Backstage.

 Nie można umieścić kontrolek przed ani po wbudowanych kontrolkach przy użyciu projektanta wstążki. Wbudowana kontrolka to formant, który jest już wyświetlany w widoku Backstage. Jeśli chcesz umieścić formanty przed lub po wbudowanych kontrolkach, musisz użyć kodu XML wstążki. Aby uzyskać więcej informacji na temat **wstążki (XML)** , zobacz [kod XML wstążki](../vsto/ribbon-xml.md). Aby uzyskać więcej informacji na temat dostosowywania widoku Backstage, zobacz [wprowadzenie do widoku Backstage pakietu office 2010 dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182189) i [Dostosuj widok backstage pakietu Office 2010 dla deweloperów](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon_2010](../vsto/includes/appliesto-ribbon-2010-md.md)]

 Aby uzyskać informacje o sposobach dodawania formantów do widoku Backstage, zobacz [How to: Dodaj formanty do widoku](../vsto/how-to-add-controls-to-the-backstage-view.md)Backstage.

## <a name="Accessibility"></a>Ułatwienia dostępu w Projektancie wstążki
 Za pomocą skrótów klawiaturowych można przenosić kontrolki w Projektancie wstążki. Niektóre skróty klawiaturowe mają zastosowanie do wszystkich kontrolek, a niektóre dotyczą tylko formantów, które mają menu.

 Skróty klawiaturowe, które mają zastosowanie do wszystkich kontrolek, przedstawiono w poniższej tabeli.

|Akcja|Skrót klawiaturowy|
|------------|-----------------------|
|Przenieś kontrolkę przed poprzednią kontrolką na liście.|**Ctrl**up+<br /><br /> Ctrl+w**lewo**|
|Przenieś kontrolkę po następnej kontrolce na liście.|Ctrl+**w dół**<br /><br /> Ctrl+w**prawo**|
|Przeniesienie zaznaczenia z jednej kontrolki do innej w tej samej grupie. Dla panelu listy rozwijanej Przechodź między kontrolką nadrzędną a kontrolkami w panelu rozwijanym.|**Konfigurowanie**<br /><br /> **Notuj**|
|Wykonaj iterację w przód przez wszystkie kontrolki.|**Karta**|
|Iterowanie do tyłu przez wszystkie kontrolki.|+**Tab** Shift|
|Usuń wybraną kontrolkę lub zestaw kontrolek.|**Delete**|
|Skopiuj wybrane kontrolki.|**Ctrl**C+|
|Wytnij zaznaczone kontrolki.|**Ctrl**+**X**|
|Wklej kontrolki ze schowka.|**Ctrl**+**V**|
|Wybierz **Przybornik**.|**Ctrl**+**Alt**+**X**|
|Wybierz składnik nadrzędny.|**ESC**|

 Skróty klawiaturowe, które mają zastosowanie tylko do menu Microsoft Office <xref:Microsoft.Office.Tools.Ribbon.RibbonMenu>, i <xref:Microsoft.Office.Tools.Ribbon.RibbonSplitButton> przedstawiono w poniższej tabeli.

|Akcja|Skrót klawiaturowy|
|------------|-----------------------|
|Wybierz kontrolkę nadrzędną, jeśli jest otwarty panel listy rozwijanej, a w panelu listy rozwijanej wybrano kontrolkę.|**po lewej stronie**|
|Zamknij panel listy rozwijanej, jeśli jest otwarty panel listy rozwijanej, a kontrolka nadrzędna jest zaznaczona.|**po lewej stronie**|
|Otwórz panel listy rozwijanej.|**Kliknij**|
|Wybierz pierwszą kontrolkę z panelu listy rozwijanej, jeśli panel listy rozwijanej jest otwarty.|**Kliknij**|
|Zamknij panel listy rozwijanej.|**ESC**|

## <a name="see-also"></a>Zobacz także

- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [XML — wstążka](../vsto/ribbon-xml.md)
- [Przewodnik: Tworzenie niestandardowej karty przy użyciu projektanta wstążki](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Instrukcje: Eksportowanie wstążki z projektanta wstążki do kodu XML wstążki](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Instrukcje: Wprowadzenie do dostosowywania wstążki](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
