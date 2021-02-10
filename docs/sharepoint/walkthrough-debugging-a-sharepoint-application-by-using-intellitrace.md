---
title: Debuguj aplikację SharePoint przy użyciu IntelliTrace
description: Użyj IntelliTrace, aby łatwiej debugować i naprawiać aplikacje programu SharePoint. Utwórz i Dodaj kod do odbiorcy funkcji. Przetestuj projekt. Zbieraj dane IntelliTrace.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e2ce8bc2c493d59b8a06a64ff69838e828315bf2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952658"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Przewodnik: debugowanie aplikacji SharePoint przy użyciu IntelliTrace

Korzystając z IntelliTrace, można łatwiej debugować rozwiązania programu SharePoint. Tradycyjne debugery dają w bieżącym momencie tylko migawkę rozwiązania. Można jednak użyć IntelliTrace do przeglądania przeszłych zdarzeń, które wystąpiły w rozwiązaniu, oraz kontekstu, w którym się znajdują, i przechodzenie do kodu.

 W tym instruktażu przedstawiono sposób debugowania projektu programu SharePoint 2010 lub SharePoint 2013 w programie Visual Studio przy użyciu Microsoft Monitoring Agent do zbierania danych IntelliTrace z wdrożonych aplikacji. Aby przeanalizować te dane, musisz użyć Visual Studio Enterprise. Ten projekt obejmuje odbiorcę funkcji, który po aktywowaniu funkcji dodaje zadanie do listy zadań i anonsu do listy anonsów. Gdy funkcja zostanie zdezaktywowana, zadanie zostanie oznaczone jako ukończone, a drugi anons zostanie dodany do listy anonsów. Jednak procedura zawiera błąd logiczny, który uniemożliwia poprawne działanie projektu. Korzystając z IntelliTrace, zlokalizuj i Popraw błąd.

 **Dotyczy:** Informacje przedstawione w tym temacie dotyczą rozwiązań SharePoint 2010 i SharePoint 2013, które zostały utworzone w programie Visual Studio.

 W instruktażu przedstawiono następujące zagadnienia:

- [Tworzenie odbiorcy funkcji](#create-a-feature-receiver)

- [Dodawanie kodu do odbiorcy funkcji](#add-code-to-the-feature-receiver)

- [Testowanie projektu](#test-the-project)

- [Zbieranie danych IntelliTrace przy użyciu Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Debuguj i rozwiązuj rozwiązanie SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Tworzenie odbiorcy funkcji

Najpierw należy utworzyć pusty projekt programu SharePoint, który ma odbiorcę funkcji.

1. Utwórz projekt rozwiązania SharePoint 2010 lub SharePoint 2013 i nadaj mu nazwę **IntelliTraceTest**.

     Zostanie wyświetlony **Kreator dostosowania programu SharePoint** , w którym można określić zarówno witrynę programu SharePoint dla projektu, jak i poziom zaufania rozwiązania.

2. Wybierz przycisk opcji **Wdróż jako rozwiązanie farmy** , a następnie wybierz przycisk **Zakończ** .

     IntelliTrace działa tylko na rozwiązaniach farmy.

3. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła **funkcje** , a następnie wybierz polecenie **Dodaj funkcję**.

     Zostanie wyświetlona *Funkcja Feature1.*

4. Otwórz menu skrótów dla Feature1. feature, a następnie wybierz polecenie **Dodaj odbiorcę zdarzeń** , aby dodać moduł kodu do funkcji.

## <a name="add-code-to-the-feature-receiver"></a>Dodawanie kodu do odbiorcy funkcji

Następnie Dodaj kod do dwóch metod w odbiorniku funkcji: `FeatureActivated` i `FeatureDeactivating` . Te metody wyzwalają za każdym razem, gdy funkcja jest aktywowana lub dezaktywowana odpowiednio w programie SharePoint.

1. W górnej części `Feature1EventReceiver` klasy Dodaj następujący kod, który deklaruje zmienne określające witrynę programu SharePoint i podlokację:

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

2. Zastąp metodę `FeatureActivated` poniższym kodem:

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

3. Zastąp metodę `FeatureDeactivating` poniższym kodem:

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

## <a name="test-the-project"></a>Testowanie projektu

Teraz, gdy kod jest dodawany do odbiorcy funkcji, a moduł zbierający dane jest uruchomiony, wdróż i uruchom rozwiązanie SharePoint, aby sprawdzić, czy działa poprawnie.

> [!IMPORTANT]
> W tym przykładzie w obsłudze zdarzeń FeatureDeactivating zostanie zgłoszony błąd. W dalszej części tego przewodnika zlokalizujesz ten błąd przy użyciu pliku. iTrace utworzonego przez moduł zbierający dane.

1. Wdróż rozwiązanie w programie SharePoint, a następnie otwórz witrynę programu SharePoint w przeglądarce.

     Funkcja zostaje automatycznie aktywowana, co powoduje, że jej odbiornik funkcji dodaje anons i zadanie.

2. Wyświetl zawartość list anonsów i zadań.

     Lista anonsów powinna mieć nowy anons o nazwie **aktywowana funkcja: IntelliTraceTest_Feature1**, a lista zadań powinna mieć nowe zadanie o nazwie **Deactivate Feature: IntelliTraceTest_Feature1**. Jeśli brakuje jednego z tych elementów, sprawdź, czy funkcja jest aktywowana. Jeśli nie jest aktywowany, aktywuj go.

3. Dezaktywuj tę funkcję, wykonując następujące czynności:

   1. W menu **Akcje witryny** w programie SharePoint wybierz pozycję **Ustawienia witryny**.

   2. W obszarze **Akcje lokacji** wybierz łącze **Zarządzaj funkcjami lokacji** .

   3. Obok pozycji **IntelliTraceTest Feature1** wybierz przycisk **Dezaktywuj** .

   4. Na stronie ostrzeżenie wybierz link **Dezaktywuj tę funkcję** .

      Procedura obsługi zdarzeń FeatureDeactivating () zgłasza błąd.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Zbieranie danych IntelliTrace przy użyciu Microsoft Monitoring Agent

W przypadku zainstalowania Microsoft Monitoring Agent w systemie, w którym działa program SharePoint, można debugować rozwiązania programu SharePoint przy użyciu danych bardziej szczegółowych niż ogólne informacje, które IntelliTrace zwraca. Agent działa poza programem Visual Studio za pomocą poleceń cmdlet programu PowerShell do przechwytywania informacji debugowania podczas działania rozwiązania programu SharePoint.

> [!NOTE]
> Informacje o konfiguracji w tej sekcji są specyficzne dla tego przykładu. Aby uzyskać więcej informacji o innych opcjach konfiguracji, zobacz [Używanie autonomicznego modułu zbierającego IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md).

1. Na komputerze, na którym działa program SharePoint, [skonfiguruj Microsoft Monitoring Agent i Rozpocznij monitorowanie rozwiązania](../debugger/using-the-intellitrace-stand-alone-collector.md).

2. Dezaktywuj funkcję:

   1. W menu **Akcje witryny** w programie SharePoint wybierz pozycję **Ustawienia witryny**.

   2. W obszarze **Akcje lokacji** wybierz łącze **Zarządzaj funkcjami lokacji** .

   3. Obok pozycji **IntelliTraceTest Feature1** wybierz przycisk **Dezaktywuj** .

   4. Na stronie ostrzeżenie wybierz link **Dezaktywuj tę funkcję** .

      Wystąpił błąd (w tym przypadku z powodu błędu zgłoszonego w obsłudze zdarzeń FeatureDeactivating ()).

3. W oknie programu PowerShell uruchom polecenie [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) , aby utworzyć plik. iTrace, Zatrzymaj monitorowanie i ponownie uruchom rozwiązanie programu SharePoint.

     **Stop-WebApplicationMonitoring***" \<SharePointSite> \\<SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Debuguj i rozwiązuj rozwiązanie SharePoint

Teraz możesz wyświetlić plik dziennika IntelliTrace w programie Visual Studio, aby znaleźć i naprawić błąd w rozwiązaniu programu SharePoint.

1. W folderze \IntelliTraceLogs Otwórz plik iTrace w programie Visual Studio.

     Zostanie wyświetlona strona **podsumowanie IntelliTrace** . Ponieważ błąd nie został obsłużony, identyfikator korelacji programu SharePoint (identyfikator GUID) pojawia się w nieobsługiwanym obszarze wyjątku sekcji **analizy** . Wybierz przycisk **stosu wywołań** , jeśli chcesz wyświetlić stos wywołań, w którym wystąpił błąd.

2. Wybierz przycisk **Debuguj wyjątek** .

     Jeśli zostanie wyświetlony monit, Załaduj pliki symboli. W oknie **IntelliTrace** wyjątek jest wyróżniony jako "zgłoszony: poważny błąd!".

     W oknie IntelliTrace wybierz wyjątek, aby wyświetlić kod, który się nie powiódł.

3. Usuń błąd, otwierając rozwiązanie SharePoint, a następnie dodając komentarz lub usuwając instrukcję **throw** na początku procedury FeatureDeactivating ().

4. Skompiluj ponownie rozwiązanie w programie Visual Studio, a następnie wdróż je ponownie w programie SharePoint.

5. Dezaktywuj tę funkcję, wykonując następujące czynności:

    1. W menu **Akcje witryny** w programie SharePoint wybierz pozycję **Ustawienia witryny**.

    2. W obszarze **Akcje lokacji** wybierz łącze **Zarządzaj funkcjami lokacji** .

    3. Obok pozycji **IntelliTraceTest Feature1** wybierz przycisk **Dezaktywuj** .

    4. Na stronie ostrzeżenie wybierz link **Dezaktywuj tę funkcję** .

6. Otwórz listę zadań i sprawdź, czy wartość **stanu** zadania Deactivate to "ukończone", a jego wartość **całkowita%** to 100%.

     Kod jest teraz uruchamiany prawidłowo.

## <a name="see-also"></a>Zobacz też

- [Weryfikowanie i debugowanie kodu programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Przewodnik: Weryfikowanie kodu programu SharePoint za pomocą testów jednostkowych](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))