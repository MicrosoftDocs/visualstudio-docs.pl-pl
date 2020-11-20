---
title: 'Przewodnik: Tworzenie wielowarstwowej aplikacji danych'
description: W tym instruktażu Utwórz wielowarstwową aplikację do obsługi danych. N-warstwowe aplikacje danych to aplikacje, które uzyskują dostęp do danych i są rozdzielone na wiele warstw logicznych lub warstw.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 76bf07e99f9965e88804c51663bcc37053bf74d6
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998086"
---
# <a name="walkthrough-create-an-n-tier-data-application"></a>Przewodnik: Tworzenie wielowarstwowej aplikacji danych
*N-warstwowe* aplikacje danych to aplikacje, które uzyskują dostęp do danych i są rozdzielone na wiele warstw logicznych lub *warstw*. Oddzielenie składników aplikacji do odrębnych warstw zwiększa łatwość utrzymania i skalowalność aplikacji. Pozwala to na łatwiejsze wdrażanie nowych technologii, które mogą być stosowane do jednej warstwy, bez konieczności ponownego projektowania całego rozwiązania. Architektura N-warstwowa obejmuje warstwę prezentacji, warstwę środkową i warstwę danych. Warstwa środkowa zazwyczaj obejmuje warstwę dostępu do danych, warstwę logiki biznesowej i składniki współużytkowane, takie jak uwierzytelnianie i sprawdzanie poprawności. Warstwa danych obejmuje relacyjną bazę danych. Aplikacje N-warstwowe zwykle przechowują informacje poufne w warstwie dostępu do danych warstwy środkowej, aby zachować izolację od użytkowników końcowych, którzy uzyskują dostęp do warstwy prezentacji. Aby uzyskać więcej informacji, zobacz [Omówienie wielowarstwowych aplikacji do obsługi danych](../data-tools/n-tier-data-applications-overview.md).

Jednym ze sposobów odseparowania różnych warstw w aplikacji n-warstwowej jest utworzenie dyskretnych projektów dla każdej warstwy, która ma zostać dołączona do aplikacji. Typy zestawów danych zawierają `DataSet Project` Właściwość, która określa projekty, do których powinien być generowany wygenerowany zestaw danych i `TableAdapter` kod.

W tym instruktażu przedstawiono sposób rozdzielania zestawu danych i `TableAdapter` kodu do odrębnych projektów biblioteki klas przy użyciu **Projektant obiektów DataSet**. Po oddzieleniu zestawu danych i TableAdapter kodu utworzysz [usługi Windows Communication Foundation i usługi danych programu WCF w usłudze Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) , aby wywoływać do warstwy dostępu do danych. Na koniec utworzysz aplikację Windows Formsową jako warstwę prezentacji. Ta warstwa uzyskuje dostęp do danych z usługi danych.

W tym instruktażu należy wykonać następujące czynności:

- Utwórz nowe rozwiązanie n-warstwowe, które zawiera wiele projektów.

- Dodaj dwa projekty biblioteki klas do rozwiązania n-warstwowego.

- Utwórz typ DataSet za pomocą **Kreatora konfiguracji źródła danych**.

- Oddziel wygenerowany kod [TableAdapters](create-and-configure-tableadapters.md) i DataSet do projektów dyskretnych.

- Utwórz usługę Windows Communication Foundation (WCF) do wywołania do warstwy dostępu do danych.

- Utwórz funkcje w usłudze, aby pobrać dane z warstwy dostępu do danych.

- Utwórz aplikację Windows Forms, która będzie działać jako warstwa prezentacji.

- Utwórz formanty Windows Forms, które są powiązane ze źródłem danych.

- Napisz kod, aby wypełnić tabele danych.

![link do wideo ](../data-tools/media/playvideo.gif) dla wersji wideo tego tematu, zobacz [wideo: jak utworzyć wielowarstwową aplikację do obsługi danych](/previous-versions/visualstudio/visual-studio-2008/cc178916(v=vs.90)).

## <a name="prerequisites"></a>Wymagania wstępne
W tym instruktażu jest stosowana SQL Server Express LocalDB i Przykładowa baza danych Northwind.

1. Jeśli nie masz SQL Server Express LocalDB, zainstaluj go na [stronie pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)lub za pośrednictwem **Instalator programu Visual Studio**. W **Instalator programu Visual Studio** można zainstalować SQL Server Express LocalDB w ramach obciążeń **programistycznych programu .NET Desktop** lub pojedynczego składnika.

2. Zainstaluj przykładową bazę danych Northwind, wykonując następujące kroki:

    1. W programie Visual Studio Otwórz okno **Eksplorator obiektów SQL Server** . (**Eksplorator obiektów SQL Server** jest instalowany jako część obciążenia **magazynu i przetwarzania danych** w Instalator programu Visual Studio). Rozwiń węzeł **SQL Server** . Kliknij prawym przyciskiem myszy wystąpienie LocalDB i wybierz pozycję **nowe zapytanie**.

       Zostanie otwarte okno edytora zapytań.

    2. Skopiuj [skrypt języka Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) do Schowka. Ten skrypt T-SQL tworzy bazę danych Northwind od podstaw i wypełnia ją danymi.

    3. Wklej skrypt T-SQL do edytora zapytań, a następnie wybierz przycisk Execute ( **Wykonaj** ).

       Po krótkim czasie zapytanie kończy działanie i zostanie utworzona baza danych Northwind.

## <a name="create-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Utwórz rozwiązanie n-warstwowe i bibliotekę klas do przechowywania zestawu danych (DataEntityTier)
Pierwszym krokiem tego instruktażu jest utworzenie rozwiązania i dwóch projektów biblioteki klas. Pierwsza Biblioteka klas zawiera zestaw danych (wygenerowanej `DataSet` klasy i tabele danych, które zawierają dane aplikacji). Ten projekt jest używany jako warstwa jednostki danych aplikacji i zwykle znajduje się w warstwie środkowej. Zestaw danych tworzy początkowy zestaw danych i automatycznie oddziela kod do dwóch bibliotek klas.

> [!NOTE]
> Upewnij się, że poprawnie Nadaj nazwę projekt i rozwiązanie, zanim klikniesz przycisk **OK**. Wykonanie tej czynności ułatwi Ci ukończenie tego przewodnika.

### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Aby utworzyć rozwiązanie n-warstwowe i DataEntityTier biblioteki klas

1. W programie Visual Studio w menu **plik** wybierz pozycję **Nowy**  >  **projekt**.

2. Rozwiń pozycję **Visual C#** lub **Visual Basic** w okienku po lewej stronie, a następnie wybierz pozycję **Windows Desktop**.

3. W środkowym okienku wybierz typ projektu **Biblioteka klas** .

4. Nazwij projekt **DataEntityTier**.

5. Nazwij rozwiązanie **NTierWalkthrough**, a następnie wybierz przycisk **OK**.

     NTierWalkthrough rozwiązanie, które zawiera projekt DataEntityTier, jest tworzone i dodawane do **Eksplorator rozwiązań**.

## <a name="create-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Utwórz bibliotekę klas do przechowywania TableAdapters (DataAccessTier)
Następnym krokiem po utworzeniu projektu DataEntityTier jest utworzenie kolejnego projektu biblioteki klas. Ten projekt zawiera wygenerowany TableAdapters i jest nazywany *warstwą dostępu do danych* aplikacji. Warstwa dostępu do danych zawiera informacje wymagane do nawiązania połączenia z bazą danych i zwykle znajdują się w warstwie środkowej.

### <a name="to-create-a-separate-class-library-for-the-tableadapters"></a>Aby utworzyć oddzielną bibliotekę klas dla TableAdapters

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** w środkowym okienku wybierz pozycję **Biblioteka klas**.

3. Nazwij projekt **DataAccessTier** i wybierz **OK**.

     Projekt DataAccessTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="create-the-dataset"></a>Tworzenie zestawu danych
Następnym krokiem jest utworzenie określonego zestawu danych. Typy zestawów danych są tworzone z klasą DataSet (łącznie z `DataTables` klasami) i `TableAdapter` klasami w pojedynczym projekcie. (Wszystkie klasy są generowane w jednym pliku). Po oddzieleniu zestawu danych i TableAdapters do różnych projektów jest to klasa DataSet, która jest przenoszona do innego projektu, pozostawiając `TableAdapter` klasy w oryginalnym projekcie. W związku z tym należy utworzyć zestaw danych w projekcie, który ostatecznie będzie zawierać TableAdapters (projekt DataAccessTier). Zestaw danych można utworzyć za pomocą **Kreatora konfiguracji źródła danych**.

> [!NOTE]
> Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind. Aby uzyskać informacje na temat sposobu konfigurowania przykładowej bazy danych Northwind, zobacz [How to: Install Sample Bases](../data-tools/installing-database-systems-tools-and-samples.md).

### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1. Wybierz **DataAccessTier** w **Eksplorator rozwiązań**.

2. W menu **dane** wybierz pozycję **Pokaż źródła danych**.

   Zostanie otwarte okno **źródła danych** .

3. W oknie **źródła danych** wybierz pozycję **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

4. Na stronie **Wybierz typ źródła danych** wybierz pozycję **baza danych** , a następnie wybierz przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

     Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, wybierz je.

     -lub-

     Wybierz pozycję **nowe połączenie** , aby otworzyć okno dialogowe **Dodawanie połączenia** .

6. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie wybierz **dalej**.

    > [!NOTE]
    > W przypadku wybrania lokalnego pliku bazy danych (zamiast nawiązywania połączenia z usługą SQL Server) może zostać wyświetlony monit o dodanie pliku do projektu. Wybierz pozycję **tak** , aby dodać plik bazy danych do projektu.

7. Na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** wybierz pozycję **dalej** .

8. Rozwiń węzeł **tabele** na stronie **Wybierz obiekty bazy danych** .

9. Zaznacz pola wyboru dla tabel **Customers** i **Orders** , a następnie wybierz pozycję **Zakończ**.

     NorthwindDataSet jest dodawany do projektu DataAccessTier i pojawia się w oknie **źródła danych** .

## <a name="separate-the-tableadapters-from-the-dataset"></a>Oddziel TableAdapters z zestawu danych
Po utworzeniu zestawu danych oddziel klasę wygenerowanego zestawu danych z TableAdapters. W tym celu należy ustawić właściwość **projektu DataSet** na nazwę projektu, w którym ma być przechowywana Klasa rozdzielanego zestawu danych.

### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Aby rozdzielić TableAdapters z zestawu danych

1. Kliknij dwukrotnie pozycję **NorthwindDataSet. xsd** w **Eksplorator rozwiązań** , aby otworzyć zestaw danych w **Projektant obiektów DataSet**.

2. Wybierz pusty obszar w projektancie.

3. Zlokalizuj węzeł **projektu zestawu danych** w oknie **Właściwości** .

4. Na liście **projekt zestawu danych** wybierz pozycję **DataEntityTier**.

5. W menu **kompilacja** wybierz opcję **Kompiluj rozwiązanie**.

   Zestaw danych i TableAdapters są rozdzielone na dwa projekty biblioteki klas. Projekt, który pierwotnie zawierał cały zestaw danych ( `DataAccessTier` ) zawiera teraz tylko TableAdapters. Projekt określony we właściwości **projektu DataSet** ( `DataEntityTier` ) zawiera zestaw danych o określonym typie: *NorthwindDataSet. DataSet. Designer. vb* (lub *NorthwindDataSet.DataSet.Designer.cs*).

> [!NOTE]
> Gdy oddzielasz zestawy danych i TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowe zestawu danych muszą być ręcznie przenoszone do projektu DataSet.

## <a name="create-a-new-service-application"></a>Utwórz nową aplikację usługi
W tym instruktażu pokazano, jak uzyskać dostęp do warstwy dostępu do danych za pomocą usługi WCF, aby utworzyć nową aplikację usługi WCF.

### <a name="to-create-a-new-wcf-service-application"></a>Aby utworzyć nową aplikację usługi WCF

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** w okienku po lewej stronie wybierz pozycję **WCF**. W środkowym okienku wybierz pozycję **Biblioteka usług WCF**.

3. Nadaj nazwę **usłudze** projektu i wybierz **przycisk OK**.

     Projekt usługi danych jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="create-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Utwórz metody w warstwie dostępu do danych, aby zwrócić dane klientów i zamówień
Usługa danych musi wywoływać dwie metody z warstwy dostępu do danych: `GetCustomers` i `GetOrders` . Metody te zwracają Northwind `Customers` i `Orders` tabele. Utwórz `GetCustomers` metody i `GetOrders` w `DataAccessTier` projekcie.

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabelę Customers

1. W **Eksplorator rozwiązań** kliknij dwukrotnie plik **NorthwindDataSet. xsd** , aby otworzyć zestaw danych.

2. Kliknij prawym przyciskiem myszy pozycję **CustomersTableAdapter** , a następnie kliknij pozycję **Dodaj zapytanie**.

3. Na stronie **Wybierz typ polecenia** pozostaw wartość domyślną **instrukcji use SQL** i kliknij przycisk **dalej**.

4. Na stronie **Wybierz typ zapytania** pozostaw wartość domyślną **opcji Select, która zwraca wiersze** , a następnie kliknij przycisk **dalej**.

5. Na stronie **określanie instrukcji SQL SELECT** pozostaw zapytanie domyślne i kliknij przycisk **dalej**.

6. Na stronie **Wybierz metody do wygenerowania** wpisz **GetCustomers** dla **nazwy metody** w sekcji **Return DataTable** .

7. Kliknij przycisk **Finish** (Zakończ).

### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabelę Orders

1. Kliknij prawym przyciskiem myszy pozycję **OrdersTableAdapter** , a następnie kliknij pozycję **Dodaj zapytanie**.

2. Na stronie **Wybierz typ polecenia** pozostaw wartość domyślną **instrukcji use SQL** i kliknij przycisk **dalej**.

3. Na stronie **Wybierz typ zapytania** pozostaw wartość domyślną **opcji Select, która zwraca wiersze** , a następnie kliknij przycisk **dalej**.

4. Na stronie **określanie instrukcji SQL SELECT** pozostaw zapytanie domyślne i kliknij przycisk **dalej**.

5. Na stronie **Wybierz metody do wygenerowania** wpisz **GetOrders** dla **nazwy metody** w sekcji **Return DataTable** .

6. Kliknij przycisk **Finish** (Zakończ).

7. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

## <a name="add-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Dodawanie odwołania do jednostek danych i warstw dostępu do danych do usługi danych
Ponieważ usługa danych wymaga informacji z zestawu danych i TableAdapters, Dodaj odwołania do projektów **DataEntityTier** i **DataAccessTier** .

### <a name="to-add-references-to-the-data-service"></a>Aby dodać odwołania do usługi danych

1. Kliknij prawym przyciskiem myszy pozycję **DataService** w **Eksplorator rozwiązań** a następnie kliknij pozycję **Dodaj odwołanie**.

2. Kliknij kartę **projekty** w oknie dialogowym **Dodaj odwołanie** .

3. Wybierz zarówno projekty **DataAccessTier** , jak i **DataEntityTier** .

4. Kliknij przycisk **OK**.

## <a name="add-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Dodawanie funkcji do usługi w celu wywołania metod GetCustomers i GetOrders w warstwie dostępu do danych
Teraz, gdy warstwa dostępu do danych zawiera metody zwracające dane, należy utworzyć metody w usłudze danych, aby wywoływać metody z warstwy dostępu do danych.

> [!NOTE]
> W przypadku projektów C# należy dodać odwołanie do `System.Data.DataSetExtensions` zestawu dla poniższego kodu do skompilowania.

### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Aby utworzyć funkcje GetCustomers i GetOrders w usłudze danych

1. W projekcie **usługi DataService** kliknij dwukrotnie pozycję **IService1. vb** lub **IService1.cs**.

2. Dodaj następujący kod w komentarzu **Dodaj swoje operacje usługi tutaj** :

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

3. W projekcie usługi DataService kliknij dwukrotnie pozycję **Service1. vb** (lub **Service1.cs**).

4. Dodaj następujący kod do klasy **Service1** :

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

5. W menu **Kompilacja** kliknij pozycję **Kompiluj rozwiązanie**.

## <a name="create-a-presentation-tier-to-display-data-from-the-data-service"></a>Utwórz warstwę prezentacji, aby wyświetlić dane z usługi danych
Teraz, gdy rozwiązanie zawiera usługę danych, która ma metody, które odwołują się do warstwy dostępu do danych, Utwórz inny projekt, który wywołuje usługę danych i zaprezentowania danych użytkownikom. W tym instruktażu Utwórz aplikację Windows Formsową. to jest warstwa prezentacji aplikacji n-warstwowej.

### <a name="to-create-the-presentation-tier-project"></a>Aby utworzyć projekt warstwy prezentacji

1. Kliknij prawym przyciskiem myszy rozwiązanie w **Eksplorator rozwiązań** i wybierz polecenie **Dodaj**  >  **Nowy projekt**.

2. W oknie dialogowym **Nowy projekt** w okienku po lewej stronie wybierz pozycję **pulpit systemu Windows**. W środkowym okienku wybierz pozycję **aplikacja Windows Forms**.

3. Nadaj projektowi nazwę **PresentationTier** i kliknij przycisk **OK**.

    Projekt PresentationTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="set-the-presentationtier-project-as-the-startup-project"></a>Ustaw projekt PresentationTier jako projekt startowy
Ustawimy projekt **PresentationTier** jako projekt startowy rozwiązania, ponieważ jest to rzeczywista aplikacja kliencka, która prezentuje i współdziała z danymi.

### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Aby ustawić nowy projekt warstwy prezentacji jako projekt startowy

- W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **PresentationTier** , a następnie kliknij pozycję **Ustaw jako projekt startowy**.

## <a name="add-references-to-the-presentation-tier"></a>Dodawanie odwołań do warstwy prezentacji
Aplikacja kliencka PresentationTier wymaga odwołania do usługi danych w celu uzyskania dostępu do metod w usłudze. Ponadto odwołanie do zestawu danych jest wymagane do włączenia udostępniania typu przez usługę WCF. Do momentu włączenia udostępniania typu za pomocą usługi danych kod dodany do klasy częściowego zestawu danych nie jest dostępny dla warstwy prezentacji. Ze względu na to, że zwykle dodajesz kod, taki jak kod sprawdzania poprawności do wierszy i kolumn zmiany zdarzeń tabeli danych, prawdopodobnie chcesz uzyskać dostęp do tego kodu z klienta.

### <a name="to-add-a-reference-to-the-presentation-tier"></a>Aby dodać odwołanie do warstwy prezentacji

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **PresentationTier** i wybierz polecenie **Dodaj odwołanie**.

2. W oknie dialogowym **Dodaj odwołanie** wybierz kartę **projekty** .

3. Wybierz pozycję **DataEntityTier** , a następnie wybierz **przycisk OK**.

### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Aby dodać odwołanie do usługi do warstwy prezentacji

1. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **PresentationTier** i wybierz pozycję **Dodaj odwołanie do usługi**.

2. W oknie dialogowym **Dodaj odwołanie do usługi** wybierz pozycję **odkryj**.

3. Wybierz pozycję **Service1** , a następnie wybierz **przycisk OK**.

    > [!NOTE]
    > Jeśli na bieżącym komputerze istnieje wiele usług, wybierz usługę utworzoną wcześniej w tym instruktażu (usługę zawierającą `GetCustomers` `GetOrders` metody i).

## <a name="add-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Dodaj kontrolki DataGridView do formularza, aby wyświetlić dane zwrócone przez usługę danych
Po dodaniu odwołania do usługi do usługi danych okno **źródła danych** zostanie automatycznie wypełnione danymi zwracanymi przez usługę.

### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Aby dodać do formularza dwie powiązane z danymi

1. W **Eksplorator rozwiązań** wybierz projekt **PresentationTier** .

2. W oknie **źródła danych** rozwiń węzeł **NorthwindDataSet** i Znajdź węzeł **Customers** .

3. Przeciągnij węzeł **Customers** na formularz Form1.

4. W oknie **źródła danych** rozwiń węzeł **klienci** i Znajdź węzeł powiązane **zamówienia** (węzeł **zamówienia** zagnieżdżony w węźle **klienci** ).

5. Przeciągnij węzeł **zamówienia** powiązane na formularz Form1.

6. Utwórz `Form1_Load` procedurę obsługi zdarzeń przez dwukrotne kliknięcie pustego obszaru formularza.

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
Wartość domyślna dla `maxReceivedMessageSize` nie jest wystarczająco duża, aby można było przechowywać dane pobierane z `Customers` `Orders` tabel i. W poniższych krokach zwiększy się wartość do 6553600. Należy zmienić wartość na kliencie, która automatycznie aktualizuje odwołanie do usługi.

> [!NOTE]
> Dolny rozmiar domyślny jest przeznaczony do ograniczania narażenia na ataki typu "odmowa usługi" (DoS). Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Aby zwiększyć wartość maxReceivedMessageSize

1. W **Eksplorator rozwiązań** kliknij dwukrotnie plik **app.config** w projekcie **PresentationTier** .

2. Znajdź atrybut **maxReceivedMessage** size i zmień wartość na `6553600` .

## <a name="test-the-application"></a>Testowanie aplikacji
Uruchom aplikację, naciskając klawisz **F5**. Dane z `Customers` `Orders` tabel i są pobierane z usługi danych i wyświetlane w formularzu.

## <a name="next-steps"></a>Następne kroki
W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po zapisaniu powiązanych danych w aplikacji opartej na systemie Windows. Można na przykład wprowadzić następujące ulepszenia dla tej aplikacji:

- Dodawanie walidacji do zestawu danych.

- Dodaj kolejne metody do usługi w celu zaktualizowania danych z powrotem do bazy danych.

## <a name="see-also"></a>Zobacz także

- [Praca z zestawami danych w aplikacjach n-warstwowych](../data-tools/work-with-datasets-in-n-tier-applications.md)
- [Aktualizacja hierarchiczna](../data-tools/hierarchical-update.md)
- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
