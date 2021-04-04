---
title: Tworzenie usługi danych WCF przy użyciu & WPF Entity Framework
description: Utwórz usługę danych programu WCF za pomocą WPF i Entity Framework, która jest hostowana w aplikacji sieci Web ASP.NET, a następnie Uzyskuj dostęp do niej z poziomu aplikacji Windows Forms.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data services in Visual Studio
- WCF Data Services, Visual Studio
- ADO.NET Data Services, Visual Studio
- WCF data services in Visual Studio
ms.assetid: da66ad1b-a25d-485c-af13-2d18f0422e3d
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: f519d8e3bfe01fc3e4a1e4cfe82f4f8502c84821
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215698"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Przewodnik: tworzenie usługi danych programu WCF za pomocą struktur WPF i Entity Framework
W tym instruktażu pokazano, jak utworzyć prostą [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , która jest hostowana w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci Web, a następnie uzyskać do niej dostęp z aplikacji Windows Forms.

W tym instruktażu:

- Utwórz aplikację sieci Web do hostowania a [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] .

- Utwórz element [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] reprezentujący `Customers` tabelę w bazie danych Northwind.

- Utwórz [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] .

- Utwórz aplikację kliencką i Dodaj odwołanie do [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] .

- Utworzenie powiązania danych z usługą i wygenerowanie interfejsu użytkownika.

- Opcjonalnie dodanie funkcji filtrowania do aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne
W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio** można zainstalować SQL Server Express LocalDB jako część obciążenia **magazynu danych i przetwarzania** lub jako pojedynczy składnik.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (**Eksplorator obiektów SQL Server** jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="creating-the-service"></a>Tworzenie usługi
Aby utworzyć [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] , należy dodać projekt sieci Web, utworzyć [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] , a następnie utworzyć usługę z modelu.

W pierwszym kroku dodasz projekt sieci Web do hostowania usługi.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Aby utworzyć projekt sieci Web

1. Na pasku menu wybierz pozycję **plik**  >  **Nowy**  >  **projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Visual C#** i **Web** nodes, a następnie wybierz szablon **aplikacja sieci Web ASP.NET** .

3. W polu tekstowym **Nazwa** wprowadź **NorthwindWeb**, a następnie wybierz przycisk **OK** .

4. W oknie dialogowym **Nowy projekt ASP.NET** , na liście **Wybierz szablon** wybierz opcję **pusty**, a następnie wybierz przycisk **OK** .

W następnym kroku utworzysz, [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] który reprezentuje `Customers` tabelę w bazie danych Northwind.

### <a name="to-create-the-entity-data-model"></a>Aby utworzyć model Entity Data Model

1. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz węzeł **dane** , a następnie wybierz element **ADO.NET Entity Data Model** .

3. W polu tekstowym **Nazwa** wprowadź `NorthwindModel` , a następnie wybierz przycisk **Dodaj** .

     Zostanie wyświetlony Kreator modelu Entity Data Model.

4. W Kreatorze Entity Data Model na stronie **Wybierz zawartość modelu** wybierz element **Dr Designer z bazy danych** , a następnie wybierz przycisk **dalej** .

5. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         -lub-

    - Wybierz przycisk **nowe połączenie** , aby skonfigurować nowe połączenie danych. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

6. Jeśli baza danych wymaga hasła, wybierz przycisk opcji **tak, Uwzględnij dane poufne w parametrach połączenia** , a następnie wybierz przycisk **dalej** .

    > [!NOTE]
    > Jeśli zostanie wyświetlone okno dialogowe, wybierz pozycję **tak** , aby zapisać plik w projekcie.

7. Na stronie **Wybierz wersję** wybierz przycisk opcji **Entity Framework 5,0** , a następnie wybierz przycisk **dalej** .

    > [!NOTE]
    > Aby można było użyć najnowszej wersji Entity Framework 6 z usługami WCF, należy zainstalować pakiet NuGet dostawcy WCF Data Services Entity Framework. Zobacz [używanie WCF Data Services 5.6.0 z Entity Framework 6 +](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Na stronie **Wybierz obiekty bazy danych** rozwiń węzeł **tabele** , zaznacz pole wyboru **klienci** , a następnie wybierz przycisk **Zakończ** .

     Zostanie wyświetlony Diagram modelu jednostki, a do projektu zostanie dodany plik *NorthwindModel. edmx* .

W następnym kroku utworzysz i testujesz usługę danych.

### <a name="to-create-the-data-service"></a>Aby utworzyć usługę danych

1. Na pasku menu wybierz **projekt**  >  **Dodaj nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz węzeł **Sieć Web** , a następnie wybierz element **Usługa danych programu WCF 5,6** .

3. W polu tekstowym **Nazwa** wprowadź `NorthwindCustomers` , a następnie wybierz przycisk **Dodaj** .

     Plik **NorthwindCustomers. svc** pojawi się w **edytorze kodu**.

4. W **edytorze kodu** Znajdź pierwszy `TODO:` komentarz i zastąp go następującym kodem:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet1":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet1":::

5. Zastąp komentarze w `InitializeService` obsłudze zdarzeń następującym kodem:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/vb/northwindcustomers.svc.vb" id="Snippet2":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/wcfdataservicewalkthrough/cs/northwindcustomers.svc.cs" id="Snippet2":::


6. Na pasku menu wybierz **Debuguj**  >  **Rozpocznij bez debugowania** , aby uruchomić usługę. Zostanie otwarte okno przeglądarki i zostanie wyświetlony schemat XML dla usługi.

7. Na pasku **adresu** wpisz `Customers` na końcu adresu URL dla **NorthwindCustomers. svc**, a następnie wybierz klawisz **Enter** .

     Zostanie wyświetlona Reprezentacja XML danych w `Customers` tabeli.

    > [!NOTE]
    > Czasami przeglądarka Internet Explorer błędnie interpretuje dane jako źródło danych RSS. Należy się upewnić, że opcja wyświetlania źródeł danych RSS jest wyłączona. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z usługą](../data-tools/troubleshooting-service-references.md).

8. Zamknij okno przeglądarki.

W następnych krokach utworzysz aplikację kliencką Windows Forms, która będzie korzystać z usługi.

## <a name="creating-the-client-application"></a>Tworzenie aplikacji klienckiej
Aby utworzyć aplikację kliencką, należy dodać drugi projekt, dodać odwołanie do usługi do projektu, skonfigurować źródło danych i utworzyć interfejs użytkownika do wyświetlania danych z usługi.

W pierwszym kroku dodasz projekt Windows Forms do rozwiązania i ustawisz go jako projekt startowy.

### <a name="to-create-the-client-application"></a>Aby utworzyć aplikację kliencką

1. Na pasku menu wybierz plik, **Dodaj**  >  **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** rozwiń węzeł **Visual Basic** lub **Visual C#** , wybierz węzeł **systemu Windows** , a następnie wybierz pozycję **aplikacja Windows Forms**.

3. W polu tekstowym **Nazwa** wprowadź `NorthwindClient` , a następnie wybierz przycisk **OK** .

4. W **Eksplorator rozwiązań** wybierz węzeł projektu **NorthwindClient** .

5. Na pasku menu wybierz **projekt**, **Ustaw jako projekt startowy**.

W następnym kroku dodasz odwołanie do usługi do elementu [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] w projekcie sieci Web.

### <a name="to-add-a-service-reference"></a>Aby dodać odwołanie do usługi

1. Na pasku menu wybierz **projekt**  >  **Dodaj odwołanie do usługi**.

2. W oknie dialogowym **Dodaj odwołanie do usługi** wybierz przycisk **odnajdywanie** .

     Adres URL usługi NorthwindCustomers pojawia się w polu **adres** .

3. Wybierz przycisk **OK** , aby dodać odwołanie do usługi.

W następnym kroku skonfigurujesz źródło danych, aby umożliwić powiązanie danych z usługą.

### <a name="to-enable-data-binding-to-the-service"></a>Aby utworzyć powiązanie danych z usługą

1. Na pasku menu wybierz opcję **Wyświetl**  >  **inne**  >  **źródła danych** systemu Windows.

   Zostanie otwarte okno **źródła danych** .

2. W oknie **źródła danych** wybierz przycisk **Dodaj nowe źródło danych** .

3. Na stronie **Wybierz typ źródła danych** w **Kreatorze konfiguracji źródła danych** wybierz **obiekt**, a następnie wybierz przycisk **dalej** .

4. Na stronie **Wybierz obiekty danych** rozwiń węzeł **NorthwindClient** , a następnie rozwiń węzeł **NorthwindClient. ServiceReference1** .

5. Zaznacz pole wyboru **Klient** , a następnie wybierz przycisk **Zakończ** .

W następnym kroku utworzysz interfejs użytkownika, który wyświetla dane z usługi.

### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika

1. W oknie **źródła danych** Otwórz menu skrótów dla węzła **klienci** i wybierz polecenie **Kopiuj**.

2. W projektancie formularzy **Form1. vb** lub **Form1. cs** Otwórz menu skrótów i wybierz polecenie **Wklej**.

    <xref:System.Windows.Forms.DataGridView>Kontrolka, <xref:System.Windows.Forms.BindingSource> składnik i <xref:System.Windows.Forms.BindingNavigator> składnik są dodawane do formularza.

3. Wybierz kontrolkę **customersDataGridView** , a następnie w oknie **Właściwości** ustaw właściwość **Dock** na **Fill**.

4. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła **Form1** i wybierz polecenie **Wyświetl kod** , aby otworzyć Edytor kodu, i Dodaj następującą `Imports` `Using` instrukcję lub na początku pliku:

   ```vb
   Imports NorthwindClient.ServiceReference1
   ```

   ```csharp
   using NorthwindClient.ServiceReference1;
   ```

5. Dodaj następujący kod do `Form1_Load` programu obsługi zdarzeń:

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

6. W **Eksplorator rozwiązań** Otwórz menu skrótów dla pliku **NorthwindCustomers. svc** i wybierz polecenie **Wyświetl w przeglądarce**. Zostanie otwarty program Internet Explorer i zostanie wyświetlony schemat XML dla usługi.

7. Skopiuj adres URL z paska adresu przeglądarki Internet Explorer.

8. W kodzie, który został dodany w kroku 4, wybierz `http://localhost:53161/NorthwindCustomers.svc/` i zastąp go adresem URL, który właśnie został skopiowany.

9. Na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie** , aby uruchomić aplikację. Informacje o kliencie są wyświetlane.

   Masz teraz działającą aplikację, która wyświetla listę klientów z usługi NorthwindCustomers. Jeśli chcesz uwidocznić dodatkowe dane za pośrednictwem usługi, możesz zmodyfikować, [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] Aby uwzględnić dodatkowe tabele z bazy danych Northwind.

W następnym opcjonalnym kroku dowiesz się, jak filtrować dane zwracane przez usługę.

## <a name="adding-filtering-capabilities"></a>Dodawanie funkcji filtrowania
W tym kroku dostosowano aplikację w celu filtrowania danych według miasta klienta.

### <a name="to-add-filtering-by-city"></a>Aby dodać filtrowanie według miejscowości

1. W **Eksplorator rozwiązań** Otwórz menu skrótów dla węzła **Form1. vb** lub **Form1. cs** i wybierz polecenie **Otwórz**.

2. Dodaj <xref:System.Windows.Forms.TextBox> kontrolkę i <xref:System.Windows.Forms.Button> kontrolkę z **przybornika** do formularza.

3. Otwórz menu skrótów dla <xref:System.Windows.Forms.Button> kontrolki, wybierz polecenie **Wyświetl kod**, a następnie Dodaj następujący kod do `Button1_Click` programu obsługi zdarzeń:

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

4. W poprzednim kodzie Zastąp ciąg `http://localhost:53161/NorthwindCustomers.svc` adresem URL z `Form1_Load` programu obsługi zdarzeń.

5. Na pasku menu wybierz **Debuguj**  >  **Rozpocznij debugowanie** , aby uruchomić aplikację.

6. W polu tekstowym wprowadź wartość **Londyn**, a następnie wybierz przycisk. Zostaną wyświetleni tylko klienci z Londynu.

## <a name="see-also"></a>Zobacz też

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołania usługi danych programu WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)
