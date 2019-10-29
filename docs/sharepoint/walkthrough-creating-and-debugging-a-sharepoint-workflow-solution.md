---
title: Utwórz & Debuguj rozwiązanie przepływu pracy programu SharePoint
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e62226147fc160c6d967115fbd3aaa52dd69995
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985063"
---
# <a name="walkthrough-create-and-debug-a-sharepoint-workflow-solution"></a>Przewodnik: Tworzenie i debugowanie rozwiązania przepływu pracy programu SharePoint
  W tym instruktażu przedstawiono sposób tworzenia podstawowego sekwencyjnego szablonu przepływu pracy. Przepływ pracy sprawdza Właściwość udostępnionej biblioteki dokumentów, aby określić, czy dokument został sprawdzony. Jeśli dokument został zrecenzowany, przepływ pracy zakończy się.

 W instruktażu przedstawiono następujące zagadnienia:

- Tworzenie projektu sekwencyjnego przepływu pracy definicji listy programu SharePoint w [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

- Tworzenie działań przepływu pracy.

- Obsługa zdarzeń działań przepływu pracy.

> [!NOTE]
> Chociaż w tym instruktażu jest stosowany projekt sekwencyjnego przepływu pracy, proces ten jest identyczny dla projektu przepływu pracy automatu Stanów.
>
> Ponadto w poniższych instrukcjach komputer może wyświetlać różne nazwy lub lokalizacje dla niektórych elementów interfejsu użytkownika programu Visual Studio. Te elementy są określane przez numer wersji Visual Studio oraz twoje ustawienia. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- Program Visual Studio.

## <a name="add-properties-to-the-sharepoint-shared-documents-library"></a>Dodawanie właściwości do biblioteki dokumentów udostępnionych programu SharePoint
 Aby śledzić stan przeglądu dokumentów w bibliotece **dokumenty udostępnione** , utworzysz trzy nowe właściwości dokumentów udostępnionych w witrynie programu SharePoint: `Status`, `Assignee`i `Review Comments`. Te właściwości są zdefiniowane w bibliotece **dokumenty udostępnione** .

#### <a name="to-add-properties-to-the-sharepoint-shared-documents-library"></a>Aby dodać właściwości do biblioteki dokumentów udostępnionych programu SharePoint

1. Otwórz witrynę programu SharePoint, taką jak http://\<system Name >/SitePages/Home.aspx, w przeglądarce internetowej.

2. Na pasku szybkiego uruchamiania wybierz pozycję **SharedDocuments**.

3. Wybierz **bibliotekę** na Wstążce **Narzędzia biblioteki** , a następnie wybierz przycisk **Utwórz kolumnę** na Wstążce, aby utworzyć nową kolumnę.

4. Nadaj nazwę kolumnie **status dokumentu**, ustaw jej typ na **wybór (menu wybierz z)** , określ następujące trzy opcje, a następnie wybierz przycisk **OK** :

    - **Wymagana weryfikacja**

    - **Przegląd zakończony**

    - **Żądane zmiany**

5. Utwórz dwie więcej kolumn i nadaj im nazwę osoby **przydzielonej** i **zapoznaj się z komentarzami**. Ustaw typ kolumny osoby zależne jako pojedynczy wiersz tekstu, a kolumna Przejrzyj Komentarze jako wiele wierszy tekstu.

## <a name="enable-documents-to-be-edited-without-requiring-a-check-out"></a>Włącz edytowanie dokumentów bez konieczności wyewidencjonowania
 Łatwiej jest przetestować szablon przepływu pracy, gdy można edytować dokumenty bez konieczności wyewidencjonowywania. W następnej procedurze należy skonfigurować witrynę programu SharePoint, aby ją włączyć.

#### <a name="to-enable-documents-to-be-edited-without-checking-them-out"></a>Aby włączyć edycję dokumentów bez ich wyewidencjonowania

1. Na pasku szybkiego uruchamiania wybierz link **dokumenty udostępnione** .

2. Na Wstążce **Narzędzia biblioteki** wybierz kartę **Biblioteka** , a następnie wybierz przycisk **Ustawienia biblioteki** , aby wyświetlić stronę **Ustawienia biblioteki dokumentów** .

3. W sekcji **Ustawienia ogólne** wybierz łącze **Ustawienia wersji** , aby wyświetlić stronę **Ustawienia przechowywania wersji** .

4. Sprawdź, czy ustawienie **Wymagaj wyewidencjonowania dokumentów, zanim będzie można edytować** , ma wartość **nie**. Jeśli tak nie jest, Zmień wartość na **nie** , a następnie wybierz przycisk **OK** .

5. Zamknij przeglądarkę.

## <a name="create-a-sharepoint-sequential-workflow-project"></a>Utwórz projekt sekwencyjnego przepływu pracy programu SharePoint
 Sekwencyjny przepływ pracy to zestaw kroków, które są wykonywane w kolejności do momentu zakończenia ostatniego działania. W tej procedurze utworzysz sekwencyjny przepływ pracy, który zostanie zastosowany do listy dokumentów udostępnionych. Kreator przepływu pracy umożliwia skojarzenie przepływu pracy z definicją lokacji lub definicją listy i pozwala określić, kiedy zostanie uruchomiony przepływ pracy.

#### <a name="to-create-a-sharepoint-sequential-workflow-project"></a>Aby utworzyć projekt sekwencyjnego przepływu pracy programu SharePoint

1. Rozpocznij [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2. Na pasku menu wybierz kolejno opcje **plik**  > **Nowy**  > **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** .

3. Rozwiń węzeł **SharePoint** w obszarze **Wizualizacja C#**  lub **Visual Basic**, a następnie wybierz węzeł **2010** .

4. W okienku **Szablony** wybierz szablon **projektu programu SharePoint 2010** .

5. W polu **Nazwa** wprowadź **MySharePointWorkflow** , a następnie wybierz przycisk **OK** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

6. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wybierz przycisk opcji **Wdróż jako farmę** , a następnie wybierz przycisk **Zakończ** , aby zaakceptować poziom zaufania i domyślną lokację.

     Ten krok powoduje ustawienie poziomu zaufania dla rozwiązania jako rozwiązania farmy — jedynej dostępnej opcji dla projektów przepływu pracy. Aby uzyskać więcej informacji, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

7. W **Eksplorator rozwiązań**wybierz węzeł projektu, a następnie na pasku menu wybierz **projekt** > **Dodaj nowy element**.

8. W obszarze **Wizualizacja C#**  lub **Visual Basic**rozwiń węzeł **SharePoint** , a następnie wybierz węzeł **2010** .

9. W okienku **Szablony** wybierz szablon **sekwencyjny przepływ pracy (tylko rozwiązanie farmy)** , a następnie wybierz przycisk **Dodaj** .

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

10. Na stronie **Określanie nazwy przepływu pracy na potrzeby debugowania** Zaakceptuj nazwę domyślną (**MySharePointWorkflow-Workflow1**). Zachowaj domyślną wartość typ szablonu przepływu pracy, **przepływ pracy listy**, a następnie wybierz przycisk **dalej** .

11. Czy chcesz, **Aby program Visual Studio automatycznie kojarzy przepływ pracy w sesji debugowania?** wybierz przycisk **dalej** , aby zaakceptować wszystkie ustawienia domyślne.

     Ten krok automatycznie kojarzy przepływ pracy z biblioteką dokumenty udostępnione.

12. Na stronie **Określ warunki uruchamiania przepływu pracy** pozostaw opcje domyślne wybrane w sekcji **jak chcesz uruchomić przepływ pracy?** , a następnie wybierz przycisk **Zakończ** .

     Ta strona umożliwia określenie czasu uruchamiania przepływu pracy. Domyślnie przepływ pracy jest uruchamiany, gdy użytkownik ręcznie uruchamia go w programie SharePoint lub gdy tworzony jest element, do którego jest skojarzony przepływ pracy.

## <a name="create-workflow-activities"></a>Tworzenie działań przepływu pracy
 Przepływy pracy zawierają co najmniej jedną *czynność* , która reprezentuje akcje do wykonania. Za pomocą projektanta przepływów pracy można rozmieścić działania dla przepływu pracy. W ramach tej procedury dodamy dwa działania do przepływu pracy: HandleExternalEventActivity i OnWorkFlowItemChanged. Te działania monitorują stan przeglądu dokumentów na liście **dokumenty udostępnione**

#### <a name="to-create-workflow-activities"></a>Aby utworzyć działania przepływu pracy

1. Przepływ pracy powinien być wyświetlany w Projektancie przepływu pracy. Jeśli tak nie jest, Otwórz **Workflow1.cs** lub **Workflow1. vb** w **Eksplorator rozwiązań**.

2. W Projektancie wybierz działanie **onWorkflowActivated1** .

3. W oknie **Właściwości** wpisz **onWorkflowActivated** obok **wywołanej** właściwości, a następnie wybierz klawisz ENTER.

     Zostanie otwarty Edytor kodu, a metoda obsługi zdarzeń o nazwie onWorkflowActivated zostanie dodana do pliku kodu Workflow1.

4. Przełącz się z powrotem do projektanta przepływów pracy, Otwórz przybornik, a następnie rozwiń węzeł **Windows Workflow v 3.0** .

5. W węźle **Windows Workflow v 3.0** **przybornika**wykonaj jeden z następujących zestawów czynności:

    1. Otwórz menu skrótów dla działania **while** , a następnie wybierz **Kopiuj**. W Projektancie przepływu pracy Otwórz menu skrótów dla wiersza w ramach działania **onWorkflowActivated1** , a następnie wybierz **Wklej**.

    2. Przeciągnij działanie **while** z **przybornika** do projektanta przepływu pracy i Połącz działanie z wierszem w obszarze działania **onWorkflowActivated1** .

6. Wybierz działanie **whileActivity1** .

7. W oknie **Właściwości** Ustaw **warunek** na warunek kodu.

8. Rozwiń Właściwość **warunek** , wprowadź **IsWorkflowPending** obok właściwości **warunek** podrzędny, a następnie wybierz klawisz ENTER.

     Zostanie otwarty Edytor kodu, a do pliku kodu Workflow1 zostanie dodana Metoda o nazwie isWorkflowPending.

9. Przełącz się z powrotem do projektanta przepływów pracy, Otwórz przybornik, a następnie rozwiń węzeł **przepływ pracy programu SharePoint** .

10. W węźle **przepływ pracy programu SharePoint** **przybornika**wykonaj jeden z następujących zestawów czynności:

    - Otwórz menu skrótów dla działania **onWorkflowItemChanged** , a następnie wybierz **Kopiuj**. W Projektancie przepływu pracy Otwórz menu skrótów dla wiersza wewnątrz działania **whileActivity1** , a następnie wybierz **Wklej**.

    - Przeciągnij działanie **onWorkflowItemChanged** z **przybornika** do projektanta przepływu pracy i Połącz działanie z wierszem w działaniu **whileActivity1** .

11. Wybierz działanie **onWorkflowItemChanged1** .

12. W oknie **Właściwości** ustaw właściwości, jak pokazano w poniższej tabeli.

    |Właściwość|Wartość|
    |--------------|-----------|
    |**CorrelationToken**|**workflowToken**|
    |**Wywoływane**|**onWorkflowItemChanged**|

## <a name="handle-activity-events"></a>Obsługa zdarzeń działań
 Na koniec sprawdź stan dokumentu z poszczególnych działań. Jeśli dokument został zrecenzowany, przepływ pracy zostanie zakończony.

#### <a name="to-handle-activity-events"></a>Aby obsłużyć zdarzenia aktywności

1. W *Workflow1.cs* lub *Workflow1. vb*Dodaj następujące pole na początku klasy `Workflow1`. To pole jest używane w działaniu, aby określić, czy przepływ pracy został ukończony.

    ```vb
    Dim workflowPending As Boolean = True
    ```

    ```csharp
    Boolean workflowPending = true;
    ```

2. Dodaj następującą metodę do klasy `Workflow1`. Ta metoda sprawdza wartość właściwości `Document Status` listy dokumentów, aby określić, czy dokument został sprawdzony. Jeśli właściwość `Document Status` jest ustawiona na `Review Complete`, Metoda `checkStatus` ustawia **wartość false** dla pola `workflowPending`, aby wskazać, że przepływ pracy jest gotowy do zakończenia.

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

3. Dodaj następujący kod do `onWorkflowActivated` i `onWorkflowItemChanged` metod, aby wywołać metodę `checkStatus`. Po uruchomieniu przepływu pracy Metoda `onWorkflowActivated` wywołuje metodę `checkStatus`, aby określić, czy dokument został już sprawdzony. Jeśli nie został on zweryfikowany, przepływ pracy będzie kontynuowany. Po zapisaniu dokumentu Metoda `onWorkflowItemChanged` ponownie wywołuje metodę `checkStatus`, aby określić, czy dokument został sprawdzony. Gdy pole `workflowPending` ma **wartość true**, przepływ pracy jest nadal uruchamiany.

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

4. Dodaj następujący kod do metody `isWorkflowPending`, aby sprawdzić stan właściwości `workflowPending`. Za każdym razem, gdy dokument jest zapisywany, działanie **whileActivity1** wywołuje metodę `isWorkflowPending`. Ta metoda sprawdza Właściwość <xref:System.Workflow.Activities.ConditionalEventArgs.Result%2A> obiektu <xref:System.Workflow.Activities.ConditionalEventArgs>, aby określić, czy działanie **whileActivity1** ma być kontynuowane czy zakończone. Jeśli właściwość ma **wartość true**, działanie będzie kontynuowane. W przeciwnym razie działanie zostanie zakończone i zakończy się przepływ pracy.

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

5. Zapisz projekt.

## <a name="test-the-sharepoint-workflow-template"></a>Testowanie szablonu przepływu pracy programu SharePoint
 Po uruchomieniu debugera [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wdraża szablon przepływu pracy na serwerze programu SharePoint i kojarzy przepływ pracy z listą **dokumenty udostępnione** . Aby przetestować przepływ pracy, uruchom wystąpienie przepływu pracy z dokumentu na liście **dokumenty udostępnione** .

#### <a name="to-test-the-sharepoint-workflow-template"></a>Aby przetestować szablon przepływu pracy programu SharePoint

1. W *Workflow1.cs* lub *Workflow1. vb*Ustaw punkt przerwania obok metody **onWorkflowActivated** .

2. Wybierz klawisz **F5** , aby skompilować i uruchomić rozwiązanie.

     Zostanie wyświetlona witryna programu SharePoint.

3. W okienku nawigacji w programie SharePoint wybierz link **dokumenty udostępnione** .

4. Na stronie **dokumenty udostępnione** wybierz link **dokumenty** na karcie **Narzędzia biblioteki** , a następnie wybierz przycisk **Przekaż dokument** .

5. W oknie dialogowym **przekazywanie dokumentu** wybierz przycisk **Przeglądaj** , wybierz dowolny plik dokumentu, wybierz przycisk **Otwórz** , a następnie wybierz przycisk **OK** .

     Spowoduje to przekazanie wybranego dokumentu do listy **dokumenty udostępnione** i uruchomienie przepływu pracy.

6. W [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]upewnij się, że debuger zatrzyma się w punkcie przerwania obok metody `onWorkflowActivated`.

7. Wybierz klawisz **F5** , aby kontynuować wykonywanie.

8. W tym miejscu możesz zmienić ustawienia dla dokumentu, ale pozostawić je na wartości domyślne dla tej pory, wybierając przycisk **Zapisz** .

     Spowoduje to powrót do strony **dokumenty udostępnione** w domyślnej witrynie sieci Web programu SharePoint.

9. Na stronie **dokumenty udostępnione** Sprawdź, czy wartość poniżej kolumny **MySharePointWorkflow-Workflow1** jest ustawiona na **w toku**. Oznacza to, że przepływ pracy jest w toku i że dokument oczekuje na przegląd.

10. Na stronie **dokumenty udostępnione** wybierz dokument, wybierz strzałkę, która zostanie wyświetlona, a następnie wybierz element menu **Edytuj właściwości** .

11. Ustaw **stan dokumentu** na **Zakończono przegląd**, a następnie wybierz przycisk **Zapisz** .

     Spowoduje to powrót do strony **dokumenty udostępnione** w domyślnej witrynie sieci Web programu SharePoint.

12. Na stronie **dokumenty udostępnione** Sprawdź, czy wartość poniżej kolumny **stan dokumentu** jest ustawiona na **Przegląd zakończono**. Odśwież stronę **dokumenty udostępnione** i sprawdź, czy wartość poniżej kolumny **MySharePointWorkflow-Workflow1** jest ustawiona na **ukończone**. Oznacza to, że przepływ pracy został zakończony i dokument został sprawdzony.

## <a name="next-steps"></a>Następne kroki
 Więcej informacji na temat tworzenia szablonów przepływu pracy można znaleźć w następujących tematach:

- Aby dowiedzieć się więcej o działaniach przepływu pracy programu SharePoint, zobacz [działania przepływu pracy dla programu SharePoint Foundation](/previous-versions/office/developer/sharepoint-2010/ms446847(v=office.14)).

- Aby dowiedzieć się więcej na temat Windows Workflow Foundation działań, zobacz [przestrzeń nazw System. Workflow. Activities](/dotnet/api/system.workflow.activities&view=netframework-4.8).

## <a name="see-also"></a>Zobacz także
- [Tworzenie rozwiązań przepływu pracy programu SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md)
- [Projekty programu SharePoint i szablony elementów projektu](../sharepoint/sharepoint-project-and-project-item-templates.md)
- [Kompilowanie i debugowanie rozwiązań SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)
