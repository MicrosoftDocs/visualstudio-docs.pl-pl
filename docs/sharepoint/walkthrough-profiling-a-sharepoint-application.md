---
title: 'Przewodnik: Profilowanie aplikacji SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4cb4e2ac95a17adc918be50fa351a35174f128b1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54867523"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Przewodnik: Profil aplikacji programu SharePoint
  Ten poradnik pokazuje jak używać narzędzi profilowania w programie Visual Studio w celu zoptymalizowania wydajności aplikacji programu SharePoint. Przykładowa aplikacja jest zawierający pętli bezczynności, który obniża wydajność odbiorcę zdarzeń funkcji odbiorcy zdarzeń funkcji programu SharePoint. Profilera Visual Studio umożliwia znalezienie i wyeliminować najbardziej kosztowne (najwolniejsze wykonanie) części projektu, znany także jako *ścieżka aktywna*.  
  
 W tym instruktażu pokazano następujące zagadnienia:  
  
- [Dodawanie funkcji i odbiorcę zdarzeń funkcji](#BKMK_AddFtrandFtrEvntReceiver).  
  
- [Konfigurowanie i wdrażanie aplikacji programu SharePoint](#BKMK_ConfigSharePointApp).  
  
- [Uruchamianie aplikacji programu SharePoint](#BKMK_RunSPApp).  
  
- [Przeglądanie i interpretowanie wyniki profilowania](#BKMK_ViewResults).  
  
  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-sharepoint-project"></a>Utwórz projekt programu SharePoint
 Najpierw utwórz projekt programu SharePoint.  
  
#### <a name="to-create-a-sharepoint-project"></a>Aby utworzyć projekt programu SharePoint  
  
1. Na pasku menu wybierz **pliku** > **New** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2. Rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz **2010** węzła.  
  
3. W okienku szablonów wybierz **projekt programu SharePoint 2010** szablonu.  
  
4. W **nazwa** wprowadź **ProfileTest**, a następnie wybierz **OK** przycisku.  
  
    **Kreator ustawień niestandardowych SharePoint** pojawia się.  
  
5. Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint server gdzie chcesz debugować definicji witryny lub użyj domyślnej lokalizacji (http://<em>Nazwa systemowa</em>/) .  
  
6. W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisku opcji.  
  
    Obecnie można tylko profile rozwiązania farmy. Aby uzyskać więcej informacji dotyczących rozwiązań sandbox w porównaniu z rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).  
  
7. Wybierz **Zakończ** przycisku. Projekt, który pojawia się w **Eksploratora rozwiązań**.  
  
## <a name="add-a-feature-and-feature-event-receiver"></a>Dodawanie funkcji i odbiorcę zdarzeń funkcji
 Następnie dodaj funkcję do projektu, wraz z obsługiwanego odbiornika dla tej funkcji. Odbiornik zdarzeń będzie zawierał kod, które mają być profilowane.  
  
#### <a name="to-add-a-feature-and-feature-event-receiver"></a>Aby dodać funkcję i odbiorcę zdarzeń funkcji  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **funkcji** węzła, wybierz **Dodaj funkcję**i pozostawić nazwę wartość domyślną **Feature1**.  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **Feature1**, a następnie wybierz **Dodaj odbiorcę zdarzeń**.  
  
     Dodaje plik kodu funkcji z kilka programów obsługi zdarzeń zakomentowany i otwiera plik do edycji.  
  
3.  W klasie odbiornika zdarzeń Dodaj następujące deklaracje zmiennych.  
  
    ```vb  
    ' SharePoint site/subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site/subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
4.  Zastąp `FeatureActivated` procedury z następującym kodem.  
  
    ```vb  
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add a new announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    ' Waste some time.  
                    TimeCounter()  
                    ' Update the list.  
                    listItem.Update()  
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
  
                    // Add a new announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +   
    DateTime.Now.ToString();  
                    // Waste some time.  
                    TimeCounter();  
                    // Update the list.  
                    listItem.Update();                          
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
5.  Dodaj procedurę poniżej `FeatureActivated`procedury.  
  
    ```vb  
  
    Public Sub TimeCounter()  
        Dim result As Integer  
        For i As Integer = 0 To 99999  
            For j As Integer = 0 To 9999  
                result = i * j  
            Next j  
        Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void TimeCounter()  
    {  
        for (int i = 0; i < 100000; i++)  
        {  
            for (int j = 0; j < 10000; j++)  
            {  
                int result = i * j;  
            }  
        }  
    }  
    ```  
  
6.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla projektu (**ProfileTest**), a następnie wybierz **właściwości**.  
  
7.  W **właściwości** okna dialogowego wybierz **SharePoint** kartę.  
  
8.  W **aktywnej konfiguracji wdrożenia** wybierz **aktywacji nie**.  
  
     Wybranie tej konfiguracji wdrożenia można ręcznie włączyć funkcję później w programie SharePoint.  
  
9. Zapisz projekt.  
  
## <a name="configure-and-deploy-the-sharepoint-application"></a>Konfigurowanie i wdrażanie aplikacji programu SharePoint
 Teraz, gdy projekt programu SharePoint jest gotowa, ją skonfigurować i wdrożyć ją na serwerze programu SharePoint.  
  
#### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Do konfigurowania i wdrażania aplikacji programu SharePoint  
  
1.  Na **analizy** menu, wybierz **Uruchom Kreatora wydajności**.  
  
2.  Na stronie jeden **kreatora wydajności**, leave — metoda profilowania jako **próbkowania Procesora** i wybierz polecenie **dalej** przycisku.  
  
     Inne metody profilowania może służyć w bardziej zaawansowane profilowania sytuacjach. Aby uzyskać więcej informacji, zobacz [metodami zbierania danych wydajności opis](/visualstudio/profiling/understanding-performance-collection-methods).  
  
3.  Na stronie dwóch **kreatora wydajności**, pozostaw element docelowy profil jako **ProfileTest** i wybierz polecenie **dalej** przycisku.  
  
     Jeśli rozwiązanie zawiera wiele projektów, zostaną one wyświetlone na tej liście.  
  
4.  Na stronie trzy **kreatora wydajności**, wyczyść **Włącz profilowanie interakcji pomiędzy warstwami** pole wyboru, a następnie wybierz **dalej** przycisku.  
  
     Funkcja profilowanie interakcji warstwy (TIP) jest przydatna do pomiaru wydajności aplikacji do tej kwerendy bazy danych i dla pokazuje, ile razy żądania strony sieci web. Ponieważ te dane nie jest wymagane w tym przykładzie, firma Microsoft nie włączać tej funkcji.  
  
5.  Na stronie czterech **kreatora wydajności**, pozostaw **Uruchom profilowanie po zakończeniu pracy kreatora** zaznaczone pole wyboru, a następnie wybierz **Zakończ** przycisku.  
  
     Kreator włącza profilowania aplikacji na serwerze, przedstawia **Eksplorator wydajności** okna, a następnie kompilacji, wdrażania i uruchamia aplikację programu SharePoint.  
  
## <a name="run-the-sharepoint-application"></a>Uruchamianie aplikacji programu SharePoint
 Uaktywnij funkcję w programie SharePoint, wyzwalania `FeatureActivation` zdarzeń kod wymagany do uruchomienia.  
  
#### <a name="to-run-the-sharepoint-application"></a>Uruchamianie aplikacji programu SharePoint  
  
1.  W programie SharePoint, należy otworzyć **Akcje witryny** menu, a następnie wybierz **ustawienia lokacji**.  
  
2.  W **Akcje witryny** wybierz **Zarządzanie funkcjami witryny** łącza.  
  
3.  W **funkcji** wybierz **Aktywuj** znajdujący się obok **ProfileTest Feature1**.  
  
     Ma przerwie, gdy to zrobisz, z powodu wykonywania pętli bezczynności wywołanego `FeatureActivated` funkcji.  
  
4.  Na **Szybkie uruchamianie** paska, wybierz polecenie **Wyświetla** a następnie w **Wyświetla** wybierz **anonsów**.  
  
     Należy zauważyć, że dodano nowe zawiadomienie do listy, stwierdzający, że funkcja została aktywowana.  
  
5.  Zamknij witryny programu SharePoint.  
  
     Po zamknięciu programu SharePoint, program profilujący tworzy przedstawia przykładowy raport profilowania i zapisuje go jako plik Vsp w **ProfileTest** folderu projektu.  
  
## <a name="view-and-interpret-the-profile-results"></a>Wyświetlanie i interpretacja wyników profilu
 Skoro masz uruchamiania i profilowania aplikacji programu SharePoint, należy wyświetlić wyniki testów.  
  
#### <a name="to-view-and-interpret-the-profile-results"></a>Aby wyświetlić i interpretacja wyników profilu
  
1.  W **funkcje wykonujące najwięcej pracy poszczególnych** sekcji raportu profilowania próbki, należy zauważyć, że `TimeCounter` znajduje się w pobliżu górnej części listy.  
  
     Ta lokalizacja wskazuje, że `TimeCounter` była jedna z funkcji o największej liczby próbek, co oznacza, jest jednym z największych wąskich gardeł wydajności w aplikacji. Ta sytuacja nie jest zaskoczysz, ponieważ była celowo zaprojektowany w ten sposób w celach demonstracyjnych.  
  
2.  W **funkcje wykonujące najwięcej pracy poszczególnych** wybierz pozycję `ProcessRequest` łącze, aby wyświetlić dystrybucji kosztów dla `ProcessRequest` funkcji.  
  
     W **nazywane funkcjami** sekcji `ProcessRequest`, zwróć uwagę, że **FeatureActiviated** funkcji znajduje się na liście jako najbardziej kosztowne wywołał funkcję.  
  
3.  W **nazywane funkcjami** wybierz pozycję **FeatureActivated** przycisku.  
  
     W **nazywane funkcjami** sekcji **FeatureActivated**, `TimeCounter` funkcji znajduje się na liście jako najbardziej kosztowne wywołał funkcję. W **widok kodu funkcji** okienko, wyróżniony kod (`TimeCounter`) jest punktem największej aktywności i wskazuje, gdzie jest potrzebne korekty.  
  
4.  Zamknij próbki celów raportu profilowania.  
  
     Aby wyświetlić raport w dowolnym momencie ponownie, otwórz plik Vsp w **Eksplorator wydajności** okna.  
  
## <a name="fix-the-code-and-reprofile-the-application"></a>Napraw kod i reprofile aplikacji
 Teraz, gdy funkcja punkt aktywny w aplikacji programu SharePoint został określony, należy go naprawić.  
  
#### <a name="to-fix-the-code-and-reprofile-the-application"></a>Aby naprawić kod i reprofile aplikacji  
  
1.  W kodzie funkcji odbiorcy zdarzeń komentarz `TimeCounter` metody wywołania w `FeatureActivated` aby zapobiec wywoływana.  
  
2.  Zapisz projekt.  
  
3.  W **Eksplorator wydajności**, otwórz folder elementów docelowych, a następnie wybierz **ProfileTest** węzła.  
  
4.  Na **Eksplorator wydajności** narzędzi w **akcje** kartę, wybrać **Uruchom profilowanie** przycisku.  
  
     Jeśli chcesz zmienić dowolne z właściwości profilowania, przed reprofiling aplikacji, wybierz opcję **Uruchom Kreatora wydajności** zamiast tego przycisku.  
  
5.  Postępuj zgodnie z instrukcjami w **uruchamianie aplikacji programu SharePoint** sekcji wcześniej w tym temacie.  
  
     Ta funkcja powinna być aktywowana znacznie szybciej, teraz, gdy wywołanie metody wykonywania pętli bezczynności zostały wyeliminowane. Przykładowy raport profilowania powinny odzwierciedlać to.  
  
## <a name="see-also"></a>Zobacz także
 [Eksplorator wydajności](/visualstudio/profiling/performance-explorer)   
 [Sesja wydajności — omówienie](/visualstudio/profiling/performance-session-overview)   
 [Profilowanie wydajności — przewodnik dla początkujących](/visualstudio/profiling/beginners-guide-to-performance-profiling)   
 [Znajdź wąskie gardła za pomocą programu Visual Studio Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)  
