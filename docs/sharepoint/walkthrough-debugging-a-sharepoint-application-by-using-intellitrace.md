---
title: 'Przewodnik: Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ad0d12560b1da99beadf2e519d2e430e8d76a45f
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875374"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Przewodnik: Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace

Za pomocą funkcji IntelliTrace, można łatwiej debugować rozwiązania programu SharePoint. Tradycyjne debugery zapewniają tylko migawki rozwiązania w danym momencie. Jednak można użyć IntelliTrace Aby przejrzeć przeszłych zdarzeń, które wystąpiły w swoim rozwiązaniu i kontekst, w którym wystąpił i przejść do kodu.

 W tym przewodniku pokazano, jak debugowanie projektu programu SharePoint 2010 lub SharePoint 2013 w programie Visual Studio przy użyciu programu Microsoft Monitoring Agent do gromadzenia danych IntelliTrace z wdrożonych aplikacji. Aby analizować te dane, należy użyć programu Visual Studio Enterprise. Ten projekt zawiera odbiorcę funkcji, gdy funkcja jest aktywowana, dodaje zadanie do listy zadań i powiadomienia na liście anonsów. Gdy ta funkcja jest aktywna, zadanie jest oznaczone jako ukończone, a drugi ogłoszenie zostanie dodany do listy anonsów. Jednak procedura zawiera logiczny błąd, który uniemożliwia poprawne działanie projektu. Za pomocą funkcji IntelliTrace, możesz znaleźć i popraw błąd.

 **Dotyczy:** Informacje przedstawione w tym temacie mają zastosowanie do rozwiązania programu SharePoint 2010 i SharePoint 2013, które zostały utworzone w programie Visual Studio.

 W instruktażu przedstawiono następujące zagadnienia:

- [Utwórz odbiorcę funkcji](#BKMK_CreateReceiver)

- [Dodaj kod do odbiorcy funkcji](#BKMK_AddCode)

- [Projekt testowy](#BKMK_Test1)

- [Zbieranie danych IntelliTrace za pomocą programu Microsoft Monitoring Agent](#BKMK_CollectDiagnosticData)

- [Debugowanie i naprawa rozwiązania SharePoint](#BKMK_DebugSolution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Utwórz odbiorcę funkcji

Najpierw należy utworzyć pusty projekt programu SharePoint, która ma odbiorcy funkcji.

1. Utwórz projekt rozwiązania programu SharePoint 2010 lub SharePoint 2013 i nadaj mu nazwę **IntelliTraceTest**.

     **Kreator ustawień niestandardowych SharePoint** pojawi się, w którym można określić witrynę programu SharePoint dla projektu i poziomu zaufania rozwiązania.

2. Wybierz **Wdróż jako rozwiązanie farmy** przycisk opcji, a następnie wybierz **Zakończ** przycisku.

     IntelliTrace działa tylko w rozwiązaniach farmy.

3. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **funkcji** węzła, a następnie wybierz **Dodaj funkcję**.

     *Feature1.Feature* pojawia się.

4. Otwórz menu skrótów dla Feature1.feature, a następnie wybierz **Dodaj odbiorcę zdarzeń** można dodać modułu kodu funkcji.

## <a name="add-code-to-the-feature-receiver"></a>Dodaj kod do odbiorcy funkcji

Następnie dodaj kod, aby dwie metody w odbiorcy funkcji: `FeatureActivated` i `FeatureDeactivating`. Te metody wyzwalanie zawsze wtedy, gdy funkcja jest aktywowane lub dezaktywowane w programie SharePoint, odpowiednio.

1. W górnej części `Feature1EventReceiver` klasy, Dodaj następujący kod, który deklaruje zmienne, które określają podwitryny i witryny programu SharePoint:

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. Zastąp `FeatureActivated` metoda następującym kodem:

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. Zastąp `FeatureDeactivating` metoda następującym kodem:

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>Projekt testowy

Teraz, gdy kod jest dodawany do odbiorcy funkcji i modułów zbierających dane jest uruchomiona, wdrażanie i uruchamianie rozwiązania programu SharePoint, aby sprawdzić, czy działa on prawidłowo.

> [!IMPORTANT]
> W tym przykładzie FeatureDeactivating programu obsługi zdarzeń, jest zgłaszany błąd. W dalszej części tego przewodnika możesz znaleźć tego błędu przy użyciu pliku .iTrace, który utworzył modułów zbierających dane.

1. Wdrażanie rozwiązania do programu SharePoint, a następnie otwórz witrynę programu SharePoint w przeglądarce.

     Ta funkcja automatycznie aktywuje, co powoduje jego odbiorcy funkcji dodać zawiadomienia i zadania.

2. Wyświetl zawartość list anonsów i zadania.

     Lista anonsów powinny mieć nowy anons, który nosi nazwę **aktywowano funkcji: IntelliTraceTest_Feature1**, i na liście zadania powinny mieć nowe zadanie, który nosi nazwę **Dezaktywuj funkcji: IntelliTraceTest_Feature1**. Jeśli brakuje jednej z tych elementów, sprawdź, czy funkcja jest aktywowana. Jeśli go nie została aktywowana, aktywuj go.

3. Dezaktywuj tę funkcję, wykonując następujące czynności:

   1. Na **Akcje witryny** menu w programie SharePoint, wybierz opcję **ustawienia lokacji**.

   2. W obszarze **Akcje witryny**, wybierz **Zarządzanie funkcjami witryny** łącza.

   3. Obok pozycji **IntelliTraceTest Feature1**, wybierz **Dezaktywuj** przycisku.

   4. Na stronie Ostrzeżenie Wybierz **Dezaktywuj tę funkcję** łącza.

      Program obsługi zdarzeń FeatureDeactivating() zgłasza błąd.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Zbieranie danych IntelliTrace za pomocą programu Microsoft Monitoring Agent

Jeśli zainstalujesz program Microsoft Monitoring Agent w systemie, na którym uruchomiony jest SharePoint można debugować rozwiązania programu SharePoint przy użyciu danych, które są bardziej szczegółowe niż ogólne informacje, które zwraca IntelliTrace. Agent działa poza programem Visual Studio przy użyciu poleceń cmdlet programu PowerShell do przechwytywania informacji debugowania podczas przebiegów rozwiązania programu SharePoint.

> [!NOTE]
> Informacje o konfiguracji w tej sekcji są specyficzne dla tego przykładu. Aby uzyskać więcej informacji na temat innych opcji konfiguracji, zobacz [przy użyciu autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. Na komputerze, na którym działa program SharePoint [skonfigurować program Microsoft Monitoring Agent i rozpocząć monitorowanie rozwiązania](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Dezaktywowanie funkcji:

   1. Na **Akcje witryny** menu w programie SharePoint, wybierz opcję **ustawienia lokacji**.

   2. W obszarze **Akcje witryny**, wybierz **Zarządzanie funkcjami witryny** łącza.

   3. Obok pozycji **IntelliTraceTest Feature1**, wybierz **Dezaktywuj** przycisku.

   4. Na stronie Ostrzeżenie Wybierz **Dezaktywuj tę funkcję** łącza.

      (W tym przypadku ze względu na zgłoszony błąd w obsłudze zdarzeń FeatureDeactivating()), wystąpi błąd.

3. W oknie programu PowerShell, uruchom [Stop-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) polecenie, aby utworzyć plik .iTrace, Zatrzymaj monitorowanie i ponownie uruchom swoje rozwiązanie programu SharePoint.

     **Stop-WebApplicationMonitoring**  *"\<SharePointSite>\\<SharePointAppName\>"*

## <a name="debug-and-fix-the-sharepoint-solution"></a>Debugowanie i naprawa rozwiązania SharePoint

Teraz możesz wyświetlać plikiem dziennika funkcji IntelliTrace w programie Visual Studio, aby znaleźć i naprawić ten błąd w rozwiązaniu programu SharePoint.

1. W folderze \IntelliTraceLogs Otwórz plik .iTrace w Visual Studio.

     **Krótki opis IntelliTrace** zostanie wyświetlona strona. Ponieważ błąd nie został obsłużony, identyfikator korelacji programu SharePoint (GUID) jest wyświetlana w obszarze nieobsługiwany wyjątek **analizy** sekcji. Wybierz **stos wywołań** przycisk, jeśli chcesz wyświetlić stos wywołań, w którym wystąpił błąd.

2. Wybierz **wyjątek debugowania** przycisku.

     Jeśli zostanie wyświetlony monit, ładować pliki symboli. W **IntelliTrace** okna, wyjątek jest wyróżniony jako "zgłoszenia: Wystąpił poważny błąd! ".

     W oknie IntelliTrace wybierz wyjątek, aby wyświetlić kod, który uległ awarii.

3. Napraw błąd, otwieranie rozwiązania programu SharePoint, a następnie zakomentowując lub usuwanie **throw** instrukcji w górnej części procedura FeatureDeactivating().

4. Ponownie skompiluj rozwiązanie w programie Visual Studio, a następnie wdrożysz go ponownie w programie SharePoint.

5. Dezaktywuj tę funkcję, wykonując następujące czynności:

    1. Na **Akcje witryny** menu w programie SharePoint, wybierz opcję **ustawienia lokacji**.

    2. W obszarze **Akcje witryny**, wybierz **Zarządzanie funkcjami witryny** łącza.

    3. Obok pozycji **IntelliTraceTest Feature1**, wybierz **Dezaktywuj** przycisku.

    4. Na stronie Ostrzeżenie Wybierz **Dezaktywuj tę funkcję** łącza.

6. Otwórz listę zadań i sprawdź, czy **stan** wartość zadania Dezaktywuj jest "ukończone" i jego **% Complete** wartość 100%.

     Kod teraz działa prawidłowo.

## <a name="see-also"></a>Zobacz także

- [Sprawdź i możliwe jest debugowanie kodu programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Przewodnik: Sprawdź kod programu SharePoint przy użyciu testów jednostkowych](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))