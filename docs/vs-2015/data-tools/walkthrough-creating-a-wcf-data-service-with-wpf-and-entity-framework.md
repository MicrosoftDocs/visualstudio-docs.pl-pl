---
title: 'Przewodnik: Tworzenie usługi danych programu WCF przy użyciu WPF i Entity Framework | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f26d81c3ac80b889f90e2a729545f0db0e52fa1a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660234"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Przewodnik: Tworzenie usługi danych programu WCF przy użyciu WPF i Entity Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym instruktażu pokazano, jak utworzyć prostą [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] hostowaną w aplikacji sieci Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], a następnie uzyskać do niej dostęp z aplikacji Windows Forms.

 W instruktażu wykonasz następujące czynności:

- Utwórz aplikację sieci Web, aby hostować [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Utwórz [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], który reprezentuje tabelę Customers w bazie danych Northwind.

- Utwórz [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Utwórz aplikację kliencką i Dodaj odwołanie do [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)].

- Utworzenie powiązania danych z usługą i wygenerowanie interfejsu użytkownika.

- Opcjonalnie dodanie funkcji filtrowania do aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne
 Następujące składniki są wymagane do przeprowadzenia tego instruktażu:

- Przykładowa bazy danych Northwind.

     Jeśli nie masz tej bazy danych na komputerze deweloperskim, możesz ją pobrać z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=98088). Aby uzyskać instrukcje, zobacz [Pobieranie przykładowych baz danych](https://msdn.microsoft.com/library/ef9d69a1-9461-43fe-94bb-7c836754bcb5).

## <a name="creating-the-service"></a>Tworzenie usługi
 Aby utworzyć [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)], należy dodać projekt sieci Web, utworzyć [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], a następnie utworzyć usługę z modelu.

 W pierwszym kroku dodasz projekt internetowy, który będzie hostował usługę.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-create-the-web-project"></a>Aby utworzyć projekt internetowy

1. Na pasku menu wybierz **plik**, **Nowy**, **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzły **Visual Basic** lub  **C# wizualizacji** i **sieci Web** , a następnie wybierz szablon **aplikacja sieci Web ASP.NET** .

3. W polu tekstowym **Nazwa** wprowadź **NorthwindWeb**, a następnie wybierz przycisk **OK** .

4. W oknie dialogowym **Nowy projekt ASP.NET** , na liście **Wybierz szablon** wybierz opcję **pusty**, a następnie wybierz przycisk **OK** .

   W tym kroku utworzysz [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], który reprezentuje tabelę Customers w bazie danych Northwind.

#### <a name="to-create-the-entity-data-model"></a>Aby utworzyć model Entity Data Model

1. Na pasku menu wybierz **projekt**, **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz węzeł **dane** , a następnie wybierz element **ADO.NET Entity Data Model** .

3. W polu tekstowym **Nazwa** wprowadź `NorthwindModel`, a następnie wybierz przycisk **Dodaj** .

    Zostanie wyświetlony Kreator modelu Entity Data Model.

4. W Kreatorze Entity Data Model na stronie **Wybierz zawartość modelu** wybierz element **Dr Designer z bazy danych** , a następnie wybierz przycisk **dalej** .

5. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

   - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

        —lub—

   - Wybierz przycisk **nowe połączenie** , aby skonfigurować nowe połączenie danych. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

6. Jeśli baza danych wymaga hasła, wybierz przycisk opcji **tak, Uwzględnij dane poufne w parametrach połączenia** , a następnie wybierz przycisk **dalej** .

   > [!NOTE]
   > Jeśli zostanie wyświetlone okno dialogowe, wybierz pozycję **tak** , aby zapisać plik w projekcie.

7. Na stronie **Wybierz wersję** wybierz przycisk opcji **Entity Framework 5,0** , a następnie wybierz przycisk **dalej** .

   > [!NOTE]
   > Aby można było użyć najnowszej wersji Entity Framework 6 z usługami WCF, należy zainstalować pakiet NuGet dostawcy Usługi danych programu WCF Entity Framework. Zobacz [używanie usługi danych programu WCF 5.6.0 z Entity Framework 6 +](http://blogs.msdn.com/b/odatateam/archive/2013/10/02/using-wcf-data-services-5-6-0-with-entity-framework-6.aspx).

8. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** , zaznacz pole wyboru **klienci** , a następnie wybierz przycisk **Zakończ** .

    Zostanie wyświetlony diagram modelu jednostek, a do projektu zostanie dodany plik NorthwindModel.edmx.

   W tym kroku utworzysz i przetestujesz usługę danych.

#### <a name="to-create-the-data-service"></a>Aby utworzyć usługę danych

1. Na pasku menu wybierz **projekt**, **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz węzeł **Sieć Web** , a następnie wybierz element **Usługa danych programu WCF 5,6** .

3. W polu tekstowym **Nazwa** wprowadź `NorthwindCustomers`, a następnie wybierz przycisk **Dodaj** .

    Plik NorthwindCustomers. svc pojawi się w **edytorze kodu**.

4. W **edytorze kodu**znajdź pierwszy `TODO:` komentarz i Zastąp kod następującym kodem:

    [!code-csharp[WCFDataServiceWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#1)]
    [!code-vb[WCFDataServiceWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#1)]

5. Zastąp komentarze w obsłudze zdarzeń `InitializeService` następującym kodem:

    [!code-csharp[WCFDataServiceWalkthrough#2](../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs#2)]
    [!code-vb[WCFDataServiceWalkthrough#2](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb#2)]

6. Na pasku menu wybierz **Debuguj**, **Uruchom bez debugowania** , aby uruchomić usługę. Zostanie otwarte okno przeglądarki i pojawi się w nim schemat XML usługi.

7. Na pasku **adresu** wprowadź `Customers` na końcu adresu URL dla NorthwindCustomers. svc, a następnie wybierz klawisz **Enter** .

    Zostanie wyświetlona reprezentacja XML danych znajdujących się w tabeli Klienci.

   > [!NOTE]
   > Czasami przeglądarka Internet Explorer błędnie interpretuje dane jako źródło danych RSS. Należy się upewnić, że opcja wyświetlania źródeł danych RSS jest wyłączona. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z usługą](../data-tools/troubleshooting-service-references.md).

8. Zamknij okno przeglądarki.

   W następnych krokach utworzysz aplikację kliencką opartą na interfejsie Windows Forms, która będzie korzystała z usługi.

## <a name="creating-the-client-application"></a>Tworzenie aplikacji klienckiej
 W celu utworzenia aplikacji klienckiej dodasz drugi projekt, dodasz odwołanie z projektu do usługi, skonfigurujesz źródło danych oraz utworzysz interfejs użytkownika, w którym będą wyświetlane dane z usługi.

 W pierwszym kroku dodasz projekt Windows Forms do rozwiązania oraz nadasz mu status projektu startowego.

#### <a name="to-create-the-client-application"></a>Aby utworzyć aplikację kliencką

1. Na pasku menu wybierz plik, **Dodaj**, **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **element wizualny C#**  , a następnie wybierz węzeł **Windows** , a następnie wybierz pozycję **aplikacja Windows Forms**.

3. W polu tekstowym **Nazwa** wprowadź `NorthwindClient`, a następnie wybierz przycisk **OK** .

4. W **Eksplorator rozwiązań**wybierz węzeł projektu **NorthwindClient** .

5. Na pasku menu wybierz **projekt**, **Ustaw jako projekt startowy**.

   W tym kroku dodasz odwołanie do usługi do [!INCLUDE[ss_data_service](../includes/ss-data-service-md.md)] w projekcie sieci Web.

#### <a name="to-add-a-service-reference"></a>Aby dodać odwołanie do usługi

1. Na pasku menu wybierz **projekt**, **Dodaj odwołanie do usługi**.

2. W oknie dialogowym **Dodaj odwołanie do usługi** wybierz przycisk **odnajdywanie** .

    Adres URL usługi NorthwindCustomers pojawia się w polu **adres** .

3. Wybierz przycisk **OK** , aby dodać odwołanie do usługi.

   W tym kroku skonfigurujesz źródło danych w celu utworzenia powiązania danych z usługą.

#### <a name="to-enable-data-binding-to-the-service"></a>Aby utworzyć powiązanie danych z usługą

1. Na pasku menu wybierz **Widok**, **inne okna**, **źródła danych**.

2. W oknie **źródła danych** wybierz przycisk **Dodaj nowe źródło danych** .

3. Na stronie **Wybierz typ źródła danych** w **Kreatorze konfiguracji źródła danych**wybierz **obiekt**, a następnie wybierz przycisk **dalej** .

4. Na stronie **Wybierz obiekty danych** rozwiń węzeł **NorthwindClient** , a następnie rozwiń węzeł **NorthwindClient. ServiceReference1** .

5. Zaznacz pole wyboru **Klient** , a następnie wybierz przycisk **Zakończ** .

   W tym kroku utworzysz interfejs użytkownika, w którym będą wyświetlane dane z usługi.

#### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika

1. W oknie **źródła danych** Otwórz menu skrótów dla węzła **klienci** i wybierz polecenie **Kopiuj**.

2. W projektancie formularzy **Form1. vb** lub **Form1.cs** Otwórz menu skrótów i wybierz polecenie **Wklej**.

    Kontrolka <xref:System.Windows.Forms.DataGridView>, składnik <xref:System.Windows.Forms.BindingSource> i składnik <xref:System.Windows.Forms.BindingNavigator> są dodawane do formularza.

3. Wybierz kontrolkę **customersDataGridView** , a następnie w oknie **Właściwości** ustaw właściwość **Dock** na **Fill**.

4. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **Form1** i wybierz polecenie **Wyświetl kod** , aby otworzyć Edytor kodu, i Dodaj następującą instrukcję Imports lub using na początku pliku:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Dodaj następujący kod do programu obsługi zdarzeń `Form1_Load`:

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

6. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku NorthwindCustomers. svc i wybierz polecenie **Wyświetl w przeglądarce**. Zostanie otwarte okno przeglądarki Internet Explorer i pojawi się w nim schemat XML usługi.

7. Skopiuj adres URL z paska adresu przeglądarki Internet Explorer.

8. W kodzie, który został dodany w kroku 4, wybierz `http://localhost:53161/NorthwindCustomers.svc/` i zastąp go adresem URL, który właśnie został skopiowany.

9. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie** , aby uruchomić aplikację. Zostaną wyświetlone informacje o kliencie.

   Masz teraz działającą aplikację, która wyświetla listę klientów z usługi NorthwindCustomers. Aby udostępnić dodatkowe dane za pośrednictwem usługi, można zmodyfikować [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] w celu uwzględnienia dodatkowych tabel z bazy danych Northwind.

   W następnym opcjonalnym kroku dowiesz się, jak filtrować dane zwracane przez usługę.

## <a name="adding-filtering-capabilities"></a>Dodawanie funkcji filtrowania
 W tym kroku dostosujesz aplikację w taki sposób, aby filtrowała dane według miejscowości zamieszkania klienta.

#### <a name="to-add-filtering-by-city"></a>Aby dodać filtrowanie według miejscowości

1. W **Eksplorator rozwiązań**Otwórz menu skrótów dla węzła **Form1. vb** lub **Form1.cs** i wybierz polecenie **Otwórz**.

2. Dodaj kontrolkę <xref:System.Windows.Forms.TextBox> i kontrolkę <xref:System.Windows.Forms.Button> z **przybornika** do formularza.

3. Otwórz menu skrótów dla kontrolki <xref:System.Windows.Forms.Button> i wybierz polecenie **Wyświetl kod**, a następnie Dodaj następujący kod do programu obsługi zdarzeń `Button1_Click`:

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

4. W poprzednim kodzie Zastąp `http://localhost:53161/NorthwindCustomers.svc` adresem URL z programu obsługi zdarzeń `Form1_Load`.

5. Na pasku menu wybierz **Debuguj**, **Rozpocznij debugowanie** , aby uruchomić aplikację.

6. W polu tekstowym wprowadź wartość **Londyn**, a następnie wybierz przycisk. Zostaną wyświetleni tylko klienci z Londynu.

## <a name="see-also"></a>Zobacz też
 [Windows Communication Foundation usług i usługi danych programu WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) [: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych programu WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
