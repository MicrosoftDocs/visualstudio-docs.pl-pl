---
title: Utwórz składnik Web Part Silverlight, który umożliwia wyświetlanie protokołu OData dla programu SharePoint
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 859944c51be0abf2e6a326a06a5e4432a69ee4ee
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655922"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Przewodnik: Tworzenie składnika Web Part programu Silverlight wyświetlającego Protokół OData dla programu SharePoint
  Program SharePoint 2010 udostępnia swoje dane listy za pomocą protokołu OData. W programie SharePoint usługa OData jest implementowana przez usługę RESTful Service ListData. svc. W tym instruktażu pokazano, jak utworzyć składnik Web Part programu SharePoint, który jest hostem aplikacji Silverlight. Aplikacja Silverlight wyświetla informacje o liście anonsów programu SharePoint za pomocą ListData. svc. Aby uzyskać więcej informacji, zobacz [Interfejs REST programu SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) i [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].,

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Tworzenie aplikacji Silverlight i składnika Web Part Silverlight
 Najpierw Utwórz aplikację Silverlight w programie Visual Studio. Aplikacja Silverlight pobiera dane z listy anonsów programu SharePoint za pomocą usługi ListData. svc.

> [!NOTE]
> Brak wersji programu Silverlight przed 4,0 obsługa wymaganych interfejsów do odwoływania się do danych listy programu SharePoint.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Aby utworzyć aplikację Silverlight i składnik Web Part Silverlight

1. Na pasku menu wybierz kolejno opcje **plik**  > **Nowy**  > **projekt** , aby wyświetlić okno dialogowe **Nowy projekt** .

2. Rozwiń węzeł **SharePoint** w obszarze **Wizualizacja C#**  lub **Visual Basic**, a następnie wybierz węzeł **2010** .

3. W okienku szablony wybierz szablon **składnika Web Part programu SharePoint 2010 Silverlight** .

4. W polu **Nazwa** wprowadź **SLWebPartTest** , a następnie wybierz przycisk **OK** .

    Zostanie wyświetlone okno dialogowe **Kreator dostosowania programu SharePoint** .

5. Na stronie **Określanie poziomu lokacji i zabezpieczeń na potrzeby debugowania** wprowadź adres URL witryny programu SharePoint Server, w której ma być debugowana definicja lokacji, lub Użyj lokalizacji domyślnej (http://<em>system Name</em>/).

6. W sekcji **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz przycisk opcji **Wdróż jako farmę** .

    Chociaż w tym przykładzie zastosowano rozwiązanie farmy, projekty części sieci Web Silverlight można wdrożyć jako rozwiązania farmy lub w trybie piaskownicy. Aby uzyskać więcej informacji o rozwiązaniach w trybie piaskownicy i rozwiązaniach farmy, zobacz [zagadnienia dotyczące rozwiązania w trybie piaskownicy](../sharepoint/sandboxed-solution-considerations.md).

7. W sekcji **jak chcesz skojarzyć składnik Web Part Silverlight** na stronie **Określanie informacji o konfiguracji programu Silverlight** wybierz przycisk opcji **Utwórz nowy projekt Silverlight i skojarz go ze składnikiem Web Part** .

8. Zmień **nazwę** na **SLApplication**, ustaw **Język** na **Visual Basic** lub **wizualizację C#** , a następnie ustaw **wersję Silverlight** na **Silverlight 4,0**.

9. Wybierz przycisk **Zakończ** . Projekty pojawiają się w **Eksplorator rozwiązań**.

     Rozwiązanie zawiera dwa projekty: aplikację Silverlight i składnik Web Part Silverlight. Aplikacja Silverlight pobiera i wyświetla listę danych z programu SharePoint, a składnik Web Part Silverlight obsługuje aplikację Silverlight, umożliwiając wyświetlanie jej w programie SharePoint.

## <a name="customize-the-silverlight-application"></a>Dostosowywanie aplikacji Silverlight
 Dodaj elementy Code i Design do aplikacji Silverlight.

#### <a name="to-customize-the-silverlight-application"></a>Aby dostosować aplikację Silverlight

1. Dodaj odwołanie do zestawu do elementu System. Windows. Data w aplikacji Silverlight. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań za pomocą okna dialogowego Dodawanie odwołania](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).

2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla **odwołań**, a następnie wybierz **Dodaj odwołanie do usługi**.

    > [!NOTE]
    > Jeśli używasz Visual Basic, musisz wybrać ikonę **Pokaż wszystkie pliki** w górnej części **Eksplorator rozwiązań** , aby wyświetlić węzeł **odwołania** .

3. W polu adres okna dialogowego **Dodaj odwołanie do usługi** wprowadź adres URL witryny programu SharePoint, na przykład **http://MySPSite** , a następnie wybierz przycisk **Przejdź** .

     Gdy program Silverlight lokalizuje usługę SharePoint OData ListData. svc, zastępuje adres adresem URL pełnego usługi. W tym przykładzie http://myserver http://myserver/_vti_bin/ListData.svc.

4. Wybierz przycisk **OK** , aby dodać odwołanie do usługi do projektu, i Użyj domyślnej nazwy usługi ServiceReference1.

5. Na pasku menu wybierz **kompiluj**  > **Kompiluj rozwiązanie**.

6. Dodaj nowe źródło danych do projektu na podstawie usługi programu SharePoint. W tym celu na pasku menu wybierz opcję **wyświetl**  >  inne  > **źródła danych** **systemu Windows** .

     W oknie **źródła danych** są wyświetlane wszystkie dostępne dane listy programu SharePoint, takie jak zadania, anonse i kalendarz.

7. Dodaj dane listy anonsów do aplikacji Silverlight. Możesz przeciągnąć "anonse" z okna **źródła danych** do projektanta Silverlight.

     Spowoduje to utworzenie kontrolki siatki powiązanej z listą anonsów witryny programu SharePoint.

8. Zmień rozmiar kontrolki siatki, aby dopasować ją do strony Silverlight.

9. W pliku kodu MainPage. XAML (*MainPage.XAML.cs* for Visual C# lub *MainPage. XAML. vb* dla Visual Basic) Dodaj następujące odwołania do przestrzeni nazw.

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. Dodaj następujące deklaracje zmiennych w górnej części klasy.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. Zastąp procedurę `UserControl_Loaded` poniższymi.

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     Pamiętaj, aby zamienić symbol zastępczy *servername* na nazwę serwera, na którym działa program SharePoint.

12. Dodaj następującą procedurę obsługi błędu.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Modyfikowanie składnika Web Part Silverlight
 Zmień właściwość w projekcie składnika Web Part Silverlight, aby włączyć debugowanie Silverlight.

#### <a name="to-modify-the-silverlight-web-part"></a>Aby zmodyfikować składnik Web Part Silverlight

1. Otwórz menu skrótów dla projektu składnika Web Part Silverlight (**SLWebPartTest**), a następnie wybierz polecenie **Właściwości**.

2. W oknie **Właściwości** wybierz kartę **SharePoint** .

3. Jeśli nie została jeszcze wybrana, zaznacz pole wyboru **Włącz debugowanie Silverlight (zamiast debugowania skryptu)** .

4. Zapisz projekt.

## <a name="test-the-silverlight-web-part"></a>Testowanie składnika Web Part Silverlight
 Przetestuj nowy składnik Web Part Silverlight w programie SharePoint, aby upewnić się, że dane listy programu SharePoint są poprawnie wyświetlane.

#### <a name="to-test-the-silverlight-web-part"></a>Aby przetestować składnik Web Part Silverlight

1. Wybierz klawisz **F5** , aby skompilować i uruchomić rozwiązanie SharePoint.

2. W programie SharePoint w menu **Akcje lokacji** wybierz polecenie **Nowa strona**.

3. W oknie dialogowym **Nowa strona** wprowadź tytuł, taki jak **test składnika Web Part SL**, a następnie wybierz przycisk **Utwórz** .

4. W projektancie stron na karcie Narzędzia do **edycji** wybierz pozycję **Wstaw**.

5. Na pasku kart wybierz pozycję **składnik Web Part**.

6. W polu **Kategorie** wybierz folder **niestandardowy** .

7. Z listy **składniki Web Part** wybierz składnik Web Part Silverlight, a następnie wybierz przycisk **Dodaj** , aby dodać składnik Web Part do projektanta.

8. Po wprowadzeniu wszystkich dodatków do strony sieci Web wybierz kartę **Strona** , a następnie wybierz przycisk **Zapisz & Zamknij** na pasku narzędzi.

     Składnik Web Part Silverlight powinien teraz wyświetlać dane anonsów z witryny programu SharePoint. Domyślnie strona jest przechowywana na liście strony witryny w programie SharePoint.

    > [!NOTE]
    > Podczas uzyskiwania dostępu do danych w programie Silverlight w różnych domenach Technologia Silverlight chroni przed lukami w zabezpieczeniach, które mogą być używane do korzystania z aplikacji sieci Web. W przypadku wystąpienia problemów podczas uzyskiwania dostępu do danych zdalnych w programie Silverlight zobacz [udostępnianie usługi w granicach domen](http://go.microsoft.com/fwlink/?LinkId=223276).

## <a name="see-also"></a>Zobacz także
- [Tworzenie składników Web Part dla programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Wdrażanie, publikowanie i uaktualnianie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
