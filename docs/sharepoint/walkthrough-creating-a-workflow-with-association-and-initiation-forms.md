---
title: 'Przewodnik: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 43ee8d26338b6d15530c51191c3368d3fc556d2c
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60081739"
---
# <a name="walkthrough-create-a-workflow-with-association-and-initiation-forms"></a>Przewodnik: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia
  W tym instruktażu pokazano, jak utworzyć podstawowy sekwencyjny przepływ pracy, który obejmuje korzystanie z formularzy skojarzenia i inicjacji. Są to formularze ASPX umożliwiające dodanie parametrów do przepływu pracy, gdy jest on pierwszy raz skojarzony przez administratora programu SharePoint (formularz skojarzenia) i po uruchomieniu przepływu pracy przez użytkownika (formularz inicjowania).

 Ten przewodnik przedstawia scenariusz, w którym użytkownik chce utworzyć przepływ pracy zatwierdzania w raportach wydatków i ma następujące wymagania:

- Gdy przepływ pracy jest skojarzony z listą, administrator jest proszony przy użyciu formularza skojarzenia o podanie limitu kwoty na raport wydatków.

- Pracownicy przesyłają swoje raporty wydatków na listę Dokumenty udostępnione, uruchamiają przepływ pracy, a następnie wprowadzają całkowitą kwotę wydatków w formularzu inicjowania przepływu pracy.

- Jeśli całkowita suma wydatków w raporcie pracownika przekracza limit wstępnie zdefiniowany przez administratora, tworzone jest zadanie dla menedżera pracownika, aby zatwierdzić raport wydatków. Jeśli jednak suma wydatków w raporcie pracownika jest mniejsza od limitu wydatków lub równa temu limitowi, na liście historii przepływu pracy zostanie zapisany komunikat o automatycznym zatwierdzeniu raportu.

  W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu programu SharePoint listy definicji sekwencyjnego przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Tworzenie harmonogramu przepływu pracy.

- Obsługa zdarzeń działania przepływu pracy.

- Tworzenie przepływu pracy, formularzy skojarzenia i inicjacji.

- Skojarzenie przepływu pracy.

- Ręczne uruchamianie przepływu pracy.

> [!NOTE]
>  Chociaż ten przewodnik korzysta z projektem sekwencyjnego przepływu pracy, proces jest taki sam dla przepływów pracy automatu stanów.
>
>  Ponadto komputer może wyświetlać różne nazwy lub lokalizacje dla niektórych [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] elementy interfejsu użytkownika w poniższych instrukcjach. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] Te elementy są określane edition, czy masz i ustawień, których używasz. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane edycje [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint.

- Program Visual Studio.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Utwórz projekt sekwencyjnego przepływu pracy programu SharePoint
 Najpierw utwórz projekt sekwencyjnego przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Sekwencyjny przepływ pracy jest serię kroków, który jest wykonywany w kolejności, aż do zakończenia ostatniej aktywności. W tej procedurze utworzysz sekwencyjnego przepływu pracy, który ma zastosowanie do listy dokumentów udostępnionych w programie SharePoint. Kreator przepływu pracy umożliwia skojarzenie przepływu pracy przy użyciu witryny lub definicji listy i pozwala określić, gdy rozpocznie się przepływ pracy.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Aby utworzyć projekt sekwencyjnego przepływu pracy programu SharePoint

1. Na pasku menu wybierz **pliku** > **New** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.

2. Rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz **2010** węzła.

3. W **szablony** okienku wybierz **projekt programu SharePoint 2010** szablonu projektu.

4. W **nazwa** wprowadź **ExpenseReport** , a następnie wybierz **OK** przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się.

5. W **Określanie witryny i poziomu zabezpieczeń dla debugowania** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisk, aby zaakceptować Witryna poziom i domyślne zaufanie.

     W tym kroku ustawi poziom zaufania dla rozwiązania, rozwiązanie farmy, który jest jedyną dostępną opcją w przypadku projektów przepływu pracy.

6. W **Eksploratora rozwiązań**, wybierz węzeł projektu.

7. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

8. W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.

9. W **szablony** okienku wybierz **sekwencyjnego przepływu pracy (tylko rozwiązanie farmy)** szablonu, a następnie wybierz **Dodaj** przycisku.

     **Kreator ustawień niestandardowych SharePoint** pojawia się.

10. W **Określ nazwę przepływu pracy debugowania** strona, zaakceptuj nazwę domyślną (**ExpenseReport - Workflow1**). Należy zachować wartość typu szablonu przepływu pracy domyślnego (**przepływu pracy dla listy)**. Wybierz **dalej** przycisku.

11. W **chcesz użyć programu Visual Studio automatycznie skojarzył przepływ pracy w sesji debugowania?** strony, usuń zaznaczenie tego pola, które automatycznie kojarzy szablonu przepływu pracy, jeśli zaznaczono opcję on.

     Ten krok pozwala ręcznie skojarzyć przepływ pracy z listą dokumenty udostępnione w późniejszym czasie na, który wyświetla formularz skojarzenia.

12. Wybierz **Zakończ** przycisku.

## <a name="add-an-association-form-to-the-workflow"></a>Dodaj formularz skojarzenia przepływu pracy
 Następnie należy utworzyć. Formularz skojarzenia ASPX, który jest wyświetlany, gdy administrator programu SharePoint najpierw skojarzenie przepływu pracy z dokumentu raportu wydatków.

#### <a name="to-add-an-association-form-to-the-workflow"></a>Aby dodać formularz skojarzenia przepływu pracy

1. Wybierz **Workflow1** w węźle **Eksploratora rozwiązań**.

2. Na pasku menu wybierz **projektu** > **Dodaj nowy element** do wyświetlenia **Dodaj nowy element** okno dialogowe.

3. W widoku drzewa okna dialogowego pole, rozwiń **Visual C#** lub **języka Visual Basic** (w zależności od Twój język projektu), rozwiń węzeł **SharePoint** węzła, a następnie wybierz polecenie **2010** węzła.

4. Z listy szablonów wybierz **formularza skojarzenia przepływu pracy** szablonu.

5. W **nazwa** tekstu wprowadź **ExpenseReportAssocForm.aspx**.

6. Wybierz **Dodaj** przycisk, aby dodać formularz do projektu.

## <a name="designing-and-coding-the-association-form"></a>Projektowanie i programowanie formularza skojarzenia
 W tej procedurze wprowadzasz funkcje do formularza skojarzenia, dodając formanty i kod do niego.

#### <a name="to-design-and-code-the-association-form"></a>Do projektu i kodu formularza skojarzenia

1. W formularzu skojarzenia (ExpenseReportAssocForm.aspx), Znajdź `asp:Content` element, który ma `ID="Main"`.

2. Bezpośrednio po pierwszy wiersz w tym elemencie content, Dodaj następujący kod do tworzenia etykiety i pola tekstowego, który wyświetla monit o zatwierdzenie limit wydatków (*AutoApproveLimit*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" runat="server" />
    <br /><br />
    ```

3. Rozwiń **ExpenseReportAssocForm.aspx** w pliku **Eksploratora rozwiązań** do wyświetlenia jego plików zależnych.

    > [!NOTE]
    >  Jeśli projekt jest w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)], musisz wybrać **Wyświetl wszystkie pliki** przycisk, aby wykonać ten krok.

4. Otwórz menu skrótów dla pliku ExpenseReportAssocForm.aspx i wybierz polecenie **Wyświetl kod**.

5. Zastąp `GetAssociationData` metody:

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
 Następnie należy utworzyć formularza inicjowania, który pojawia się podczas uruchamiania przepływu pracy przez użytkowników względem ich raporty wydatków.

#### <a name="to-create-an-initiation-form"></a>Aby utworzyć formularza inicjowania

1. Wybierz **Workflow1** w węźle **Eksploratora rozwiązań**.

2. Na pasku menu wybierz **projektu** > **Dodaj nowy element** wyświetlić **Dodaj nowy element** okno dialogowe.

3. W widoku drzewa okna dialogowego pole, rozwiń **Visual C#** lub **języka Visual Basic** (w zależności od Twój język projektu), rozwiń węzeł **SharePoint** węzła, a następnie wybierz polecenie **2010** węzła.

4. Z listy szablonów wybierz **formularza inicjowania przepływu pracy** szablonu.

5. W **nazwa** tekstu wprowadź **ExpenseReportInitForm.aspx**.

6. Wybierz **Dodaj** przycisk, aby dodać formularz do projektu.

## <a name="designing-and-coding-the-initiation-form"></a>Projektowanie i programowanie formularza inicjowania
 Następnie wprowadzić funkcje do formularza inicjowania, dodając formanty i kod do niego.

#### <a name="to-code-the-initiation-form"></a>Do kodu formularza inicjowania

1. W formularzu inicjowania (ExpenseReportInitForm.aspx), Znajdź `asp:Content` element, który zawiera `ID="Main"`.

2. Bezpośrednio po pierwszy wiersz w tym elemencie content, Dodaj następujący kod, aby utworzyć etykiety i pole tekstowe zawierające zatwierdzenia limitu wydatków (*AutoApproveLimit*) wprowadzone w formularzu skojarzenia i inną etykietę i pole tekstowe, aby monitować o łączny koszt (*ExpenseTotal*):

    ```aspx-csharp
    <asp:Label ID="lblAutoApproveLimit" Text="Auto Approval Limit:" runat="server" />

    <asp:TextBox ID="AutoApproveLimit" ReadOnly="true" runat="server" />
    <br /><br />
    <asp:Label ID="lblExpenseTotal" Text="Expense Total:" runat="server" />

    <asp:TextBox ID="ExpenseTotal" runat="server" />
    <br /><br />
    ```

3. Rozwiń **ExpenseReportInitForm.aspx** w pliku **Eksploratora rozwiązań** do wyświetlenia jego plików zależnych.

4. Otwórz menu skrótów dla pliku ExpenseReportInitForm.aspx i wybierz polecenie **Wyświetl kod**.

5. Zastąp `Page_Load` metody z poniższym przykładzie:

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

6. Zastąp `GetInitiationData` metody z poniższym przykładzie:

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

## <a name="cutomize-the-workflow"></a>Dostosowywanie przepływu pracy
 Następnie można dostosować przepływ pracy. Później które skojarzysz dwie formy do przepływu pracy.

#### <a name="to-customize-the-workflow"></a>Aby dostosować przepływ pracy

1. Wyświetl przepływ pracy w Projektancie przepływu pracy, otwierając Workflow1 w projekcie.

2. W **przybornika**, rozwiń węzeł **Windows Workflow 3.0** węzła i Znajdź **Jeślilub** działania.

3. Dodaj to działanie w przepływie pracy, wykonując jedną z następujących czynności:

    - Otwórz menu skrótów dla **Jeślilub** działania, wybierz **kopiowania**, otwórz menu skrótów dla linii poniżej **onWorkflowActivated1** działania w Projektancie przepływu pracy a następnie wybierz **Wklej**.

    - Przeciągnij **Jeślilub** działanie z **przybornika**i podłącz go do nowego wiersza w obszarze **onWorkflowActiviated1** działania w Projektancie przepływu pracy.

4. W przyborniku, rozwiń węzeł **przepływu pracy programu SharePoint** węzła i Znajdź **createtask —** działania.

5. Dodaj to działanie w przepływie pracy, wykonując jedną z następujących czynności:

    - Otwórz menu skrótów dla **createtask —** działania, wybierz **kopiowania**, otwórz menu skrótów dla jednej z dwóch **Upuść tutaj działania** obszarów w obrębie  **IfElseActivity1** w Projektancie przepływu pracy, a następnie wybierz **Wklej**.

    - Przeciągnij **createtask —** działanie z **przybornika** na jedną z dwóch **Upuść tutaj działania** obszarów w obrębie **IfElseActivity1**.

6. W **właściwości** okna, wprowadź wartość właściwości *taskToken* dla **CorrelationToken** właściwości.

7. Rozwiń **CorrelationToken** właściwości, wybierając znak plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) obok niego.

8. Wybierz strzałkę listy rozwijanej na **OwnerActivityName** sub właściwości, a następnie ustaw *Workflow1* wartości.

9. Wybierz **TaskId** właściwości, a następnie wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) przycisk, aby wyświetlić **Powiązania właściwości** okno dialogowe.

10. Wybierz **powiązać nowy element członkowski** kartę, wybrać **utworzyć pole** przycisk opcji, a następnie wybierz **OK** przycisku.

11. Wybierz **TaskProperties** właściwości, a następnie wybierz przycisk wielokropka (![elipsy projektanta Mobile ASP.NET](../sharepoint/media/mwellipsis.gif "elipsy projektanta Mobile ASP.NET")) przycisk, aby wyświetlić  **Powiąż właściwości** okno dialogowe.

12. Wybierz **powiązać nowy element członkowski** kartę, wybrać **utworzyć pole** przycisk opcji, a następnie wybierz **OK** przycisku.

13. W **przybornika**, rozwiń węzeł **przepływu pracy programu SharePoint** węzła, a następnie zlokalizuj **LogToHistoryListActivity** działania.

14. Dodaj to działanie w przepływie pracy, wykonując jedną z następujących czynności:

    - Otwórz menu skrótów dla **LogToHistoryListActivity** działania, wybierz **kopiowania**, otwórz menu skrótów dla siebie **Upuść tutaj działania** obszar w obrębie **IfElseActivity1** w Projektancie przepływu pracy, a następnie wybierz **Wklej**.

    - Przeciągnij **LogToHistoryListActivity** działanie z **przybornika**i upuść go na innych **Upuść tutaj działania** obszar w obrębie **IfElseActivity1** .

## <a name="add-code-to-the-workflow"></a>Dodaj kod do przepływu pracy
 Następnie dodaj kod do przepływu pracy w celu nadania mu funkcji.

#### <a name="to-add-code-to-the-workflow"></a>Aby dodać kod do przepływu pracy

1. Otwórz menu skrótów dla **createTask1** działania w Projektancie przepływu pracy, a następnie wybierz **Wyświetl kod**.

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
    >  W kodzie, Zastąp `somedomain\\someuser` o nazwie domeny i użytkownika, dla której zostanie utworzone zadanie, takie jak "`Office\\JoeSch`". W przypadku badania jest najprostszym korzystać z konta, które tworzysz przy użyciu.

3. Poniżej `MethodInvoking` metody, Dodaj poniższy przykład:

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

4. W Projektancie przepływu pracy wybierz **ifElseBranchActivity1** działania.

5. W **właściwości** okna, wybierz strzałkę listy rozwijanej **warunek** właściwości, a następnie ustaw *warunek kodu* wartość.

6. Rozwiń **warunek** właściwości, wybierając znak plus (![TreeView plus](../sharepoint/media/plus.gif "TreeView plus")) obok niej, a następnie ustaw jego wartość na *checkApprovalNeeded* .

7. W Projektancie przepływu pracy, otwórz menu skrótów dla **logToHistoryListActivity1** działania, a następnie wybierz **Generowanie programów obsługi** można wygenerować pusty metody dla `MethodInvoking` zdarzeń.

8. Zastąp `MethodInvoking` kod następującym kodem:

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

9. Wybierz **F5** klawisz, aby debugować program.

     Kompiluje aplikacji, pakietów go, wdraża ją, aktywuje jej funkcji, jest odtwarzana [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] puli aplikacji, a następnie uruchamia przeglądarkę w lokalizacji określone w **adres Url witryny** właściwości.

## <a name="associating-the-workflow-to-the-documents-list"></a>Skojarzenie przepływu pracy do listy dokumentów
 Następnie Wyświetl formularz skojarzenia przepływu pracy przez skojarzenie przepływu pracy przy użyciu **SharedDocuments** listy w witrynie programu SharePoint.

#### <a name="to-associate-the-workflow"></a>Aby skojarzyć przepływ pracy

1. Wybierz **dokumenty udostępnione** łączy na pasku szybkiego uruchamiania.

2. Wybierz **biblioteki** link **narzędzia biblioteki** kartę, a następnie wybierz **ustawienia biblioteki** przycisk na Wstążce.

3. W **uprawnienia i zarządzanie** wybierz pozycję **ustawienia przepływu pracy** łącze, a następnie wybierz **Dodaj przepływ pracy** link **przepływówpracy** strony.

4. W górnym listy na stronie ustawień przepływu pracy, wybierz **ExpenseReport - Workflow1** szablonu.

5. Wprowadź w polu dalej **ExpenseReportWorkflow** , a następnie wybierz **dalej** przycisku.

     Spowoduje to skojarzenie przepływu pracy przy użyciu **dokumenty udostępnione** listy, a następnie wyświetla formularz skojarzenia przepływu pracy.

6. W **automatycznego zatwierdzenia limitu** tekstu wprowadź **1200** , a następnie wybierz **skojarzenia przepływu pracy** przycisku.

## <a name="start-the-workflow"></a>Uruchom przepływ pracy
 Następnie skojarzenia przepływu pracy do jednego z dokumentów w **dokumenty udostępnione** listy, aby wyświetlić formularz inicjowania przepływu pracy.

#### <a name="to-start-the-workflow"></a>Aby uruchomić przepływ pracy

1. Na stronie programu SharePoint wybierz **Home** przycisku.

2. Wybierz **dokumenty udostępnione** łączy na pasku szybkiego uruchamiania, aby wyświetlić **dokumenty udostępnione** listy.

3. Wybierz **dokumenty** link **narzędzia biblioteki** karcie w górnej części strony, a następnie wybierz **Przekaż dokument** przycisk na Wstążce Aby przekazać nowy dokument do **Dokumenty udostępnione** listy.

4. W **Przekaż dokument** okna dialogowego wybierz **Przeglądaj** przycisku, wybierz dowolny plik dokumentu, wybierz **Otwórz** przycisk, a następnie wybierz **OK** przycisku.

     Możesz zmienić ustawienia dla dokumentu, w tym oknie dialogowym, ale pozostaw ich wartości domyślne, wybierając **Zapisz** przycisku.

5. Wybierz przekazanego dokumentu, wybierz strzałkę listy rozwijanej, która pojawia się, a następnie wybierz **przepływy pracy** elementu.

6. Wybierz obraz obok ExpenseReportWorkflow.

     Spowoduje to wyświetlenie formularza inicjowania przepływu pracy. (Należy pamiętać, że wartość jest wyświetlana w **automatycznego zatwierdzenia limitu** pole jest tylko do odczytu, ponieważ został wprowadzony w postaci skojarzenia.)

7. W **łączny koszt** tekstu wprowadź **1600**, a następnie wybierz **Uruchom przepływ pracy** przycisku.

     Spowoduje to wyświetlenie **dokumenty udostępnione** ponownie listę. Nowa kolumna **ExpenseReportWorkflow** wartością **Ukończono** zostanie dodany do elementu właśnie został uruchomiony przepływ pracy.

8. Wybierz strzałkę listy rozwijanej obok przekazanego dokumentu, a następnie wybierz **przepływy pracy** element, aby wyświetlić na stronie stanu przepływu pracy. Wybierz **Ukończono** wartości w obszarze **ukończone przepływy pracy**. Zadanie jest wyświetlana w obszarze **zadania** sekcji.

9. Wybierz tytuł zadania, aby wyświetlić jego szczegóły zadania.

10. Wróć do **SharedDocuments** listy, a następnie ponownie uruchom przepływ pracy przy użyciu tego samego dokumentu lub inną.

11. Wprowadź kwotę na stronie inicjowania, która jest mniejsza niż ilość wprowadzone na stronie skojarzenia (**1200**).

     W takiej sytuacji, zamiast zadania jest tworzony wpis na liście historii. Wyświetla wpis **historii przepływu pracy** sekcji na stronie stanu przepływu pracy. Należy pamiętać, wiadomości w **wynik** kolumny zdarzenia historii. Zawiera on tekst wprowadzony w `logToHistoryListActivity1.MethodInvoking` zdarzeń, który zawiera kwotę, które zostało zatwierdzone automatycznie.

## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu tworzenia szablonów przepływu pracy w tych tematach:

- Aby dowiedzieć się więcej na temat przepływów pracy programu SharePoint, zobacz [przepływów pracy w programie Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkID=166275).

## <a name="see-also"></a>Zobacz także
- [Tworzenie rozwiązań przepływu pracy SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Przewodnik: Dodawanie strony aplikacji do przepływu pracy](../sharepoint/walkthrough-add-an-application-page-to-a-workflow.md)
