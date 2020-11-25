---
title: Tworzenie przepływu pracy z formularzami skojarzenia i inicjowania
description: W tym instruktażu programu SharePoint Utwórz podstawowy sekwencyjny przepływ pracy, który obejmuje użycie formularzy skojarzenia i inicjacji.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- SharePoint development in Visual Studio, workflow association forms
- workflows [SharePoint development in Visual Studio]
- association forms [SharePoint development in Visual Studio]
- initiation forms [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, workflow initiation forms
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62501a23695b81ee0437d3210dced7c81f9b054e
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/24/2020
ms.locfileid: "95970436"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Przewodnik: tworzenie przepływu pracy z formularzami skojarzenia i inicjowania
  W tym instruktażu pokazano, jak utworzyć podstawowy sekwencyjny przepływ pracy, który obejmuje użycie formularzy skojarzenia i inicjacji. Są to formularze ASPX, które umożliwiają dodawanie parametrów do przepływu pracy, gdy jest on najpierw skojarzony przez administratora programu SharePoint (formularz skojarzenia) i gdy przepływ pracy jest uruchamiany przez użytkownika (formularz inicjacji).

 W tym instruktażu przedstawiono scenariusz, w którym użytkownik chce utworzyć przepływ pracy zatwierdzania dla raportów wydatków, które mają następujące wymagania:

- Gdy przepływ pracy jest skojarzony z listą, administrator zostanie monitowany przy użyciu formularza skojarzenia, gdzie wprowadza limit dolarów dla raportów wydatków.

- Pracownicy przekazują raporty wydatków do listy Dokumenty udostępnione, uruchamiają przepływ pracy, a następnie wprowadzają sumę wydatków w formularzu inicjowania przepływu pracy.

- Jeśli raport wydatków pracowników łącznie przekracza wstępnie zdefiniowany limit administratora, zadanie zostanie utworzone dla Menedżera pracownika, aby zatwierdzić raport wydatków. Jeśli jednak raport wydatków pracownika jest mniejszy lub równy limitowi wydatków, zostanie on zapisany na liście historii przepływu pracy.

  W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu sekwencyjnego przepływu pracy definicji listy programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

- Tworzenie harmonogramu przepływu pracy.

- Obsługa zdarzeń działań przepływu pracy.

- Tworzenie skojarzenia przepływu pracy i formularzy inicjacji.

- Kojarzenie przepływu pracy.

- Ręczne uruchamianie przepływu pracy.

> [!NOTE]
> Chociaż w tym instruktażu jest stosowany projekt sekwencyjnego przepływu pracy, proces ten jest taki sam dla przepływów pracy automatu Stanów.
>
> Ponadto na komputerze mogą być wyświetlane różne nazwy lub lokalizacje dla niektórych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementów interfejsu użytkownika w poniższych instrukcjach. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]Wersja, która jest używana, oraz używane ustawienia określają te elementy. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje programów [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i SharePoint.

- Programu Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Utwórz projekt sekwencyjnego przepływu pracy programu SharePoint
 Najpierw utwórz projekt sekwencyjnego przepływu pracy w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . Sekwencyjny przepływ pracy to seria kroków, które są wykonywane w kolejności do momentu zakończenia ostatniego działania. W tej procedurze utworzysz sekwencyjny przepływ pracy, który jest stosowany do listy Dokumenty udostępnione w programie SharePoint. Kreator przepływu pracy umożliwia skojarzenie przepływu pracy z witryną lub definicją listy i pozwala określić, kiedy zostanie uruchomiony przepływ pracy.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Aby utworzyć projekt sekwencyjnego przepływu pracy programu SharePoint

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** .

2. Rozwiń węzeł **SharePoint** w **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **2010** .

3. W okienku **Szablony** wybierz szablon projektu **projektu programu SharePoint 2010** .

4. W polu **Nazwa** wprowadź **ExpenseReport** , a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

5. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wybierz przycisk opcji **Wdróż jako farmę** , a następnie wybierz przycisk **Zakończ** , aby zaakceptować poziom zaufania i domyślną lokację.

     Ten krok ustawia również poziom zaufania dla rozwiązania jako rozwiązanie farmy, które jest jedyną dostępną opcją dla projektów przepływu pracy.

6. W **Eksplorator rozwiązań** wybierz węzeł projektu.

7. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

8. W obszarze **Visual C#** lub **Visual Basic** rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

9. W okienku **Szablony** wybierz szablon **sekwencyjny przepływ pracy (tylko rozwiązanie farmy)** , a następnie wybierz przycisk **Dodaj** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

10. Na stronie **Określanie nazwy przepływu pracy na potrzeby debugowania** Zaakceptuj nazwę domyślną (**ExpenseReport-Workflow1**). Zachowaj domyślną wartość typu szablonu przepływu pracy (**przepływ pracy listy)**. Wybierz przycisk **dalej** .

11. Czy chcesz, **Aby program Visual Studio automatycznie kojarzy przepływ pracy w sesji debugowania?** wyczyść pole, które automatycznie kojarzy szablon przepływu pracy, jeśli jest zaznaczone.

     Ten krok pozwala ręcznie skojarzyć przepływ pracy z listą udostępnionych dokumentów w dalszej części, która wyświetla formularz skojarzenia.

12. Wybierz przycisk **Zakończ** .

## <a name="add-an-association-form-to-the-workflow"></a>Dodawanie formularza skojarzenia do przepływu pracy
 Następnie utwórz. Formularz skojarzenia ASPX, który jest wyświetlany, gdy administrator programu SharePoint najpierw skojarzy przepływ pracy z dokumentem raportu wydatków.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Aby dodać formularz skojarzenia do przepływu pracy

1. Wybierz węzeł **Workflow1** w **Eksplorator rozwiązań**.

2. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element** , aby wyświetlić okno dialogowe **Dodaj nowy element** .

3. W widoku drzewa okna dialogowego rozwiń pozycję **Visual C#** lub **Visual Basic** (w zależności od języka projektu), rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. Na liście szablonów wybierz szablon **formularza skojarzenia przepływu pracy** .

5. W polu tekstowym **Nazwa** wprowadź **ExpenseReportAssocForm. aspx**.

6. Wybierz przycisk **Dodaj** , aby dodać formularz do projektu.

## <a name="designing-and-coding-the-association-form"></a>Projektowanie i kodowanie formularza skojarzenia
 W tej procedurze wprowadzasz funkcję do formularza skojarzenia przez dodanie formantów i kodu do niego.

#### <a name="to-design-and-code-the-association-form"></a>Aby zaprojektować i zakodować formularz skojarzenia

1. W formularzu skojarzenia (ExpenseReportAssocForm. aspx) Znajdź `asp:Content` element, który ma `ID="Main"` .

2. Bezpośrednio po pierwszym wierszu w tym elemencie zawartości Dodaj następujący kod, aby utworzyć etykietę i pole tekstowe z komunikatem o limicie zatwierdzenia wydatków (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Rozwiń plik **ExpenseReportAssocForm. aspx** w **Eksplorator rozwiązań** , aby wyświetlić jego pliki zależne.

    > [!NOTE]
    > Jeśli projekt jest w programie [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] , musisz wybrać przycisk **Wyświetl wszystkie pliki** , aby wykonać ten krok.

4. Otwórz menu skrótów dla pliku ExpenseReportAssocForm. aspx i wybierz polecenie **Wyświetl kod**.

5. Zastąp `GetAssociationData` metodę:

    ```vb
    Private Function GetAssociationData() As String
        ' TODO: Return a string that contains the association data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return Me.AutoApproveLimit.Text
    End Function
    ```

    ```csharp
    private string GetAssociationData()
    {
        // TODO: Return a string that contains the association data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.AutoApproveLimit.Text;
    }
    ```

## <a name="add-an-initiation-form-to-the-workflow"></a>Dodawanie formularza inicjowania do przepływu pracy
 Następnie Utwórz formularz inicjowania, który pojawia się, gdy użytkownicy uruchamiają przepływ pracy względem raportów wydatków.

#### <a name="to-create-an-initiation-form"></a>Aby utworzyć formularz inicjowania

1. Wybierz węzeł **Workflow1** w **Eksplorator rozwiązań**.

2. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element** Wyświetl okno dialogowe **Dodaj nowy element** .

3. W widoku drzewa okna dialogowego rozwiń pozycję **Visual C#** lub **Visual Basic**  (w zależności od języka projektu), rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

4. Na liście szablonów wybierz szablon **formularza inicjowania przepływu pracy** .

5. W polu tekstowym **Nazwa** wprowadź **ExpenseReportInitForm. aspx**.

6. Wybierz przycisk **Dodaj** , aby dodać formularz do projektu.

## <a name="designing-and-coding-the-initiation-form"></a>Projektowanie i kodowanie formularza inicjacji
 Następnie wprowadź funkcje do formularza inicjowania, dodając formanty i kod do niego.

#### <a name="to-code-the-initiation-form"></a>Aby zakodować formularz inicjowania

1. W formularzu inicjowania (ExpenseReportInitForm. aspx) Znajdź `asp:Content` element, który zawiera `ID="Main"` .

2. Bezpośrednio po pierwszym wierszu w tym elemencie zawartości Dodaj następujący kod, aby utworzyć etykietę i pole tekstowe, które wyświetla limit zatwierdzania wydatków (*AutoApproveLimit*), który został wprowadzony w formularzu skojarzenia, a następnie inną etykietę i pole tekstowe, aby wyświetlić monit o podanie sumy wydatków (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Rozwiń plik **ExpenseReportInitForm. aspx** w **Eksplorator rozwiązań** , aby wyświetlić jego pliki zależne.

4. Otwórz menu skrótów dla pliku ExpenseReportInitForm. aspx i wybierz polecenie **Wyświetl kod**.

5. Zastąp `Page_Load` metodę następującym przykładem:

    ```vb
    Protected Sub Page_Load(ByVal sender As Object, ByVal e As
      EventArgs) Handles Me.Load
        InitializeParams()
        Me.AutoApproveLimit.Text = workflowList.WorkflowAssociations(New
          Guid(associationGuid)).AssociationData
        ' Optionally, add code here to pre-populate your form fields.
    End Sub
    ```

    ```csharp
    protected void Page_Load(object sender, EventArgs e)
    {
        InitializeParams();
        this.AutoApproveLimit.Text =
          workflowList.WorkflowAssociations[new
          Guid(associationGuid)].AssociationData;
    }
    ```

6. Zastąp `GetInitiationData` metodę następującym przykładem:

    ```vb
    ' This method is called when the user clicks the button to start the workflow.
    Private Function GetInitiationData() As String
        Return Me.ExpenseTotal.Text
        ' TODO: Return a string that contains the initiation data that
        ' will be passed to the workflow. Typically, this is in XML
        ' format.
        Return String.Empty
    End Function
    ```

    ```csharp
    // This method is called when the user clicks the button to start the workflow.
    private string GetInitiationData()
    {
        // TODO: Return a string that contains the initiation data that
        // will be passed to the workflow. Typically, this is in XML
        // format.
        return this.ExpenseTotal.Text;
    }
    ```

## <a name="cutomize-the-workflow"></a>Cutomize przepływ pracy
 Następnie dostosuj przepływ pracy. Później będziesz kojarzyć dwa formularze z przepływem pracy.

#### <a name="to-customize-the-workflow"></a>Aby dostosować przepływ pracy

1. Wyświetl przepływ pracy w Projektancie przepływów pracy, otwierając Workflow1 w projekcie.

2. W **przyborniku** rozwiń węzeł **Windows Workflow v 3.0** i Znajdź działanie **jeślilub** .

3. Dodaj to działanie do przepływu pracy, wykonując jedną z następujących czynności:

    - Otwórz menu skrótów dla działania **jeślilub** , wybierz polecenie **Kopiuj**, otwórz menu skrótów dla wiersza w działaniu **onWorkflowActivated1** w Projektancie przepływu pracy, a następnie wybierz **Wklej**.

    - Przeciągnij działanie **jeślilub** z **przybornika** i połącz je z wierszem w obszarze działania **onWorkflowActiviated1** w Projektancie przepływu pracy.

4. W przyborniku rozwiń węzeł **przepływ pracy programu SharePoint** i Znajdź działanie w ramach **zadania** .

5. Dodaj to działanie do przepływu pracy, wykonując jedną z następujących czynności:

    - Otwórz menu skrótów dla działania **zadania** , wybierz polecenie **Kopiuj**, otwórz menu skrótów dla jednej z dwóch **działań upuść** w obszarze **IfElseActivity1** w Projektancie przepływu pracy, a następnie wybierz **Wklej**.

    - Przeciągnij działanie **zadania** podrzędnego z **przybornika** na jedną z dwóch **działań upuszczania** w obszarze **IfElseActivity1**.

6. W oknie **Właściwości** wprowadź wartość właściwości *TaskToken* dla właściwości **CorrelationToken** .

7. Rozwiń Właściwość **CorrelationToken** , wybierając znak plus (![TreeView Plus](../sharepoint/media/plus.gif "TreeView i")) obok niego.

8. Wybierz strzałkę listy rozwijanej we właściwości Sub **OwnerActivityName** i ustaw wartość *Workflow1* .

9. Wybierz właściwość **TaskID** , a następnie wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")), aby wyświetlić okno dialogowe **Właściwości powiązania** .

10. Wybierz kartę **powiąż z nowym członkiem** , wybierz przycisk opcji **Utwórz pole** , a następnie wybierz przycisk **OK** .

11. Wybierz właściwość **TaskProperties** , a następnie wybierz przycisk wielokropka (![ASP.net Mobile Designer](../sharepoint/media/mwellipsis.gif "Wielokropek projektanta ASP.NET Mobile")), aby wyświetlić okno dialogowe **Właściwości powiązania** .

12. Wybierz kartę **powiąż z nowym członkiem** , wybierz przycisk opcji **Utwórz pole** , a następnie wybierz przycisk **OK** .

13. W **przyborniku** rozwiń węzeł **przepływ pracy programu SharePoint** i Znajdź działanie **LogToHistoryListActivity** .

14. Dodaj to działanie do przepływu pracy, wykonując jedną z następujących czynności:

    - Otwórz menu skrótów dla działania **LogToHistoryListActivity** , wybierz polecenie **Kopiuj**, otwórz menu skrótów dla innych **działań upuść** w obszarze **IfElseActivity1** w Projektancie przepływu pracy, a następnie wybierz **Wklej**.

    - Przeciągnij działanie **LogToHistoryListActivity** z **przybornika** i upuść je na inne **działania upuść** w obszarze **IfElseActivity1**.

## <a name="add-code-to-the-workflow"></a>Dodawanie kodu do przepływu pracy
 Następnie Dodaj kod do przepływu pracy, aby zapewnić jego funkcjonalność.

#### <a name="to-add-code-to-the-workflow"></a>Aby dodać kod do przepływu pracy

1. Otwórz menu skrótów dla działania **createTask1** w Projektancie przepływu pracy, a następnie wybierz polecenie **Wyświetl kod**.

2. Dodaj następującą metodę:

    ```vb
    Private Sub createTask1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        createTask1_TaskId1 = Guid.NewGuid
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser"
        createTask1_TaskProperties1.Description = "Please approve the
          expense report"
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed"
    End Sub
    ```

    ```csharp
    private void createTask1_MethodInvoking(object sender, EventArgs e)
    {
        createTask1_TaskId1 = Guid.NewGuid();
        createTask1_TaskProperties1.AssignedTo = "somedomain\\someuser";
        createTask1_TaskProperties1.Description = "Please approve the
          expense report";
        createTask1_TaskProperties1.Title = "Expense Report Approval
          Needed";
    }
    ```

    > [!NOTE]
    > W kodzie Zastąp `somedomain\\someuser` wartość domeną i nazwą użytkownika, dla którego zadanie zostanie utworzone, na przykład " `Office\\JoeSch` ". W przypadku testowania najłatwiejszym rozwiązaniem jest użycie konta, które jest opracowywane.

3. Poniżej `MethodInvoking` metody Dodaj następujący przykład:

    ```vb
    Private Sub checkApprovalNeeded(ByVal sender As Object, ByVal e As
      ConditionalEventArgs)
        Dim approval As Boolean = False
        If (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData)) Then
            approval = True
        End If
        e.Result = approval
    End Sub
    ```

    ```csharp
    private void checkApprovalNeeded(object sender, ConditionalEventArgs
      e)
    {
        bool approval = false;
        if (Convert.ToInt32(workflowProperties.InitiationData) >
          Convert.ToInt32(workflowProperties.AssociationData))
        {
            approval = true;
        }
        e.Result = approval;
    }
    ```

4. W Projektancie przepływu pracy wybierz działanie **ifElseBranchActivity1** .

5. W oknie **Właściwości** , wybierz strzałkę listy rozwijanej właściwości **warunek** , a następnie ustaw wartość *warunek kodu* .

6. Rozwiń Właściwość **Condition** , wybierając znak plus (![TreeView Plus](../sharepoint/media/plus.gif "TreeView i")) obok niego, a następnie ustaw jego wartość na *checkApprovalNeeded*.

7. W Projektancie przepływu pracy Otwórz menu skrótów dla działania **logToHistoryListActivity1** , a następnie wybierz polecenie **Generuj programy obsługi** , aby wygenerować pustą metodę dla `MethodInvoking` zdarzenia.

8. Zastąp `MethodInvoking` kod następującym:

    ```vb
    Private Sub logToHistoryListActivity1_MethodInvoking(ByVal sender As
      System.Object, ByVal e As System.EventArgs)
        Me.logToHistoryListActivity1.HistoryOutcome = ("Expense was auto
          approved for " + workflowProperties.InitiationData)
    End Sub
    ```

    ```csharp
    private void logToHistoryListActivity1_MethodInvoking(object sender,
      EventArgs e)
    {
        this.logToHistoryListActivity1.HistoryOutcome = "Expense was
          auto approved for " + workflowProperties.InitiationData;
    }
    ```

9. Wybierz klawisz **F5** , aby debugować program.

     Spowoduje to skompilowanie aplikacji, jej pakiet, wdrożenie, aktywowanie jej funkcji, [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] odtworzenie puli aplikacji, a następnie uruchomienie przeglądarki w lokalizacji określonej we właściwości **adres URL witryny** .

## <a name="associating-the-workflow-to-the-documents-list"></a>Kojarzenie przepływu pracy z listą dokumentów
 Następnie Wyświetl formularz skojarzenia przepływu pracy, kojarząc przepływ pracy z listą **SharedDocuments** w witrynie programu SharePoint.

#### <a name="to-associate-the-workflow"></a>Aby skojarzyć przepływ pracy

1. Na pasku szybkiego uruchamiania wybierz link **dokumenty udostępnione** .

2. Wybierz łącze **Biblioteka** na karcie **Narzędzia biblioteki** , a następnie wybierz przycisk wstążki **Ustawienia biblioteki** .

3. W sekcji **uprawnienia i zarządzanie** wybierz łącze **Ustawienia przepływu pracy** , a następnie wybierz łącze **Dodaj przepływ pracy** na stronie **przepływy** pracy.

4. Na górnej liście na stronie Ustawienia przepływu pracy wybierz szablon **ExpenseReport-Workflow1** .

5. W następnym polu wpisz **ExpenseReportWorkflow** , a następnie wybierz przycisk **dalej** .

     Spowoduje to skojarzenie przepływu pracy z listą **udostępnionych dokumentów** i wyświetlenie formularza skojarzenia przepływu pracy.

6. W polu tekstowym **Limit autozatwierdzania** wprowadź **1200** , a następnie wybierz przycisk **Skojarz przepływ pracy** .

## <a name="start-the-workflow"></a>Uruchom przepływ pracy
 Następnie skojarz przepływ pracy z jednym z dokumentów na liście **dokumenty udostępnione** , aby wyświetlić formularz inicjowania przepływu pracy.

#### <a name="to-start-the-workflow"></a>Aby uruchomić przepływ pracy

1. Na stronie programu SharePoint wybierz przycisk **Strona główna** .

2. Wybierz link **dokumenty udostępnione** na pasku szybkiego uruchamiania, aby wyświetlić listę **dokumenty udostępnione** .

3. Wybierz link **dokumenty** na karcie **Narzędzia biblioteki** w górnej części strony, a następnie wybierz przycisk **Przekaż dokument** na Wstążce, aby przekazać nowy dokument do listy **dokumenty udostępnione** .

4. W oknie dialogowym **przekazywanie dokumentu** wybierz przycisk **Przeglądaj** , wybierz dowolny plik dokumentu, wybierz przycisk **Otwórz** , a następnie wybierz przycisk **OK** .

     Możesz zmienić ustawienia dla dokumentu w tym oknie dialogowym, ale pozostaw je wartościami domyślnymi, wybierając przycisk **Zapisz** .

5. Wybierz przekazany dokument, wybierz strzałkę listy rozwijanej, która zostanie wyświetlona, a następnie wybierz element **przepływy pracy** .

6. Wybierz obraz obok ExpenseReportWorkflow.

     Spowoduje to wyświetlenie formularza inicjowania przepływu pracy. (Należy zauważyć, że wartość wyświetlana w polu **Limit autozatwierdzania** jest tylko do odczytu, ponieważ została wprowadzona w formularzu skojarzenia).

7. W polu tekstowym **Łączny koszt** wprowadź **1600**, a następnie wybierz przycisk **Uruchom przepływ pracy** .

     Spowoduje to wyświetlenie listy **dokumenty udostępnione** ponownie. Nowa kolumna o nazwie **ExpenseReportWorkflow** z **Zakończono** wartością zostanie dodana do elementu, w którym właśnie uruchomiono przepływ pracy.

8. Wybierz strzałkę listy rozwijanej obok przekazanego dokumentu, a następnie wybierz element **przepływy pracy** , aby wyświetlić stronę Stan przepływu pracy. Wybierz wartość **ukończoną** w obszarze **ukończone przepływy pracy**. Zadanie jest wyświetlane w sekcji **zadania** .

9. Wybierz tytuł zadania, aby wyświetlić jego szczegóły zadania.

10. Wróć do listy **SharedDocuments** i ponownie uruchom przepływ pracy przy użyciu tego samego dokumentu lub innego.

11. Wprowadź kwotę na stronie inicjowania, która jest mniejsza lub równa wartości wprowadzonej na stronie skojarzenie (**1200**).

     W takim przypadku zostanie utworzony wpis na liście historia zamiast zadania. Wpis zostanie wyświetlony w sekcji **Historia przepływu pracy** na stronie stan przepływu pracy. Zanotuj komunikat w kolumnie **wynik** zdarzenia historii. Zawiera tekst wprowadzony w `logToHistoryListActivity1.MethodInvoking` zdarzeniu, który obejmuje kwotę, która została zatwierdzona.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia szablonów przepływu pracy można znaleźć w następujących tematach:

- Aby dowiedzieć się więcej na temat przepływów pracy programu SharePoint, zobacz [przepływy pracy w programie Windows SharePoint Services](/previous-versions/office/developer/sharepoint-2010/ms416312(v=office.14)).

## <a name="see-also"></a>Zobacz też
- [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Przewodnik: Dodawanie strony aplikacji do przepływu pracy](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
