---
title: 'Przewodnik: Dodawanie strony aplikacji do przepływu pracy | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f54914e6676e0cc2400fa04ebb089fac08f58c3c
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015496"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Przewodnik: Dodawanie strony aplikacji do przepływu pracy
  W tym instruktażu przedstawiono sposób dodawania strony aplikacji, która wyświetla dane pochodzące z przepływu pracy do projektu przepływu pracy. Kompiluje się on na projekcie opisanym w [przewodniku tematu: tworzenie przepływu pracy z formularzami skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 W tym instruktażu przedstawiono następujące zadania:

- Dodawanie strony aplikacji ASPX do projektu przepływu pracy programu SharePoint.

- Uzyskiwanie danych z projektu przepływu pracy i manipulowanie nim.

- Wyświetlanie danych w tabeli na stronie aplikacji.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje programów [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i SharePoint.

- Program Visual Studio.

- Należy również ukończyć projekt w [przewodniku tematu: tworzenie przepływu pracy przy użyciu formularzy skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="ammend-the-workflow-code"></a>Ammend kod przepływu pracy
 Najpierw Dodaj wiersz kodu do przepływu pracy, aby ustawić wartość kolumny wynik na ilość raportu wydatków. Ta wartość jest używana później w obliczeniach podsumowania raportów wydatków.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Aby ustawić wartość kolumny wynik w przepływie pracy

1. Załaduj ukończony projekt z [przewodnika: tworzenie przepływu pracy z formularzami skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

2. Otwórz kod dla *Workflow1.cs* lub *Workflow1. vb* (w zależności od języka programowania).

3. Na dole `createTask1_MethodInvoking` metody Dodaj następujący kod:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Tworzenie strony aplikacji
 Następnie dodaj formularz ASPX do projektu. Ten formularz będzie wyświetlał dane uzyskane z projektu przepływu pracy raportu wydatków. W tym celu dodasz stronę aplikacji. Strona aplikacji używa tej samej strony wzorcowej co inne strony programu SharePoint, co oznacza, że będzie wyglądać podobnie do innych stron w witrynie programu SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Aby dodać stronę aplikacji do projektu

1. Wybierz projekt ExpenseReport, a następnie na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

2. W okienku **Szablony** wybierz szablon **Strona aplikacji** , Użyj domyślnej nazwy dla elementu projektu (**ApplicationPage1. aspx**), a następnie wybierz przycisk **Dodaj** .

3. W programie [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1. aspx Zastąp `PlaceHolderMain` sekcję następującymi tematami:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Ten kod dodaje tabelę do strony wraz z tytułem.

4. Dodaj tytuł do strony aplikacji, zastępując `PlaceHolderPageTitleInTitleArea` sekcję następującym:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Kod strony aplikacji
 Następnie Dodaj kod do strony podsumowania raportów o wydatkach. Po otwarciu strony kod skanuje listę zadań w programie SharePoint pod kątem wydatków, które przekroczyły przydzieloną wartość limitu wydatków. Raport zawiera listę wszystkich elementów wraz z sumą wydatków.

#### <a name="to-code-the-application-page"></a>Aby zakodować stronę aplikacji

1. Wybierz węzeł **ApplicationPage1. aspx** , a następnie na pasku menu wybierz polecenie **Wyświetl**  >  **kod** , aby wyświetlić kod związany ze stroną aplikacji.

2. Zastąp instrukcje **using** lub **Import** (w zależności od języka programowania) w górnej części klasy następującym:

    ```vb
    Imports System
    Imports Microsoft.SharePoint
    Imports Microsoft.SharePoint.WebControls
    Imports System.Collections
    Imports System.Data
    Imports System.Web.UI
    Imports System.Web.UI.WebControls
    Imports System.Web.UI.WebControls.WebParts
    Imports System.Drawing
    Imports Microsoft.SharePoint.Navigation
    ```

    ```csharp
    using System;
    using Microsoft.SharePoint;
    using Microsoft.SharePoint.WebControls;
    using System.Collections;
    using System.Data;
    using System.Web.UI;
    using System.Web.UI.WebControls;
    using System.Web.UI.WebControls.WebParts;
    using System.Drawing;
    using Microsoft.SharePoint.Navigation;
    ```

3. Dodaj następujący kod do metody `Page_Load`:

    ```vb
    Try
        ' Reference the Tasks list on the SharePoint site.
        ' Replace "TestServer" with a valid SharePoint server name.
        Dim site As SPSite = New SPSite("http://TestServer")
        Dim list As SPList = site.AllWebs(0).Lists("Tasks")
        ' string text = "";
        Dim sum As Integer = 0
        Table1.Rows.Clear()
        ' Add table headers.
        Dim hr As TableHeaderRow = New TableHeaderRow
        hr.BackColor = Color.LightBlue
        Dim hc1 As TableHeaderCell = New TableHeaderCell
        Dim hc2 As TableHeaderCell = New TableHeaderCell
        hc1.Text = "Expense Report Name"
        hc2.Text = "Amount Exceeded"
        hr.Cells.Add(hc1)
        hr.Cells.Add(hc2)
        ' Add the TableHeaderRow as the first item
        ' in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr)
        ' Iterate through the tasks in the Task list and collect those
        ' that have values in the "Related Content" and "Outcome" fields
        ' - the fields written to when expense approval is required.
        For Each item As SPListItem In list.Items
            Dim s_relContent As String = ""
            Dim s_outcome As String = ""
            Try
                ' Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related Content")
                s_outcome = item.GetFormattedValue("Outcome")
            Catch erx As System.Exception
                ' Task does not have fields - skip it.
                Continue For
            End Try
            ' Convert amount to an int and keep a running total.
            If (Not String.IsNullOrEmpty(s_relContent) And Not
              String.IsNullOrEmpty(s_outcome)) Then
                sum = (sum + Convert.ToInt32(s_outcome))
                Dim relContent As TableCell = New TableCell
                relContent.Text = s_relContent
                Dim outcome As TableCell = New TableCell
                outcome.Text = ("$" + s_outcome)
                Dim dataRow2 As TableRow = New TableRow
                dataRow2.Cells.Add(relContent)
                dataRow2.Cells.Add(outcome)
                Table1.Rows.Add(dataRow2)
            End If
        Next
        ' Report the sum of the reports in the table footer.
        Dim tfr As TableFooterRow = New TableFooterRow
        tfr.BackColor = Color.LightGreen
        ' Create a TableCell object to contain the
        ' text for the footer.
        Dim ftc1 As TableCell = New TableCell
        Dim ftc2 As TableCell = New TableCell
        ftc1.Text = "TOTAL: "
        ftc2.Text = ("$" + Convert.ToString(sum))
        ' Add the TableCell object to the Cells
        ' collection of the TableFooterRow.
        tfr.Cells.Add(ftc1)
        tfr.Cells.Add(ftc2)
        ' Add the TableFooterRow to the Rows
        ' collection of the table.
        Table1.Rows.Add(tfr)
    Catch errx As Exception
        System.Diagnostics.Debug.WriteLine(("Error: " + errx.ToString))
    End Try
    ```

    ```csharp
    try
    {
        // Reference the Tasks list on the SharePoint site.
        // Replace "TestServer" with a valid SharePoint server name.
        SPSite site = new SPSite("http://TestServer");
        SPList list = site.AllWebs[0].Lists["Tasks"];

        // string text = "";
        int sum = 0;

        Table1.Rows.Clear();

        // Add table headers.
        TableHeaderRow hr = new TableHeaderRow();
        hr.BackColor = Color.LightBlue;
        TableHeaderCell hc1 = new TableHeaderCell();
        TableHeaderCell hc2 = new TableHeaderCell();
        hc1.Text = "Expense Report Name";
        hc2.Text = "Amount Exceeded";
        hr.Cells.Add(hc1);
        hr.Cells.Add(hc2);
        // Add the TableHeaderRow as the first item
        // in the Rows collection of the table.
        Table1.Rows.AddAt(0, hr);

        // Iterate through the tasks in the Task list and collect those
        // that have values in the "Related Content" and "Outcome"
        // fields - the fields written to when expense approval is
        // required.
        foreach (SPListItem item in list.Items)
        {
            string s_relContent = "";
            string s_outcome = "";

            try
            {
                // Task has the fields - treat as expense report.
                s_relContent = item.GetFormattedValue("Related
                  Content");
                s_outcome = item.GetFormattedValue("Outcome");
            }
            catch
            {
                // Task does not have fields - skip it.
                continue;
            }

            if (!String.IsNullOrEmpty(s_relContent) &&
              !String.IsNullOrEmpty(s_outcome))
            {
                // Convert amount to an int and keep a running total.
                sum += Convert.ToInt32(s_outcome);
                TableCell relContent = new TableCell();
                relContent.Text = s_relContent;
                TableCell outcome = new TableCell();
                outcome.Text = "$" + s_outcome;
                TableRow dataRow2 = new TableRow();
                dataRow2.Cells.Add(relContent);
                dataRow2.Cells.Add(outcome);
                Table1.Rows.Add(dataRow2);
            }
        }

        // Report the sum of the reports in the table footer.
           TableFooterRow tfr = new TableFooterRow();
        tfr.BackColor = Color.LightGreen;

        // Create a TableCell object to contain the
        // text for the footer.
        TableCell ftc1 = new TableCell();
        TableCell ftc2 = new TableCell();
        ftc1.Text = "TOTAL: ";
        ftc2.Text = "$" + Convert.ToString(sum);

        // Add the TableCell object to the Cells
        // collection of the TableFooterRow.
        tfr.Cells.Add(ftc1);
        tfr.Cells.Add(ftc2);

        // Add the TableFooterRow to the Rows
        // collection of the table.
        Table1.Rows.Add(tfr);
    }

    catch (Exception errx)
    {
        System.Diagnostics.Debug.WriteLine("Error: " + errx.ToString());
    }
    ```

    > [!WARNING]
    > Pamiętaj, aby zamienić ciąg "TestServer" w kodzie na nazwę prawidłowego serwera, na którym działa program SharePoint.

## <a name="test-the-application-page"></a>Testowanie strony aplikacji
 Następnie ustal, czy na stronie aplikacji są wyświetlane dane wydatków prawidłowo.

#### <a name="to-test-the-application-page"></a>Aby przetestować stronę aplikacji

1. Wybierz klawisz **F5** , aby uruchomić i wdrożyć projekt w programie SharePoint.

2. Wybierz przycisk **Strona główna** , a następnie wybierz link **dokumenty udostępnione** na pasku szybkiego startu, aby wyświetlić listę dokumenty udostępnione w witrynie programu SharePoint.

3. Aby przedstawić raporty wydatków na potrzeby tego przykładu, Przekaż kilka nowych dokumentów do listy dokumenty, wybierając link **dokumenty** na karcie **LibraryTools** w górnej części strony, a następnie wybierając przycisk **Przekaż dokument** na Wstążce narzędzi.

4. Po przekazaniu niektórych dokumentów Utwórz wystąpienie przepływu pracy, wybierając link **biblioteki** na karcie **LibraryTools** w górnej części strony, a następnie wybierając przycisk **Ustawienia biblioteki** na Wstążce narzędzi.

5. Na stronie **Ustawienia biblioteki dokumentów** wybierz łącze **Ustawienia przepływu pracy** w sekcji **uprawnienia i zarządzanie** .

6. Na stronie **Ustawienia przepływu pracy** wybierz łącze **Dodaj przepływ pracy** .

7. Na stronie **Dodawanie przepływu pracy** wybierz przepływ pracy **ExpenseReport-Workflow1** , wprowadź nazwę przepływu pracy, na przykład **ExpenseTest**, a następnie wybierz przycisk **dalej** .

    Zostanie wyświetlony formularz skojarzenia przepływu pracy. Służy do raportowania kwoty limitu wydatków.

8. W formularzu skojarzenia wprowadź **1000** w polu **Limit autozatwierdzania** , a następnie wybierz przycisk **Skojarz przepływ pracy** .

9. Wybierz przycisk **Strona główna** , aby powrócić do strony głównej programu SharePoint.

10. Na pasku szybkiego uruchamiania wybierz link **dokumenty udostępnione** .

11. Wybierz jeden z przekazanych dokumentów, aby wyświetlić strzałkę listy rozwijanej, wybierz ją, a następnie wybierz element **przepływy pracy** .

12. Wybierz obraz obok ExpenseTest, aby wyświetlić formularz inicjowania przepływu pracy.

13. W polu tekstowym **Łączny koszt** wprowadź wartość większą niż 1000, a następnie wybierz przycisk **Uruchom przepływ pracy** .

     Gdy raportowane wydatki przekraczają przydzieloną kwotę wydatków, zadanie jest dodawane do Lista zadań. Kolumna o nazwie **ExpenseTest** z **ukończoną** wartością jest również dodawana do elementu raportu wydatków na liście dokumenty udostępnione.

14. Powtórz kroki 11-13 z innymi dokumentami na liście dokumenty udostępnione. (Dokładna liczba dokumentów nie jest ważna).

15. Wyświetl stronę podsumowania raportu wydatków, otwierając następujący adres URL w przeglądarce sieci Web: **http://**<em>systemname</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Na stronie Podsumowanie raportu wydatków są wyświetlane wszystkie raporty wydatków, które przekroczyły przydzieloną kwotę, ilość przekroczeń przez program oraz łączna kwota wszystkich raportów.

## <a name="next-steps"></a>Następne kroki
 Aby uzyskać więcej informacji o stronach aplikacji programu SharePoint, zobacz [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Aby dowiedzieć się więcej na temat projektowania zawartości strony programu SharePoint, można użyć Visual Web Designer w programie Visual Studio z następujących tematów:

- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

- [Tworzenie kontrolek wielokrotnego użytku dla części sieci Web lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: tworzenie przepływu pracy z formularzami skojarzenia i inicjowania](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Instrukcje: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)