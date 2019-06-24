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
ms.openlocfilehash: fa86c07ba964ca918c7ad225d5152b31a2e1d9ae
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67328347"
---
# <a name="walkthrough-display-custom-task-panes-with-email-messages-in-outlook"></a>Przewodnik: Wyświetlanie niestandardowych okienek zadań z wiadomościami e-mail w programie Outlook
  W tym instruktażu przedstawiono sposób wyświetlania unikatowego wystąpienia niestandardowego okienka zadań z każdej wiadomości e-mail, który został utworzony lub otwarty. Użytkowników można wyświetlić lub ukryć niestandardowego okienka zadań, za pomocą przycisku na Wstążce każdej wiadomości e-mail.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

 Aby wyświetlić niestandardowego okienka zadań z wielu Eksploratora lub Inspektora systemu windows, należy utworzyć wystąpienia niestandardowego okienka zadań dla każdego okna, który jest otwierany. Aby uzyskać więcej informacji o zachowaniu niestandardowych okienek zadań w programie Outlook w systemie windows, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

> [!NOTE]
> W tym instruktażu przedstawiono kod dodatku narzędzi VSTO dla programów w krótkich sekcjach, aby ułatwić omówić logiki stojącej za kod.

 W instruktażu przedstawiono następujące zagadnienia:

- Projektowanie interfejsu użytkownika (UI) z niestandardowego okienka zadań.

- Tworzenie niestandardowego interfejsu użytkownika wstążki.

- Wyświetlanie niestandardowego interfejsu użytkownika wstążki, za pomocą wiadomości e-mail.

- Tworzenie klasy do zarządzania windows Inspektor i niestandardowe okienka zadań.

- Inicjowanie i oczyszczanie zasobów używanych przez dodatku narzędzi VSTO.

- Synchronizowanie przycisk przełączania wstążki z niestandardowego okienka zadań.

> [!NOTE]
> Na komputerze w poniższych instrukcjach mogą być wyświetlane inne nazwy i lokalizacje niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft [!INCLUDE[Outlook_15_short](../vsto/includes/outlook-15-short-md.md)] lub programu Microsoft Outlook 2010.

  ![Link do wideo](../vsto/media/playvideo.gif "link do wideo") powiązane demonstracyjne wideo – zobacz [jak: Użyj okienka zadań w programie Outlook? ](http://go.microsoft.com/fwlink/?LinkID=130309).

## <a name="create-the-project"></a>Utwórz projekt
 Niestandardowe okienka zadań są implementowane w dodatkach VSTO. Rozpocznij od utworzenia projektu dodatku narzędzi VSTO dla programu Outlook.

### <a name="to-create-a-new-project"></a>Aby utworzyć nowy projekt

1. Tworzenie **dodatku programu Outlook** projekt o nazwie **OutlookMailItemTaskPane**. Użyj **dodatku programu Outlook** szablonu projektu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Otwiera *ThisAddIn.cs* lub *ThisAddIn.vb* plik kodu i dodaje **OutlookMailItemTaskPane** projekt **Eksploratora rozwiązań**.

## <a name="design-the-user-interface-of-the-custom-task-pane"></a>Projektowanie interfejsu użytkownika niestandardowego okienka zadań
 Brak wizualnego projektanta dla niestandardowych okienek zadań, ale można zaprojektować formant użytkownika za pomocą interfejsu użytkownika ma. Niestandardowego okienka zadań w tym dodatku narzędzi VSTO dla programów ma prosty interfejs użytkownika, który zawiera <xref:System.Windows.Forms.TextBox> kontroli. W dalszej części tego przewodnika dodasz formant użytkownika do niestandardowego okienka zadań.

### <a name="to-design-the-user-interface-of-the-custom-task-pane"></a>Projekt interfejsu użytkownika niestandardowego okienka zadań

1. W **Eksploratora rozwiązań**, kliknij przycisk **OutlookMailItemTaskPane** projektu.

2. Na **projektu** menu, kliknij przycisk **Dodaj kontrolkę użytkownika**.

3. W **Dodaj nowy element** okna dialogowego pole, Zmień nazwę kontrolki użytkownika do **TaskPaneControl**, a następnie kliknij przycisk **Dodaj**.

     Formant użytkownika zostanie otwarty w projektancie.

4. Z **wspólnych formantów** karcie **przybornika**, przeciągnij **TextBox** kontrolki do kontrolki użytkownika.

## <a name="design-the-user-interface-of-the-ribbon"></a>Projektowanie interfejsu użytkownika wstążki
 Jest jednym z celów dla tego dodatku narzędzi VSTO dla programów pozwala użytkownikom sposób, aby ukryć lub wyświetlić niestandardowego okienka zadań z poziomu wstążki każdej wiadomości e-mail. Aby zapewnić interfejsu użytkownika, należy utworzyć niestandardowy interfejs użytkownika wstążki, który wyświetla przycisk przełącznika, który użytkownicy mogą kliknąć, aby wyświetlić lub ukryć niestandardowego okienka zadań.

### <a name="to-create-a-custom-ribbon-ui"></a>Aby utworzyć niestandardowego interfejsu użytkownika wstążki

1. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.

2. W **Dodaj nowy element** okno dialogowe, wybierz opcję **Wstążka (Projektant graficzny)** .

3. Zmień nazwę nowego wstążki do **ManageTaskPaneRibbon**i kliknij przycisk **Dodaj**.

     *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon.vb* plik zostanie otwarty w Projektancie Wstążki i wyświetla domyślną kartę i grupę.

4. W Projektancie Wstążki kliknij **grupa1**.

5. W **właściwości** oknie **etykiety** właściwości **Menedżera okienka zadań**.

6. Z **formanty wstążki Office** karcie **przybornika**, przeciągnij formant ToggleButton na **Menedżera okienka zadań** grupy.

7. Click **toggleButton1**.

8. W **właściwości** oknie **etykiety** właściwości **Pokaż okienko zadań**.

## <a name="display-the-custom-ribbon-user-interface-with-email-messages"></a>Wyświetl niestandardowy interfejs użytkownika wstążki za pomocą wiadomości e-mail
 Niestandardowego okienka zadań utworzoną w tym przewodniku zaprojektowano w celu są wyświetlane tylko w przypadku systemu windows Inspector, zawierających wiadomości e-mail. W związku z tym Ustaw właściwości, aby wyświetlić niestandardowy interfejs użytkownika wstążki tylko z tych okien.

### <a name="to-display-the-custom-ribbon-ui-with-email-messages"></a>Aby wyświetlić niestandardowy interfejs użytkownika wstążki, za pomocą wiadomości e-mail

1. W Projektancie Wstążki kliknij **ManageTaskPaneRibbon** wstążki.

2. W **właściwości** , kliknij listę rozwijaną listę obok **RibbonType**i wybierz **Microsoft.Outlook.Mail.Compose** i  **Microsoft.Outlook.Mail.Read**.

## <a name="create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Utwórz klasę do zarządzania windows Inspektor i niestandardowych okienek zadań
 Istnieje kilka przypadków, w których dodatku narzędzi VSTO dla programów należy określić które niestandardowego okienka zadań jest skojarzony z określoną wiadomością e-mail. Te przypadki są następujące:

- Gdy użytkownik zamknie wiadomości e-mail. W tym przypadku dodatku narzędzi VSTO dla programów należy usunąć odpowiedniego niestandardowego okienka zadań, aby upewnić się, że zasoby używane przez dodatek narzędzi VSTO dla programów są poprawnie czyszczone.

- Gdy użytkownik zamknie niestandardowego okienka zadań. W tym przypadku dodatku narzędzi VSTO dla programów należy zaktualizować stan przycisku przełącznika na Wstążce wiadomości e-mail.

- Kiedy użytkownik klika przycisk przełączania na Wstążce. W tym przypadku dodatku narzędzi VSTO musi ukryć lub wyświetlić odpowiednie okienka zadań.

  Aby włączyć dodatek narzędzi VSTO dla programów do śledzenia które niestandardowego okienka zadań jest skojarzony z każdej otwartej wiadomości e-mail, należy utworzyć klasę niestandardową, która otacza pary <xref:Microsoft.Office.Interop.Outlook.Inspector> i <xref:Microsoft.Office.Tools.CustomTaskPane> obiektów. Ta klasa tworzy nowy obiekt w okienku zadania niestandardowego dla każdej wiadomości e-mail, a następnie usuwa niestandardowego okienka zadań, gdy odpowiednia wiadomość e-mail jest zamknięty.

### <a name="to-create-a-class-to-manage-inspector-windows-and-custom-task-panes"></a>Aby utworzyć klasę do zarządzania windows Inspektor i niestandardowych okienek zadań

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy *ThisAddIn.cs* lub *ThisAddIn.vb* pliku, a następnie kliknij przycisk **Wyświetl kod**.

2. Dodaj następujące instrukcje na górze pliku.

     [!code-csharp[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#2)]
     [!code-vb[Trin_OutlookMailItemTaskPane#2](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#2)]

3. Dodaj następujący kod do *ThisAddIn.cs* lub *ThisAddIn.vb* plików poza `ThisAddIn` klasy (dla języka Visual C#, Dodaj następujący kod wewnątrz `OutlookMailItemTaskPane` przestrzeni nazw). `InspectorWrapper` Klasa zarządza parę <xref:Microsoft.Office.Interop.Outlook.Inspector> i <xref:Microsoft.Office.Tools.CustomTaskPane> obiektów. Zostanie ukończona definicja tej klasy w poniższych krokach.

     [!code-csharp[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#3)]
     [!code-vb[Trin_OutlookMailItemTaskPane#3](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#3)]

4. Dodaj następujący Konstruktor po kodzie dodanym w poprzednim kroku. Ten konstruktor tworzy i inicjuje nowego niestandardowego okienka zadań skojarzonym z <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który jest przekazywany w. W języku C#, Konstruktor dołącza również programów obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> zdarzenia <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu i <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzenia <xref:Microsoft.Office.Tools.CustomTaskPane> obiektu.

     [!code-csharp[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#4)]
     [!code-vb[Trin_OutlookMailItemTaskPane#4](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#4)]

5. Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda jest program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.CustomTaskPane.VisibleChanged> zdarzenia <xref:Microsoft.Office.Tools.CustomTaskPane> obiekt, który jest zawarty w `InspectorWrapper` klasy. Ten kod aktualizuje stan przycisku przełącznika zawsze wtedy, gdy użytkownik otwiera lub zamyka niestandardowego okienka zadań.

     [!code-csharp[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#5)]
     [!code-vb[Trin_OutlookMailItemTaskPane#5](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#5)]

6. Dodaj następującą metodę po kodzie dodanym w poprzednim kroku. Ta metoda jest program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorEvents_Event.Close> zdarzenia <xref:Microsoft.Office.Interop.Outlook.Inspector> obiekt, który zawiera bieżącą wiadomość e-mail. Program obsługi zdarzeń zwalnia zasoby, gdy wiadomość e-mail jest zamknięty. Program obsługi zdarzeń spowoduje również usunięcie bieżącego niestandardowego okienka zadań z `CustomTaskPanes` kolekcji. Pozwala to zapobiec wiele wystąpień niestandardowego okienka zadań, po otwarciu dalej wiadomości e-mail.

     [!code-csharp[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#6)]
     [!code-vb[Trin_OutlookMailItemTaskPane#6](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#6)]

7. Dodaj następujący kod po kodzie dodanym w poprzednim kroku. W dalszej części tego przewodnika ta właściwość wywoła metodę niestandardowego interfejsu użytkownika wstążki, aby wyświetlić lub ukryć niestandardowego okienka zadań.

     [!code-csharp[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#7)]
     [!code-vb[Trin_OutlookMailItemTaskPane#7](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#7)]

## <a name="initialize-and-clean-up-resources-used-by-the-add-in"></a>Inicjowanie i oczyszczanie zasobów używanych przez dodatek
 Dodaj kod, aby `ThisAddIn` klasy można zainicjować dodatku narzędzi VSTO dla programów, podczas jego ładowania oraz aby wyczyścić zasoby używane przez dodatek narzędzi VSTO dla programów, gdy jest zwolniony. Należy zainicjować, konfigurując program obsługi zdarzeń dla dodatku narzędzi VSTO <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzeń i przekazanie wszystkich istniejących wiadomości e-mail do tego programu obsługi zdarzeń. Gdy dodatku narzędzi VSTO jest zwalniana, odłącz program obsługi zdarzeń i czyszczenie obiektów używanych przez dodatku narzędzi VSTO.

### <a name="to-initialize-and-clean-up-resources-used-by-the-vsto-add-in"></a>Aby zainicjować i wyczyścić zasoby używane przez dodatku narzędzi VSTO

1. W *ThisAddIn.cs* lub *ThisAddIn.vb* pliku, Znajdź definicję `ThisAddIn` klasy.

2. Dodaj następujące deklaracje na `ThisAddIn` klasy:

   - `inspectorWrappersValue` Pole zawiera wszystkie <xref:Microsoft.Office.Interop.Outlook.Inspector> i `InspectorWrapper` obiekty, które są zarządzane przez dodatku narzędzi VSTO.

   - `inspectors` Pola obsługuje odwołania do kolekcji Inspektor okna w bieżącym wystąpieniu programu Outlook. Zapobiega to odwołanie moduł zbierający elementy bezużyteczne zwalnianie pamięci, który zawiera program obsługi zdarzeń dla <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenie, które ciąg zostanie zadeklarowany w następnym kroku.

     [!code-csharp[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#8)]
     [!code-vb[Trin_OutlookMailItemTaskPane#8](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#8)]

3. Zastąp `ThisAddIn_Startup` metoda następującym kodem. Ten kod dołącza program obsługi zdarzeń do <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> zdarzenia i przekazuje co istniejące <xref:Microsoft.Office.Interop.Outlook.Inspector> obiektu do narzędzia obsługi zdarzeń. Jeśli użytkownik załaduje dodatku narzędzi VSTO po program Outlook jest już uruchomiony, dodatku narzędzi VSTO używa tych informacji do tworzenia niestandardowych okienek zadań dla wszystkich wiadomości e-mail, które są już otwarte.

    [!code-csharp[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#9)]
    [!code-vb[Trin_OutlookMailItemTaskPane#9](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#9)]

4. Zastąp `ThisAddIn_ShutDown` metoda następującym kodem. Ten kod powoduje odłączenie <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> program obsługi zdarzeń i czyści obiekty używane przez dodatek narzędzi VSTO dla programów.

    [!code-csharp[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#10)]
    [!code-vb[Trin_OutlookMailItemTaskPane#10](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#10)]

5. Dodaj następujący kod <xref:Microsoft.Office.Interop.Outlook.InspectorsEvents_Event.NewInspector> procedurę obsługi zdarzeń do `ThisAddIn` klasy. Jeśli nowy <xref:Microsoft.Office.Interop.Outlook.Inspector> zawiera wiadomości e-mail, ta metoda tworzy wystąpienie nowej `InspectorWrapper` obiektu do relacji między wiadomości e-mail i odpowiednie okienko zadań zarządzania.

    [!code-csharp[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#11)]
    [!code-vb[Trin_OutlookMailItemTaskPane#11](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#11)]

6. Dodaj następującą właściwość do `ThisAddIn` klasy. Ta właściwość udostępnia prywatna `inspectorWrappersValue` pole kodu poza `ThisAddIn` klasy.

    [!code-csharp[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ThisAddIn.cs#12)]
    [!code-vb[Trin_OutlookMailItemTaskPane#12](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ThisAddIn.vb#12)]

## <a name="checkpoint"></a>Punkt kontrolny
 Skompilować projekt, aby upewnić się, że kompiluje bez błędów.

### <a name="to-build-your-project"></a>Do kompilowania projektu

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **OutlookMailItemTaskPane** projektu, a następnie kliknij przycisk **kompilacji**. Upewnij się, że projekt kompiluje bez błędów.

## <a name="synchronize-the-ribbon-toggle-button-with-the-custom-task-pane"></a>Synchronizowanie przycisk przełączania wstążki z niestandardowego okienka zadań
 Przycisk przełączania, zostanie wyświetlony jako nacisnąć okienko zadań jest widoczne, gdy pojawi się nie naciśnięcia w przypadku okienka zadań jest ukryta. Aby zsynchronizować stan przycisku z niestandardowego okienka zadań, należy zmodyfikować <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> program obsługi zdarzeń przycisku przełączania.

### <a name="to-synchronize-the-custom-task-pane-with-the-toggle-button"></a>Aby zsynchronizować niestandardowego okienka zadań z przyciskiem przełączania

1. W Projektancie wstążki, kliknij dwukrotnie **Pokaż okienko zadań** przycisku przełączania.

     Program Visual Studio automatycznie generuje moduł obsługi zdarzeń o nazwie `toggleButton1_Click`, która obsługuje <xref:Microsoft.Office.Tools.Ribbon.RibbonToggleButton.Click> zdarzenia przycisku przełącznika. Program Visual Studio otwiera również *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon.vb* plik w edytorze kodu.

2. Dodaj następujące instrukcje na górze *ManageTaskPaneRibbon.cs* lub *ManageTaskPaneRibbon.vb* pliku.

     [!code-csharp[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#14)]
     [!code-vb[Trin_OutlookMailItemTaskPane#14](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#14)]

3. Zastąp `toggleButton1_Click` programu obsługi zdarzeń z następującym kodem. Gdy użytkownik kliknie przycisk przełączania, ta metoda ukrywa lub wyświetla niestandardowego okienka zadań skojarzony z bieżącym oknem Inspector.

     [!code-csharp[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/CSharp/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.cs#15)]
     [!code-vb[Trin_OutlookMailItemTaskPane#15](../vsto/codesnippet/VisualBasic/Trin_OutlookMailItemTaskPane/ManageTaskPaneRibbon.vb#15)]

## <a name="test-the-project"></a>Projekt testowy
 Po rozpoczęciu debugowania projektu, zostanie otwarty program Outlook i dodatku narzędzi VSTO jest ładowany. Dodatek narzędzi VSTO dla programów Wyświetla unikatowego wystąpienia niestandardowego okienka zadań z każdej wiadomości e-mail, który jest otwierany. Utwórz kilka nowych wiadomości e-mail do testowania kodu.

### <a name="to-test-the-vsto-add-in"></a>Aby przetestować dodatku narzędzi VSTO

1. Naciśnij klawisz **F5**.

2. W programie Outlook, kliknij przycisk **New** do tworzenia nowych wiadomości e-mail.

3. Na Wstążce wiadomości e-mail, kliknij przycisk **Add-Ins** kartę, a następnie kliknij przycisk **Pokaż okienko zadań** przycisku.

    Upewnij się, że okienka zadań z tytułem **okienko zadań** jest wyświetlany z wiadomością e-mail.

4. W okienku zadań wpisz **pierwszego okienka zadań** w polu tekstowym.

5. Zamknij okienko zadań.

    Upewnij się, że stan **Pokaż okienko zadań** przycisku zmienia się tak, aby nie był wciśnięty.

6. Kliknij przycisk **Pokaż okienko zadań** ponownie przycisk.

    Sprawdź, czy zostanie otwarte okienko zadania i pola tekstowego będzie nadal zawiera ciąg **pierwszego okienka zadań**.

7. W programie Outlook, kliknij przycisk **New** do utworzenia drugiej wiadomości e-mail.

8. Na Wstążce wiadomości e-mail, kliknij przycisk **Add-Ins** kartę, a następnie kliknij przycisk **Pokaż okienko zadań** przycisku.

    Upewnij się, że okienka zadań z tytułem **okienko zadań** jest wyświetlany za pomocą wiadomości e-mail i pole tekstowe, w tym okienku zadań jest puste.

9. W okienku zadań wpisz **drugi okienka zadań** w polu tekstowym.

10. Zmień fokus na pierwszy wiadomości e-mail.

     Sprawdź, czy okienko zadań, który jest skojarzony z tej wiadomości e-mail, nadal wyświetlany **pierwszego okienka zadań** w polu tekstowym.

    Ten dodatek narzędzi VSTO dla programów obsługuje także kilka zaawansowanych scenariuszy, które możesz wypróbować. Na przykład, testowanie zachowania podczas wyświetlania wiadomości e-mail przy użyciu **następny element** i **poprzedni element** przycisków. Możesz także testować zachowanie, gdy zwolnienie dodatku narzędzi VSTO dla programów, otwórz kilka wiadomości e-mail i ponownie załadować dodatku narzędzi VSTO.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu tworzenia niestandardowych okienek zadań z tych tematów:

- Tworzenie niestandardowego okienka zadań w dodatku narzędzi VSTO dla różnych aplikacji. Aby uzyskać więcej informacji na temat aplikacji, które obsługują niestandardowe okienka zadań, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).

- Automatyzowanie aplikacji pakietu Microsoft Office, korzystając z niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [instruktażu: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md).

- Utwórz przycisk na wstążce programu Excel, która pozwala ukryć lub wyświetlić niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [instruktażu: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md).

## <a name="see-also"></a>Zobacz także
- [Niestandardowe okienka zadań](../vsto/custom-task-panes.md)
- [Instrukcje: Dodawanie niestandardowego okienka zadań do aplikacji](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Przewodnik: Automatyzacja aplikacji z niestandardowego okienka zadań](../vsto/walkthrough-automating-an-application-from-a-custom-task-pane.md)
- [Przewodnik: Synchronizuj niestandardowego okienka zadań z przyciskiem wstążki](../vsto/walkthrough-synchronizing-a-custom-task-pane-with-a-ribbon-button.md)
- [Wstążka — omówienie](../vsto/ribbon-overview.md)
- [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)
- [Dostęp do wstążki w czasie wykonywania](../vsto/accessing-the-ribbon-at-run-time.md)
