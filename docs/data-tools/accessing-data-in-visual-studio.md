---
title: Dostęp do danych i narzędzia
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
ms.openlocfilehash: 3a53561e8c62fcf523f13d17d5228d33a6a0af6d
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916717"
---
# <a name="access-data-in-visual-studio"></a>Uzyskiwanie dostępu do danych w programie Visual Studio

W programie Visual Studio, można utworzyć aplikacji, które łączą się z danymi w praktycznie dowolnego produktu bazy danych lub usługi, w dowolnym formacie, dowolnym miejscu — na komputerze lokalnym, w sieci lokalnej lub w chmurze prywatnej, publicznej lub hybrydowej.

Dla aplikacji JavaScript, Python, PHP, Ruby lub C++ możesz łączyć się dane tak jak dowolne inne, uzyskując bibliotek i pisania kodu. W przypadku aplikacji .NET program Visual Studio udostępnia narzędzia umożliwiające Eksplorowanie źródeł danych, tworzenie modeli obiektów do przechowywania i manipulowanie danymi w pamięci oraz Powiązywanie danych z interfejsem użytkownika. Microsoft Azure udostępnia zestawy SDK for .NET, Java, Node.js, PHP, Python, Ruby i aplikacje mobilne i narzędzi w programie Visual Studio do łączenia się z usługi Azure Storage.

Poniższej przedstawiono kilka wiele systemów bazy danych i magazynu, które mogą być używane w programie Visual Studio. Oferty [Microsoft Azure](https://azure.microsoft.com/) to usługi danych, które obejmują wszystkie aprowizacji i administrowanie bazowym magazynem danych. Obciążenie **Programowanie na platformie Azure** w programie [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) umożliwia korzystanie z magazynów danych platformy Azure bezpośrednio z poziomu programu Visual Studio.

![Obciążenie programistyczne platformy Azure](media/azure-development-workload.png)

Większość innych języków SQL i NoSQL bazy danych produktów, które są wymienione w tym miejscu mogą być hostowane na komputerze lokalnym, w sieci lokalnej lub w systemie Microsoft Azure na maszynie wirtualnej. Jeśli baza danych jest hostowana na Microsoft Azure maszynie wirtualnej, użytkownik jest odpowiedzialny za zarządzanie bazą danych.

**Microsoft Azure**

- Baza danych SQL
- Azure Cosmos DB
- Storage (obiekty BLOB, tabel, kolejek, plików)
- Usługa SQL Data Warehouse
- SQL Server Stretch Database
- Usługi StorSimple
- i więcej...

**SQL**

- SQL Server 2005-2016 (obejmuje Express i LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite
- i więcej...

**NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- Lokalizacji
- OrientDB|
- RavenDB
- VelocityDB
- i więcej...

::: moniker range="vs-2017"

Wielu dostawców bazy danych i innych firm obsługuje integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z oferty w witrynie nuget.org, lub za pośrednictwem Menedżera pakietów NuGet w programie Visual Studio (**narzędzia** > **Menedżera pakietów NuGet** > **zarządzania pakietami NuGet Pakietami dla rozwiązania**). Inne produkty bazy danych Integracja z programem Visual Studio jako rozszerzenie. Możesz przeglądać te oferty w [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub poprzez przechodzenie do **narzędzi** > **rozszerzenia i aktualizacje** , a następnie wybierając pozycję **online** w lewym okienku okna dialogowego. Aby uzyskać więcej informacji, zobacz [zgodne systemy baz danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Wielu dostawców bazy danych i innych firm obsługuje integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z oferty w witrynie nuget.org, lub za pośrednictwem Menedżera pakietów NuGet w programie Visual Studio (**narzędzia** > **Menedżera pakietów NuGet** > **zarządzania pakietami NuGet Pakietami dla rozwiązania**). Inne produkty bazy danych Integracja z programem Visual Studio jako rozszerzenie. Możesz przeglądać te oferty w [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub poprzez przechodzenie do **rozszerzeń** > **zarządzania rozszerzeniami** , a następnie wybierając pozycję **online** w lewym okienku okna dialogowego. Aby uzyskać więcej informacji, zobacz [zgodne systemy baz danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Rozszerzona pomoc techniczna dla programu SQL Server 2005 zakończona w dniu 12 kwietnia 2016 r. Nie ma gwarancji, że narzędzia danych w programie Visual Studio 2015 i nowszych będą nadal działały z SQL Server 2005. Aby uzyskać więcej informacji, zobacz [anons zakończenia okresu objęcia wsparciem dla programu SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Języków .NET

Wszystkie funkcje dostępu do danych platformy .NET, w tym na platformie .NET Core, bazują na ADO.NET, zestawie klas, który definiuje interfejs do uzyskiwania dostępu do dowolnego rodzaju źródła danych, zarówno relacyjnych, jak i nierelacyjnych. Program Visual Studio ma kilka narzędzi i projektantów, współpracujących za pomocą narzędzia ADO.NET w celu łatwiejszego nawiązania połączenia z bazami danych, manipulowania danymi i prezentowania danych użytkownika. W dokumentacji w tej sekcji opisano sposób używania tych narzędzi. Ponadto można programować bezpośrednio w odniesieniu do obiektów poleceń ADO.NET. Aby uzyskać więcej informacji na temat bezpośredniego wywoływania interfejsów API ADO.NET, zobacz [ADO.NET](/dotnet/framework/data/adonet/index).

Aby uzyskać dokumentację dostępu do danych powiązaną z ASP.NET, zobacz [Praca z danymi](https://www.asp.net/web-forms/overview/presenting-and-managing-data) w witrynie ASP.NET. Samouczek dotyczący używający narzędzia Entity Framework z platformą ASP.NET MVC, zobacz [wprowadzenie do programu Entity Framework 6 Code First wykorzystaniem MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Aplikacje platforma uniwersalna systemu Windows (platformy UWP) w C# programie lub Visual Basic mogą używać zestaw Microsoft Azure SDK dla platformy .NET do uzyskiwania dostępu do usługi Azure Storage i innych usług platformy Azure. Klasa Windows.Web.HttpClient umożliwia komunikację z dowolnej usługi RESTful. Aby uzyskać więcej informacji, zobacz [jak nawiązać połączenie z serwerem HTTP przy użyciu systemu Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Do przechowywania danych na komputerze lokalnym Zalecanym podejściem jest użycie bazy danych SQLite, która jest uruchamiana w tym samym procesie co aplikacja. Jeśli wymagana jest warstwa Mapowania obiektowo relacyjny (ORM), można użyć programu Entity Framework. Aby uzyskać więcej informacji, zobacz [dostęp do danych](/windows/uwp/data-access/index) w Centrum deweloperów Windows.

Jeśli łączysz się z usługami platformy Azure, pamiętaj pobrać najnowsze [zestawu Azure SDK tools](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Dostawcy danych

Aby baza danych jest w użyciu w ADO.NET, musi mieć niestandardową *dostawcy danych ADO.NET* lub inne musi ujawniać interfejsu ODBC lub OLE DB. Firma Microsoft udostępnia [listę dostawców danych ADO.NET](/dotnet/framework/data/adonet/ado-net-overview) dla produktów SQL Server, a także dostawców ODBC i OLE DB.

### <a name="data-modeling"></a>Modelowanie danych

Na platformie .NET dostępne są trzy możliwości do modelowania i manipulowanie danymi w pamięci po jej pobraniu ze źródła danych:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) Preferowana Technologia Microsoft ORM. Umożliwia ona Programowanie w relacyjnej bazie danych jako najwyższej klasy obiektów platformy .NET. Gdy model jest wymagany dla nowych aplikacji, powinno być pierwszy wybór domyślny. Wymaga ona dodatkowej pomocy technicznej od podstawowego dostawcy ADO.NET.

[LINQ to SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) Mapowanie obiektu starszej generacji. Działa dobrze sprawdza się w mniej złożonych scenariuszy, ale nie jest już aktywnie.

[Zestawy danych](../data-tools/dataset-tools-in-visual-studio.md) Najstarsza z trzech technologii modelowania. Jest ona przeznaczona przede wszystkim do szybkiego opracowywania aplikacji "formularzy nad danymi", w których są nie przetwarzanie ogromnych ilości danych lub wykonywania kwerend złożonych lub przekształcenia. Obiekt DataSet składa się z obiektów DataTable i DataRow, które logicznie przypominają obiekty bazy danych SQL znacznie więcej niż obiekty .NET. W przypadku stosunkowo prostej aplikacji opartej na źródłach danych SQL, nadal może być to dobry wybór.

Nie istnieje wymóg, aby użyć dowolnego z tych technologii. W niektórych scenariuszach, szczególnie w przypadku, gdy wydajność ma kluczowe znaczenie, po prostu służy obiekt DataReader do odczytu z bazy danych, a następnie skopiuj wartości, które należy do obiektu kolekcji, takich jak lista\<T >.

## <a name="native-c"></a>Natywnych języka C++

C++aplikacje łączące się z SQL Server powinny używać [sterownika ODBC firmy Microsoft® SQL Server 13,1](https://www.microsoft.com/download/details.aspx?id=53339) w większości przypadków. Jeśli serwery są połączone, OLE DB jest konieczne i w przypadku korzystania z [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Możesz uzyskać dostęp do innych baz danych za pomocą [ODBC](/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) lub sterowników OLE DB bezpośrednio. ODBC jest bieżącego interfejsu database w warstwie standardowa, ale większość systemów bazy danych dostarczają niestandardowych funkcjonalności, które nie są dostępne za pośrednictwem interfejsu ODBC. OLE DB jest technologią starszą dostęp do danych modelu COM, która jest w dalszym ciągu obsługiwany, ale nie jest zalecane dla nowych aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do danych C++w programie Visual ](/cpp/data/data-access-in-cpp).

Programy w języku C++, korzystanie z usług REST, które można użyć [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programy w języku C++, które działają z usługą Microsoft Azure Storage można użyć [Microsoft Azure Storage Client](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Modelowanie danych&mdash;Visual Studio nie zapewnia warstwy ORM dla C++. [ODB](https://www.codesynthesis.com/products/odb/) to popularne ORM typu open source dla języka C++.

Aby dowiedzieć się więcej na temat łączenia C++ się z bazami danych z aplikacji, zobacz [Visual Studio Data Tools for C++ ](../data-tools/visual-studio-data-tools-for-cpp.md). Aby uzyskać więcej informacji na temat C++ starszych technologii dostępu do danych wizualnych, zobacz [dostęp do danych](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[Język JavaScript w programie Visual Studio](/scripting/javascript/javascript-language-reference) do najważniejszych języków do tworzenia aplikacji dla wielu platform, aplikacje platformy uniwersalnej systemu Windows, usług w chmurze, witryn sieci Web i aplikacji sieci web. Możesz użyć Bower, grunt, Gulp, npm i NuGet z poziomu programu Visual Studio, aby zainstalować Ulubione biblioteki JavaScript i produkty bazy danych. Podłączanie do usługi Azure storage i usług, pobierając zestawy SDK dostępne w [witryny sieci Web Azure](https://azure.microsoft.com/). Edge.js jest bibliotekę, która łączy JavaScript po stronie serwera (Node.js) do źródeł danych ADO.NET.

## <a name="python"></a>Python

Zainstaluj [obsługę języka Python w programie Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) , aby tworzyć aplikacje w języku Python. Dokumentacja platformy Azure zawiera kilka samouczków dotyczących łączenia się z danymi, w tym:

- [Django i SQL Database na platformie Azure](/azure/app-service/app-service-web-get-started-python)
- [Django i MySQL na platformie Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Pracuj z obiektami [BLOB](/azure/storage/blobs/storage-quickstart-blobs-python), [plikami](/azure/storage/files/storage-python-how-to-use-file-storage), [kolejkami](/azure/storage/queues/storage-python-how-to-use-queue-storage)i [tabelami (Cosmo DB)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Tematy pokrewne

[Platforma Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;zawiera wprowadzenie do inteligentnej chmury firmy Microsoft, w tym pakietu Cortana Analytics Suite i pomocy technicznej dla Internet rzeczy.

[Microsoft Azure Storage](/azure/storage/)&mdash;opisuje usługę Azure Storage oraz sposób tworzenia aplikacji przy użyciu obiektów blob, tabel, kolejek i plików platformy Azure.

[Azure SQL Database](/azure/sql-database/)&mdash;opisuje sposób nawiązywania połączenia z Azure SQL Database, relacyjną bazą danych jako usługą.

[SQL Server narzędzia danych](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;opisuje narzędzia, które upraszczają projektowanie, eksplorację, testowanie i wdrażanie aplikacji połączonych z danymi oraz baz danych.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;opisuje architekturę ADO.NET i sposób używania klas ADO.NET do zarządzania danymi aplikacji i współdziałania ze źródłami danych i XML.

[ADO.NET Entity Framework](/ef/ef6/)&mdash;opisuje sposób tworzenia aplikacji do danych, które umożliwiają deweloperom programowanie w modelu koncepcyjnym, a nie bezpośrednio względem relacyjnej bazy danych.

[Usługi danych programu WCF 4,5](/dotnet/framework/data/wcf/index)&mdash;opisuje, jak używać [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] do wdrażania usług danych w sieci Web lub intranecie implementujących [protokół Open Data Protocol (OData)](https://www.odata.org/).

[Dane w rozwiązaniach pakietu office](../vsto/data-in-office-solutions.md)&mdash;zawierają linki do tematów, które wyjaśniają, jak dane działają w rozwiązaniach pakietu Office. W tym informacje dotyczące programowania schematycznego, buforowania danych i dostęp do danych po stronie serwera.

[LINQ (zapytanie zintegrowane z językiem)](/dotnet/csharp/linq/)&mdash;opisuje możliwości zapytania wbudowane w C# i Visual Basic oraz wspólny model służący do wykonywania zapytań dotyczących relacyjnych baz danych, dokumentów XML, zestawów danych i kolekcji w pamięci.

[Narzędzia XML Tools w programie Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;omawiają pracę z danymi XML, debugowaniem XSLT, funkcjami XML platformy .NET i architekturą kwerendy XML.

[Dokumenty XML i&mdash;danych](/dotnet/standard/data/xml/index) zawierają omówienie kompleksowego i zintegrowanego zestawu klas, które działają z dokumentami XML i danymi w środowisku .NET.
