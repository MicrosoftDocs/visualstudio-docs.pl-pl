---
title: Debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace
description: Używaj funkcji IntelliTrace, aby łatwiej debugować i naprawiać aplikacje SharePoint. Tworzenie i dodawanie kodu do odbiornika funkcji. Przetestuj projekt. Zbieranie danych funkcji IntelliTrace.
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
ms.openlocfilehash: cf7fa6c7255e05c465d6c209db5e9581a49aee64
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112835"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>Przewodnik: debugowanie aplikacji SharePoint przy użyciu funkcji IntelliTrace

Za pomocą funkcji IntelliTrace można łatwiej debugować rozwiązania programu SharePoint. W tej chwili tradycyjne debugery zapewniają tylko migawkę rozwiązania. Można jednak użyć funkcji IntelliTrace, aby przejrzeć wcześniejsze zdarzenia, które wystąpiły w rozwiązaniu, oraz kontekst, w którym wystąpiły, i przejść do kodu.

 W tym przewodniku pokazano, jak debugować projekt programu SharePoint w programie Visual Studio przy użyciu Microsoft Monitoring Agent do zbierania danych IntelliTrace z wdrożonych aplikacji. Aby analizować te dane, należy użyć Visual Studio Enterprise. Ten projekt zawiera odbiornik funkcji, który po aktywowaniu funkcji dodaje zadanie do listy Zadań i anons do listy Anonse. Po dezaktywacji funkcji zadanie jest oznaczane jako ukończone, a drugie zawiadomienie jest dodawane do listy Anonse. Jednak procedura zawiera błąd logiczny, który uniemożliwia poprawne uruchomienie projektu. Za pomocą funkcji IntelliTrace zlokalizujesz i poprawisz błąd.

 **Dotyczy:** Informacje zawarte w tym temacie dotyczą rozwiązań programu SharePoint utworzonych w programie Visual Studio.

 W instruktażu przedstawiono następujące zagadnienia:

- [Tworzenie odbiornika funkcji](#create-a-feature-receiver)

- [Dodawanie kodu do odbiornika funkcji](#add-code-to-the-feature-receiver)

- [Testowanie projektu](#test-the-project)

- [Zbieranie danych IntelliTrace przy użyciu Microsoft Monitoring Agent](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [Debugowanie i naprawianie rozwiązania SharePoint](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne

Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Windows i programu SharePoint.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>Tworzenie odbiornika funkcji

Najpierw należy utworzyć pusty projekt programu SharePoint z odbiornikiem funkcji.

1. Utwórz projekt rozwiązania programu SharePoint przeznaczony dla zainstalowanej wersji programu SharePoint i nadaj jej nazwę **IntelliTraceTest.**

     Zostanie wyświetlony Kreator dostosowywania programu **SharePoint,** w którym można określić zarówno witrynę programu SharePoint dla projektu, jak i poziom zaufania rozwiązania.

2. Wybierz przycisk **Wdeń jako rozwiązanie farmy,** a następnie wybierz **przycisk** Zakończ.

     IntelliTrace działa tylko na rozwiązaniach farmy.

3. W **Eksplorator rozwiązań** otwórz menu skrótów dla węzła **Funkcje,** a następnie wybierz pozycję **Dodaj funkcję.**

     *Zostanie wyświetlona funkcja Feature1.feature.*

4. Otwórz menu skrótów feature1.feature, a następnie wybierz pozycję **Dodaj** odbiornik zdarzeń, aby dodać moduł kodu do funkcji.

## <a name="add-code-to-the-feature-receiver"></a>Dodawanie kodu do odbiornika funkcji

Następnie dodaj kod do dwóch metod w odbiorniku funkcji: `FeatureActivated` i `FeatureDeactivating` . Te metody są wyzwalane za każdym razem, gdy funkcja zostanie aktywowana lub zdezaktywowana odpowiednio w programie SharePoint.

1. Na początku klasy dodaj następujący kod, który deklaruje zmienne określające witrynę programu `Feature1EventReceiver` SharePoint i lokację podrzędną:

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

Teraz, gdy kod został dodany do odbiornika funkcji i moduł zbierający dane jest uruchomiony, wd wdrażaj i uruchamiaj rozwiązanie programu SharePoint, aby sprawdzić, czy działa prawidłowo.

> [!IMPORTANT]
> W tym przykładzie w obsłudze zdarzeń FeatureDeactivating jest zgłaszany błąd. W dalszej części tego przewodnika znajdziesz ten błąd przy użyciu pliku iTrace utworzonego przez moduł zbierający dane.

1. Wd wdrażaj rozwiązanie w programie SharePoint, a następnie otwórz witrynę programu SharePoint w przeglądarce.

     Funkcja jest automatycznie aktywowana, co powoduje, że jej odbiornik funkcji dodaje anons i zadanie.

2. Wyświetl zawartość list Anonse i Zadania.

     Lista Anonse powinna mieć nową anons o nazwie Aktywowana **funkcja: IntelliTraceTest_Feature1, a** lista Zadania powinna mieć nowe zadanie o nazwie Dezaktywuj **funkcję: IntelliTraceTest_Feature1**. Jeśli brakuje jednego z tych elementów, sprawdź, czy funkcja została aktywowana. Jeśli nie jest on aktywowany, aktywuj go.

3. Dezaktywuj funkcję, wykonując następujące kroki:

   1. W menu **Akcje witryny w** programie SharePoint wybierz pozycję Ustawienia **witryny.**

   2. W **obszarze Akcje lokacji** wybierz link **Zarządzaj funkcjami lokacji.**

   3. Obok opcji **IntelliTraceTest Feature1** wybierz przycisk **Dezaktywuj.**

   4. Na stronie Ostrzeżenie wybierz link **Dezaktywuj tę** funkcję.

      Procedura obsługi zdarzeń FeatureDeactivating() zgłasza błąd.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Zbieranie danych funkcji IntelliTrace przy użyciu Microsoft Monitoring Agent

Jeśli zainstalujesz Microsoft Monitoring Agent systemie z uruchomionym programem SharePoint, możesz debugować rozwiązania programu SharePoint przy użyciu danych bardziej szczegółowych niż ogólne informacje zwracane przez intelliTrace. Agent działa poza programem Visual Studio polecenia cmdlet programu PowerShell w celu przechwytywania informacji debugowania podczas działania rozwiązania SharePoint.

> [!NOTE]
> Informacje o konfiguracji w tej sekcji są specyficzne dla tego przykładu. Aby uzyskać więcej informacji na temat innych opcji konfiguracji, zobacz [Using the IntelliTrace stand-alone collector (Używanie autonomicznego modułu zbierającego IntelliTrace).](../debugger/using-the-intellitrace-stand-alone-collector.md)

1. Na komputerze z uruchomionym programem SharePoint skonfiguruj program [Microsoft Monitoring Agent i rozpocznij monitorowanie rozwiązania.](../debugger/using-the-intellitrace-stand-alone-collector.md)

2. Dezaktywuj funkcję:

   1. W menu **Akcje witryny w** programie SharePoint wybierz pozycję Ustawienia **witryny.**

   2. W **obszarze Akcje lokacji** wybierz link **Zarządzaj funkcjami lokacji.**

   3. Obok opcji **IntelliTraceTest Feature1** wybierz przycisk **Dezaktywuj.**

   4. Na stronie Ostrzeżenie wybierz link **Dezaktywuj tę** funkcję.

      Występuje błąd (w tym przypadku z powodu błędu zgłoszonego w programie obsługi zdarzeń FeatureDeactivating().

3. W oknie programu PowerShell uruchom polecenie [Stop-WebApplicationMonitoring,](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) aby utworzyć plik iTrace, zatrzymać monitorowanie i ponownie uruchomić rozwiązanie programu SharePoint.

     **Stop-WebApplicationMonitoring***"<\<SharePointSite> \\ SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>Debugowanie i naprawianie rozwiązania programu SharePoint

Teraz możesz wyświetlić plik dziennika IntelliTrace w Visual Studio, aby znaleźć i naprawić błąd w rozwiązaniu programu SharePoint.

1. W folderze \IntelliTraceLogs otwórz plik iTrace w Visual Studio.

     Zostanie **wyświetlona strona Podsumowanie funkcji IntelliTrace.** Ponieważ błąd nie został obsłużony, w obszarze nieobsługiwanego wyjątku w sekcji **Analiza** pojawia się identyfikator korelacji programu SharePoint (identyfikator GUID). Wybierz przycisk **Stos wywołań,** jeśli chcesz wyświetlić stos wywołań, w którym wystąpił błąd.

2. Wybierz przycisk **Debuguj** wyjątek.

     Po wyświetleniu monitu załaduj pliki symboli. W **oknie IntelliTrace** wyjątek jest wyróżniony jako "Wyrzucono: wystąpił poważny błąd!".

     W oknie IntelliTrace wybierz wyjątek, aby wyświetlić kod, który zakończył się niepowodzeniem.

3. Napraw błąd, otwierając rozwiązanie programu SharePoint, a następnie usuwając komentarz lub usuwając instrukcje **throw** w górnej części procedury FeatureDeactivating().

4. Ponownie skompilować rozwiązanie w Visual Studio, a następnie ponownie wdeń je w programie SharePoint.

5. Dezaktywuj funkcję, wykonując następujące kroki:

    1. W menu **Akcje witryny w** programie SharePoint wybierz pozycję Ustawienia **witryny.**

    2. W **obszarze Akcje lokacji** wybierz link **Zarządzaj funkcjami lokacji.**

    3. Obok opcji **IntelliTraceTest Feature1** wybierz przycisk **Dezaktywuj.**

    4. Na stronie Ostrzeżenie wybierz link **Dezaktywuj tę** funkcję.

6. Otwórz listę Zadanie i sprawdź, czy wartość **Stan** zadania Dezaktywuj ma wartość "Ukończono", a jej **wartość % Complete** wynosi 100%.

     Kod działa teraz prawidłowo.

## <a name="see-also"></a>Zobacz też

- [Weryfikowanie i debugowanie kodu programu SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [Przewodnik: weryfikowanie kodu SharePoint za pomocą testów jednostkowych](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
