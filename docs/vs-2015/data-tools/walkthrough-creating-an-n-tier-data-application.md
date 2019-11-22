---
title: 'Przewodnik: Tworzenie wielowarstwowej aplikacji do obsługi danych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, creating
- n-tier applications, walkthroughs
ms.assetid: d15e4d31-2839-48d9-9e0e-2e73404d82a2
caps.latest.revision: 51
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bd77006eda03b716e3c54c0b5b52ac633a383377
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299587"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Wskazówki: tworzenie aplikacji warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N-warstwowa * aplikacje danych to aplikacje, które uzyskują dostęp do danych i są rozdzielone na wiele warstw logicznych lub *warstw*. Oddzielenie składników aplikacji do odrębnych warstw zwiększa łatwość utrzymania i skalowalność aplikacji. Pozwala to na łatwiejsze wdrażanie nowych technologii, które mogą być stosowane do jednej warstwy, bez konieczności ponownego projektowania całego rozwiązania. Architektura N-warstwowa obejmuje warstwę prezentacji, warstwę środkową i warstwę danych. Warstwa środkowa zazwyczaj obejmuje warstwę dostępu do danych, warstwę logiki biznesowej i składniki współużytkowane, takie jak uwierzytelnianie i sprawdzanie poprawności. Warstwa danych obejmuje relacyjną bazę danych. Aplikacje N-warstwowe zwykle przechowują informacje poufne w warstwie dostępu do danych warstwy środkowej, aby zachować izolację od użytkowników końcowych, którzy uzyskują dostęp do warstwy prezentacji. Aby uzyskać więcej informacji, zobacz [Omówienie wielowarstwowych aplikacji do obsługi danych](../data-tools/n-tier-data-applications-overview.md).

 Jednym ze sposobów odseparowania różnych warstw w aplikacji n-warstwowej jest utworzenie dyskretnych projektów dla każdej warstwy, która ma zostać dołączona do aplikacji. Typy zestawów danych zawierają Właściwość `DataSet Project`, która określa projekty, do których mają zostać wygenerowane zestawy danych i `TableAdapter`.

 W tym instruktażu przedstawiono sposób rozdzielania zestawu danych i kodu `TableAdapter` na osobne projekty bibliotek klas przy użyciu **Projektant obiektów DataSet**. Po oddzieleniu zestawu danych i TableAdapter kodu utworzysz usługi [Windows Communication Foundation i usługi danych programu WCF w usłudze Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) , aby wywoływać do warstwy dostępu do danych. Na koniec utworzysz aplikację Windows Formsową jako warstwę prezentacji. Ta warstwa uzyskuje dostęp do danych z usługi danych.

 W tym instruktażu wykonasz następujące czynności:

- Utwórz nowe rozwiązanie n-warstwowe, które będzie zawierać wiele projektów.

- Dodaj dwa projekty biblioteki klas do rozwiązania n-warstwowego.

- Utwórz typ DataSet za pomocą **Kreatora konfiguracji źródła danych**.

- Oddziel wygenerowany kod [TableAdapters](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) i DataSet do projektów dyskretnych.

- Utwórz usługę Windows Communication Foundation (WCF) do wywołania do warstwy dostępu do danych.

- Utwórz funkcje w usłudze, aby pobrać dane z warstwy dostępu do danych.

- Utwórz aplikację Windows Forms, która będzie działać jako warstwa prezentacji.

- Utwórz formanty Windows Forms, które są powiązane ze źródłem danych.

- Napisz kod, aby wypełnić tabele danych.

  ![link do wideo](../data-tools/media/playvideo.gif "PlayVideo") Aby uzyskać wersję wideo tego tematu, zobacz [wideo How to: Tworzenie wielowarstwowej aplikacji do obsługi danych](https://go.microsoft.com/fwlink/?LinkId=115188).

## <a name="prerequisites"></a>Wymagania wstępne
 Aby ukończyć ten przewodnik, potrzebne są:

- Dostęp do przykładowej bazy danych Northwind.

## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Tworzenie rozwiązania N-warstwowego i biblioteki klas do przechowywania zestawu danych (DataEntityTier)
 Pierwszym krokiem tego instruktażu jest utworzenie rozwiązania i dwóch projektów biblioteki klas. Pierwsza Biblioteka klas będzie przechowywać zestaw danych (klasy wygenerowanego zestawu danych i tabel danych, w których będą przechowywane dane aplikacji). Ten projekt jest używany jako warstwa jednostki danych aplikacji i zwykle znajduje się w warstwie środkowej. Projektant obiektów Dataset jest używany do tworzenia początkowego zestawu danych i automatycznego rozdzielenia kodu do dwóch bibliotek klas.

> [!NOTE]
> Upewnij się, że poprawnie Nadaj nazwę projekt i rozwiązanie, zanim klikniesz przycisk **OK**. Wykonanie tej czynności ułatwi Ci ukończenie tego przewodnika.

#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Aby utworzyć rozwiązanie n-warstwowe i DataEntityTier biblioteki klas

1. Z menu **plik** Utwórz nowy projekt.

    > [!NOTE]
    > **Projektant obiektów DataSet** jest obsługiwana w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i C# projektach. Utwórz nowy projekt w jednym z tych języków.

2. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** kliknij pozycję **Windows**.

3. Kliknij szablon **Biblioteka klas** .

4. Nazwij projekt **DataEntityTier**.

5. Nazwij rozwiązanie **NTierWalkthrough**.

6. Kliknij przycisk **OK**.

     NTierWalkthrough rozwiązanie, które zawiera projekt DataEntityTier, jest tworzone i dodawane do **Eksplorator rozwiązań**.

## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Tworzenie biblioteki klas do przechowywania TableAdapters (DataAccessTier)
 Następnym krokiem po utworzeniu projektu DataEntityTier jest utworzenie kolejnego projektu biblioteki klas. Ten projekt będzie przechowywać wygenerowany `TableAdapter`s i jest nazywany *warstwą dostępu do danych* aplikacji. Warstwa dostępu do danych zawiera informacje wymagane do nawiązania połączenia z bazą danych i zwykle znajdują się w warstwie środkowej.

#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Aby utworzyć nową bibliotekę klas dla TableAdapters

1. Z menu **plik** Dodaj nowy projekt do rozwiązania NTierWalkthrough.

2. W oknie dialogowym **Nowy projekt** w okienku **Szablony** kliknij pozycję **Biblioteka klas**.

3. Nadaj projektowi nazwę **DataAccessTier** i kliknij przycisk **OK**.

     Projekt DataAccessTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="creating-the-dataset"></a>Tworzenie zestawu danych
 Następnym krokiem jest utworzenie określonego zestawu danych. Typy zestawów danych są tworzone z klasą DataSet (łącznie z klasami DataTables) i klasami `TableAdapter` w pojedynczym projekcie. (Wszystkie klasy są generowane w jednym pliku). Po oddzieleniu zestawu danych i `TableAdapter`do różnych projektów jest to Klasa zestawu danych, która jest przenoszona do innego projektu, pozostawiając klasy `TableAdapter` w oryginalnym projekcie. W związku z tym należy utworzyć zestaw danych w projekcie, który ostatecznie będzie zawierać `TableAdapter`s (projekt DataAccessTier). Zestaw danych zostanie utworzony za pomocą **Kreatora konfiguracji źródła danych**.

> [!NOTE]
> Aby utworzyć połączenie, musisz mieć dostęp do przykładowej bazy danych Northwind.

#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych

1. Kliknij pozycję DataAccessTier w **Eksplorator rozwiązań**.

2. Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.

3. W oknie **źródła danych** kliknij przycisk **Dodaj nowe źródło danych** , aby uruchomić **Kreatora konfiguracji źródła danych**.

4. Na stronie **Wybierz typ źródła danych** kliknij pozycję **baza danych** , a następnie kliknij przycisk **dalej**.

5. Na stronie **Wybierz połączenie danych** wykonaj jedną z następujących czynności:

     Jeśli połączenie danych z przykładową bazą danych Northwind jest dostępne na liście rozwijanej, kliknij ją.

     —lub—

     Kliknij pozycję **nowe połączenie** , aby otworzyć okno dialogowe **Dodawanie połączenia** .

6. Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.

    > [!NOTE]
    > W przypadku wybrania lokalnego pliku bazy danych (zamiast nawiązywania połączenia z usługą SQL Server) może zostać wyświetlony monit o dodanie pliku do projektu. Kliknij przycisk **tak** , aby dodać plik bazy danych do projektu.

7. Kliknij przycisk **dalej** na stronie **Zapisz parametry połączenia do pliku konfiguracji aplikacji** .

8. Rozwiń węzeł **tabele** na stronie **Wybierz obiekty bazy danych** .

9. Kliknij pola wyboru dla tabel **Customers** i **Orders** , a następnie kliknij przycisk **Zakończ**.

     NorthwindDataSet jest dodawany do projektu DataAccessTier i pojawia się w oknie **źródła danych** .

## <a name="separating-the-tableadapters-from-the-dataset"></a>Rozdzielenie TableAdapters z zestawu danych
 Po utworzeniu zestawu danych oddziel klasę wygenerowanego zestawu danych z TableAdapters. W tym celu należy ustawić właściwość **projektu DataSet** na nazwę projektu, w którym ma być przechowywana Klasa rozdzielanego zestawu danych.

#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Aby rozdzielić TableAdapters z zestawu danych

1. Kliknij dwukrotnie pozycję **NorthwindDataSet. xsd** w **Eksplorator rozwiązań** , aby otworzyć zestaw danych w **Projektant obiektów DataSet**.

2. Kliknij pusty obszar w projektancie.

3. Zlokalizuj węzeł **projektu zestawu danych** w oknie **Właściwości** .

4. Na liście **projekt zestawu danych** kliknij pozycję **DataEntityTier**.

5. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

   Zestaw danych i TableAdapters są rozdzielone na dwa projekty biblioteki klas. Projekt, który pierwotnie zawierał cały zestaw danych (DataAccessTier), zawiera teraz tylko TableAdapters. Projekt określony we właściwości **projektu DataSet** (DataEntityTier) zawiera zestaw danych o określonym typie: NorthwindDataSet. DataSet. Designer. vb (lub NorthwindDataSet.DataSet.Designer.cs).

> [!NOTE]
> Gdy oddzielasz zestawy danych i TableAdapters (ustawiając właściwość **projektu DataSet** ), istniejące częściowe klasy zestawu danych w projekcie nie będą przenoszone automatycznie. Istniejące klasy częściowe zestawu danych muszą być ręcznie przenoszone do projektu DataSet.

## <a name="creating-a-new-service-application"></a>Tworzenie nowej aplikacji usługi
 Ponieważ w tym instruktażu pokazano, jak uzyskać dostęp do warstwy dostępu do danych za pomocą usługi WCF, Utwórz nową aplikację usługi WCF.

#### <a name="to-create-a-new-wcf-service-application"></a>Aby utworzyć nową aplikację usługi WCF

1. Z menu **plik** Dodaj nowy projekt do rozwiązania NTierWalkthrough.

2. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** kliknij pozycję **WCF**. W okienku **Szablony** kliknij pozycję **Biblioteka usług WCF**.

3. Nadaj nazwę **usłudze** dataproject, a następnie kliknij przycisk **OK**.

     Projekt usługi danych jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Tworzenie metod w warstwie dostępu do danych w celu zwrócenia danych dotyczących klientów i zamówień
 Usługa danych musi wywoływać dwie metody w warstwie dostępu do danych: GetCustomers i GetOrders. Te metody zwracają tabele Customers i Orders firmy Northwind. Utwórz metody GetCustomers i GetOrders w projekcie DataAccessTier.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabelę Customers

1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik NorthwindDataSet. xsd, aby otworzyć zestaw danych w Projektant obiektów DataSet.

2. Kliknij prawym przyciskiem myszy pozycję CustomersTableAdapter, a następnie kliknij pozycję **Dodaj zapytanie** , aby edytować TableAdapter.

3. Na stronie **Wybierz typ polecenia** pozostaw wartość domyślną **instrukcji use SQL** i kliknij przycisk **dalej**.

4. Na stronie **Wybierz typ zapytania** pozostaw wartość domyślną **opcji Select, która zwraca wiersze** , a następnie kliknij przycisk **dalej**.

5. Na stronie **określanie instrukcji SQL SELECT** pozostaw zapytanie domyślne i kliknij przycisk **dalej**.

6. Na stronie **Wybierz metody do wygenerowania** wpisz **GetCustomers** dla **nazwy metody** w sekcji **Return DataTable** .

7. Kliknij przycisk **Zakończ**.

#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabelę Orders

1. Kliknij prawym przyciskiem myszy pozycję OrdersTableAdapter, a następnie kliknij pozycję **Dodaj zapytanie**.

2. Na stronie **Wybierz typ polecenia** pozostaw wartość domyślną **instrukcji use SQL** i kliknij przycisk **dalej**.

3. Na stronie **Wybierz typ zapytania** pozostaw wartość domyślną **opcji Select, która zwraca wiersze** , a następnie kliknij przycisk **dalej**.

4. Na stronie **określanie instrukcji SQL SELECT** pozostaw zapytanie domyślne i kliknij przycisk **dalej**.

5. Na stronie **Wybierz metody do wygenerowania** wpisz **GetOrders** dla **nazwy metody** w sekcji **Return DataTable** .

6. Kliknij przycisk **Zakończ**.

7. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Dodawanie odwołania do jednostek danych i warstw dostępu do danych do usługi danych
 Ponieważ usługa danych wymaga informacji z zestawu danych i TableAdapters, Dodaj odwołania do projektów DataEntityTier i DataAccessTier.

#### <a name="to-add-references-to-the-data-service"></a>Aby dodać odwołania do usługi danych

1. Kliknij prawym przyciskiem myszy pozycję DataService w **Eksplorator rozwiązań** a następnie kliknij pozycję **Dodaj odwołanie**.

2. Kliknij kartę **projekty** w oknie dialogowym **Dodaj odwołanie** .

3. Wybierz zarówno projekty **DataAccessTier** , jak i **DataEntityTier** .

4. Kliknij przycisk **OK**.

## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Dodawanie funkcji do usługi w celu wywołania metod GetCustomers i GetOrders w warstwie dostępu do danych
 Teraz, gdy warstwa dostępu do danych zawiera metody zwracające dane, należy utworzyć metody w usłudze danych, aby wywoływać metody z warstwy dostępu do danych.

> [!NOTE]
> W C# przypadku projektów należy dodać odwołanie do zestawu `System.Data.DataSetExtensions` dla następującego kodu do skompilowania.

#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Aby utworzyć funkcje GetCustomers i GetOrders w usłudze danych

1. W projekcie **usługi DataService** kliknij dwukrotnie pozycję IService1. vb lub IService1.cs.

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

3. W projekcie usługi DataService kliknij dwukrotnie pozycję Service1. vb (lub Service1.cs).

4. Dodaj następujący kod do klasy Service1:

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

## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Tworzenie warstwy prezentacji do wyświetlania danych z usługi danych
 Teraz, gdy rozwiązanie zawiera usługę danych, która ma metody, które wywołują do warstwy dostępu do danych, należy utworzyć kolejny projekt, który będzie wywoływał usługę danych i przedstawić dane użytkownikom. W tym instruktażu Utwórz aplikację Windows Formsową. to jest warstwa prezentacji aplikacji n-warstwowej.

#### <a name="to-create-the-presentation-tier-project"></a>Aby utworzyć projekt warstwy prezentacji

1. Z menu **plik** Dodaj nowy projekt do rozwiązania NTierWalkthrough.

2. W oknie dialogowym **Nowy projekt** w okienku **typy projektów** kliknij pozycję **Windows**. W okienku **Szablony** kliknij pozycję **Windows Forms aplikacji**.

3. Nadaj projektowi nazwę **PresentationTier** i kliknij przycisk **OK**.

4. Projekt PresentationTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.

## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Ustawianie projektu PresentationTier jako projektu startowego
 Ponieważ warstwa prezentacji to rzeczywista aplikacja kliencka, która jest używana do prezentowania i współdziałania z danymi, należy ustawić projekt PresentationTier jako projekt startowy.

#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Aby ustawić nowy projekt warstwy prezentacji jako projekt startowy

- W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **PresentationTier** , a następnie kliknij pozycję **Ustaw jako projekt startowy**.

## <a name="adding-references-to-the-presentation-tier"></a>Dodawanie odwołań do warstwy prezentacji
 Aplikacja kliencka PresentationTier wymaga odwołania do usługi danych w celu uzyskania dostępu do metod w usłudze. Ponadto odwołanie do zestawu danych jest wymagane do włączenia udostępniania typu przez usługę WCF. Do momentu włączenia udostępniania typu za pomocą usługi danych kod dodany do klasy częściowego zestawu danych nie będzie dostępny dla warstwy prezentacji. Ponieważ zazwyczaj dodajesz kod, taki jak Walidacja, do wierszy i kolumn zmiany zdarzeń tabeli danych, prawdopodobnie chcesz uzyskać dostęp do tego kodu z klienta.

#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Aby dodać odwołanie do warstwy prezentacji

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję PresentationTier, a następnie kliknij pozycję **Dodaj odwołanie**.

2. W oknie dialogowym **Dodawanie odwołania** kliknij kartę **projekty** .

3. Wybierz pozycję **DataEntityTier** , a następnie kliknij przycisk **OK**.

#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Aby dodać odwołanie do usługi do warstwy prezentacji

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję PresentationTier, a następnie kliknij pozycję **Dodaj odwołanie do usługi**.

2. W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odkryj**.

3. Wybierz pozycję **Service1** , a następnie kliknij przycisk **OK**.

    > [!NOTE]
    > Jeśli na bieżącym komputerze istnieje wiele usług, wybierz usługę utworzoną wcześniej w tym instruktażu (usługę zawierającą metody GetCustomers i GetOrders).

## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Dodawanie kontrolek DataGridView do formularza w celu wyświetlenia danych zwróconych przez usługę danych
 Po dodaniu odwołania do usługi do usługi danych okno **źródła danych** zostanie automatycznie wypełnione danymi zwracanymi przez usługę.

#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Aby dodać do formularza dwie powiązane z danymi

1. W **Eksplorator rozwiązań**wybierz projekt PresentationTier.

2. W oknie **źródła danych** rozwiń węzeł **NorthwindDataSet** i Znajdź węzeł **Customers** .

3. Przeciągnij węzeł **Customers** na formularz Form1.

4. W oknie **źródła danych** rozwiń węzeł **klienci** i Znajdź węzeł powiązane **zamówienia** (węzeł **zamówienia** zagnieżdżony w węźle **klienci** ).

5. Przeciągnij węzeł **zamówienia** powiązane na formularz Form1.

6. Utwórz procedurę obsługi zdarzeń `Form1_Load` przez dwukrotne kliknięcie pustego obszaru formularza.

7. Dodaj następujący kod do programu obsługi zdarzeń `Form1_Load`.

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

## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Zwiększenie maksymalnego rozmiaru wiadomości dozwolonego przez usługę
 Ponieważ usługa zwraca dane z tabel klienci i zamówienia, wartość domyślna parametru maxReceivedMessageSize nie jest wystarczająco duża, aby można było przechowywać dane i musi być zwiększona. W tym instruktażu zmienisz wartość na 6553600. Wartość zostanie zmieniona na kliencie. spowoduje to automatyczne zaktualizowanie odwołania do usługi.

> [!NOTE]
> Dolny rozmiar domyślny jest przeznaczony do ograniczania narażenia na ataki typu "odmowa usługi" (DoS). Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.

#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Aby zwiększyć wartość maxReceivedMessageSize

1. W **Eksplorator rozwiązań**kliknij dwukrotnie plik App. config w projekcie PresentationTier.

2. Znajdź atrybut **maxReceivedMessage** size i zmień wartość na `6553600`.

## <a name="testing-the-application"></a>Testowanie aplikacji
 Uruchom aplikację. Dane są pobierane z usługi danych i wyświetlane w formularzu.

#### <a name="to-test-the-application"></a>Aby przetestować aplikację

1. Naciśnij F5.

2. Dane z tabel Customers i Orders są pobierane z usługi danych i wyświetlane w formularzu.

## <a name="next-steps"></a>Następne kroki
 W zależności od wymagań aplikacji istnieje kilka kroków, które można wykonać po zapisaniu powiązanych danych w aplikacji opartej na systemie Windows. Można na przykład wprowadzić następujące ulepszenia dla tej aplikacji:

- Dodawanie walidacji do zestawu danych. Aby uzyskać więcej informacji, zobacz [Przewodnik: Dodawanie walidacji do wielowarstwowej aplikacji danych](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).

- Dodaj kolejne metody do usługi w celu zaktualizowania danych z powrotem do bazy danych.

## <a name="see-also"></a>Zobacz też
 [Współpraca z zestawami danych w aplikacjach n-warstwowych —](../data-tools/work-with-datasets-in-n-tier-applications.md) [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md) [dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
