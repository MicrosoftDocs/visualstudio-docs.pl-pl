---
title: 'Przewodnik: Tworzenie aplikacji warstwowych'
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 471f0e9b97293bd70457a8f41cb7efddd6acf6c1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60091827"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Przewodnik: Tworzenie n-warstwowej aplikacji do obsługi danych
*N-warstwowa* danych aplikacji są aplikacje, uzyskiwać dostęp do danych, które są rozdzielone na wiele warstw logiczne, lub *warstwy*. Rozdzielanie składników aplikacji na dyskretne warstwy, łatwość konserwacji i zwiększa skalowalność aplikacji. Dzieje się tak, należy włączyć ułatwia przyjęcie nowych technologii, które mogą być stosowane do poszczególnych warstw, bez konieczności zmiany projektu całego rozwiązania. Architektura N-warstwowa zawiera warstwę prezentacji, warstwy środkowej i warstwy danych. Warstwa środkowa zazwyczaj zawiera warstwy dostępu do danych, warstwy logiki biznesowej i składniki współużytkowane, takie jak uwierzytelnianie i sprawdzania poprawności. Warstwa danych obejmuje relacyjnej bazy danych. N-warstwowych zazwyczaj przechowują wrażliwe informacje w warstwę dostępu do danych w warstwie środkowej do obsługi izolacji użytkowników końcowych, którzy uzyskują dostęp warstwy prezentacji. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).

Pierwszym sposobem rozdzielenia różnych warstw w n warstwowej aplikacji jest utworzenie dyskretnych projektów dla każdej warstwy, które mają zostać uwzględnione w aplikacji. Typizowanych elementów DataSet zawiera `DataSet Project` właściwość określający, które projekty wygenerowanego zestawu danych i `TableAdapter` kodu, należy przejść do.

W tym instruktażu pokazano, jak rozdzielić zestawu danych i `TableAdapter` kod do klasy dyskretne projekty biblioteki za pomocą **Projektanta obiektów Dataset**. Po oddzielisz zestaw danych i TableAdapter kodu, należy utworzyć [Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) usługi do wywołania w warstwie dostępu do danych. Na koniec można utworzyć aplikację Windows Forms jako Warstwa prezentacji. Ta warstwa uzyskuje dostęp do danych z usługi danych.

Z tego instruktażu należy wykonać następujące czynności:

- Utwórz nowe rozwiązanie n warstwowej, który zawiera wiele projektów.

- Dodaj dwa projekty bibliotek klas do rozwiązania n warstwowej.

- Tworzenie typizowanego zestawu danych za pomocą **Kreatora konfiguracji źródła danych**.

- Oddziel wygenerowany [TableAdapters](create-and-configure-tableadapters.md) i kod zestawu danych w dyskretne projekty.

- Tworzenie usługi Windows Communication Foundation (WCF) do wywołania w warstwie dostępu do danych.

- Tworzenie funkcji w usłudze w celu pobierania danych z warstwy dostępu do danych.

- Tworzenie aplikacji Windows Forms jako Warstwa prezentacji.

- Tworzenie formantów formularzy Windows, które są powiązane ze źródłem danych.

- Pisz kod, aby wypełnić tabele danych.

![Link do wideo](../data-tools/media/playvideo.gif) wersja wideo tego tematu, zobacz [poradnik wideo: Tworzenie aplikacji n warstwowa danych](http://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Wymagania wstępne
Ten przewodnik korzysta z programu SQL Server Express LocalDB i bazie danych Northwind.

1. Jeśli nie masz programu SQL Server Express LocalDB, zainstaluj go z [stronę pobierania programu SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), lub za pomocą **Instalatora programu Visual Studio**. W **Instalatora programu Visual Studio**, można zainstalować programu SQL Server Express LocalDB, jako część **programowanie aplikacji klasycznych dla platformy .NET** obciążenie, lub jako poszczególnych składników.

2. Instalowanie przykładowej bazy danych Northwind, wykonaj następujące czynności:

    1. W programie Visual Studio, otwórz **Eksplorator obiektów SQL Server** okna. (**Eksplorator obiektów SQL Server** jest instalowany jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio.) Rozwiń **programu SQL Server** węzła. Kliknij prawym przyciskiem myszy w ramach wystąpienia LocalDB, a następnie wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Kopiuj [skryptów języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt języka T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją z danymi.

    3. Wklej skrypt języka T-SQL do edytora zapytań, a następnie wybierz **Execute** przycisku.

       Po pewnym czasie odliczania zapytania i utworzeniu bazy danych Northwind.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Tworzenie biblioteki rozwiązania i klasa n warstwowej do przechowywania zestawu danych (DataEntityTier)
 Pierwszym krokiem w tym instruktażu jest tworzyć rozwiązania i dwa projekty bibliotek klas. Najwyższej klasy biblioteki zawiera zestaw danych (wygenerowany wpisane `DataSet` klasy i DataTable, która przechowuje dane aplikacji). Ten projekt jest używany jako warstwy jednostek danych, aplikacji i zwykle znajduje się w warstwie środkowej. Zestaw danych tworzy początkowego zestawu danych i automatycznie oddziela kod w bibliotekach dwóch klas.

> [!NOTE]
> Pamiętaj poprawnie nazwę projektu i rozwiązania, zanim klikniesz pozycję **OK**. Ten sposób ułatwi służących do przeprowadzenia tego instruktażu.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Aby utworzyć rozwiązanie n warstwowe i biblioteki klas DataEntityTier

1. W programie Visual Studio na **pliku** menu, wybierz opcję **New** > **projektu**.

2. Rozwiń **Visual C#** lub **języka Visual Basic** w okienku po lewej stronie, a następnie zaznacz **pulpitu Windows**.

3. W środkowym okienku wybierz **biblioteki klas** typ projektu.

4. Nadaj projektowi nazwę **DataEntityTier**.

5. Nazwij rozwiązanie **NTierWalkthrough**, a następnie wybierz **OK**.

     Rozwiązanie NTierWalkthrough, który zawiera projekt DataEntityTier zostanie utworzony i dodany do **Eksploratora rozwiązań**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Utwórz bibliotekę klas, aby pomieścić TableAdapters (DataAccessTier)
 Następnym krokiem po utworzeniu projektu DataEntityTier jest Utwórz inny projekt biblioteki klas. Ten projekt zawiera wygenerowanego TableAdapters i nosi nazwę *warstwy dostępu do danych* aplikacji. Warstwa dostępu do danych zawiera informacje, który jest wymagany do połączenia z bazą danych i zazwyczaj znajduje się w warstwie środkowej.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Aby utworzyć bibliotece osobnej klasy dla elementów TableAdapter

1. Kliknij prawym przyciskiem myszy nad rozwiązaniem w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

2. W **nowy projekt** w środkowym okienku wybierz w oknie dialogowym **biblioteki klas**.

3. Nadaj projektowi nazwę **DataAccessTier** i wybierz polecenie **OK**.

     W projekcie DataAccessTier zostanie utworzony i dodany do rozwiązania NTierWalkthrough.

## <a name="create-the-dataset"></a>Tworzenie zestawu danych
 Następnym krokiem jest, aby utworzyć typizowany zestaw danych. Typizowane zestawy danych są tworzone za pomocą klasy zestawu danych (w tym `DataTables` klasy) oraz `TableAdapter` klas w jednym projekcie. (Wszystkie klasy są generowane w jednym pliku). Po oddzieleniu zestawu danych i TableAdapters do różnych projektów, to klasa zestawu danych, która zostanie przeniesiony do innego projektu, pozostawiając `TableAdapter` klas w oryginalnym projekcie. W związku z tym należy utworzyć zestaw danych w projekcie, który ostatecznie będzie zawierać TableAdapters (projekcie DataAccessTier). Tworzenie zestawu danych przy użyciu **Kreatora konfiguracji źródła danych**.

> [!NOTE]
> Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia. Aby uzyskać informacje dotyczące sposobu konfigurowania przykładowej bazy danych Northwind, zobacz [jak: Zainstalować przykładowe bazy danych](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1. Wybierz **DataAccessTier** w **Eksploratora rozwiązań**.

2. Na **danych** menu, wybierz opcję **Pokaż źródła danych**.

   **Źródeł danych** zostanie otwarte okno.

3. W **źródeł danych** wybierz **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.

4. Na **wybierz typ źródła danych** wybierz opcję **bazy danych** , a następnie wybierz **dalej**.

5. Na **wybierz połączenie danych** strony, wykonaj jedną z następujących czynności:

     Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

     —lub—

     Wybierz **nowe połączenie** otworzyć **Dodaj połączenie** okno dialogowe.

6. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.

    > [!NOTE]
    > W przypadku wybrania lokalnego pliku bazy danych (zamiast nawiązywania połączenia z SQL Server) może zostać poproszony, jeśli chcesz dodać plik do projektu. Wybierz **tak** możesz dodać do projektu plik bazy danych.

7. Wybierz **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.

8. Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.

9. Zaznacz pole wyboru dla **klientów** i **zamówienia** tabele, a następnie wybierz **Zakończ**.

     NorthwindDataSet jest dodawany do projektu DataAccessTier i pojawia się w **źródeł danych** okna.

## <a name="separate-the-tableadapters-from-the-dataset"></a>Oddziel elementów TableAdapter z zestawu danych
 Po utworzeniu zestawu danych, należy oddzielić wygenerowaną klasę zestawu danych, od elementów TableAdapter. Możesz to zrobić, ustawiając **projektu DataSet** właściwość na nazwę projektu, w którym będzie przechowywany rozdzielonych się klasy dataset.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Do oddzielania elementów TableAdapter z zestawu danych

1. Kliknij dwukrotnie **NorthwindDataSet.xsd** w **Eksploratora rozwiązań** można otworzyć zestawu danych w **Projektanta obiektów Dataset**.

2. Wybierz pusty obszar w projektancie.

3. Znajdź **projektu DataSet** w węźle **właściwości** okna.

4. W **projektu DataSet** listy wybierz **DataEntityTier**.

5. Na **kompilacji** menu, wybierz opcję **Kompiluj rozwiązanie**.

   Zestaw danych i TableAdapters są podzielone na dwie klasy projekty biblioteki. Projekt, który pierwotnie zawierał całego zestawu danych (`DataAccessTier`) zawiera teraz tylko adapterów TableAdapter. Projekt umieszczoną **projektu DataSet** właściwości (`DataEntityTier`) zawiera typizowany zestaw danych: *NorthwindDataSet.Dataset.Designer.vb* (lub *NorthwindDataSet.Dataset.Designer.cs*).

> [!NOTE]
> Kiedy oddzielisz zestawy danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie zostaną automatycznie przeniesione. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.

## <a name="create-a-new-service-application"></a>Tworzenie nowej aplikacji usługi
W tym instruktażu przedstawiono sposób dostępu do warstwy dostępu do danych przy użyciu usługi WCF, więc Utwórz nową aplikację usługi WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Aby utworzyć nową aplikację usługi WCF

1. Kliknij prawym przyciskiem myszy nad rozwiązaniem w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

2. W **nowy projekt** w okienku po lewej stronie, wybierz w oknie dialogowym **WCF**. W środkowym okienku wybierz **biblioteki usługi WCF**.

3. Nadaj projektowi nazwę **usługi DataService** i wybierz **OK**.

     Projekt usługi danych jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Tworzenie metod w warstwie dostępu do danych, aby zwrócić dane klientów i zamówień
 Usługa danych musi wywołać dwie metody w warstwie dostępu do danych: `GetCustomers` i `GetOrders`. Te metody zwracają Northwind `Customers` i `Orders` tabel. Tworzenie `GetCustomers` i `GetOrders` metody `DataAccessTier` projektu.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabelę Klienci

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **NorthwindDataset.xsd** można otworzyć zestawu danych.

2. Kliknij prawym przyciskiem myszy **CustomersTableAdapter** i kliknij przycisk **Dodaj zapytanie**.

3. Na **wybierz typ polecenia** zostaw wartość domyślną **użyj instrukcji SQL** i kliknij przycisk **dalej**.

4. Na **wybierz typ zapytania** zostaw wartość domyślną **SELECT, która zwraca wiersze** i kliknij przycisk **dalej**.

5. Na **określić instrukcję SQL SELECT** strony, pozostaw zapytanie domyślne i kliknij przycisk **dalej**.

6. Na **Wybierz metody do generowania** wpisz **GetCustomers** dla **nazwę metody** w **róć tabelę DataTable** sekcji.

7. Kliknij przycisk **Zakończ**.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabeli Orders

1. Kliknij prawym przyciskiem myszy **OrdersTableAdapter** i kliknij przycisk **Dodaj zapytanie**.

2. Na **wybierz typ polecenia** zostaw wartość domyślną **użyj instrukcji SQL** i kliknij przycisk **dalej**.

3. Na **wybierz typ zapytania** zostaw wartość domyślną **SELECT, która zwraca wiersze** i kliknij przycisk **dalej**.

4. Na **określić instrukcję SQL SELECT** strony, pozostaw zapytanie domyślne i kliknij przycisk **dalej**.

5. Na **Wybierz metody do generowania** wpisz **GetOrders** dla **nazwę metody** w **róć tabelę DataTable** sekcji.

6. Kliknij przycisk **Zakończ**.

7. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Dodaj odwołanie do jednostki danych i warstwy dostępu do danych do usługi danych
 Ponieważ usługa danych wymaga informacji z zestawu danych i adapterów TableAdapter, należy dodać odwołania do **DataEntityTier** i **DataAccessTier** projektów.

### <a name="to-add-references-to-the-data-service"></a>Aby dodać odwołania do usługi danych

1. Kliknij prawym przyciskiem myszy **usługi DataService** w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj odwołanie**.

2. Kliknij przycisk **projektów** karcie **Dodaj odwołanie** okno dialogowe.

3. Wybierz obie **DataAccessTier** i **DataEntityTier** projektów.

4. Kliknij przycisk **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Dodawanie funkcji do usługi w celu wywołania metody GetCustomers i GetOrders w warstwie dostępu do danych
 Teraz, gdy warstwa dostępu do danych zawiera metody, aby zwrócić dane, tworzyć metody w usłudze danych do wywołania metody w warstwie dostępu do danych.

> [!NOTE]
> Dla projektów C#, należy dodać odwołanie do `System.Data.DataSetExtensions` zestawu dla następujący kod do skompilowania.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Aby utworzyć funkcji GetCustomers i GetOrders usługi danych

1. W **usługi DataService** projektu, kliknij dwukrotnie **IService1.vb** lub **IService1.cs**.

2. Dodaj następujący kod w obszarze **Dodaj tutaj operacje usługi** komentarz:

    ```vb
    <OperationContract()> _
    Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable

    <OperationContract()> _
    Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable
    ```

    ```csharp
    [OperationContract]
    DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers();

    [OperationContract]
    DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders();
    ```

3. W projekcie usługi danych, kliknij dwukrotnie **Service1.vb** (lub **Service1.cs**).

4. Dodaj następujący kod do **Service1** klasy:

    ```vb
    Public Function GetCustomers() As DataEntityTier.NorthwindDataSet.CustomersDataTable Implements IService1.GetCustomers
        Dim CustomersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
        Return CustomersTableAdapter1.GetCustomers()
    End Function

    Public Function GetOrders() As DataEntityTier.NorthwindDataSet.OrdersDataTable Implements IService1.GetOrders
        Dim OrdersTableAdapter1 As New DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
        Return OrdersTableAdapter1.GetOrders()
    End Function
    ```

    ```csharp
    public DataEntityTier.NorthwindDataSet.CustomersDataTable GetCustomers()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter
             CustomersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.CustomersTableAdapter();
        return CustomersTableAdapter1.GetCustomers();
    }
    public DataEntityTier.NorthwindDataSet.OrdersDataTable GetOrders()
    {
        DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter
             OrdersTableAdapter1
            = new DataAccessTier.NorthwindDataSetTableAdapters.OrdersTableAdapter();
        return OrdersTableAdapter1.GetOrders();
    }
    ```

5. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Utwórz warstwę prezentacji, aby wyświetlić dane z usługi danych
 Teraz, gdy rozwiązanie zawiera usługi danych, która ma metody, które wywołują danych dostęp do warstwy, Utwórz innego projektu, który wywołuje usługę danych i prezentować je użytkownikom. W tym przewodniku tworzenie aplikacji Windows Forms; jest to warstwa prezentacji aplikacji n warstwowej.

### <a name="to-create-the-presentation-tier-project"></a>Aby utworzyć projekt warstwy prezentacji

1. Kliknij prawym przyciskiem myszy nad rozwiązaniem w **Eksploratora rozwiązań** i wybierz polecenie **Dodaj** > **nowy projekt**.

2. W **nowy projekt** w okienku po lewej stronie, wybierz w oknie dialogowym **pulpitu Windows**. W środkowym okienku wybierz **Windows Forms App**.

3. Nadaj projektowi nazwę **PresentationTier** i kliknij przycisk **OK**.

    Projekt PresentationTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Ustaw projekt PresentationTier jako projekt startowy
Ustawimy **PresentationTier** projekt jako projekt startowy dla rozwiązania, ponieważ jest aplikacją kliencką rzeczywista, która umożliwia wyświetlanie i wchodzi w interakcję z danymi.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Aby ustawić nowy projekt warstwy prezentacji jako projekt startowy

- W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **PresentationTier** i kliknij przycisk **Ustaw jako projekt startowy**.

## <a name="add-references-to-the-presentation-tier"></a>Dodaj odwołania do warstwy prezentacji
 Aplikacja kliencka PresentationTier wymaga odwołanie do usługi danych usługi, aby uzyskać dostęp do metod w usłudze. Ponadto odwołania do zestawu danych trzeba włączyć udostępnianie przez usługę WCF typu. Do momentu włączenia udostępnianie za pośrednictwem usługi danych typu kodu dodanego do klasy częściowego zestawu danych nie jest dostępna dla warstwy prezentacji. Ponieważ zazwyczaj dodaje się kod, taki jak kod walidacji do wiersza i kolumny zmieniający wydarzenia tabel danych prawdopodobnie należy uzyskać dostęp do tego kodu z klienta.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Można dodać odwołania do warstwy prezentacji

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **PresentationTier** i wybierz **Dodaj odwołanie**.

2. W **Dodaj odwołanie** okno dialogowe, wybierz opcję **projektów** kartę.

3. Wybierz **DataEntityTier** i wybierz polecenie **OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Aby dodać odwołanie do usługi do warstwy prezentacji

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **PresentationTier** i wybierz **Dodaj odwołanie do usługi**.

2. W **Dodaj odwołanie do usługi** okno dialogowe, wybierz opcję **odnajdź**.

3. Wybierz **Service1** i wybierz polecenie **OK**.

    > [!NOTE]
    > Jeśli masz wiele usług na bieżącym komputerze, wybierz usługę, utworzony wcześniej w tym przewodniku (usługa, która zawiera `GetCustomers` i `GetOrders` metody).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Dodaj DataGridViews do formularza w celu wyświetlenia danych zwróconych przez usługę danych
 Po dodaniu odwołania do usługi do usługi danych **źródeł danych** okno zostanie automatycznie wypełniona danych, który jest zwracany przez usługę.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Aby dodać dwa dane powiązane DataGridViews do formularza

1. W **Eksploratora rozwiązań**, wybierz opcję **PresentationTier** projektu.

2. W **źródeł danych** okna, rozwiń węzeł **NorthwindDataSet** i Znajdź **klientów** węzła.

3. Przeciągnij **klientów** węzła na formularz Form1.

4. W **źródeł danych** okna, rozwiń węzeł **klientów** węzła i Znajdź powiązane **zamówienia** węzła ( **zamówienia** węzła zagnieżdżona w  **Klienci** węzła).

5. Przeciągnij powiązane **zamówienia** węzła na formularz Form1.

6. Utwórz `Form1_Load` program obsługi zdarzeń przez dwukrotne kliknięcie pustego obszaru formularza.

7. Dodaj następujący kod do `Form1_Load` programu obsługi zdarzeń.

    ```vb
    Dim DataSvc As New ServiceReference1.Service1Client
    NorthwindDataSet.Customers.Merge(DataSvc.GetCustomers)
    NorthwindDataSet.Orders.Merge(DataSvc.GetOrders)
    ```

    ```csharp
    ServiceReference1.Service1Client DataSvc =
        new ServiceReference1.Service1Client();
    northwindDataSet.Customers.Merge(DataSvc.GetCustomers());
    northwindDataSet.Orders.Merge(DataSvc.GetOrders());
    ```

## <a name="increase-the-maximum-message-size-allowed-by-the-service"></a>Zwiększ maksymalny rozmiar komunikatu dozwolony przez usługę
Wartością domyślną dla `maxReceivedMessageSize` nie jest wystarczająco duży, aby pomieścić dane pobrane z `Customers` i `Orders` tabel. W poniższych krokach będziesz zwiększyć wartość 6553600. Możesz zmienić wartości na komputerze klienckim, który automatycznie aktualizuje odwołanie do usługi.

> [!NOTE]
> Niższe domyślny rozmiar ma na celu ograniczenia narażenia na ataki (DoS). Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Aby zwiększyć wartości maxReceivedMessageSize

1. W **Eksploratora rozwiązań**, kliknij dwukrotnie **app.config** w pliku **PresentationTier** projektu.

2. Znajdź **maxReceivedMessage** rozmiar atrybutu i zmień wartość na `6553600`.

## <a name="test-the-application"></a>Testowanie aplikacji
Uruchom aplikację, naciskając klawisz **F5**. Dane z `Customers` i `Orders` tabele są pobierane z usługi danych i wyświetlane w formularzu.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które warto wykonać po zapisaniu powiązanych danych w aplikacji systemu Windows. Na przykład można wprowadzić następujące ulepszenia do tej aplikacji:

- Dodawanie walidacji do zestawu danych.

- Dodaj dodatkowe metody do usługi w przypadku aktualizowania danych w bazie danych.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami danych w aplikacjach n-warstwowych](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)