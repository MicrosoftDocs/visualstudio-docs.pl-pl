---
title: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Outlook [Office development in Visual Studio], custom task panes
- task panes [Office development in Visual Studio], displaying with e-mail messages
- displaying custom task panes in e-mail
- e-mail [Office development in Visual Studio], custom task panes displayed in
- custom task panes [Office development in Visual Studio], displaying with e-mail messages
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9e94bedf95b58d9876d37eb496ede0c5ec9a8531
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985453"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook
  W tym instruktażu pokazano, jak wyświetlić unikatowe wystąpienie niestandardowego okienka zadań z każdą wiadomością e-mail, która została utworzona lub otwarta. Użytkownicy mogą wyświetlać lub ukrywać niestandardowe okienko zadań przy użyciu przycisku na Wstążce każdej wiadomości e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Aby wyświetlić niestandardowe okienko zadań z wieloma oknami Eksploratora lub inspektorów, należy utworzyć wystąpienie niestandardowego okienka zadań dla każdego otwartego okna. Aby uzyskać więcej informacji o zachowaniu niestandardowych okienek zadań w programie Outlook w systemie Windows, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

> [!NOTE]
> Ten Instruktaż przedstawia kod dodatku narzędzi VSTO w małych sekcjach, aby ułatwić omawianie logiki za kodem.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika (UI) niestandardowego okienka zadań.

- Tworzenie niestandardowego interfejsu użytkownika wstążki.

- Wyświetlanie niestandardowego interfejsu użytkownika wstążki z wiadomościami e-mail.

- Tworzenie klasy do zarządzania oknami inspektorów i niestandardowymi okienkami zadań.

- Inicjowanie i Oczyszczanie zasobów używanych przez dodatek narzędzi VSTO.

- Synchronizowanie przycisku przełączania wstążki z okienkiem zadania niestandardowego.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub Microsoft Outlook 2010.

## <a name="create-the-project"></a>Utwórz projekt
 Niestandardowe okienka zadań są implementowane w dodatkach programu VSTO. Zacznij od utworzenia projektu dodatku VSTO dla programu Outlook.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt **dodatku programu Outlook** o nazwie **OutlookMailItemTaskPane**. Użyj szablonu projektu **dodatku programu Outlook** . Aby uzyskać więcej informacji, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] otwiera plik kodu *ThisAddIn.cs* lub *ThisAddIn. vb* i dodaje projekt **OutlookMailItemTaskPane** do **Eksplorator rozwiązań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Nie istnieje projektant wizualny dla niestandardowych okienek zadań, ale można zaprojektować kontrolkę użytkownika z żądanym INTERFEJSem użytkownika. Niestandardowe okienko zadań w tym dodatku VSTO ma prosty interfejs użytkownika, który zawiera kontrolkę <xref:System.Windows.Forms.TextBox>. W dalszej części tego instruktażu dodasz kontrolkę użytkownika do niestandardowego okienka zadań.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Aby zaprojektować interfejs użytkownika niestandardowego okienka zadań

1. W **Eksplorator rozwiązań**kliknij projekt **OutlookMailItemTaskPane** .

2. W menu **projekt** kliknij polecenie **Dodaj kontrolkę użytkownika**.

3. W oknie dialogowym **Dodaj nowy element** Zmień nazwę kontrolki użytkownika na **TaskPaneControl**, a następnie kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

4. Na karcie **Formanty standardowe** **przybornika**przeciągnij kontrolkę **TextBox** do kontrolki użytkownika.

## <a name="design-the-user-interface-of-the-ribbon"></a>Projektowanie interfejsu użytkownika wstążki
 Jednym z celów tego dodatku narzędzi VSTO jest udostępnienie użytkownikom możliwości ukrycia lub wyświetlenia niestandardowego okienka zadań na Wstążce każdej wiadomości e-mail. Aby zapewnić interfejs użytkownika, Utwórz niestandardowy interfejs użytkownika wstążki, który wyświetla przycisk przełączania, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowe okienko zadań.

### <a name="to-create-a-custom-ribbon-ui"></a>Aby utworzyć niestandardowy interfejs użytkownika wstążki

1. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz pozycję **wstążka (projektant wizualny)** .

3. Zmień nazwę nowej wstążki na **ManageTaskPaneRibbon**, a następnie kliknij przycisk **Dodaj**.

     Plik *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon. vb* zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i Grupa.

4. W Projektancie wstążki kliknij pozycję **grupa1**.

5. W oknie **Właściwości** ustaw właściwość **etykieta** na **Menedżer okienka zadań**.

6. Na karcie **kontrolki wstążki pakietu Office** w **przyborniku**przeciągnij kontrolkę ToggleButton na grupę **Menedżera okienka zadań** .

7. Kliknij pozycję **toggleButton1**.

8. W oknie **Właściwości** ustaw właściwość **etykieta** na **Pokaż okienko zadań**.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Wyświetlanie niestandardowego interfejsu użytkownika wstążki z wiadomościami e-mail
 Niestandardowe okienko zadań utworzone w tym instruktażu zaprojektowano tak, aby były wyświetlane tylko w oknach inspektorów zawierających wiadomości e-mail. W związku z tym ustaw właściwości, aby wyświetlać niestandardowy interfejs użytkownika wstążki tylko przy użyciu tych okien.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Aby wyświetlić niestandardowy interfejs użytkownika wstążki z wiadomościami e-mail

1. W Projektancie wstążki kliknij Wstążkę **ManageTaskPaneRibbon** .

2. W oknie **Właściwości** kliknij listę rozwijaną obok pozycji **wstążka**, a następnie wybierz pozycję **Microsoft. Outlook. mail. redagowanie** i **Microsoft. Outlook. mail. Read**.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Utwórz klasę, aby zarządzać oknami inspektorów i niestandardowymi okienkami zadań
 Istnieje kilka przypadków, w których dodatek VSTO musi zidentyfikować niestandardowe okienko zadań skojarzone z konkretną wiadomością e-mail. Są to następujące przypadki:

- Gdy użytkownik zamknie wiadomość e-mail. W takim przypadku dodatek VSTO musi usunąć odpowiednie niestandardowe okienko zadań, aby upewnić się, że zasoby używane przez dodatek VSTO zostały poprawnie oczyszczone.

- Gdy użytkownik zamknie niestandardowe okienko zadań. W takim przypadku dodatek VSTO musi zaktualizować stan przycisku przełączania na Wstążce wiadomości e-mail.

- Gdy użytkownik kliknie przycisk przełączania na Wstążce. W takim przypadku dodatek VSTO musi ukryć lub wyświetlić odpowiednie okienko zadań.

  Aby włączyć dodatek VSTO do śledzenia, które niestandardowe okienko zadań jest skojarzone z każdą otwartą wiadomością e-mail, należy utworzyć klasę niestandardową, która otacza pary <xref:Microsoft.Office.Interop.Outlook.Inspector> i <xref:Microsoft.Office.Tools.CustomTaskPane> obiektów. Ta klasa tworzy nowy obiekt niestandardowego okienka zadań dla każdej wiadomości e-mail i usuwa niestandardowe okienko zadań po zamknięciu odpowiedniej wiadomości e-mail.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Aby utworzyć klasę do zarządzania oknami inspektorów i niestandardowymi okienkami zadań

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy plik *ThisAddIn.cs* lub *ThisAddIn. vb* , a następnie kliknij polecenie **Wyświetl kod**.

2. Dodaj poniższe instrukcje na początku pliku.

     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]

3. Dodaj następujący kod do pliku *ThisAddIn.cs* lub *ThisAddIn. vb* , poza klasą `ThisAddIn` (dla wizualizacji C#Dodaj ten kod wewnątrz`OutlookMailItemTaskPane`przestrzeni nazw). Klasa `InspectorWrapper` zarządza parą obiektów <xref:Microsoft.Office.Interop.Outlook.Inspector> i <xref:Microsoft.Office.Tools.CustomTaskPane>. Definicja tej klasy zostanie ukończona w poniższych krokach.

     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]

4. Dodaj następujący Konstruktor po kodzie dodanym w poprzednim kroku. Ten konstruktor tworzy i Inicjuje nowe niestandardowe okienko zadań, które jest skojarzone z przekazaną <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektem. W C#programie Konstruktor dołącza także programy obsługi zdarzeń do zdarzenia<xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close>obiektu<xref:Microsoft.Office.Interop.Outlook.Inspector>i zdarzenia<xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged>obiektu<xref:Microsoft.Office.Tools.CustomTaskPane>.

     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]

5. Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda jest programem obsługi zdarzeń dla zdarzenia <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> obiektu <xref:Microsoft.Office.Tools.CustomTaskPane>, który znajduje się w klasie `InspectorWrapper`. Ten kod aktualizuje stan przycisku przełączania za każdym razem, gdy użytkownik otworzy lub zamknie niestandardowe okienko zadań.

     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]

6. Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda jest programem obsługi zdarzeń dla zdarzenia <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> obiektu <xref:Microsoft.Office.Interop.Outlook.Inspector> zawierającego bieżącą wiadomość e-mail. Program obsługi zdarzeń zwalnia zasoby po zamknięciu wiadomości e-mail. Program obsługi zdarzeń usuwa również bieżące niestandardowe okienko zadań z kolekcji `CustomTaskPanes`. Pozwala to zapobiec wielu wystąpieniu niestandardowego okienka zadań po otwarciu następnej wiadomości e-mail.

     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]

7. Dodaj następujący kod po kodzie dodanym w poprzednim kroku. W dalszej części tego instruktażu wywołasz tę właściwość z metody w interfejsie użytkownika niestandardowej wstążki, aby wyświetlić lub ukryć niestandardowe okienko zadań.

     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inicjowanie i czyszczenie zasobów używanych przez dodatek
 Dodaj kod do klasy `ThisAddIn`, aby zainicjować dodatek narzędzi VSTO podczas ładowania, i wyczyścić zasoby używane przez dodatek VSTO po jego zwolnieniu. Dodatek VSTO można zainicjować przez skonfigurowanie programu obsługi zdarzeń dla zdarzenia <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> i przekazanie wszystkich istniejących wiadomości e-mail do tego programu obsługi zdarzeń. Gdy dodatek narzędzi VSTO zostanie zwolniony, odłącz procedurę obsługi zdarzeń i oczyść obiekty używane przez dodatek VSTO.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Aby zainicjować i oczyścić zasoby używane przez dodatek VSTO

1. W pliku *ThisAddIn.cs* lub *ThisAddIn. vb* Znajdź definicję klasy `ThisAddIn`.

2. Dodaj następujące deklaracje do klasy `ThisAddIn`:

   - Pole `inspectorWrappersValue` zawiera wszystkie obiekty <xref:Microsoft.Office.Interop.Outlook.Inspector> i `InspectorWrapper`, które są zarządzane przez dodatek VSTO.

   - Pole `inspectors` przechowuje odwołanie do kolekcji okien inspektorów w bieżącym wystąpieniu programu Outlook. To odwołanie zapobiega zwalnianiu pamięci przez moduł wyrzucania elementów bezużytecznych, która zawiera program obsługi zdarzeń dla zdarzenia <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>, który zostanie zadeklarowany w następnym kroku.

     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]

3. Zastąp metodę `ThisAddIn_Startup` poniższym kodem. Ten kod dołącza procedurę obsługi zdarzeń do zdarzenia <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> i przekazuje każdy istniejący obiekt <xref:Microsoft.Office.Interop.Outlook.Inspector> do programu obsługi zdarzeń. Jeśli użytkownik załaduje dodatek VSTO po uruchomieniu programu Outlook, dodatek VSTO używa tych informacji do tworzenia niestandardowych okienek zadań dla wszystkich wiadomości e-mail, które są już otwarte.

    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]

4. Zastąp metodę `ThisAddIn_ShutDown` poniższym kodem. Ten kod odłącza procedurę obsługi zdarzeń <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> i czyści obiekty używane przez dodatek narzędzi VSTO.

    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]

5. Dodaj do klasy `ThisAddIn` następującą procedurę obsługi zdarzeń <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector>. Jeśli nowy <xref:Microsoft.Office.Interop.Outlook.Inspector> zawiera wiadomość e-mail, metoda tworzy wystąpienie nowego obiektu `InspectorWrapper` do zarządzania relacjami między wiadomością e-mail i odpowiednim okienkiem zadania.

    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]

6. Dodaj następującą właściwość do klasy `ThisAddIn`. Ta właściwość uwidacznia pole `inspectorWrappersValue` prywatnego do kodu poza klasą `ThisAddIn`.

    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]

## <a name="checkpoint"></a>Elementu
 Skompiluj projekt, aby upewnić się, że kompiluje się bez błędów.

### <a name="to-build-your-project"></a>Aby skompilować projekt

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **OutlookMailItemTaskPane** , a następnie kliknij pozycję **Kompiluj**. Upewnij się, że projekt kompiluje się bez błędów.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronizuj przycisk przełączania wstążki z okienkiem zadania niestandardowego
 Przycisk przełączania zostanie naciśnięty, gdy okienko zadań będzie widoczne i pojawi się, gdy okienko zadań jest ukryte. Aby zsynchronizować stan przycisku przy użyciu niestandardowego okienka zadań, należy zmodyfikować procedurę obsługi zdarzeń <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> przycisku przełączania.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Aby zsynchronizować niestandardowe okienko zadań z przyciskiem przełączania

1. W Projektancie wstążki kliknij dwukrotnie przycisk Przełącz **okienko zadań** .

     Program Visual Studio automatycznie generuje procedurę obsługi zdarzeń o nazwie `toggleButton1_Click`, która obsługuje zdarzenie <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> przycisku przełączania. Program Visual Studio otwiera także plik *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon. vb* w edytorze kodu.

2. Dodaj następujące instrukcje na początku pliku *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon. vb* .

     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]

3. Zastąp procedurę obsługi zdarzeń `toggleButton1_Click` poniższym kodem. Gdy użytkownik kliknie przycisk przełączania, ta metoda ukrywa lub wyświetla niestandardowe okienko zadań skojarzone z bieżącym oknem inspektora.

     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]

## <a name="test-the-project"></a>Testowanie projektu
 Po rozpoczęciu debugowania projektu zostanie otwarty program Outlook, a dodatek VSTO zostanie załadowany. Dodatek VSTO wyświetla unikatowe wystąpienie niestandardowego okienka zadań z każdą otwartą wiadomością e-mail. Utwórz kilka nowych wiadomości e-mail w celu przetestowania kodu.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek narzędzi VSTO

1. Naciśnij klawisz **F5**.

2. W programie Outlook kliknij pozycję **Nowy** , aby utworzyć nową wiadomość e-mail.

3. Na Wstążce wiadomości e-mail kliknij kartę **Dodatki** , a następnie kliknij przycisk **Pokaż okienko zadań** .

    Sprawdź, czy okienko zadań z tytułem **moje zadanie** jest wyświetlane wraz z wiadomością e-mail.

4. W okienku zadań wpisz **pierwsze okienko zadań** w polu tekstowym.

5. Zamknij okienko zadań.

    Sprawdź, czy stan przycisku **Pokaż okienko zadania** zmienia się, aby nie był już wcionięty.

6. Kliknij ponownie przycisk **Pokaż okienko zadań** .

    Sprawdź, czy okienko zadań otwiera się i czy pole tekstowe nadal zawiera **pierwsze okienko zadań**.

7. W programie Outlook kliknij pozycję **Nowy** , aby utworzyć drugą wiadomość e-mail.

8. Na Wstążce wiadomości e-mail kliknij kartę **Dodatki** , a następnie kliknij przycisk **Pokaż okienko zadań** .

    Sprawdź, czy okienko zadań z tytułem **moje zadanie** jest wyświetlane wraz z wiadomością e-mail, a pole tekstowe w tym okienku zadań jest puste.

9. W okienku zadań wpisz **drugie okienko zadań** w polu tekstowym.

10. Zmień fokus na pierwszą wiadomość e-mail.

     Upewnij się, że okienko zadań skojarzone z tą wiadomością e-mail nadal wyświetla **pierwsze okienko zadań** w polu tekstowym.

    Ten dodatek narzędzi VSTO obsługuje również bardziej zaawansowane scenariusze, które można wypróbować. Na przykład można przetestować zachowanie podczas przeglądania wiadomości e-mail przy użyciu przycisków **Następny element** i **poprzedni element** . Można również przetestować zachowanie po zwolnieniu dodatku VSTO, otwarciu kilku wiadomości e-mail, a następnie załadowaniu dodatku VSTO.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia niestandardowych okienek zadań można znaleźć w następujących tematach:

- Utwórz niestandardowe okienko zadań w dodatku narzędzi VSTO dla innej aplikacji. Aby uzyskać więcej informacji o aplikacjach, które obsługują niestandardowe okienka zadań, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

- Automatyzacja aplikacji Microsoft Office przy użyciu niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Utwórz przycisk wstążki w programie Excel, którego można użyć do ukrycia lub wyświetlenia niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [Przewodnik: synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

## <a name="see-also"></a>Zobacz także
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: synchronizowanie niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Omówienie wstążki](../vsto/ribbon-overview.md)
- [Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)
- [Uzyskiwanie dostępu do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
