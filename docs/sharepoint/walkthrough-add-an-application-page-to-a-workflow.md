---
title: 'Przewodnik: Dodawanie strony aplikacji do przepływu pracy | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, adding applications page to workflow
- application page [SharePoint development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: cb0dfa7212cae1dd4e7c62f71f423c0f8fd275d9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53938202"
---
# <a name="walkthrough-add-an-application-page-to-a-workflow"></a>Przewodnik: Dodawanie strony aplikacji do przepływu pracy
  W tym instruktażu pokazano, jak dodać stronę aplikacja wyświetlającą dane pochodzące z przepływu pracy do projektu przepływu pracy. Opiera się na projekt, opisana w temacie [instruktażu: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

 W tym instruktażu pokazano następujące zagadnienia:

- Dodawanie strony aplikacji ASPX do projektu przepływu pracy programu SharePoint.

- Uzyskiwanie danych z projektu przepływu pracy i modyfikowania go.

- Wyświetlanie danych w tabeli na stronie aplikacji.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

-   Obsługiwane edycje [!INCLUDE[TLA#tla_win](../sharepoint/includes/tlasharptla-win-md.md)] i programu SharePoint.

-   Program Visual Studio.

-   Musisz też ukończenia projektu w temacie [instruktażu: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md).

## <a name="ammend-the-workflow-code"></a>Ammend kod przepływu pracy
 Najpierw dodaj wiersz kodu do przepływu pracy, aby ustawić wartość kolumny wynik ilość raportu wydatków. Ta wartość jest używana w dalszej części Obliczanie podsumowania raportu wydatków.

#### <a name="to-set-the-value-of-the-outcome-column-in-the-workflow"></a>Aby ustawić wartość kolumny wynik w przepływie pracy

1.  Ładowanie ukończone projektu z tematu [instruktażu: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md) do [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].

2.  Otwórz kod *Workflow1.cs* lub *Workflow1.vb* (w zależności od języka programowania).

3.  Na koniec `createTask1_MethodInvoking` metody, Dodaj następujący kod:

    ```vb
    createTask1_TaskProperties1.ExtendedProperties("Outcome") =
      workflowProperties.InitiationData
    ```

    ```csharp
    createTask1_TaskProperties1.ExtendedProperties["Outcome"] =
      workflowProperties.InitiationData;
    ```

## <a name="create-an-application-page"></a>Tworzenie strony aplikacji
 Następnie dodaj ASPX formularza do projektu. Ten formularz, będą wyświetlane dane uzyskane z projektu przepływu pracy raportu wydatków. Aby to zrobić, dodasz strony aplikacji. Na stronie aplikacji używa tej samej strony wzorcowej jako innych stron programu SharePoint, co oznacza, że będzie on podobny innych stron w witrynie programu SharePoint.

#### <a name="to-add-an-application-page-to-the-project"></a>Aby dodać strony aplikacji do projektu

1.  Wybierz projekt ExpenseReport, a następnie na pasku menu wybierz **projektu** > **Dodaj nowy element**.

2.  W **szablony** okienku wybierz **strony aplikacji** szablon, użyj domyślnej nazwy dla elementu projektu (**ApplicationPage1.aspx**) i wybierz polecenie **Dodaj** przycisku.

3.  W [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] ApplicationPage1.aspx, Zamień `PlaceHolderMain` sekcję poniższym kodem:

    ```aspx-csharp
    <asp:Content ID="Main" ContentPlaceHolderID="PlaceHolderMain" runat="server">
        <asp:Label ID="Label1" runat="server" Font-Bold="True"
            Text="Expenses that exceeded allotted amount" Font-Size="Medium"></asp:Label>
        <br />
        <asp:Table ID="Table1" runat="server">
        </asp:Table>
    </asp:Content>
    ```

     Ten kod dodaje tabelę do strony razem z tytułu.

4.  Dodaj tytuł na stronie aplikacji, zastępując `PlaceHolderPageTitleInTitleArea` sekcję poniższym kodem:

    ```aspx-csharp
    <asp:Content ID="PageTitleInTitleArea" ContentPlaceHolderID="PlaceHolderPageTitleInTitleArea" runat="server" >
        Expense Report Summary
    </asp:Content>
    ```

## <a name="code-the-application-page"></a>Kodu strony aplikacji
 Następnie dodaj kod, na stronie podsumowania aplikacji raportu wydatków. Po otwarciu strony, kod skanuje listy zadań w programie SharePoint wydatków, które przekroczyły przydzielony limit wydatków. Raport zawiera listę każdego elementu, wraz z sumą kosztów.

#### <a name="to-code-the-application-page"></a>Do kodu strony aplikacji

1.  Wybierz **ApplicationPage1.aspx** węzła, a następnie na pasku menu wybierz **widoku** > **kodu** do wyświetlenia w kodzie strony aplikacji.

2.  Zastąp **przy użyciu** lub **importu** instrukcji (w zależności od języka programowania) w górnej części klasy następującym kodem:

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

3.  Dodaj następujący kod do `Page_Load` metody:

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
    >  Koniecznie Zastąp "element TestServer" w kodzie o nazwie prawidłowy serwer, na którym uruchomiony jest SharePoint.

## <a name="test-the-application-page"></a>Testowanie strony aplikacji
 Następnie należy określić, czy strona aplikacji przedstawia dane wydatków poprawnie.

#### <a name="to-test-the-application-page"></a>Aby przetestować stronę aplikacji

1. Wybierz **F5** klucza do uruchamiania i wdrażania projektu w programie SharePoint.

2. Wybierz **Home** przycisk, a następnie wybierz **dokumenty udostępnione** łączy na pasku szybkiego uruchamiania, aby wyświetlić listę dokumenty udostępnione w witrynie programu SharePoint.

3. Do reprezentowania raporty wydatków w tym przykładzie, Przekaż niektóre nowe dokumenty do listy dokumentów, wybierając **dokumenty** link **LibraryTools** kartę w górnej części strony, a następnie wybierając  **Przekaż dokument** przycisk na wstążce narzędzi.

4. Po przekazaniu niektóre dokumenty wystąpienia przepływu pracy, wybierając **biblioteki** link **LibraryTools** kartę w górnej części strony, a następnie wybierając **ustawienia biblioteki**przycisk na wstążce narzędzi.

5. W **ustawienia biblioteki dokumentów** wybierz **ustawienia przepływu pracy** łącze w **uprawnienia i zarządzanie** sekcji.

6. W **ustawienia przepływu pracy** wybierz **Dodaj przepływ pracy** łącza.

7. W **Dodaj przepływ pracy** wybierz **ExpenseReport - Workflow1** przepływu pracy, wprowadź nazwę przepływu pracy, takich jak **ExpenseTest**, a następnie wybierz polecenie **Dalej** przycisku.

    Zostanie wyświetlony formularz skojarzenia przepływu pracy. Dzięki niemu raportu kwotę limitu wydatków.

8. W formularzu skojarzenia wprowadź **1000** do **automatycznego zatwierdzenia limitu** , a następnie wybierz **skojarzenia przepływu pracy** przycisku.

9. Wybierz **macierzystego** przycisk, aby wrócić do strony głównej programu SharePoint.

10. Wybierz **dokumenty udostępnione** łączy na pasku szybkiego uruchamiania.

11. Wybierz jeden z przekazanych dokumentów, aby wyświetlić strzałkę listy rozwijanej, wybierz go, a następnie wybierz **przepływy pracy** elementu.

12. Wybierz obraz obok ExpenseTest do wyświetlania formularza inicjowania przepływu pracy.

13. W **łączny koszt** polu tekstowym wprowadź wartość, która jest większa niż 1000, a następnie wybierz **Uruchom przepływ pracy** przycisku.

     Gdy zgłaszane wydatków przekroczy kwota wydatków przydzielone, zadanie zostanie dodane do listy zadań. Kolumna o nazwie **ExpenseTest** wartością **Ukończono** jest także dodawane do elementu raportu wydatków na liście dokumentów udostępnionych.

14. Powtórz kroki od 11 13 z innych dokumentów na liście dokumentów udostępnionych. (Dokładna liczba dokumentów nie jest ważna.)

15. Wyświetlenia strony podsumowania aplikacja raport wydatków, otwierając następujący adres URL w przeglądarce sieci Web: **http://**<em>SystemName</em>**/_layouts/ExpenseReport/ApplicationPage1.aspx**.

     Na stronie podsumowania raportu wydatków zawiera listę wszystkich raportów wydatków, które przekroczyło przydzielony ilość, kwotę, które przekroczyły go i sumę dla wszystkich raportów.

## <a name="next-steps"></a>Następne kroki
 Aby uzyskać więcej informacji dotyczących stron aplikacji programu SharePoint, zobacz [tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

 Możesz dowiedzieć się więcej o projektowaniu zawartości strony SharePoint przy użyciu Visual Web Designer w programie Visual Studio w tych tematach:

-   [Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

-   [Tworzenie formantów wielokrotnych dla części sieciowych lub stron aplikacji](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie przepływu pracy z formularzami inicjacji i skojarzenia](../sharepoint/walkthrough-creating-a-workflow-with-association-and-initiation-forms.md)
- [Instrukcje: Tworzenie strony aplikacji](../sharepoint/how-to-create-an-application-page.md)
- [Tworzenie stron aplikacji dla programu SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Opracowywanie rozwiązań SharePoint](../sharepoint/developing-sharepoint-solutions.md)