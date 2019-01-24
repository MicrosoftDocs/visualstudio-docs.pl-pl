---
title: 'Przewodnik: Tworzenie aplikacji N-warstwowa danych | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f3185a6b7ebe4f5f37428e04f1b4215431921c51
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54769682"
---
# <a name="walkthrough-creating-an-n-tier-data-application"></a>Przewodnik: Tworzenie aplikacji warstwowych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
N-warstwy * dane aplikacji są aplikacjom dostęp do danych i są rozdzielone na wiele warstw logiczne, lub *warstwy*. Rozdzielanie składników aplikacji na dyskretne warstwy, łatwość konserwacji i zwiększa skalowalność aplikacji. Dzieje się tak, należy włączyć ułatwia przyjęcie nowych technologii, które mogą być stosowane do poszczególnych warstw, bez konieczności zmiany projektu całego rozwiązania. Architektura N-warstwowa zawiera warstwę prezentacji, warstwy środkowej i warstwy danych. Warstwa środkowa zazwyczaj zawiera warstwy dostępu do danych, warstwy logiki biznesowej i składniki współużytkowane, takie jak uwierzytelnianie i sprawdzania poprawności. Warstwa danych obejmuje relacyjnej bazy danych. N-warstwowych zazwyczaj przechowują wrażliwe informacje w warstwę dostępu do danych w warstwie środkowej do obsługi izolacji użytkowników końcowych, którzy uzyskują dostęp warstwy prezentacji. Aby uzyskać więcej informacji, zobacz [N-warstwowa danych aplikacji — omówienie](../data-tools/n-tier-data-applications-overview.md).  
  
 Pierwszym sposobem rozdzielenia różnych warstw w n warstwowej aplikacji jest utworzenie dyskretnych projektów dla każdej warstwy, które mają zostać uwzględnione w aplikacji. Typizowanych elementów DataSet zawiera `DataSet Project` właściwość określający, które projekty wygenerowanego zestawu danych i `TableAdapter` kodu, należy przejść do.  
  
 W tym instruktażu pokazano, jak rozdzielić zestawu danych i `TableAdapter` kod do klasy dyskretne projekty biblioteki za pomocą **Projektanta obiektów Dataset**. Po oddzielisz zestawu danych i kod TableAdapter utworzy [Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md) usługi do wywołania w warstwie dostępu do danych. Na koniec utworzysz aplikację Windows Forms jako Warstwa prezentacji. Ta warstwa uzyskuje dostęp do danych z usługi danych.  
  
 Z tego instruktażu wykonasz następujące czynności:  
  
- Utwórz nowe rozwiązanie n warstwowej, który będzie zawierać wiele projektów.  
  
- Dodaj dwa projekty bibliotek klas do rozwiązania n warstwowej.  
  
- Tworzenie typizowanego zestawu danych za pomocą **Kreatora konfiguracji źródła danych**.  
  
- Oddziel wygenerowany [TableAdapters](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) i kod zestawu danych w dyskretne projekty.  
  
- Tworzenie usługi Windows Communication Foundation (WCF) do wywołania w warstwie dostępu do danych.  
  
- Tworzenie funkcji w usłudze w celu pobierania danych z warstwy dostępu do danych.  
  
- Tworzenie aplikacji Windows Forms jako Warstwa prezentacji.  
  
- Tworzenie formantów formularzy Windows, które są powiązane ze źródłem danych.  
  
- Pisz kod, aby wypełnić tabele danych.  
  
  ![Link do wideo](../data-tools/media/playvideo.gif "PlayVideo") wersja wideo tego tematu, zobacz [poradnik wideo: Tworzenie aplikacji N-warstwowa danych](http://go.microsoft.com/fwlink/?LinkId=115188).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Aby ukończyć ten przewodnik, potrzebne są:  
  
-   Dostęp do przykładowej bazy danych Northwind.
  
## <a name="creating-the-n-tier-solution-and-class-library-to-hold-the-dataset-dataentitytier"></a>Tworzenie rozwiązanie N-warstwowe i biblioteki klas, aby pomieścić zestawu danych (DataEntityTier)  
 Pierwszym krokiem w tym instruktażu jest tworzyć rozwiązania i dwa projekty bibliotek klas. Najwyższej klasy biblioteki będzie przechowywać zestawu danych (wygenerowany wpisanych klasy DataSet i DataTable, który będzie przechowywać dane aplikacji). Ten projekt jest używany jako warstwy jednostek danych, aplikacji i zwykle znajduje się w warstwie środkowej. Projektanta obiektów Dataset służy do tworzenia początkowego zestawu danych i automatycznie odseparowania kodu w bibliotekach klas dwa.  
  
> [!NOTE]
>  Pamiętaj poprawnie nazwę projektu i rozwiązania, zanim klikniesz pozycję **OK**. Ten sposób ułatwi służących do przeprowadzenia tego instruktażu.  
  
#### <a name="to-create-the-n-tier-solution-and-dataentitytier-class-library"></a>Aby utworzyć rozwiązanie n warstwowe i biblioteki klas DataEntityTier  
  
1.  Z **pliku** menu, Utwórz nowy projekt.  
  
    > [!NOTE]
    >  **Projektanta obiektów Dataset** jest obsługiwana w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] i projektów języka C#. Utwórz nowy projekt w jednym z tych języków.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienku kliknij **Windows**.  
  
3.  Kliknij przycisk **biblioteki klas** szablonu.  
  
4.  Nadaj projektowi nazwę **DataEntityTier**.  
  
5.  Nazwij rozwiązanie **NTierWalkthrough**.  
  
6.  Kliknij przycisk **OK**.  
  
     Rozwiązanie NTierWalkthrough, który zawiera projekt DataEntityTier zostanie utworzony i dodany do **Eksploratora rozwiązań**.  
  
## <a name="creating-the-class-library-to-hold-the-tableadapters-dataaccesstier"></a>Tworzenie biblioteki klas na potrzeby przechowywania TableAdapters (DataAccessTier)  
 Następnym krokiem po utworzeniu projektu DataEntityTier jest Utwórz inny projekt biblioteki klas. Ten projekt będzie przechowywać wygenerowany `TableAdapter`s i nosi nazwę *warstwy dostępu do danych* aplikacji. Warstwa dostępu do danych zawiera informacje, który jest wymagany do połączenia z bazą danych i zazwyczaj znajduje się w warstwie środkowej.  
  
#### <a name="to-create-the-new-class-library-for-the-tableadapters"></a>Aby utworzyć nową bibliotekę klas dla elementów TableAdapter  
  
1.  Z **pliku** menu Dodaj nowy projekt do rozwiązania NTierWalkthrough.  
  
2.  W **nowy projekt** dialogowym **szablony** okienku kliknij **biblioteki klas**.  
  
3.  Nadaj projektowi nazwę **DataAccessTier** i kliknij przycisk **OK**.  
  
     W projekcie DataAccessTier zostanie utworzony i dodany do rozwiązania NTierWalkthrough.  
  
## <a name="creating-the-dataset"></a>Tworzenie zestawu danych  
 Następnym krokiem jest, aby utworzyć typizowany zestaw danych. Typizowane zestawy danych są tworzone przy użyciu zarówno klasy zestawu danych (w tym klasy DataTable) i `TableAdapter` klas w jednym projekcie. (Wszystkie klasy są generowane w jednym pliku). Kiedy oddzielisz zestawu danych i `TableAdapter`s do różnych projektów, to klasa zestawu danych, która zostanie przeniesiony do innego projektu, pozostawiając `TableAdapter` klas w oryginalnym projekcie. W związku z tym, należy utworzyć zestaw danych w projekcie, który ostatecznie będzie zawierać `TableAdapter`s (projekcie DataAccessTier). Utworzysz zestaw danych za pomocą **Kreatora konfiguracji źródła danych**.  
  
> [!NOTE]
> Musi mieć dostęp do przykładowej bazy danych Northwind do utworzenia połączenia.
  
#### <a name="to-create-the-dataset"></a>Aby utworzyć zestaw danych  
  
1.  Kliknij przycisk DataAccessTier w **Eksploratora rozwiązań**.  
  
2.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
3.  W **źródeł danych** okna, kliknij przycisk **Dodaj nowe źródło danych** można uruchomić **Kreatora konfiguracji źródła danych**.  
  
4.  Na **wybierz typ źródła danych** kliknij **bazy danych** a następnie kliknij przycisk **dalej**.  
  
5.  Na **wybierz połączenie danych** strony, wykonaj jedną z następujących czynności:  
  
     Jeśli połączenie danych z przykładowej bazy danych Northwind jest dostępne na liście rozwijanej, kliknij go.  
  
     —lub—  
  
     Kliknij przycisk **nowe połączenie** otworzyć **Dodaj połączenie** okno dialogowe.  
  
6.  Jeśli baza danych wymaga hasła, wybierz opcję dołączenia danych poufnych, a następnie kliknij przycisk **dalej**.  
  
    > [!NOTE]
    >  W przypadku wybrania lokalnego pliku bazy danych (zamiast nawiązywania połączenia z SQL Server) może zostać poproszony, jeśli chcesz dodać plik do projektu. Kliknij przycisk **tak** możesz dodać do projektu plik bazy danych.  
  
7.  Kliknij przycisk **dalej** na **Zapisz parametry połączenia do pliku konfiguracji aplikacji** strony.  
  
8.  Rozwiń **tabel** węzeł **wybierz obiekty bazy danych** strony.  
  
9. Kliknij pola wyboru dla **klientów** i **zamówienia** tabel, a następnie kliknij **Zakończ**.  
  
     NorthwindDataSet jest dodawany do projektu DataAccessTier i pojawia się w **źródeł danych** okna.  
  
## <a name="separating-the-tableadapters-from-the-dataset"></a>Oddzielanie elementów TableAdapter z zestawu danych  
 Po utworzeniu zestawu danych, należy oddzielić wygenerowaną klasę zestawu danych, od elementów TableAdapter. Możesz to zrobić, ustawiając **projektu DataSet** właściwość na nazwę projektu, w którym będzie przechowywany rozdzielonych się klasy dataset.  
  
#### <a name="to-separate-the-tableadapters-from-the-dataset"></a>Do oddzielania elementów TableAdapter z zestawu danych  
  
1. Kliknij dwukrotnie **NorthwindDataSet.xsd** w **Eksploratora rozwiązań** można otworzyć zestawu danych w **Projektanta obiektów Dataset**.  
  
2. Kliknij pusty obszar w projektancie.  
  
3. Znajdź **projektu DataSet** w węźle **właściwości** okna.  
  
4. W **projektu DataSet** kliknij **DataEntityTier**.  
  
5. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
   Zestaw danych i TableAdapters są podzielone na dwie klasy projekty biblioteki. Projekt, który pierwotnie zawierał teraz całego zestawu danych (DataAccessTier) zawiera tylko adapterów TableAdapter. Projekt umieszczoną **projektu DataSet** właściwość (DataEntityTier) zawiera typizowany zestaw danych: NorthwindDataSet.Dataset.Designer.vb (lub NorthwindDataSet.Dataset.Designer.cs).  
  
> [!NOTE]
>  Kiedy oddzielisz zestawy danych i TableAdapters (przez ustawienie **projektu DataSet** właściwości), istniejące częściowe klasy zestawu danych w projekcie nie zostaną automatycznie przeniesione. Istniejące klasy częściowego zestawu danych należy przenieść ręcznie do projektu zestawu danych.  
  
## <a name="creating-a-new-service-application"></a>Tworzenie nowej aplikacji usługi  
 Ponieważ w tym instruktażu pokazano, jak dostęp do warstwy dostępu do danych przy użyciu usługi WCF, należy utworzyć nową aplikację usługi WCF.  
  
#### <a name="to-create-a-new-wcf-service-application"></a>Aby utworzyć nową aplikację usługi WCF  
  
1.  Z **pliku** menu Dodaj nowy projekt do rozwiązania NTierWalkthrough.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienku kliknij **WCF**. W **szablony** okienku kliknij **biblioteki usługi WCF**.  
  
3.  Nadaj projektowi nazwę **usługi DataService** i kliknij przycisk **OK**.  
  
     Projekt usługi danych jest tworzony i dodawany do rozwiązania NTierWalkthrough.  
  
## <a name="creating-methods-in-the-data-access-tier-to-return-the-customers-and-orders-data"></a>Tworzenie metod w warstwie dostępu do danych do zwrócenia klientów i porządkuje dane  
 Usługa danych musi wywołać dwie metody w warstwie dostępu do danych: GetCustomers i GetOrders. Te metody zwróci tabeli klientów Northwind i zamówień. Utwórz metody GetCustomers i GetOrders w projekcie DataAccessTier.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-customers-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabelę Klienci  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie NorthwindDataset.xsd, aby otworzyć zestaw danych w Projektancie obiektów Dataset.  
  
2.  Kliknij prawym przyciskiem myszy CustomersTableAdapter, a następnie kliknij przycisk **Dodaj zapytanie** do edycji elementu Tableadapter.  
  
3.  Na **wybierz typ polecenia** zostaw wartość domyślną **użyj instrukcji SQL** i kliknij przycisk **dalej**.  
  
4.  Na **wybierz typ zapytania** zostaw wartość domyślną **SELECT, która zwraca wiersze** i kliknij przycisk **dalej**.  
  
5.  Na **określić instrukcję SQL SELECT** strony, pozostaw zapytanie domyślne i kliknij przycisk **dalej**.  
  
6.  Na **Wybierz metody do generowania** wpisz **GetCustomers** dla **nazwę metody** w **róć tabelę DataTable** sekcji.  
  
7.  Kliknij przycisk **Zakończ**.  
  
#### <a name="to-create-a-method-in-the-data-access-tier-that-returns-the-orders-table"></a>Aby utworzyć metodę w warstwie dostępu do danych, która zwraca tabeli Orders  
  
1.  Kliknij prawym przyciskiem myszy OrdersTableAdapter, a następnie kliknij przycisk **Dodaj zapytanie**.  
  
2.  Na **wybierz typ polecenia** zostaw wartość domyślną **użyj instrukcji SQL** i kliknij przycisk **dalej**.  
  
3.  Na **wybierz typ zapytania** zostaw wartość domyślną **SELECT, która zwraca wiersze** i kliknij przycisk **dalej**.  
  
4.  Na **określić instrukcję SQL SELECT** strony, pozostaw zapytanie domyślne i kliknij przycisk **dalej**.  
  
5.  Na **Wybierz metody do generowania** wpisz **GetOrders** dla **nazwę metody** w **róć tabelę DataTable** sekcji.  
  
6.  Kliknij przycisk **Zakończ**.  
  
7.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
## <a name="adding-a-reference-to-the-data-entity-and-data-access-tiers-to-the-data-service"></a>Dodawanie odwołania do jednostki danych i warstwy dostępu do danych do usługi danych  
 Ponieważ usługa danych wymaga informacji z zestawu danych i adapterów TableAdapter, należy dodać odwołania do projektów DataEntityTier i DataAccessTier.  
  
#### <a name="to-add-references-to-the-data-service"></a>Aby dodać odwołania do usługi danych  
  
1.  Kliknij prawym przyciskiem myszy usługi danych w **Eksploratora rozwiązań** i kliknij przycisk **Dodaj odwołanie**.  
  
2.  Kliknij przycisk **projektów** karcie **Dodaj odwołanie** okno dialogowe.  
  
3.  Wybierz obie **DataAccessTier** i **DataEntityTier** projektów.  
  
4.  Kliknij przycisk **OK**.  
  
## <a name="adding-functions-to-the-service-to-call-the-getcustomers-and-getorders-methods-in-the-data-access-tier"></a>Dodawanie funkcji do usługi w celu wywołania GetCustomers i metod GetOrders danych dostęp do warstwy  
 Teraz, gdy warstwa dostępu do danych zawiera metody, aby zwrócić dane, tworzyć metody w usłudze danych do wywołania metody w warstwie dostępu do danych.  
  
> [!NOTE]
>  Dla projektów C#, należy dodać odwołanie do `System.Data.DataSetExtensions` zestawu dla następujący kod do skompilowania.  
  
#### <a name="to-create-the-getcustomers-and-getorders-functions-in-the-data-service"></a>Aby utworzyć funkcji GetCustomers i GetOrders usługi danych  
  
1.  W **usługi DataService** projektu, kliknij dwukrotnie IService1.vb lub IService1.cs.  
  
2.  Dodaj następujący kod w obszarze **Dodaj tutaj operacje usługi** komentarz:  
  
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
  
3.  W projekcie usługi danych kliknij dwukrotnie Service1.vb (lub Service1.cs).  
  
4.  Dodaj następujący kod do klasy Service1:  
  
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
  
5.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
## <a name="creating-a-presentation-tier-to-display-data-from-the-data-service"></a>Tworzenie warstwy prezentacji, aby wyświetlić dane z usługi danych  
 Teraz, gdy rozwiązanie zawiera usługi danych, która ma metody odwołujące się do warstwy dostępu do danych, należy utworzyć innego projektu, który będzie wywoływać usługi danych i prezentować je użytkownikom. W tym przewodniku tworzenie aplikacji Windows Forms; jest to warstwa prezentacji aplikacji n warstwowej.  
  
#### <a name="to-create-the-presentation-tier-project"></a>Aby utworzyć projekt warstwy prezentacji  
  
1.  Z **pliku** menu Dodaj nowy projekt do rozwiązania NTierWalkthrough.  
  
2.  W **nowy projekt** dialogowym **typów projektów** okienku kliknij **Windows**. W **szablony** okienku kliknij **aplikacja interfejsu Windows Forms**.  
  
3.  Nadaj projektowi nazwę **PresentationTier** i kliknij przycisk **OK**.  
  
4.  Projekt PresentationTier jest tworzony i dodawany do rozwiązania NTierWalkthrough.  
  
## <a name="setting-the-presentationtier-project-as-the-startup-project"></a>Ustawienia projektu PresentationTier jako projekt startowy  
 Warstwa prezentacji jest aplikacją kliencką rzeczywista, która służy do przedstawienia i wchodzić w interakcje z danymi, należy ustawić projekt PresentationTier jako projekt startowy.  
  
#### <a name="to-set-the-new-presentation-tier-project-as-the-startup-project"></a>Aby ustawić nowy projekt warstwy prezentacji jako projekt startowy  
  
-   W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **PresentationTier** i kliknij przycisk **Ustaw jako projekt startowy**.  
  
## <a name="adding-references-to-the-presentation-tier"></a>Dodawanie odwołań do warstwy prezentacji  
 Aplikacja kliencka PresentationTier wymaga odwołanie do usługi danych usługi, aby uzyskać dostęp do metod w usłudze. Ponadto odwołania do zestawu danych trzeba włączyć udostępnianie przez usługę WCF typu. Do momentu włączenia udostępnianie za pośrednictwem usługi danych typu kodu dodanego do klasy częściowego zestawu danych nie będą dostępne w warstwie prezentacji. Ponieważ zwykle możesz dodać kod, takie jak weryfikacja, do wiersza i kolumny zmieniający wydarzenia tabel danych, jest prawdopodobne, należy uzyskać dostęp do tego kodu z klienta.  
  
#### <a name="to-add-a-reference-to-the-presentation-tier"></a>Można dodać odwołania do warstwy prezentacji  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy PresentationTier i kliknij przycisk **Dodaj odwołanie**.  
  
2.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **projektów** kartę.  
  
3.  Wybierz **DataEntityTier** i kliknij przycisk **OK**.  
  
#### <a name="to-add-a-service-reference-to-the-presentation-tier"></a>Aby dodać odwołanie do usługi do warstwy prezentacji  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy PresentationTier i kliknij przycisk **Dodaj odwołanie do usługi**.  
  
2.  W **Dodaj odwołanie do usługi** okno dialogowe, kliknij przycisk **odnajdź**.  
  
3.  Wybierz **Service1** i kliknij przycisk **OK**.  
  
    > [!NOTE]
    >  Jeśli masz wiele usług na bieżącym komputerze, wybierz usługę, utworzony wcześniej w tym przewodniku (usługa zawiera metody GetCustomers i GetOrders).  
  
## <a name="adding-datagridviews-to-the-form-to-display-the-data-returned-by-the-data-service"></a>Dodawanie DataGridViews do formularza w celu wyświetlania danych zwróconych przez usługę danych  
 Po dodaniu odwołania do usługi do usługi danych **źródeł danych** okno zostanie automatycznie wypełniona danych, który jest zwracany przez usługę.  
  
#### <a name="to-add-two-data-bound-datagridviews-to-the-form"></a>Aby dodać dwa dane powiązane DataGridViews do formularza  
  
1.  W **Eksploratora rozwiązań**, wybierz projekt PresentationTier.  
  
2.  W **źródeł danych** okna, rozwiń węzeł **NorthwindDataSet** i Znajdź **klientów** węzła.  
  
3.  Przeciągnij **klientów** węzła na formularz Form1.  
  
4.  W **źródeł danych** okna, rozwiń węzeł **klientów** węzła i Znajdź powiązane **zamówienia** węzła ( **zamówienia** węzła zagnieżdżona w  **Klienci** węzła).  
  
5.  Przeciągnij powiązane **zamówienia** węzła na formularz Form1.  
  
6.  Utwórz `Form1_Load` program obsługi zdarzeń przez dwukrotne kliknięcie pustego obszaru formularza.  
  
7.  Dodaj następujący kod do `Form1_Load` programu obsługi zdarzeń.  
  
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
  
## <a name="increasing-the-maximum-message-size-allowed-by-the-service"></a>Zwiększyć maksymalny rozmiar komunikatu dozwolony przez usługę  
 Ponieważ usługa zwraca dane z tabel Klienci i zamówienia, wartość domyślna właściwości MaxReceivedMessageSize nie jest wystarczająco duży, aby pomieścić dane i musi zostać zwiększona. W tym przewodniku zostanie Zmień wartość na 6553600. Zmieni wartość na komputerze klienckim i odwołanie do usługi spowoduje automatyczne zaktualizowanie.  
  
> [!NOTE]
>  Niższe domyślny rozmiar ma na celu ograniczenia narażenia na ataki (DoS). Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.WSHttpBindingBase.MaxReceivedMessageSize%2A>.  
  
#### <a name="to-increase-the-maxreceivedmessagesize-value"></a>Aby zwiększyć wartości maxReceivedMessageSize  
  
1.  W **Eksploratora rozwiązań**, kliknij dwukrotnie plik app.config w projekcie PresentationTier.  
  
2.  Znajdź **maxReceivedMessage** rozmiar atrybutu i zmień wartość na `6553600`.  
  
## <a name="testing-the-application"></a>Testowanie aplikacji  
 Uruchom aplikację. Dane są pobierane z usługi danych i wyświetlane w formularzu.  
  
#### <a name="to-test-the-application"></a>Aby przetestować aplikację  
  
1.  Naciśnij F5.  
  
2.  Dane z tabel Klienci i zamówienia jest pobierane z usługi danych i wyświetlane w formularzu.  
  
## <a name="next-steps"></a>Następne kroki  
 W zależności od wymagań aplikacji istnieje kilka kroków, które warto wykonać po zapisaniu powiązanych danych w aplikacji systemu Windows. Na przykład można wprowadzić następujące ulepszenia do tej aplikacji:  
  
-   Dodawanie walidacji do zestawu danych. Aby uzyskać informacje, zobacz [instruktażu: Dodawanie walidacji do aplikacji warstwowych](http://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265).  
  
-   Dodaj dodatkowe metody do usługi w przypadku aktualizowania danych w bazie danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Praca z zestawami danych w aplikacjach n warstwowych](../data-tools/work-with-datasets-in-n-tier-applications.md)   
 [Hierarchiczna aktualizacja](../data-tools/hierarchical-update.md)   
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
