---
title: 'Przewodnik: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Workflow.WorkflowConditions
- VS.SharePointTools.Workflow.WorkflowList
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, workflows
- workflows [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: bfd1d1e434826a652525fb7e7151ecf0e8e13b75
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53912993"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Przewodnik: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint
  W tym instruktażu pokazano, jak utworzyć szablon podstawowy sekwencyjny przepływ pracy. Właściwość Biblioteka dokumentów udostępnionych w celu ustalenia, czy dokument został przejrzany sprawdza, czy przepływ pracy. Jeśli dokument został przejrzany, przepływ pracy zakończy się.  
  
 W instruktażu przedstawiono następujące zagadnienia:  
  
-   Tworzenie projektu programu SharePoint listy definicji sekwencyjnego przepływu pracy w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
-   Tworzenie działań przepływu pracy.  
  
-   Obsługa zdarzeń działania przepływu pracy.  
  
> [!NOTE]  
>  Chociaż ten przewodnik korzysta z projektem sekwencyjnego przepływu pracy, ten proces jest taka sama dla projektu przepływu pracy stanu komputera.  
>   
>  Ponadto komputer może wyświetlać różne nazwy lub lokalizacje dla niektórych użytkowników programu Visual Studio elementy interfejsu w poniższych instrukcjach. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.  
  
-   Program Visual Studio.  
  
## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Dodaj właściwości do biblioteki udostępnionych dokumentów programu SharePoint
 Aby śledzić stan przeglądu dokumentów w **dokumenty udostępnione** biblioteki, utworzymy trzy nowe właściwości dotyczące udostępnionych dokumentów w naszej witrynie programu SharePoint: `Status`, `Assignee`, i `Review Comments`. Definiujemy tych właściwości w **dokumenty udostępnione** biblioteki.  
  
#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Aby dodać właściwości do programu SharePoint, udostępnionych dokumentów biblioteki  
  
1.  Otwórz witrynę programu SharePoint, takiej jak http://\<Nazwa systemowa > / SitePages/Home.aspx w przeglądarce sieci Web.  
  
2.  Na pasku szybkiego uruchamiania wybierz **SharedDocuments**.  
  
3.  Wybierz **biblioteki** na **narzędzia biblioteki** wstążki, a następnie wybierz **Utwórz kolumnę** przycisk na Wstążce, aby utworzyć nową kolumnę.  
  
4.  Nadaj kolumnie nazwę **stan dokumentu**, Ustaw typ **wyboru (menu do wyboru)** określ następujące trzy opcje, a następnie wybierz **OK** przycisku:  
  
    -   **Potrzebny Przegląd**  
  
    -   **Zakończenie przeglądu**  
  
    -   **Żądanych zmian**  
  
5.  Utwórz dwie kolumny i nazwij je **Assignee** i **komentarzy**. Ustaw typ kolumny Assignee jako pojedynczy wiersz tekstu i komentarzy typ kolumny jako wiele wierszy tekstu.  
  
## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Włączanie dokumentów do edycji bez konieczności wyewidencjonowanie
 Łatwiej można przetestować szablonu przepływu pracy, gdy edytujesz dokumenty bez konieczności ich wyewidencjonowania. W następnej procedurze skonfigurujesz witryny programu SharePoint, aby to umożliwić.  
  
#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Aby włączyć dokumentów do edycji bez wyewidencjonowania ich  
  
1.  Na pasku szybkiego uruchamiania wybierz **dokumenty udostępnione** łącza.  
  
2.  Na **narzędzia biblioteki** Wstążce, wybierz polecenie **biblioteki** kartę, a następnie wybierz **ustawienia biblioteki** przycisk, aby wyświetlić **ustawienia biblioteki dokumentów** strony.  
  
3.  W **ustawienia ogólne** wybierz pozycję **ustawienia przechowywania wersji** łącze, aby wyświetlić **ustawienia przechowywania wersji** strony.  
  
4.  Upewnij się, że ustawienie **wymagają dokumentów, aby zostać wyewidencjonowany zanim można edytować** jest **nie**. Jeśli nie jest, zmień ją na **nie** , a następnie wybierz **OK** przycisku.  
  
5.  Zamknij przeglądarkę.  
  
## <a name="create-a-sharepoint-sequential-workflow-project"></a>Utwórz projekt sekwencyjnego przepływu pracy programu SharePoint
 Sekwencyjny przepływ pracy jest zestaw kroków, który jest wykonywany w kolejności, aż do zakończenia ostatniej aktywności. W tej procedurze utworzymy sekwencyjnego przepływu pracy, które zostaną zastosowane do naszej listy Dokumenty udostępnione. Kreator przepływ pracy umożliwia skojarzenie przepływu pracy przy użyciu definicji witryny lub definicji listy i pozwala określić, gdy rozpocznie się przepływ pracy.  
  
#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Aby utworzyć projekt sekwencyjnego przepływu pracy programu SharePoint  
  
1.  Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
2.  Na pasku menu wybierz **pliku** > **New** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
3.  Rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz **2010** węzła.  
  
4.  W **szablony** okienku wybierz **projekt programu SharePoint 2010** szablonu.  
  
5.  W **nazwa** wprowadź **MySharePointWorkflow** , a następnie wybierz **OK** przycisku.  
  
     **Kreator ustawień niestandardowych SharePoint** pojawia się.  
  
6.  W **Określanie witryny i poziomu zabezpieczeń dla debugowania** wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisk, aby zaakceptować Witryna poziom i domyślne zaufanie.  
  
     W tym kroku ustawia poziom zaufania dla rozwiązania jako rozwiązanie farmy, jedyną dostępną opcją w przypadku projektów przepływu pracy. Aby uzyskać więcej informacji, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  W **Eksploratora rozwiązań**, wybierz węzeł projektu, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.  
  
8.  W obszarze **Visual C#** lub **języka Visual Basic**, rozwiń węzeł **SharePoint** węzła, a następnie wybierz **2010** węzła.  
  
9. W **szablony** okienku wybierz **sekwencyjnego przepływu pracy (tylko rozwiązanie farmy)** szablonu, a następnie wybierz **Dodaj** przycisku.  
  
     **Kreator ustawień niestandardowych SharePoint** pojawia się.  
  
10. W **Określ nazwę przepływu pracy debugowania** strona, zaakceptuj nazwę domyślną (**MySharePointWorkflow - Workflow1**). Należy zachować wartość typu szablonu przepływu pracy domyślnego, **przepływu pracy dla listy**, a następnie wybierz **dalej** przycisku.  
  
11. W **chcesz użyć programu Visual Studio automatycznie skojarzył przepływ pracy w sesji debugowania?** wybierz **dalej** przycisk, aby zaakceptować ustawienia domyślne.  
  
     W tym kroku automatycznie kojarzy przepływu pracy przy użyciu biblioteki Dokumenty udostępnione.  
  
12. W **Określanie warunków dotyczących sposobu uruchamiania przepływu pracy** zostaw domyślne opcje wybrane w **jaki sposób ma zostać uruchomiony przepływ pracy?** sekcji, a następnie wybierz **Zakończ** przycisku.  
  
     Ta strona umożliwia określenie, po rozpoczęciu pracy. Domyślnie, przepływ pracy jest uruchamiany albo po użytkownik ręcznie uruchamia go w programie SharePoint lub po utworzeniu elementu, z którym jest skojarzony przepływ pracy.  
  
## <a name="create-workflow-activities"></a>Tworzenie działań przepływu pracy
 Przepływy pracy zawierają co najmniej jeden *działania* reprezentujące akcje do wykonania. Rozmieść działań przepływu pracy za pomocą projektanta przepływu pracy. W tej procedurze dodamy dwa działania do przepływu pracy: Działanie HandleExternalEventActivity i OnWorkFlowItemChanged. Te działania monitorowania stanu przeglądu dokumentów w **dokumenty udostępnione** listy  
  
#### <a name="to-create-workflow-activities"></a>Do tworzenia działań przepływu pracy  
  
1.  Przepływ pracy powinien być wyświetlany w Projektancie przepływu pracy. Jeśli nie jest dostępne, następnie otwórz okno dialogowe **Workflow1.cs** lub **Workflow1.vb** w **Eksploratora rozwiązań**.  
  
2.  W projektancie, wybierz **OnWorkflowActivated1** działania.  
  
3.  W **właściwości** oknie wprowadź **ramach działania onWorkflowActivated** obok **Invoked** właściwości, a następnie naciśnij klawisz Enter.  
  
     Zostanie otwarty Edytor kodu i metodę programu obsługi zdarzeń o nazwie w ramach działania onWorkflowActivated są dodawane do pliku kodu Workflow1.  
  
4.  Przejdź z powrotem do projektanta przepływów pracy, Otwórz przybornik, a następnie rozwiń **Windows Workflow 3.0** węzła.  
  
5.  W **Windows Workflow 3.0** węźle **przybornika**, wykonaj jedną z następujących zbiorów czynności:  
  
    1.  Otwórz menu skrótów dla **podczas** działania, a następnie wybierz **kopiowania**. W Projektancie przepływu pracy, otwórz menu skrótów dla linii poniżej **onWorkflowActivated1** działania, a następnie wybierz **Wklej**.  
  
    2.  Przeciągnij **podczas** działanie z **przybornika** do projektanta przepływów pracy i połącz działania do wiersza, w obszarze **onWorkflowActivated1** działania.  
  
6.  Wybierz **WhileActivity1** działania.  
  
7.  W **właściwości** oknie **warunek** do kodu stanu.  
  
8.  Rozwiń **warunek** właściwości wprowadź **isWorkflowPending** obok elementu podrzędnego **warunek** właściwości, a następnie naciśnij klawisz Enter.  
  
     Zostanie otwarty Edytor kodu i metodę o nazwie isWorkflowPending są dodawane do pliku kodu Workflow1.  
  
9. Przejdź z powrotem do projektanta przepływów pracy, Otwórz przybornik, a następnie rozwiń **przepływu pracy programu SharePoint** węzła.  
  
10. W **przepływu pracy programu SharePoint** węźle **przybornika**, wykonaj jedną z następujących zbiorów czynności:  
  
    -   Otwórz menu skrótów dla **OnWorkflowItemChanged** działania, a następnie wybierz **kopiowania**. W Projektancie przepływu pracy, otwórz menu skrótów dla wiersza wewnątrz **whileActivity1** działania, a następnie wybierz **Wklej**.  
  
    -   Przeciągnij **OnWorkflowItemChanged** działanie z **przybornika** do projektanta przepływów pracy i połącz działania do wiersza wewnątrz **whileActivity1** działania.  
  
11. Wybierz **onWorkflowItemChanged1** działania.  
  
12. W **właściwości** okna, ustaw właściwości, jak pokazano w poniższej tabeli.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |**CorrelationToken**|**workflowToken**|  
    |**Wywołany**|**onWorkflowItemChanged**|  
  
## <a name="handle-activity-events"></a>Obsługa zdarzeń działania
 Na koniec sprawdź stan dokumentu z każdego działania. Jeśli dokument został przejrzany, przepływu pracy zostało zakończone.  
  
#### <a name="to-handle-activity-events"></a>Do obsługi zdarzeń działania  
  
1.  W *Workflow1.cs* lub *Workflow1.vb*, Dodaj następujące pole na początku `Workflow1` klasy. To pole jest używane w działaniu w celu ustalenia, czy przepływ pracy jest zakończone.  
  
    ```vb  
    Dim workflowPending As Boolean = True  
    ```  
  
    ```csharp  
    Boolean workflowPending = true;  
    ```  
  
2.  Dodaj następującą metodę do `Workflow1` klasy. Ta metoda sprawdza wartość `Document Status` właściwości listy dokumentów, aby ustalić, czy dokument został przejrzany. Jeśli `Document Status` właściwość jest ustawiona na `Review Complete`, a następnie `checkStatus` metody ustawia `workflowPending` pole **false** do wskazania, że przepływ pracy jest gotowy do zakończenia.  
  
    ```vb  
    Private Sub checkStatus()  
        If CStr(workflowProperties.Item("Document Status")) = "Review Complete" Then  
            workflowPending = False  
        End If  
    End Sub   
    ```  
  
    ```csharp  
    private void checkStatus()  
    {  
        if ((string)workflowProperties.Item["Document Status"] == "Review Complete")  
        workflowPending = false;  
    }  
    ```  
  
3.  Dodaj następujący kod do `onWorkflowActivated` i `onWorkflowItemChanged` metod do wywołania `checkStatus` metody. Po uruchomieniu przepływu pracy, `onWorkflowActivated` wywołania metody `checkStatus` metodę pozwala ustalić, czy dokument ma już przejrzane. Jeśli go nie została sprawdzona, przepływ pracy jest kontynuowany. Po zapisaniu dokumentu `onWorkflowItemChanged` wywołania metody `checkStatus` metoda ponownie, aby określić, czy dokument został przejrzany. Gdy `workflowPending` pole jest ustawione na **true**, przepływ pracy będzie nadal działać.  
  
    ```vb  
    Private Sub onWorkflowActivated(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
  
    Private Sub onWorkflowItemChanged(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ExternalDataEventArgs)  
        checkStatus()  
    End Sub  
    ```  
  
    ```csharp  
    private void onWorkflowActivated(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
  
    private void onWorkflowItemChanged(object sender, ExternalDataEventArgs e)  
    {  
        // Check the status.  
        checkStatus();  
    }  
    ```  
  
4.  Dodaj następujący kod do `isWorkflowPending` metodę, aby sprawdzić stan `workflowPending` właściwości. Każdorazowo, dokument zostanie zapisany, **whileActivity1** wywołania działania `isWorkflowPending` metody. Ta metoda sprawdza, czy <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> właściwość <xref:System.Workflow.Activities.ConditionalEventArgs> obiektu, aby określić, czy **WhileActivity1** działania należy kontynuować, lub Zakończ. Jeśli ustawiono właściwość **true**, kontynuuje działanie. W przeciwnym razie kończy działanie i zakończeniu przepływu pracy.  
  
    ```vb  
    Private Sub isWorkflowPending(ByVal sender As System.Object, ByVal e As System.Workflow.Activities.ConditionalEventArgs)  
        e.Result = workflowPending  
    End Sub  
    ```  
  
    ```csharp  
    private void isWorkflowPending(object sender, ConditionalEventArgs e)  
    {  
        e.Result = workflowPending;  
    }  
    ```  
  
5.  Zapisz projekt.  
  
## <a name="test-the-sharepoint-workflow-template"></a>Testowanie szablonu przepływu pracy programu SharePoint
 Podczas uruchamiania debugera, [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wdraża szablonu przepływu pracy na serwerze programu SharePoint i skojarzenie przepływu pracy przy użyciu **dokumenty udostępnione** listy. Aby przetestować przepływ pracy, należy uruchomić wystąpienie przepływu pracy z dokumentu **dokumenty udostępnione** listy.  
  
#### <a name="to-test-the-sharepoint-workflow-template"></a>Aby przetestować szablonu przepływu pracy programu SharePoint  
  
1.  W *Workflow1.cs* lub *Workflow1.vb*, ustaw punkt przerwania obok **ramach działania onWorkflowActivated** metody.  
  
2.  Wybierz **F5** klawisz, aby skompilować i uruchomić rozwiązanie.  
  
     Zostanie wyświetlona witryna programu SharePoint.  
  
3.  W okienku nawigacji w programie SharePoint, wybierz **dokumenty udostępnione** łącza.  
  
4.  W **dokumenty udostępnione** wybierz **dokumenty** link **narzędzia biblioteki** kartę, a następnie wybierz **Przekaż dokument** przycisku .  
  
5.  W **Przekaż dokument** okna dialogowego wybierz **Przeglądaj** przycisku, wybierz dowolny plik dokumentu, wybierz **Otwórz** przycisk, a następnie wybierz **OK** przycisku.  
  
     To przekazanie wybranego dokumentu w **dokumenty udostępnione** listy i uruchamia przepływ pracy.  
  
6.  W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], sprawdź, czy debuger zatrzymuje się w punkcie przerwania obok `onWorkflowActivated` metody.  
  
7.  Wybierz **F5** klawisz, aby kontynuować wykonywanie.  
  
8.  Możesz zmienić ustawienia dla dokumentu, w tym miejscu, ale pozostaw ich wartości domyślne teraz, wybierając **Zapisz** przycisku.  
  
     Nastąpi powrót do **dokumenty udostępnione** stronę domyślnej witryny sieci Web programu SharePoint.  
  
9. W **dokumenty udostępnione** Sprawdź, czy wartość poniżej **MySharePointWorkflow - Workflow1** kolumny ustawiono **w toku**. Oznacza to, że przepływ pracy jest w toku i że dokument oczekuje na Przegląd.  
  
10. W **dokumenty udostępnione** strony, wybierz dokument, wybierz strzałkę, która pojawia się, a następnie wybierz **Edytuj właściwości** elementu menu.  
  
11. Ustaw **stan dokumentu** do **kompletny przegląd**, a następnie wybierz **Zapisz** przycisku.  
  
     Nastąpi powrót do **dokumenty udostępnione** stronę domyślnej witryny sieci Web programu SharePoint.  
  
12. W **dokumenty udostępnione** Sprawdź, czy wartość poniżej **stan dokumentu** kolumny ustawiono **kompletny przegląd**. Odśwież **dokumenty udostępnione** strony i upewnij się, że wartość poniżej **MySharePointWorkflow - Workflow1** kolumny ustawiono **Ukończono**. Oznacza to, że przepływ pracy został zakończony, a dokument został przejrzany.  
  
## <a name="next-steps"></a>Następne kroki
 Możesz dowiedzieć się więcej na temat sposobu tworzenia szablonów przepływu pracy w tych tematach:  
  
-   Aby dowiedzieć się więcej na temat działania przepływu pracy programu SharePoint, zobacz [działań przepływu pracy programu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=178992).  
  
-   Aby dowiedzieć się więcej na temat działania Windows Workflow Foundation, zobacz [Namespace System.Workflow.Activities](http://go.microsoft.com/fwlink/?LinkId=178993).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie rozwiązań przepływu pracy SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)   
 [Projekt SharePoint oraz szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md)   
 [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
