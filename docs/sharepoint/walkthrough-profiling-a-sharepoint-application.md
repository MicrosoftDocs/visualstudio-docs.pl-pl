---
title: 'Przewodnik: Profilowanie aplikacji SharePoint | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: c900a1496d3ef864e50d40092379348c05a4706b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: pl-PL
ms.lasthandoff: 07/06/2020
ms.locfileid: "86017104"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>Przewodnik: Profilowanie aplikacji SharePoint
  W tym instruktażu pokazano, jak za pomocą narzędzi profilowania w programie Visual Studio zoptymalizować wydajność aplikacji SharePoint. Przykładowa aplikacja jest odbiorcą zdarzeń funkcji programu SharePoint, który zawiera pętlę bezczynności, która obniża wydajność odbiorcy zdarzeń funkcji. Program Visual Studio profiler umożliwia znalezienie i wyeliminowanie najbardziej kosztownego (najwolniejszego wykonania) części projektu, zwanej również *ścieżką gorącą*.

 W tym instruktażu przedstawiono następujące zadania:

- [Dodaj funkcję i odbiorcę zdarzeń funkcji](#add-a-feature-and-feature-event-receiver).

- [Skonfiguruj i Wdróż aplikację programu SharePoint](#configure-and-deploy-the-sharepoint-application).

- [Uruchom aplikację SharePoint](#run-the-sharepoint-application).

- [Wyświetl i Interpretuj wyniki profilu](#view-and-interpret-the-profile-results).

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>Tworzenie projektu programu SharePoint
 Najpierw utwórz projekt programu SharePoint.

### <a name="to-create-a-sharepoint-project"></a>Aby utworzyć projekt programu SharePoint

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** .

2. Rozwiń węzeł **SharePoint** w **Visual C#** lub **Visual Basic**, a następnie wybierz węzeł **2010** .

3. W okienku szablony wybierz szablon **projektu programu SharePoint 2010** .

4. W polu **Nazwa** wprowadź **ProfileTest**, a następnie wybierz przycisk **OK** .

    Zostanie wyświetlony **Kreator dostosowania programu SharePoint** .

5. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wprowadź adres URL witryny programu SharePoint Server, w której ma być debugowana definicja lokacji, lub Użyj lokalizacji domyślnej (http://<em>system Name</em>/).

6. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz przycisk opcji **Wdróż jako farmę** .

    Obecnie można tylko profilować rozwiązania farmy. Aby uzyskać więcej informacji o rozwiązaniach w trybie piaskownicy a rozwiązaniach farmy, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

7. Wybierz przycisk **Zakończ** . Projekt pojawia się w **Eksplorator rozwiązań**.

## <a name="add-a-feature-and-feature-event-receiver"></a>Dodaj funkcję i odbiorcę zdarzeń funkcji
 Następnie Dodaj funkcję do projektu wraz z odbiorcą zdarzeń dla tej funkcji. Ten odbiorca zdarzeń będzie zawierać kod, który ma zostać profilowany.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>Aby dodać funkcję i odbiorcę zdarzeń funkcji

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **funkcje** , wybierz polecenie **Dodaj funkcję**i pozostaw nazwę domyślną, **Feature1**.

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **Feature1**, a następnie wybierz polecenie **Dodaj odbiorcę zdarzeń**.

     Spowoduje to dodanie pliku kodu do funkcji z kilkoma komentarzami do obsługi zdarzeń, a następnie otwarcie pliku do edycji.

3. W klasie odbiorcy zdarzeń Dodaj następujące deklaracje zmiennych.

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

4. Zastąp `FeatureActivated` procedurę poniższym kodem.

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

5. Dodaj następującą procedurę poniżej `FeatureActivated` procedury.

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

6. W **Eksplorator rozwiązań**Otwórz menu skrótów dla projektu (**ProfileTest**), a następnie wybierz **Właściwości**.

7. W oknie dialogowym **Właściwości** wybierz kartę **SharePoint** .

8. Na liście **Konfiguracja wdrożenia aktywnego** wybierz pozycję **Brak aktywacji**.

     Wybranie tej konfiguracji wdrożenia umożliwia ręczne aktywowanie tej funkcji później w programie SharePoint.

9. Zapisz projekt.

## <a name="configure-and-deploy-the-sharepoint-application"></a>Konfigurowanie i wdrażanie aplikacji programu SharePoint
 Teraz, gdy projekt programu SharePoint jest gotowy, skonfiguruj go i Wdróż na serwerze programu SharePoint.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>Aby skonfigurować i wdrożyć aplikację SharePoint

1. W menu **Analizuj** wybierz polecenie **Uruchom Kreatora wydajności**.

2. Na pierwszej stronie **Kreatora wydajności**pozostaw metodę profilowania jako **próbkowanie procesora** , a następnie wybierz przycisk **dalej** .

     Inne metody profilowania mogą być używane w bardziej zaawansowanych sytuacjach profilowania. Aby uzyskać więcej informacji, zobacz [Omówienie metod zbierania danych o wydajności](../profiling/understanding-performance-collection-methods.md).

3. Na stronie dwóch **Kreatora wydajności**pozostaw obiekt docelowy profilu jako **ProfileTest** , a następnie wybierz przycisk **dalej** .

     Jeśli rozwiązanie ma wiele projektów, pojawiają się na tej liście.

4. Na trzeciej stronie **Kreatora wydajności**wyczyść pole wyboru **Włącz profilowanie interakcji między warstwami** , a następnie wybierz przycisk **dalej** .

     Funkcja profilowania interakcji między warstwami (TIP) jest przydatna do mierzenia wydajności aplikacji, które wysyłają zapytania do baz danych i pokazują, ile razy żąda się strony sieci Web. Ponieważ te dane nie są wymagane do tego przykładu, ta funkcja nie zostanie włączona.

5. Na stronie cztery w **Kreatorze wydajności**pozostaw zaznaczone pole wyboru **Uruchom profilowanie po zakończeniu pracy Kreatora** , a następnie wybierz przycisk **Zakończ** .

     Kreator umożliwia Profilowanie aplikacji na serwerze, wyświetla okno **Eksplorator wydajności** , a następnie kompiluje, wdraża i uruchamia aplikację SharePoint.

## <a name="run-the-sharepoint-application"></a>Uruchom aplikację SharePoint
 Aktywuj funkcję w programie SharePoint, wyzwalając `FeatureActivation` Kod zdarzenia do uruchomienia.

### <a name="to-run-the-sharepoint-application"></a>Aby uruchomić aplikację SharePoint

1. W programie SharePoint otwórz menu **Akcje witryny** , a następnie wybierz pozycję **Ustawienia lokacji**.

2. Na liście **Akcje lokacji** wybierz łącze **Zarządzaj funkcjami lokacji** .

3. Na liście **funkcje** wybierz przycisk **Aktywuj** obok pozycji **ProfileTest Feature1**.

     Po wykonaniu tej czynności występuje pauza z powodu wywołania bezczynnej pętli w `FeatureActivated` funkcji.

4. Na pasku **szybkiego uruchamiania** wybierz pozycję **listy** , a następnie **na liście listy** wybierz pozycję **Anonsy**.

     Zwróć uwagę, że do listy zostało dodane nowe powiadomienie z informacją, że funkcja została aktywowana.

5. Zamknij witrynę programu SharePoint.

     Po zamknięciu programu SharePoint Profiler tworzy i wyświetla przykładowy raport profilowania i zapisuje go jako plik VSP w folderze projektu **ProfileTest** .

## <a name="view-and-interpret-the-profile-results"></a>Wyświetlanie i Interpretowanie wyników profilu
 Teraz, gdy masz uruchomioną i profilowaną aplikację SharePoint, Wyświetl wyniki testów.

### <a name="to-view-and-interpret-the-profile-results"></a>Aby wyświetlać i interpretować wyniki profilu

1. W oknie funkcje, w której znajduje się **najbardziej szczególna część pracy** przykładowego raportu profilowania, Zauważ, że `TimeCounter` znajduje się w górnej części listy.

     Ta lokalizacja wskazuje, że `TimeCounter` była jedną z funkcji o najwyższej liczbie próbek, co oznacza, że jest to jeden z największych wąskich gardeł w aplikacji. Ta sytuacja nie jest jednak zaskakujące, ponieważ została celowo zaprojektowana w celach demonstracyjnych.

2. W obszarze **funkcje wykonujące najwięcej poszczególnych zadań** wybierz `ProcessRequest` łącze, aby wyświetlić dystrybucję kosztów dla `ProcessRequest` funkcji.

     **Called functions** `ProcessRequest` Zwróć uwagę, że funkcja **FeatureActiviated** jest wyświetlana w sekcji o nazwie Functions jako najbardziej kosztownej nazwie funkcji.

3. W sekcji **wywoływane funkcje** wybierz przycisk **FeatureActivated** .

     W sekcji **o nazwie** Functions for **FeatureActivated** `TimeCounter` Funkcja jest wyświetlana jako najbardziej kosztowna funkcja. W okienku **Widok kodu funkcji** wyróżniony kod ( `TimeCounter` ) jest punktem aktywnym i wskazuje, gdzie jest wymagana korekta.

4. Zamknij przykładowy raport profilowania.

     Aby ponownie wyświetlić raport w dowolnym momencie, Otwórz plik VSP w oknie **Eksplorator wydajności** .

## <a name="fix-the-code-and-reprofile-the-application"></a>Popraw kod i przeprofiluj aplikację
 Teraz funkcja hotspot w aplikacji SharePoint została zidentyfikowana. napraw ją.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>Aby naprawić kod i zmienić profil aplikacji

1. W kodzie odbiorcy zdarzeń funkcji należy dodać komentarz do `TimeCounter` wywołania metody w `FeatureActivated` celu uniemożliwienia jego wywołania.

2. Zapisz projekt.

3. W **Eksplorator wydajności**Otwórz folder targets, a następnie wybierz węzeł **ProfileTest** .

4. Na pasku narzędzi **Eksplorator wydajności** na karcie **Akcje** wybierz przycisk **Rozpocznij profilowanie** .

     Jeśli chcesz zmienić właściwości profilowania przed ponownym profilem aplikacji, wybierz przycisk **Kreator wydajności uruchamiania** .

5. Postępuj zgodnie z instrukcjami w sekcji **Uruchamianie aplikacji SharePoint** wcześniej w tym temacie.

     Funkcja powinna aktywować znacznie szybciej, gdy wywołanie do pętli bezczynności zostało wyeliminowane. Przykładowy raport profilowania powinien odzwierciedlać ten sposób.

## <a name="see-also"></a>Zobacz także
- [Przegląd sesji wydajności](../profiling/performance-session-overview.md)
- [Początkujący Przewodnik dotyczący profilowania wydajności](../profiling/beginners-guide-to-performance-profiling.md)
- [Znajdowanie wąskich gardeł aplikacji za pomocą programu Visual Studio profiler](https://msdn.microsoft.com/magazine/cc337887.aspx)
