---
title: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook
description: Dowiedz się, jak wyświetlić unikatowe wystąpienie niestandardowego okienka zadań z każdą utworzoną lub otwartą wiadomością e-mail w programie Microsoft Outlook.
ms.custom: SEO-VS-2020
titleSuffix: ''
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: bb1aed5ef110b726dae6e51337b0934ae0a8e69d
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824214"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Przewodnik: wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook
  W tym przewodniku pokazano, jak wyświetlić unikatowe wystąpienie niestandardowego okienka zadań z każdą utworzoną lub otwartą wiadomością e-mail. Użytkownicy mogą wyświetlać lub ukrywać niestandardowe okienko zadań przy użyciu przycisku na wstążce każdej wiadomości e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Aby wyświetlić niestandardowe okienko zadań z wieloma oknami Eksplorator lub Inspektor, należy utworzyć wystąpienie niestandardowego okienka zadań dla każdego otwartego okna. Aby uzyskać więcej informacji na temat zachowania niestandardowych okienek zadań w oknach programu Outlook, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

> [!NOTE]
> Ten przewodnik przedstawia kod dodatku VSTO w małych sekcjach, aby ułatwić omówienie logiki kodu.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika niestandardowego okienka zadań.

- Tworzenie niestandardowego interfejsu użytkownika wstążki.

- Wyświetlanie niestandardowego interfejsu użytkownika wstążki z wiadomościami e-mail.

- Tworzenie klasy do zarządzania oknami inspektora i niestandardowymi okienkami zadań.

- Inicjowanie i oczyszczanie zasobów używanych przez dodatek VSTO.

- Synchronizowanie przycisku przełączania wstążki z niestandardowym okienkiem zadań.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [Personalizowanie środowiska IDE Visual Studio .](../ide/personalizing-the-visual-studio-ide.md)

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub Microsoft Outlook 2010.

## <a name="create-the-project"></a>Tworzenie projektu
 Niestandardowe okienka zadań są implementowane w dodatki narzędzi VSTO. Rozpocznij od utworzenia projektu dodatku VSTO dla programu Outlook.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Utwórz projekt **dodatku programu Outlook** o nazwie **OutlookMailItemTaskPane.** Użyj szablonu **projektu dodatku programu Outlook.** Aby uzyskać więcej informacji, [zobacz How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera plik kodu *ThisAddIn.cs* lub *ThisAddIn.vb* i dodaje projekt **OutlookMailItemTaskPane** do **Eksplorator rozwiązań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Nie ma projektanta wizualnego dla niestandardowych okienek zadań, ale możesz zaprojektować kontrolkę użytkownika przy użyciu interfejsu użytkownika. Niestandardowe okienko zadań w tym dodatku narzędzi VSTO ma prosty interfejs użytkownika, który zawiera <xref:System.Windows.Forms.TextBox> kontrolkę. W dalszej części tego przewodnika dodasz kontrolkę użytkownika do niestandardowego okienka zadań.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Aby zaprojektować interfejs użytkownika niestandardowego okienka zadań

1. W **Eksplorator rozwiązań** kliknij projekt **OutlookMailItemTaskPane.**

2. W menu **Project (Projekt)** kliknij pozycję **Add User Control (Dodaj kontrolkę użytkownika).**

3. W **oknie dialogowym Dodawanie** nowego elementu zmień nazwę kontrolki użytkownika na **TaskPaneControl,** a następnie kliknij przycisk **Dodaj**.

     Kontrolka użytkownika zostanie otwarta w projektancie.

4. Na karcie **Typowe kontrolki** **przybornika** przeciągnij **kontrolkę TextBox** do kontrolki użytkownika.

## <a name="design-the-user-interface-of-the-ribbon"></a>Projektowanie interfejsu użytkownika wstążki
 Jednym z celów tego dodatku narzędzi VSTO jest umożliwianie użytkownikom ukrywania lub wyświetlania niestandardowego okienka zadań na wstążce każdej wiadomości e-mail. Aby udostępnić interfejs użytkownika, utwórz niestandardowy interfejs użytkownika wstążki, który wyświetla przycisk przełączania, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowe okienko zadań.

### <a name="to-create-a-custom-ribbon-ui"></a>Aby utworzyć niestandardowy interfejs użytkownika wstążki

1. W menu **Project (Projekt)** kliknij **pozycję Add New Item (Dodaj nowy element).**

2. W **oknie dialogowym Dodawanie nowego elementu** wybierz pozycję **Wstążka (Projektant wizualny).**

3. Zmień nazwę nowej wstążki na **ManageTaskPaneRibbon,** a następnie kliknij przycisk **Dodaj**.

     Plik *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon.vb* zostanie otwarty w Projektancie wstążki i zostanie wyświetlona domyślna karta i grupa.

4. W Projektancie wstążki kliknij pozycję **grupa1.**

5. W **oknie Właściwości** ustaw właściwość **Etykieta** na Menedżera **okienka zadań.**

6. Na karcie **Kontrolki wstążki pakietu Office** **przybornika** przeciągnij kontrolkę ToggleButton do grupy **Menedżer okienka** zadań.

7. Kliknij **pozycję toggleButton1**.

8. W **oknie Właściwości** ustaw właściwość **Etykieta** na Pokaż **okienko zadań**.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Wyświetlanie niestandardowego interfejsu użytkownika wstążki z wiadomościami e-mail
 Niestandardowe okienko zadań, które tworzysz w tym przewodniku, ma być wyświetlane tylko z oknami Inspector (Inspektor), które zawierają wiadomości e-mail. W związku z tym ustaw właściwości, aby wyświetlać niestandardowy interfejs użytkownika wstążki tylko z tymi oknami.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Aby wyświetlić niestandardowy interfejs użytkownika wstążki z wiadomościami e-mail

1. W Projektancie wstążki kliknij **wstążkę ManageTaskPaneRibbon.**

2. W **oknie Właściwości** kliknij listę rozwijaną obok właściwości **RibbonType** i wybierz pozycję **Microsoft.Outlook.Mail.Compose** i **Microsoft.Outlook.Mail.Read.**

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Tworzenie klasy do zarządzania oknami inspektora i niestandardowymi okienkami zadań
 Istnieje kilka przypadków, w których dodatek VSTO musi identyfikować, które niestandardowe okienko zadań jest skojarzone z określoną wiadomością e-mail. Są to między innymi następujące przypadki:

- Gdy użytkownik zamknie wiadomość e-mail. W takim przypadku dodatek VSTO musi usunąć odpowiednie niestandardowe okienko zadań, aby upewnić się, że zasoby używane przez dodatek VSTO są czyszczone poprawnie.

- Gdy użytkownik zamknie niestandardowe okienko zadań. W takim przypadku dodatek VSTO musi zaktualizować stan przycisku przełączania na wstążce wiadomości e-mail.

- Gdy użytkownik kliknie przycisk przełączania na wstążce. W takim przypadku dodatek narzędzi VSTO musi ukryć lub wyświetlić odpowiednie okienko zadań.

  Aby umożliwić dodatku narzędzi VSTO śledzenie, które niestandardowe okienko zadań jest skojarzone z każdą otwartą wiadomością e-mail, utwórz niestandardową klasę, która opakuje <xref:Microsoft.Office.Interop.Outlook.Inspector> pary obiektów <xref:Microsoft.Office.Tools.CustomTaskPane> i . Ta klasa tworzy nowy obiekt niestandardowego okienka zadań dla każdej wiadomości e-mail i usuwa niestandardowe okienko zadań po zamknięciu odpowiedniej wiadomości e-mail.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Aby utworzyć klasę do zarządzania oknami inspektora i niestandardowymi okienkami zadań

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy plik *ThisAddIn.cs* lub *ThisAddIn.vb,* a następnie kliknij polecenie **Wyświetl kod.**

2. Dodaj następujące instrukcje na początku pliku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet2":::

3. Dodaj następujący kod do pliku *ThisAddIn.cs* lub *ThisAddIn.vb* poza klasą (w przypadku języka Visual C# dodaj ten kod wewnątrz przestrzeni `ThisAddIn` `OutlookMailItemTaskPane` nazw ). Klasa `InspectorWrapper` zarządza parą obiektów <xref:Microsoft.Office.Interop.Outlook.Inspector> i <xref:Microsoft.Office.Tools.CustomTaskPane> . Definicję tej klasy ukończysz w poniższych krokach.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet3":::

4. Dodaj następujący konstruktor po kodzie dodanym w poprzednim kroku. Ten konstruktor tworzy i inicjuje nowe niestandardowe okienko zadań skojarzone z <xref:Microsoft.Office.Interop.Outlook.Inspector> przekazywanym obiektem. W języku C# konstruktor dołącza również procedury obsługi zdarzeń do zdarzenia obiektu i <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> <xref:Microsoft.Office.Interop.Outlook.Inspector> zdarzenia obiektu <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> <xref:Microsoft.Office.Tools.CustomTaskPane> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet4":::

5. Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda jest programem obsługi zdarzeń <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> dla zdarzenia <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu, który jest zawarty w klasie `InspectorWrapper` . Ten kod aktualizuje stan przycisku przełączania za każdym razem, gdy użytkownik otwiera lub zamyka niestandardowe okienko zadań.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet5":::

6. Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda to procedura obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> zdarzenia <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu, który zawiera bieżącą wiadomość e-mail. Procedura obsługi zdarzeń zamyka zasoby po zamknięciu wiadomości e-mail. Procedura obsługi zdarzeń usuwa również bieżące niestandardowe okienko zadań z `CustomTaskPanes` kolekcji. Zapobiega to wystąpieniu wielu wystąpień niestandardowego okienka zadań po otwarciu następnej wiadomości e-mail.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet6":::

7. Dodaj następujący kod po kodzie dodanym w poprzednim kroku. W dalszej części tego przewodnika wywołasz tę właściwość z metody w niestandardowym interfejsie użytkownika wstążki, aby wyświetlić lub ukryć niestandardowe okienko zadań.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet7":::

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inicjowanie i oczyszczanie zasobów używanych przez dodatek
 Dodaj kod do klasy , aby zainicjować dodatek VSTO po załadowaniu i wyczyścić zasoby używane przez dodatek VSTO, gdy jest `ThisAddIn` zwalniany. Dodatek VSTO można zainicjować, ustawiając program obsługi zdarzeń dla zdarzenia i przekazując wszystkie istniejące wiadomości e-mail <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> do tej procedury obsługi zdarzeń. Gdy dodatek VSTO zostanie zwolniony, odłącz program obsługi zdarzeń i wyczyść obiekty używane przez dodatek VSTO.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Aby zainicjować i wyczyścić zasoby używane przez dodatek VSTO

1. W *pliku ThisAddIn.cs* lub *ThisAddIn.vb* znajdź definicję `ThisAddIn` klasy .

2. Dodaj następujące deklaracje do `ThisAddIn` klasy :

   - Pole `inspectorWrappersValue` zawiera wszystkie obiekty i , które są zarządzane przez dodatek <xref:Microsoft.Office.Interop.Outlook.Inspector> `InspectorWrapper` VSTO.

   - Pole `inspectors` zawiera odwołanie do kolekcji okien Inspector (Inspektor) w bieżącym wystąpieniu programu Outlook. To odwołanie uniemożliwia modułowi odśmiecania pamięci, która zawiera program obsługi zdarzeń dla zdarzenia, który zostanie zadeklarowany <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> w następnym kroku.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet8":::

3. Zastąp metodę `ThisAddIn_Startup` następującym kodem. Ten kod dołącza program obsługi zdarzeń do zdarzenia i przekazuje każdy <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> istniejący obiekt do procedury obsługi <xref:Microsoft.Office.Interop.Outlook.Inspector> zdarzeń. Jeśli użytkownik ładuje dodatek VSTO po uruchomieniu programu Outlook, dodatek VSTO używa tych informacji do tworzenia niestandardowych okienek zadań dla wszystkich wiadomości e-mail, które są już otwarte.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet9":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet9":::

4. Zastąp metodę `ThisAddIn_ShutDown` następującym kodem. Ten kod odłącza program <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> obsługi zdarzeń i czyści obiekty używane przez dodatek VSTO.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet10":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet10":::

5. Dodaj następującą <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> obsługę zdarzeń do klasy `ThisAddIn` . Jeśli nowy obiekt zawiera wiadomość e-mail, metoda tworzy wystąpienie nowego obiektu w celu zarządzania relacją między wiadomością <xref:Microsoft.Office.Interop.Outlook.Inspector> `InspectorWrapper` e-mail i odpowiednim okienkiem zadań.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet11":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet11":::

6. Dodaj następującą właściwość do `ThisAddIn` klasy . Ta właściwość uwidacznia pole `inspectorWrappersValue` prywatne kodowi `ThisAddIn` spoza klasy .

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs" id="Snippet12":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb" id="Snippet12":::

## <a name="checkpoint"></a>Punkt kontrolny
 Skompiluj projekt, aby upewnić się, że kompiluje się bez błędów.

### <a name="to-build-your-project"></a>Aby skompilować projekt

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy projekt **OutlookMailItemTaskPane,** a następnie kliknij polecenie **Skompilować**. Sprawdź, czy projekt jest kompilowany bez błędów.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronizowanie przycisku przełączania wstążki z niestandardowym okienkiem zadań
 Przycisk przełączania będzie wyświetlany jako naciśnięty, gdy okienko zadań jest widoczne, a po ukryciu okienka zadań zostanie on naciśnięty. Aby zsynchronizować stan przycisku z niestandardowym okienkiem zadań, zmodyfikuj program <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> obsługi zdarzeń przycisku przełączania.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Aby zsynchronizować niestandardowe okienko zadań za pomocą przycisku przełączania

1. W Projektancie wstążki kliknij dwukrotnie przycisk przełączania **Pokaż** okienko zadań.

     Visual Studio automatycznie generuje program obsługi zdarzeń o nazwie `toggleButton1_Click` , który obsługuje zdarzenie <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> przycisku przełączania. Visual Studio także otwiera plik *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon.vb* w Edytorze kodu.

2. Dodaj następujące instrukcje na początku pliku *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon.vb.*

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet14":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet14":::

3. Zastąp program `toggleButton1_Click` obsługi zdarzeń następującym kodem. Gdy użytkownik kliknie przycisk przełączania, ta metoda ukrywa lub wyświetla niestandardowe okienko zadań skojarzone z bieżącym oknem Inspector (Inspektor).

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs" id="Snippet15":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb" id="Snippet15":::

## <a name="test-the-project"></a>Testowanie projektu
 Po rozpoczęciu debugowania projektu zostanie otwarty program Outlook i zostanie załadowany dodatek narzędzi VSTO. Dodatek VSTO wyświetla unikatowe wystąpienie niestandardowego okienka zadań z każdą otwartą wiadomością e-mail. Utwórz kilka nowych wiadomości e-mail, aby przetestować kod.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatek VSTO

1. Naciśnij klawisz **F5**.

2. W programie Outlook kliknij **pozycję Nowy,** aby utworzyć nową wiadomość e-mail.

3. Na wstążce wiadomości **e-mail** kliknij kartę Dodatki, a następnie kliknij przycisk **Pokaż okienko** zadań.

    Sprawdź, czy jest wyświetlane okienko zadań o tytule **Moje okienko zadań** z wiadomością e-mail.

4. W okienku zadań wpisz **w** polu tekstowym pierwsze okienko zadań.

5. Zamknij okienko zadań.

    Sprawdź, czy stan przycisku **Pokaż okienko zadań** zmienia się, aby nie był już naciśnięty.

6. Kliknij ponownie **przycisk Pokaż okienko** zadań.

    Sprawdź, czy zostanie otwarte okienko zadań i czy pole tekstowe nadal zawiera ciąg **Pierwsze okienko zadań.**

7. W programie Outlook kliknij pozycję **Nowy,** aby utworzyć drugą wiadomość e-mail.

8. Na wstążce wiadomości **e-mail** kliknij kartę Dodatki, a następnie kliknij przycisk **Pokaż okienko** zadań.

    Sprawdź, czy jest wyświetlane okienko zadań o tytule Moje okienko **zadań** z wiadomością e-mail, a pole tekstowe w tym okienku zadań jest puste.

9. W okienku zadań wpisz **Drugie okienko zadań** w polu tekstowym.

10. Zmień fokus na pierwszą wiadomość e-mail.

     Sprawdź, czy w okienku zadań skojarzonym z tą wiadomością e-mail nadal jest wyświetlane okienko **Pierwsze zadanie** w polu tekstowym.

    Ten dodatek VSTO obsługuje również bardziej zaawansowane scenariusze, które można wypróbować. Możesz na przykład przetestować zachowanie podczas wyświetlania wiadomości e-mail przy użyciu przycisków **Następny element** **i Poprzedni element.** Możesz również przetestować zachowanie podczas zwalniania dodatku VSTO, otwierania kilku wiadomości e-mail, a następnie ponownego ładowania dodatku VSTO.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia niestandardowych okienek zadań można znaleźć w tych tematach:

- Utwórz niestandardowe okienko zadań w dodatku narzędzi VSTO dla innej aplikacji. Aby uzyskać więcej informacji na temat aplikacji, które obsługują niestandardowe okienka zadań, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

- Automatyzowanie aplikacji Microsoft Office przy użyciu niestandardowego okienka zadań. Aby uzyskać więcej informacji, [zobacz Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań.](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)

- Utwórz przycisk wstążki w programie Excel, który może służyć do ukrywania lub wyświetlania niestandardowego okienka zadań. Aby uzyskać więcej informacji, [zobacz Przewodnik: synchronizowanie niestandardowego](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)okienka zadań za pomocą przycisku wstążki .

## <a name="see-also"></a>Zobacz też
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [How to: Add a custom task pane to an application (Jak dodać niestandardowe okienko zadań do aplikacji)](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: automatyzowanie aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: synchronizowanie niestandardowego okienka zadań za pomocą przycisku wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md)
- [Uzyskiwanie dostępu do wstążki w czasie uruchamiania](../vsto/accessing-the-ribbon-at-run-time.md)
