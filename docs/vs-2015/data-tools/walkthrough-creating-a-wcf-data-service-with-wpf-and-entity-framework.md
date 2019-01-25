---
title: 'Przewodnik: Tworzenie usługi danych programu WCF za pomocą struktur WPF i Entity Framework | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
caps.latest.revision: 28
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2be6c030cf8602f053472971a98508043b253e43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777850"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Przewodnik: Tworzenie usługi danych programu WCF za pomocą struktur WPF i Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
W tym instruktażu przedstawiono sposób tworzenia prostej [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] hostowaną w [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji sieci Web, a następnie Uzyskaj dostęp z aplikacji Windows Forms.  
  
 W instruktażu wykonasz następujące czynności:  
  
-   Tworzenie aplikacji internetowej do hosta [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Utwórz [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] reprezentujący tabelę Klienci w bazie danych Northwind.  
  
-   Utwórz [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Utworzenie aplikacji klienckiej i dodanie odwołania do [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].  
  
-   Utworzenie powiązania danych z usługą i wygenerowanie interfejsu użytkownika.  
  
-   Opcjonalnie dodanie funkcji filtrowania do aplikacji.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:  
  
-   Przykładowa bazy danych Northwind.  
  
     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz pobrać go z [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088). Aby uzyskać instrukcje, zobacz [Downloading Sample Databases](http://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).  
  
## <a name="creating-the-service"></a>Tworzenie usługi  
 Do utworzenia [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], będzie dodać projekt internetowy, utworzyć [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], a następnie Utwórz usługę z modelu.  
  
 W pierwszym kroku dodasz projekt internetowy, który będzie hostował usługę.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
#### <a name="to-create-the-web-project"></a>Aby utworzyć projekt internetowy  
  
1. Na pasku menu wybierz **pliku**, **New**, **projektu**.  
  
2. W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** i **sieci Web** węzłów, a następnie wybierz **ASP. Aplikacja sieci Web NET** szablonu.  
  
3. W **nazwa** tekstu wprowadź **NorthwindWeb**, a następnie wybierz **OK** przycisku.  
  
4. W **nowy projekt ASP.NET** okno dialogowe, **wybierz szablon** wybierz **pusty**, a następnie wybierz **OK** przycisku.  
  
   W tym kroku utworzysz [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] reprezentujący tabelę Klienci w bazie danych Northwind.  
  
#### <a name="to-create-the-entity-data-model"></a>Aby utworzyć model Entity Data Model  
  
1. Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
2. W **Dodaj nowy element** okna dialogowego wybierz **danych** węzła, a następnie wybierz **ADO.NET Entity Data Model** elementu.  
  
3. W **nazwa** tekstu wprowadź `NorthwindModel`, a następnie wybierz **Dodaj** przycisku.  
  
    Zostanie wyświetlony Kreator modelu Entity Data Model.  
  
4. W kreatorze modelu danych jednostki w **wybierz zawartość modelu** wybierz **projektancie platformy EF z bazy danych** elementu, a następnie wybierz **dalej** przycisku.  
  
5. Na **wybierz połączenie danych** strony, wykonaj jedną z następujących czynności:  
  
   -   Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.  
  
        —lub—  
  
   -   Wybierz **nowe połączenie** przycisk, aby skonfigurować nowe połączenie danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
6. Jeśli baza danych wymaga hasła, wybierz opcję **tak, Dołącz dane poufne w parametrach połączenia** przycisk opcji, a następnie wybierz **dalej** przycisku.  
  
   > [!NOTE]
   >  Jeśli pojawi się okno dialogowe, wybierz **tak** można zapisać pliku do projektu.  
  
7. Na **wybierz wersję** wybierz **Entity Framework 5.0** przycisk opcji, a następnie wybierz **dalej** przycisku.  
  
   > [!NOTE]
   >  Aby można było używać najnowszej wersji programu Entity Framework 6 za pomocą usługi WCF, należy zainstalować pakiet NuGet dostawcy Framework jednostki usługi danych WCF. Zobacz [przy użyciu programu WCF Data Services 5.6.0 z platformą Entity Framework 6](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).  
  
8. Na **wybierz obiekty bazy danych** rozwiń **tabel** węzeł **klientów** pole wyboru, a następnie wybierz **Zakończ** przycisk.  
  
    Zostanie wyświetlony diagram modelu jednostek, a do projektu zostanie dodany plik NorthwindModel.edmx.  
  
   W tym kroku utworzysz i przetestujesz usługę danych.  
  
#### <a name="to-create-the-data-service"></a>Aby utworzyć usługę danych  
  
1. Na pasku menu wybierz **projektu**, **Dodaj nowy element**.  
  
2. W **Dodaj nowy element** okna dialogowego wybierz **Web** węzła, a następnie wybierz **5.6 usługi danych WCF** elementu.  
  
3. W **nazwa** tekstu wprowadź `NorthwindCustomers`, a następnie wybierz **Dodaj** przycisku.  
  
    Plik NorthwindCustomers.svc pojawi się w **Edytor kodu**.  
  
4. W **Edytor kodu**, odszukaj pierwszy `TODO:` komentarz i Zastąp kod następującym kodem:  
  
    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]  
  
5. Zastąp komentarze w `InitializeService` programu obsługi zdarzeń z następującym kodem:  
  
    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]  
  
6. Na pasku menu wybierz **debugowania**, **Rozpocznij bez debugowania** do uruchamiania usługi. Zostanie otwarte okno przeglądarki i pojawi się w nim schemat XML usługi.  
  
7. W **adres** paska, wprowadź `Customers` na końcu adresu URL pliku northwindcustomers.SVC, a następnie wybierz **ENTER** klucza.  
  
    Zostanie wyświetlona reprezentacja XML danych znajdujących się w tabeli Klienci.  
  
   > [!NOTE]
   >  Czasami przeglądarka Internet Explorer błędnie interpretuje dane jako źródło danych RSS. Należy się upewnić, że opcja wyświetlania źródeł danych RSS jest wyłączona. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md).  
  
8. Zamknij okno przeglądarki.  
  
   W następnych krokach utworzysz aplikację kliencką opartą na interfejsie Windows Forms, która będzie korzystała z usługi.  
  
## <a name="creating-the-client-application"></a>Tworzenie aplikacji klienckiej  
 W celu utworzenia aplikacji klienckiej dodasz drugi projekt, dodasz odwołanie z projektu do usługi, skonfigurujesz źródło danych oraz utworzysz interfejs użytkownika, w którym będą wyświetlane dane z usługi.  
  
 W pierwszym kroku dodasz projekt Windows Forms do rozwiązania oraz nadasz mu status projektu startowego.  
  
#### <a name="to-create-the-client-application"></a>Aby utworzyć aplikację kliencką  
  
1. Na pasku menu wybierz plik, **Dodaj**, **nowy projekt**.  
  
2. W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** węzeł i wybierz polecenie **Windows** węzła, a następnie wybierz polecenie  **Windows Forms aplikacji**.  
  
3. W **nazwa** tekstu wprowadź `NorthwindClient`, a następnie wybierz **OK** przycisku.  
  
4. W **Eksploratora rozwiązań**, wybierz **NorthwindClient** węzeł projektu.  
  
5. Na pasku menu wybierz **projektu**, **Ustaw jako projekt startowy**.  
  
   W tym kroku dodasz odwołanie do usługi [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] w projekcie sieci Web.  
  
#### <a name="to-add-a-service-reference"></a>Aby dodać odwołanie do usługi  
  
1. Na pasku menu wybierz **projektu**, **Dodaj odwołanie do usługi**.  
  
2. W **Dodaj odwołanie do usługi** okna dialogowego wybierz **odnajdź** przycisku.  
  
    Adres URL usługi NorthwindCustomers pojawia się w **adres** pola.  
  
3. Wybierz **OK** przycisk, aby dodać odwołanie do usługi.  
  
   W tym kroku skonfigurujesz źródło danych w celu utworzenia powiązania danych z usługą.  
  
#### <a name="to-enable-data-binding-to-the-service"></a>Aby utworzyć powiązanie danych z usługą  
  
1. Na pasku menu wybierz **widoku**, **Windows inne**, **źródeł danych**.  
  
2. W **źródeł danych** oknie Wybierz **Dodaj nowe źródło danych** przycisku.  
  
3. Na **wybierz typ źródła danych** strony **Kreatora konfiguracji źródła danych**, wybierz **obiektu**, a następnie wybierz **dalej** przycisku .  
  
4. Na **wybierz obiekty danych** rozwiń **NorthwindClient** węzła, a następnie rozwiń węzeł **Northwindkliencka.servicereference1** węzła.  
  
5. Wybierz **klienta** pole wyboru, a następnie wybierz **Zakończ** przycisku.  
  
   W tym kroku utworzysz interfejs użytkownika, w którym będą wyświetlane dane z usługi.  
  
#### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika  
  
1. W **źródeł danych** okna, otwórz menu skrótów dla **klientów** węzeł i wybierz polecenie **kopiowania**.  
  
2. W **Form1.vb** lub **Form1.cs** projektancie formularzy, otwórz menu skrótów i wybierz **Wklej**.  
  
    A <xref:System.Windows.Forms.DataGridView> kontroli <xref:System.Windows.Forms.BindingSource> składnika, a <xref:System.Windows.Forms.BindingNavigator> składników są dodawane do formularza.  
  
3. Wybierz **CustomersDataGridView** kontroli, a następnie w polu **właściwości** zestaw okna **Dock** właściwości **wypełnienia**.  
  
4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **Form1** węzeł i wybierz polecenie **Wyświetl kod** otwarcie edytora kodu i dodaj następujące instrukcje importu lub przy użyciu instrukcji w na początku pliku:  
  
   ```vb  
   Imports NorthwindClient.ServiceReference1  
   ```  
  
   ```csharp  
   using NorthwindClient.ServiceReference1;  
   ```  
  
5. Dodaj następujący kod do `Form1_Load` program obsługi zdarzeń:  
  
   ```vb  
   Private Sub Form1_Load(sender As Object, e As EventArgs) Handles MyBase.Load  
           Dim proxy As New NorthwindEntities _  
   (New Uri("http://localhost:53161/NorthwindCustomers.svc/"))  
           Me.CustomersBindingSource.DataSource = proxy.Customers  
       End Sub  
   ```  
  
   ```csharp  
   private void Form1_Load(object sender, EventArgs e)  
   {  
   NorthwindEntities proxy = new NorthwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc/"));  
   this.CustomersBindingSource.DataSource = proxy.Customers;  
   }  
  
   ```  
  
6. W **Eksploratora rozwiązań**, otwórz menu skrótów pliku NorthwindCustomers.svc i wybierz **Pokaż w przeglądarce**. Zostanie otwarte okno przeglądarki Internet Explorer i pojawi się w nim schemat XML usługi.  
  
7. Skopiuj adres URL z paska adresu przeglądarki Internet Explorer.  
  
8. W kodzie dodanym w kroku 4 Zaznacz `http://localhost:53161/NorthwindCustomers.svc/` i zastąp adres URL, który właśnie został skopiowany.  
  
9. Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do uruchomienia aplikacji. Zostaną wyświetlone informacje o kliencie.  
  
   Masz teraz działającą aplikację, która wyświetla listę klientów z usługi NorthwindCustomers. Jeśli chcesz udostępnić dodatkowe dane za pośrednictwem usługi, możesz zmodyfikować [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] celu uwzględnienia dodatkowych tabel z bazy danych Northwind.  
  
   W następnym opcjonalnym kroku dowiesz się, jak filtrować dane zwracane przez usługę.  
  
## <a name="adding-filtering-capabilities"></a>Dodawanie funkcji filtrowania  
 W tym kroku dostosujesz aplikację w taki sposób, aby filtrowała dane według miejscowości zamieszkania klienta.  
  
#### <a name="to-add-filtering-by-city"></a>Aby dodać filtrowanie według miejscowości  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów dla **Form1.vb** lub **Form1.cs** węzeł i wybierz polecenie **Otwórz**.  
  
2.  Dodaj <xref:System.Windows.Forms.TextBox> kontroli i <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.  
  
3.  Otwórz menu skrótów dla <xref:System.Windows.Forms.Button> sterowania, a następnie wybierz **Wyświetl kod**, a następnie dodaj następujący kod w `Button1_Click` programu obsługi zdarzeń:  
  
    ```vb  
    Private Sub Button1_Click(sender As Object, e As EventArgs) Handles Button1.Click  
            Dim proxy As New northwindEntities _  
    (New Uri("http://localhost:53161/NorthwindCustomers.svc"))  
            Dim city As String = TextBox1.Text  
  
            If city <> "" Then  
                Me.CustomersBindingSource.DataSource = From c In _  
             proxy.Customers Where c.City = city  
            End If  
  
        End Sub  
    ```  
  
    ```csharp  
    private void Button1_Click(object sender, EventArgs e)  
    {  
    ServiceReference1.northwindModel.northwindEntities proxy = new northwindEntities(new Uri("http://localhost:53161/NorthwindCustomers.svc"));  
    string city = TextBox1.Text;  
  
    if (!string.IsNullOrEmpty(city)) {  
    this.CustomersBindingSource.DataSource = from c in proxy.Customers where c.City == city;  
    }  
  
    }  
    ```  
  
4.  W poprzednim kodzie Zastąp `http://localhost:53161/NorthwindCustomers.svc` za pomocą adresu URL z `Form1_Load` programu obsługi zdarzeń.  
  
5.  Na pasku menu wybierz **debugowania**, **Rozpocznij debugowanie** do uruchomienia aplikacji.  
  
6.  W polu tekstowym wprowadź **Londyn**, a następnie wybierz przycisk. Zostaną wyświetleni tylko klienci z Londynu.  
  
## <a name="see-also"></a>Zobacz też  
 [Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)   
 [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych programu WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
