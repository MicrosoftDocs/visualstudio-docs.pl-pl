---
title: Tworzenie usługi danych WCF przy użyciu WPF i Entity Framework
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 368d92010da062f2883d63161824e528d5d22c84
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/28/2019
ms.locfileid: "66261084"
---
# <a name="walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework"></a>Przewodnik: Tworzenie usługi danych WCF w technologii WPF i Entity Framework
W tym instruktażu przedstawiono sposób tworzenia prostej [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] hostowaną w [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] aplikacji sieci web, a następnie Uzyskaj dostęp z aplikacji Windows Forms.

W tym przewodniku możesz:

- Tworzenie aplikacji internetowej do hosta [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Tworzenie [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] reprezentujący `Customers` tabeli w bazie danych Northwind.

- Utwórz [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Utworzenie aplikacji klienckiej i dodanie odwołania do [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)].

- Utworzenie powiązania danych z usługą i wygenerowanie interfejsu użytkownika.

- Opcjonalnie dodanie funkcji filtrowania do aplikacji.

## <a name="prerequisites"></a>Wymagania wstępne
Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **przechowywanie i przetwarzanie danych** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (**Eksplorator obiektów SQL Server** jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="creating-the-service"></a>Tworzenie usługi
Do utworzenia [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)], będzie dodać projekt internetowy, utworzyć [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], a następnie Utwórz usługę z modelu.

W pierwszym kroku dodasz projekt sieci web do obsługi usługi.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-create-the-web-project"></a>Aby utworzyć projekt sieci web

1. Na pasku menu wybierz **pliku** > **New** > **projektu**.

2. W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** i **sieci Web** węzłów, a następnie wybierz **ASP. Aplikacja sieci Web NET** szablonu.

3. W **nazwa** tekstu wprowadź **NorthwindWeb**, a następnie wybierz **OK** przycisku.

4. W **nowy projekt ASP.NET** okno dialogowe, **wybierz szablon** wybierz **pusty**, a następnie wybierz **OK** przycisku.

W następnym kroku utworzysz [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] reprezentujący `Customers` tabeli w bazie danych Northwind.

### <a name="to-create-the-entity-data-model"></a>Aby utworzyć model Entity Data Model

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

2. W **Dodaj nowy element** okna dialogowego wybierz **danych** węzła, a następnie wybierz **ADO.NET Entity Data Model** elementu.

3. W **nazwa** tekstu wprowadź `NorthwindModel`, a następnie wybierz **Dodaj** przycisku.

     Zostanie wyświetlony Kreator modelu Entity Data Model.

4. W kreatorze modelu danych jednostki w **wybierz zawartość modelu** wybierz **projektancie platformy EF z bazy danych** elementu, a następnie wybierz **dalej** przycisku.

5. Na **wybierz połączenie danych** strony, wykonaj jedną z następujących czynności:

    - Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

         —lub—

    - Wybierz **nowe połączenie** przycisk, aby skonfigurować nowe połączenie danych. Aby uzyskać więcej informacji, zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

6. Jeśli baza danych wymaga hasła, wybierz opcję **tak, Dołącz dane poufne w parametrach połączenia** przycisk opcji, a następnie wybierz **dalej** przycisku.

    > [!NOTE]
    > Jeśli pojawi się okno dialogowe, wybierz **tak** można zapisać pliku do projektu.

7. Na **wybierz wersję** wybierz **Entity Framework 5.0** przycisk opcji, a następnie wybierz **dalej** przycisku.

    > [!NOTE]
    > Aby można było używać najnowszej wersji programu Entity Framework 6 za pomocą usługi WCF, należy zainstalować pakiet NuGet dostawcy Framework jednostki usługi danych WCF. Zobacz [przy użyciu programu WCF Data Services 5.6.0 z platformą Entity Framework 6](https://devblogs.microsoft.com/odata/using-wcf-data-services-5-6-0-with-entity-framework-6/).

8. Na **wybierz obiekty bazy danych** rozwiń **tabel** węzeł **klientów** pole wyboru, a następnie wybierz **Zakończ** przycisk.

     Wyświetla diagram modelu jednostek, a *NorthwindModel.edmx* plik zostanie dodany do projektu.

W następnym kroku utworzysz i przetestujesz usługę danych.

### <a name="to-create-the-data-service"></a>Aby utworzyć usługę danych

1. Na pasku menu wybierz **projektu** > **Dodaj nowy element**.

2. W **Dodaj nowy element** okna dialogowego wybierz **Web** węzła, a następnie wybierz **5.6 usługi danych WCF** elementu.

3. W **nazwa** tekstu wprowadź `NorthwindCustomers`, a następnie wybierz **Dodaj** przycisku.

     **NorthwindCustomers.svc** plik pojawia się w **Edytor kodu**.

4. W **Edytor kodu**, odszukaj pierwszy `TODO:` komentarz i Zastąp kod następującym kodem:

     [!code-vb[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#1](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_1.cs)]

5. Zastąp komentarze w `InitializeService` programu obsługi zdarzeń z następującym kodem:

     [!code-vb[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/VisualBasic/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.vb)]
     [!code-csharp[WCFDataServiceWalkthrough#2](../data-tools/codesnippet/CSharp/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework_2.cs)]

6. Na pasku menu wybierz **debugowania** > **Rozpocznij bez debugowania** do uruchamiania usługi. Zostanie otwarte okno przeglądarki i Wyświetla schemat XML usługi.

7. W **adres** paska, wprowadź `Customers` na końcu adresu URL **NorthwindCustomers.svc**, a następnie wybierz **Enter** klucza.

     Reprezentacja XML danych w `Customers` zostanie wyświetlona tabela.

    > [!NOTE]
    > Czasami przeglądarka Internet Explorer błędnie interpretuje dane jako źródło danych RSS. Należy się upewnić, że opcja wyświetlania źródeł danych RSS jest wyłączona. Aby uzyskać więcej informacji, zobacz [Rozwiązywanie problemów z odwołaniami usługi](../data-tools/troubleshooting-service-references.md).

8. Zamknij okno przeglądarki.

W następnych krokach utworzysz aplikację klienta Windows Forms do korzystania z usługi.

## <a name="creating-the-client-application"></a>Tworzenie aplikacji klienckiej
 Aby utworzyć aplikację klienta, możesz dodasz drugi projekt, Dodaj odwołanie do projektu usługi, konfigurowanie źródła danych i Tworzenie interfejsu użytkownika, aby wyświetlić dane z usługi.

 W pierwszym kroku możesz dodać projekt Windows Forms do rozwiązania i jest ustawiony jako projekt startowy.

### <a name="to-create-the-client-application"></a>Aby utworzyć aplikację kliencką

1. Na pasku menu wybierz plik, **Dodaj** > **nowy projekt**.

2. W **nowy projekt** okna dialogowego rozwiń **języka Visual Basic** lub **Visual C#** węzła, wybierz **Windows** węzła, a następnie wybierz polecenie  **Windows Forms aplikacji**.

3. W **nazwa** tekstu wprowadź `NorthwindClient`, a następnie wybierz **OK** przycisku.

4. W **Eksploratora rozwiązań**, wybierz **NorthwindClient** węzeł projektu.

5. Na pasku menu wybierz **projektu**, **Ustaw jako projekt startowy**.

W następnym kroku dodasz odwołanie do usługi [!INCLUDE[ss_data_service](../data-tools/includes/ss_data_service_md.md)] w projekcie sieci web.

### <a name="to-add-a-service-reference"></a>Aby dodać odwołanie do usługi

1. Na pasku menu wybierz **projektu** > **Dodaj odwołanie do usługi**.

2. W **Dodaj odwołanie do usługi** okna dialogowego wybierz **odnajdź** przycisku.

     Adres URL usługi NorthwindCustomers pojawia się w **adres** pola.

3. Wybierz **OK** przycisk, aby dodać odwołanie do usługi.

W następnym kroku skonfigurujesz źródło danych w celu włączenia możliwości wiązania danych do usługi.

### <a name="to-enable-data-binding-to-the-service"></a>Aby utworzyć powiązanie danych z usługą

1. Na pasku menu wybierz **widoku** > **Windows inne** > **źródeł danych**.

   **Źródeł danych** zostanie otwarte okno.

2. W **źródeł danych** oknie Wybierz **Dodaj nowe źródło danych** przycisku.

3. Na **wybierz typ źródła danych** strony **Kreatora konfiguracji źródła danych**, wybierz **obiektu**, a następnie wybierz **dalej** przycisku .

4. Na **wybierz obiekty danych** rozwiń **NorthwindClient** węzła, a następnie rozwiń węzeł **Northwindkliencka.servicereference1** węzła.

5. Wybierz **klienta** pole wyboru, a następnie wybierz **Zakończ** przycisku.

W następnym kroku utworzysz interfejs użytkownika, który wyświetla dane z usługi.

### <a name="to-create-the-user-interface"></a>Aby utworzyć interfejs użytkownika

1. W **źródeł danych** okna, otwórz menu skrótów dla **klientów** węzeł i wybierz polecenie **kopiowania**.

2. W **Form1.vb** lub **Form1.cs** projektancie formularzy, otwórz menu skrótów i wybierz **Wklej**.

    A <xref:System.Windows.Forms.DataGridView> kontroli <xref:System.Windows.Forms.BindingSource> składnika, a <xref:System.Windows.Forms.BindingNavigator> składników są dodawane do formularza.

3. Wybierz **CustomersDataGridView** kontroli, a następnie w polu **właściwości** zestaw okna **Dock** właściwości **wypełnienia**.

4. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **Form1** węzeł i wybierz polecenie **Wyświetl kod** otwarcie edytora kodu i Dodaj następujący kod `Imports` lub `Using`instrukcji w górnej części pliku:

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

6. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **NorthwindCustomers.svc** pliku, a następnie wybierz **Pokaż w przeglądarce**. Program Internet Explorer otwiera i Wyświetla schemat XML usługi.

7. Skopiuj adres URL z paska adresu przeglądarki Internet Explorer.

8. W kodzie dodanym w kroku 4 Zaznacz `http://localhost:53161/NorthwindCustomers.svc/` i zastąp adres URL, który właśnie został skopiowany.

9. Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** do uruchomienia aplikacji. Informacje o kliencie są wyświetlane.

   Masz teraz działającą aplikację, która wyświetla listę klientów z usługi NorthwindCustomers. Jeśli chcesz udostępnić dodatkowe dane za pośrednictwem usługi, możesz zmodyfikować [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] celu uwzględnienia dodatkowych tabel z bazy danych Northwind.

W następnym opcjonalnym kroku dowiesz się, jak filtrować dane, które są zwracane przez usługę.

## <a name="adding-filtering-capabilities"></a>Dodawanie funkcji filtrowania
 W tym kroku możesz dostosować ją do filtrowania danych według miasta klienta.

### <a name="to-add-filtering-by-city"></a>Aby dodać filtrowanie według miejscowości

1. W **Eksploratora rozwiązań**, otwórz menu skrótów dla **Form1.vb** lub **Form1.cs** węzeł i wybierz polecenie **Otwórz**.

2. Dodaj <xref:System.Windows.Forms.TextBox> kontroli i <xref:System.Windows.Forms.Button> z kontrolować **przybornika** do formularza.

3. Otwórz menu skrótów dla <xref:System.Windows.Forms.Button> sterowania, wybierz **Wyświetl kod**, a następnie dodaj następujący kod w `Button1_Click` programu obsługi zdarzeń:

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

4. W poprzednim kodzie Zastąp `http://localhost:53161/NorthwindCustomers.svc` za pomocą adresu URL z `Form1_Load` programu obsługi zdarzeń.

5. Na pasku menu wybierz **debugowania** > **Rozpocznij debugowanie** do uruchomienia aplikacji.

6. W polu tekstowym wprowadź **Londyn**, a następnie wybierz przycisk. Zostaną wyświetleni tylko klienci z Londynu.

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Instrukcje: Dodawanie, aktualizowanie lub usuwanie odwołań usługi danych WCF](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)