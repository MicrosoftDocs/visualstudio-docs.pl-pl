---
title: 'Przewodnik: Tworzenie składnik Web Part Silverlight wyświetlającego dane OData dla programu SharePoint | Dokumentacja firmy Microsoft'
ms.date: 02/22/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 658417d07fdc0031a6e018d332bdbdd1d7edb1a6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905718"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>Przewodnik: Tworzenie składnika web part programu Silverlight, na który wyświetlającego dane OData dla programu SharePoint
  SharePoint 2010 udostępnia swoje dane listy za pomocą protokołu OData. W programie SharePoint usługi OData jest implementowany przez usługi RESTful ListData.svc. W tym instruktażu przedstawiono sposób tworzenia składnika web part programu SharePoint, na który jest hostem aplikacji Silverlight. Aplikacja Silverlight Wyświetla informacje o liście anons programu SharePoint przy użyciu ListData.svc. Aby uzyskać więcej informacji, zobacz [interfejsu REST w programie SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) i [Open Data Protocol](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Obsługiwane wersje systemu Microsoft Windows i programu SharePoint.
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Tworzenie aplikacji programu Silverlight i składnika web part Silverlight
 Najpierw utwórz aplikacji Silverlight w programie Visual Studio. Aplikacji Silverlight pobiera dane z listy anonsów programu SharePoint przy użyciu usługi ListData.svc.  
  
> [!NOTE]  
>  Nie wersji dodatku Silverlight przed 4.0 obsługuje interfejsami wymaganymi do odwoływania się do danych z listy programu SharePoint.  
  
#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Aby utworzyć aplikację Silverlight i składnika web part Silverlight
  
1. Na pasku menu wybierz **pliku** > **New** > **projektu** do wyświetlenia **nowy projekt** okno dialogowe.  
  
2. Rozwiń **SharePoint** węźle albo **Visual C#** lub **języka Visual Basic**, a następnie wybierz **2010** węzła.  
  
3. W okienku szablonów wybierz **składnik Web Part Silverlight programu SharePoint 2010** szablonu.  
  
4. W **nazwa** wprowadź **SLWebPartTest** , a następnie wybierz **OK** przycisku.  
  
    **Kreator ustawień niestandardowych SharePoint** pojawi się okno dialogowe.  
  
5. Na **Określanie witryny i poziomu zabezpieczeń dla debugowania** strony, wprowadź adres URL witryny programu SharePoint server gdzie chcesz debugować definicji witryny lub użyj domyślnej lokalizacji (http://<em>Nazwa systemowa</em>/) .  
  
6. W **co to jest poziom zaufania dla tego rozwiązania programu SharePoint?** wybierz pozycję **Wdróż jako rozwiązanie farmy** przycisku opcji.  
  
    Mimo że w tym przykładzie użyto rozwiązania farmy, projekty programu Silverlight web part można wdrożyć jako farmy lub rozwiązania w trybie piaskownicy. Aby uzyskać więcej informacji na temat rozwiązania w trybie piaskownicy oraz rozwiązaniami farmy, zobacz [uwagi dotyczące rozwiązania typu piaskownica](../sharepoint/sandboxed-solution-considerations.md).  
  
7. W **jak chcesz skojarzyć składnik Web Part Silverlight** części **Określ informacje o konfiguracji programu Silverlight** wybierz **Utwórz nowy projekt Silverlight i Skojarz go ze składnikiem web part** przycisku opcji.  
  
8. Zmiana **nazwa** do **SLApplication**ustaw **języka** do jednej **języka Visual Basic** lub **Visual C#**, a następnie ustaw **wersji dodatku Silverlight** do **Silverlight 4.0**.  
  
9. Wybierz **Zakończ** przycisku. Projekty są wyświetlane w **Eksploratora rozwiązań**.  
  
     Rozwiązanie zawiera dwa projekty: aplikacja Silverlight i składnika web part programu Silverlight. Aplikacja Silverlight pobiera i wyświetla dane listy z poziomu programu SharePoint i składnik web part Silverlight obsługuje aplikację Silverlight, dzięki któremu można go wyświetlić w programie SharePoint.  
  
## <a name="customize-the-silverlight-application"></a>Dostosuj aplikację Silverlight
 Dodaj elementy projektu i kodu do aplikacji Silverlight.  
  
#### <a name="to-customize-the-silverlight-application"></a>Aby dostosować aplikację Silverlight
  
1.  Dodaj odwołanie do zestawu do System.Windows.Data w aplikacji Silverlight. Aby uzyskać więcej informacji, zobacz [jak: Dodawanie lub usuwanie odwołań za pomocą okno dialogowe Dodaj odwołanie](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **odwołania**, a następnie wybierz **Dodaj odwołanie do usługi**.  
  
    > [!NOTE]  
    >  Jeśli używasz języka Visual Basic, należy wybrać **Pokaż wszystkie pliki** ikonę u góry **Eksploratora rozwiązań** do wyświetlenia **odwołania** węzła.  
  
3.  W polu adresu **Dodaj odwołanie do usługi** okna dialogowego wprowadź adres URL witryny programu SharePoint, takich jak **http://MySPSite**, a następnie wybierz **Przejdź** przycisku.  
  
     Gdy Silverlight lokalizuje usługę SharePoint OData ListData.svc, zastępuje adres za pomocą adresu URL wszystkich usług. W tym przykładzie http://myserver staje się http://myserver/_vti_bin/ListData.svc.  
  
4.  Wybierz **OK** przycisk, aby dodać odwołanie do usługi do projektu i użyj domyślnej nazwy usługi ServiceReference1.  
  
5.  Na pasku menu wybierz **kompilacji** > **Kompiluj rozwiązanie**.  
  
6.  Dodaj nowe źródło danych do projektu, w oparciu o usługi programu SharePoint. Aby to zrobić, na pasku menu, wybierz opcję **widoku** > **Windows inne** > **źródeł danych**.  
  
     **Źródeł danych** okno wyświetla wszystkie dostępne dane listy programu SharePoint, takich jak zadania, ogłoszenia i kalendarza.  
  
7.  Dodaj dane listy ogłoszeń do aplikacji Silverlight. Można przeciągnąć "Anonsów" z **źródeł danych** okna do projektanta Silverlight.  
  
     Spowoduje to utworzenie formantu siatki powiązana lista anonsów witryny programu SharePoint.  
  
8.  Rozmiar formantu siatki w celu dopasowania do strony programu Silverlight.  
  
9. W pliku MainPage.xaml kodu (*MainPage.xaml.cs* dla języka Visual C# lub *MainPage.xaml.vb* dla języka Visual Basic), Dodaj następujące odwołania do przestrzeni nazw.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
10. Dodaj następujące deklaracje zmiennych u góry klasy.  
  
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
   
11. Zastąp `UserControl_Loaded` procedury następującym kodem.  
  
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
     Koniecznie Zastąp *ServerName* symbol zastępczy nazwą serwera, na którym uruchomiony jest SharePoint.  
  
12. Dodaj procedurę obsługi błędów.  
  
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
       
## <a name="modify-the-silverlight-web-part"></a>Modyfikowanie składnika web part Silverlight
 Zmień właściwość w projekcie Silverlight web part włączyć debugowanie Silverlight.  
  
#### <a name="to-modify-the-silverlight-web-part"></a>Aby zmodyfikować składnika web part Silverlight  
  
1.  Otwórz menu skrótów dla projektu części sieci web programu Silverlight (**SLWebPartTest**), a następnie wybierz **właściwości**.  
  
2.  W **właściwości** oknie Wybierz **SharePoint** kartę.  
  
3.  Jeśli nie została jeszcze wybrana, wybierz opcję **Włącz debugowanie programu Silverlight (zamiast debugowanie skryptów)** pole wyboru.  
  
4.  Zapisz projekt.  
  
## <a name="test-the-silverlight-web-part"></a>Testowanie składnika web part Silverlight
 Przetestuj nowy składnik web part Silverlight w programie SharePoint, aby zapewnić prawidłowe wyświetlanie danych listy programu SharePoint.  
  
#### <a name="to-test-the-silverlight-web-part"></a>Aby przetestować składnika web part Silverlight  
  
1.  Wybierz **F5** klawisz, aby skompilować i uruchomić rozwiązanie programu SharePoint.  
  
2.  W programie SharePoint na **Akcje witryny** menu, wybierz **nową stronę**.  
  
3.  W **nową stronę** okno dialogowe, wprowadź tytuł, takich jak **testu części sieci Web SL**, a następnie wybierz **Utwórz** przycisk.  
  
4.  W projektancie stron na **narzędzia edycji** kartę, wybrać **Wstaw**.  
  
5.  Na pasku karty Wybierz **składnika Web Part**.  
  
6.  W **kategorie** wybierz **niestandardowe** folderu.  
  
7.  W **składników Web Part** , wybierz składnik web part Silverlight, a następnie wybierz **Dodaj** przycisk, aby dodać składnik web part do projektanta.  
  
8.  Po dokonaniu wszystkie dodatki do strony sieci web, który ma, wybierz **strony** kartę, a następnie wybierz **Zapisz i Zamknij** przycisk na pasku narzędzi.  
  
     Składnik web part Silverlight powinny teraz wyświetlanie danych anonsu z witryny programu SharePoint. Domyślnie strony znajduje się na liście stron witryny w programie SharePoint.  
  
    > [!NOTE]  
    >  Podczas uzyskiwania dostępu do danych w technologii Silverlight w domenach, Silverlight chroni przed luki w zabezpieczeniach, których można użyć w celu wykorzystania aplikacji sieci web. Jeśli napotkasz problemy podczas uzyskiwania dostępu do danych zdalnych w programie Silverlight, zobacz [wprowadzania Service Available Across Domain Boundaries](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie składników web Part programu SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Wdrażanie, publikowanie oraz aktualizowanie pakietów rozwiązania SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
