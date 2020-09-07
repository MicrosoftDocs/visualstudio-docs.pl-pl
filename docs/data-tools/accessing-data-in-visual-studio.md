---
title: Praca z danymi w programie Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 36fc3d3fd0b002c110e9184a6d7b15c9fa367c48
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509838"
---
# <a name="work-with-data-in-visual-studio"></a>Praca z danymi w programie Visual Studio

W programie Visual Studio można tworzyć aplikacje, które łączą się z danymi praktycznie dowolnego produktu lub usługi bazy danych, w dowolnym formacie, w dowolnym miejscu — na komputerze lokalnym, w sieci lokalnej lub w chmurze publicznej, prywatnej lub hybrydowej.

W przypadku aplikacji w językach JavaScript, Python, PHP, Ruby lub C++ możesz łączyć się z danymi, takimi jak coś innego, pobierając biblioteki i pisząc kod. W przypadku aplikacji .NET program Visual Studio udostępnia narzędzia umożliwiające Eksplorowanie źródeł danych, tworzenie modeli obiektów do przechowywania i manipulowanie danymi w pamięci oraz Powiązywanie danych z interfejsem użytkownika. Microsoft Azure udostępnia zestawy SDK dla aplikacji .NET, Java, Node.js, PHP, Python, Ruby i Mobile oraz narzędzia w programie Visual Studio do łączenia się z usługą Azure Storage.

::: moniker range="vs-2017"
Na poniższych listach przedstawiono zaledwie kilka systemów baz danych i pamięci masowej, które mogą być używane w programie Visual Studio. Oferty [Microsoft Azure](https://azure.microsoft.com/) to usługi danych, które obejmują wszystkie aprowizacji i administrowanie bazowym magazynem danych. Obciążenie **Programowanie na platformie Azure** w programie [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) umożliwia korzystanie z magazynów danych platformy Azure bezpośrednio z poziomu programu Visual Studio.
::: moniker-end
::: moniker range=">=vs-2019"
Na poniższych listach przedstawiono zaledwie kilka systemów baz danych i pamięci masowej, które mogą być używane w programie Visual Studio. Oferty [Microsoft Azure](https://azure.microsoft.com/) to usługi danych, które obejmują wszystkie aprowizacji i administrowanie bazowym magazynem danych. Obciążenie **Programowanie na platformie Azure** w programie [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) umożliwia korzystanie z magazynów danych platformy Azure bezpośrednio z poziomu programu Visual Studio.
::: moniker-end

![Obciążenie Programowanie na platformie Azure](media/azure-development-workload.png)

Większość innych produktów baz danych SQL i NoSQL, które są wymienione w tym miejscu, mogą być hostowane na komputerze lokalnym, w sieci lokalnej lub w Microsoft Azure na maszynie wirtualnej. Jeśli baza danych jest hostowana na Microsoft Azure maszynie wirtualnej, użytkownik jest odpowiedzialny za zarządzanie bazą danych.

**Microsoft Azure**

- Baza danych SQL
- Azure Cosmos DB
- Magazyn (obiekty blob, tabele, kolejki, pliki)
- SQL Data Warehouse
- SQL Server Stretch Database
- Magazyn StorSimple
- I nie tylko...

**SQL**

- SQL Server 2005-2016 (obejmuje Express i LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- I nie tylko...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB |
- RavenDB
- VelocityDB
- I nie tylko...

::: moniker range="vs-2017"

Wielu dostawców baz danych i inne firmy obsługują integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z ofertami w witrynie NuGet.org lub za pomocą Menedżera pakietów NuGet w programie Visual Studio (**Narzędzia**  >  **Menedżer pakietów NuGet**zarządzanie pakietami  >  **NuGet dla rozwiązania**). Inne produkty bazy danych integrują się z programem Visual Studio jako rozszerzeniem. Możesz przeglądać te oferty w [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub, przechodząc do obszaru **Narzędzia**  >  **rozszerzenia i aktualizacje** , a następnie wybierając pozycję **online** w lewym okienku okna dialogowego. Aby uzyskać więcej informacji, zobacz [zgodne systemy baz danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Wielu dostawców baz danych i inne firmy obsługują integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z ofertami w witrynie NuGet.org lub za pomocą Menedżera pakietów NuGet w programie Visual Studio (**Narzędzia**  >  **Menedżer pakietów NuGet**zarządzanie pakietami  >  **NuGet dla rozwiązania**). Inne produkty bazy danych integrują się z programem Visual Studio jako rozszerzeniem. Możesz przeglądać te oferty w [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub poprzez przechodzenie do **rozszerzeń**  >  **Zarządzanie rozszerzeniami** , a następnie wybranie **trybu online** w lewym okienku okna dialogowego. Aby uzyskać więcej informacji, zobacz [zgodne systemy baz danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Rozszerzona pomoc techniczna dla SQL Server 2005 zakończyła się 12 kwietnia 2016. Nie ma gwarancji, że narzędzia danych w programie Visual Studio 2015 i nowszych będą nadal działały z SQL Server 2005. Aby uzyskać więcej informacji, zobacz [anons końca pomocy technicznej dla SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Języki .NET

Wszystkie funkcje dostępu do danych platformy .NET, w tym na platformie .NET Core, bazują na ADO.NET, zestawie klas, który definiuje interfejs do uzyskiwania dostępu do dowolnego rodzaju źródła danych, zarówno relacyjnych, jak i nierelacyjnych. Program Visual Studio zawiera kilka narzędzi i projektantów, które współpracują z usługą ADO.NET, aby ułatwić łączenie się z bazami danych, manipulowanie danymi oraz prezentowanie danych użytkownikom. W dokumentacji w tej sekcji opisano sposób korzystania z tych narzędzi. Możesz również programować bezpośrednio w odniesieniu do obiektów poleceń ADO.NET. Aby uzyskać więcej informacji na temat bezpośredniego wywoływania interfejsów API ADO.NET, zobacz [ADO.NET](/dotnet/framework/data/adonet/index).

Aby uzyskać dokumentację dostępu do danych powiązaną z ASP.NET, zobacz [Praca z danymi](https://www.asp.net/web-forms/overview/presenting-and-managing-data) w witrynie ASP.NET. Aby zapoznać się z samouczkiem dotyczącym używania Entity Framework z ASP.NET MVC, zobacz [wprowadzenie z Entity Framework 6 Code First przy użyciu MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Aplikacje platforma uniwersalna systemu Windows (platformy UWP) w języku C# lub Visual Basic mogą używać Zestaw Microsoft Azure SDK dla platformy .NET do uzyskiwania dostępu do usługi Azure Storage i innych usług platformy Azure. Klasa Windows. Web. HttpClient umożliwia komunikację z dowolną usługą RESTful. Aby uzyskać więcej informacji, zobacz [jak nawiązać połączenie z serwerem HTTP przy użyciu systemu Windows. Web. http](/previous-versions/windows/apps/dn469430(v=win.10)).

W przypadku przechowywania danych na komputerze lokalnym zalecanym rozwiązaniem jest użycie oprogramowania SQLite, które jest uruchamiane w tym samym procesie co aplikacja. Jeśli wymagana jest warstwa mapowania obiektów relacyjnych (ORM), można użyć Entity Framework. Aby uzyskać więcej informacji, zobacz [dostęp do danych](/windows/uwp/data-access/index) w centrum deweloperów systemu Windows.

Jeśli łączysz się z usługami platformy Azure, pamiętaj o pobraniu najnowszych [narzędzi zestawu Azure SDK](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Dostawcy danych

Aby można było korzystać z bazy danych w programie ADO.NET, musi ona mieć niestandardowego *dostawcę danych ADO.NET* lub musi uwidaczniać interfejs ODBC lub OLE DB. Firma Microsoft udostępnia [listę dostawców danych ADO.NET](/dotnet/framework/data/adonet/ado-net-overview) dla produktów SQL Server, a także dostawców ODBC i OLE DB.

### <a name="data-modeling"></a>Modelowanie danych

W programie .NET dostępne są trzy opcje modelowania i manipulowania danymi w pamięci po pobraniu ich ze źródła danych:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Preferowana Technologia Microsoft ORM. Można jej używać do programowania danych relacyjnych jako obiektów pierwszej klasy .NET. W przypadku nowych aplikacji powinien być pierwszym wyborem, gdy wymagany jest model. Wymaga to obsługi niestandardowej od bazowego dostawcy ADO.NET.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Mapowanie obiektu starszej generacji. Dobrze sprawdza się w przypadku mniej złożonych scenariuszy, ale nie jest już aktywnym programowaniem.

[Zestawy danych](../data-tools/dataset-tools-in-visual-studio.md) Najstarsza z trzech technologii modelowania. Jest ona zaprojektowana głównie do szybkiego opracowywania aplikacji "Forms na dane", w których nie są przetwarzane ogromne ilości danych ani wykonywanie złożonych zapytań lub transformacji. Obiekt DataSet składa się z obiektów DataTable i DataRow, które logicznie przypominają obiekty bazy danych SQL znacznie więcej niż obiekty .NET. W przypadku stosunkowo prostej aplikacji opartej na źródłach danych SQL, nadal może być to dobry wybór.

Korzystanie z tych technologii nie jest wymagane. W niektórych scenariuszach, szczególnie w przypadku, gdy wydajność jest krytyczna, można po prostu użyć obiektu DataReader do odczytu z bazy danych i skopiować wartości, które są potrzebne do obiektu kolekcji, takiego jak List \<T> .

## <a name="native-c"></a>Natywny język C++

Aplikacje C++ łączące się z SQL Server powinny używać [sterownika ODBC firmy Microsoft® 13,1 dla SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) w większości przypadków. Jeśli serwery są połączone, OLE DB jest konieczne i w przypadku korzystania z [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Możesz uzyskać dostęp do innych baz danych za pomocą [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) lub sterowników OLE DB bezpośrednio. ODBC jest bieżącym standardowym interfejsem bazy danych, ale większość systemów baz danych oferuje niestandardowe funkcje, do których nie można uzyskać dostępu za pośrednictwem interfejsu ODBC. OLE DB to Starsza technologia dostępu do danych COM, która jest nadal obsługiwana, ale nie jest zalecana w przypadku nowych aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do danych w Visual C++](/cpp/data/data-access-in-cpp).

Programy c++ korzystające z usług REST mogą korzystać z [zestawu SDK REST języka c++](https://github.com/Microsoft/cpprestsdk).

Programy w języku C++, które współpracują z Microsoft Azure Storage mogą korzystać z [klienta Microsoft Azure Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Modelowanie danych &mdash; w programie Visual Studio nie zapewnia warstwy ORM dla języka C++. [ODB](https://www.codesynthesis.com/products/odb/) to popularne ORM typu open source dla języka C++.

Aby dowiedzieć się więcej na temat łączenia się z bazami danych z aplikacji C++, zobacz [Visual Studio Data Tools for c++](../data-tools/visual-studio-data-tools-for-cpp.md). Aby uzyskać więcej informacji na temat starszych technologii dostępu do danych Visual C++, zobacz [dostęp do danych](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

Język [JavaScript w programie Visual Studio](/scripting/javascript/javascript-language-reference) to pierwsza klasa języka do tworzenia aplikacji dla wielu platform, aplikacji platformy UWP, usług Cloud Services, witryn sieci Web i aplikacji internetowych. Możesz użyć Bower, grunt, Gulp, npm i NuGet z poziomu programu Visual Studio, aby zainstalować Ulubione biblioteki JavaScript i produkty bazy danych. Połącz się z usługą Azure Storage i usługami, pobierając zestawy SDK z [witryny sieci Web systemu Azure](https://azure.microsoft.com/). Edge.js to biblioteka, która łączy kod JavaScript po stronie serwera (Node.js) ze źródłami danych ADO.NET.

## <a name="python"></a>Python

Zainstaluj [obsługę języka Python w programie Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) , aby tworzyć aplikacje w języku Python. Dokumentacja platformy Azure zawiera kilka samouczków dotyczących łączenia się z danymi, w tym:

- [Django i SQL Database na platformie Azure](/azure/app-service/app-service-web-get-started-python)
- [Django i MySQL na platformie Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Pracuj z obiektami [BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [plikami](/azure/storage/files/storage-python-how-to-use-file-storage), [kolejkami](/azure/storage/queues/storage-python-how-to-use-queue-storage)i [tabelami (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Powiązane tematy

[Platforma](https://azure.microsoft.com/overview/ai-platform/?v=17.42w) &mdash; Microsoft AI Zawiera wprowadzenie do inteligentnej chmury firmy Microsoft, w tym pakietu Cortana Analytics Suite i pomocy technicznej dla Internet rzeczy.

[Microsoft Azure Storage](/azure/storage/) &mdash; Opisuje usługę Azure Storage oraz sposób tworzenia aplikacji przy użyciu obiektów blob, tabel, kolejek i plików platformy Azure.

[Azure SQL Database](/azure/sql-database/) &mdash; Opisuje sposób nawiązywania połączenia z Azure SQL Database, relacyjną bazą danych jako usługą.

[Narzędzia](/sql/ssdt/download-sql-server-data-tools-ssdt) &mdash; danych SQL Server Zawiera opis narzędzi, które upraszczają projektowanie, eksplorację, testowanie i wdrażanie aplikacji połączonych z danymi oraz baz danych.

[ADO.NET](/dotnet/framework/data/adonet/index) &mdash; W tym artykule opisano architekturę ADO.NET oraz sposób używania klas ADO.NET do zarządzania danymi aplikacji i współdziałania ze źródłami danych i XML.

[ADO.NET Entity Framework](/ef/ef6/) &mdash; Zawiera opis sposobu tworzenia aplikacji do danych, które umożliwiają deweloperom programowanie w modelu koncepcyjnym, a nie bezpośrednio w odniesieniu do relacyjnej bazy danych.

[Usługi danych programu WCF 4,5](/dotnet/framework/data/wcf/index) &mdash; Opisuje, jak używać [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] programu do wdrażania usług danych w sieci Web lub intranecie implementujących [protokół Open Data Protocol (OData)](https://www.odata.org/).

[Dane w rozwiązaniach](../vsto/data-in-office-solutions.md) &mdash; pakietu Office Zawiera łącza do tematów, które wyjaśniają, jak dane działają w rozwiązaniach pakietu Office. Obejmuje to informacje o programowaniu zorientowanym na schematach, buforowaniu danych i dostępie do danych po stronie serwera.

[LINQ (zapytanie zintegrowane z językiem)](/dotnet/csharp/linq/) &mdash; Opisuje możliwości zapytania wbudowane w Języki C# i Visual Basic oraz wspólny model służący do wykonywania zapytań dotyczących relacyjnych baz danych, dokumentów XML, zestawów danych i kolekcji w pamięci.

[Narzędzia XML w programie Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) &mdash; W tym artykule omówiono pracę z danymi XML, debugowanie XSLT, funkcje języka .NET XML i architekturę kwerendy XML.

[Dokumenty i dane XML](/dotnet/standard/data/xml/index) &mdash; Zawiera omówienie kompleksowego i zintegrowanego zestawu klas, które działają z dokumentami XML i danymi w programie .NET.