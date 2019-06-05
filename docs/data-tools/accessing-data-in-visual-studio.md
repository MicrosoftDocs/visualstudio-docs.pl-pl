---
title: Dostęp do danych i narzędzia
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- "80025080"
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 5403803a4da0821978a8c6bbfc31e45c31104640
ms.sourcegitcommit: 5483e399f14fb01f528b3b194474778fd6f59fa6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/05/2019
ms.locfileid: "66715276"
---
# <a name="access-data-in-visual-studio"></a>Uzyskiwanie dostępu do danych w programie Visual Studio

W programie Visual Studio, można utworzyć aplikacji, które łączą się z danymi w praktycznie dowolnego produktu bazy danych lub usługi, w dowolnym formacie, dowolnym miejscu — na komputerze lokalnym, w sieci lokalnej lub w chmurze prywatnej, publicznej lub hybrydowej.

Dla aplikacji JavaScript, Python, PHP, Ruby lub C++ możesz łączyć się dane tak jak dowolne inne, uzyskując bibliotek i pisania kodu. Dla aplikacji .NET Visual Studio udostępnia narzędzia, które umożliwia poznawanie źródeł danych, tworzyć modele obiektów do przechowywania i manipulowanie danymi w pamięci i powiązać dane z interfejsu użytkownika. Microsoft Azure udostępnia zestawy SDK for .NET, Java, Node.js, PHP, Python, Ruby i aplikacje mobilne i narzędzi w programie Visual Studio do łączenia się z usługi Azure Storage.

Poniższej przedstawiono kilka wiele systemów bazy danych i magazynu, które mogą być używane w programie Visual Studio. [Microsoft Azure](https://azure.microsoft.com/) oferty są usług danych, które obejmują aprowizacji i administrowania źródłowy magazyn danych. **Programowanie na platformie Azure** obciążenie w [programu Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) umożliwia pracę z magazynami danych na platformie Azure bezpośrednio z programu Visual Studio.

![Obciążenie programistyczne platformy Azure](media/azure-development-workload.png)

Większość innych języków SQL i NoSQL bazy danych produktów, które są wymienione w tym miejscu mogą być hostowane na komputerze lokalnym, w sieci lokalnej lub w systemie Microsoft Azure na maszynie wirtualnej. Jeśli na serwerze bazy danych na maszynie wirtualnej Microsoft Azure jest odpowiedzialny za zarządzanie sama baza danych.

**Microsoft Azure**

- SQL Database
- Azure Cosmos DB
- Storage (obiekty BLOB, tabel, kolejek, plików)
- Usługa SQL Data Warehouse
- SQL Server Stretch Database
- Usługi StorSimple
- i więcej...

**SQL**

- SQL Server 2005-2016 (w tym Express i LocalDB)
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- Bazy danych SQLite
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

Wielu dostawców bazy danych i innych firm obsługuje integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z oferty w witrynie nuget.org, lub za pośrednictwem Menedżera pakietów NuGet w programie Visual Studio (**narzędzia** > **Menedżera pakietów NuGet** > **zarządzania pakietami NuGet Pakietami dla rozwiązania**). Inne produkty bazy danych Integracja z programem Visual Studio jako rozszerzenie. Możesz przeglądać te oferty w [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub przechodząc do **narzędzia** > **rozszerzenia i aktualizacje** , a następnie wybierając  **Online** w lewym okienku okna dialogowego. Aby uzyskać więcej informacji, zobacz [zgodne systemy bazy danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

::: moniker range=">=vs-2019"

Wielu dostawców bazy danych i innych firm obsługuje integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z oferty w witrynie nuget.org, lub za pośrednictwem Menedżera pakietów NuGet w programie Visual Studio (**narzędzia** > **Menedżera pakietów NuGet** > **zarządzania pakietami NuGet Pakietami dla rozwiązania**). Inne produkty bazy danych Integracja z programem Visual Studio jako rozszerzenie. Możesz przeglądać te oferty w [Visual Studio Marketplace](https://marketplace.visualstudio.com/) lub przechodząc do **rozszerzenia** > **Zarządzaj rozszerzeniami** , a następnie wybierając  **Online** w lewym okienku okna dialogowego. Aby uzyskać więcej informacji, zobacz [zgodne systemy bazy danych dla programu Visual Studio](../data-tools/installing-database-systems-tools-and-samples.md).

::: moniker-end

> [!NOTE]
> Rozszerzona pomoc techniczna dla programu SQL Server 2005 zakończona w dniu 12 kwietnia 2016 r. Nie ma żadnej gwarancji, że narzędzia danych w programie Visual Studio 2015 i nowszych wersjach będą nadal działać przy użyciu programu SQL Server 2005. Aby uzyskać więcej informacji, zobacz [anons zakończenia okresu objęcia wsparciem dla programu SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

## <a name="net-languages"></a>Języków .NET

.NET dostępu do wszystkich danych, w tym programie .NET Core jest oparty na ADO.NET, zestaw klas, który definiuje interfejs do uzyskiwania dostępu do dowolnego rodzaju źródła danych relacyjnych i nierelacyjnych. Program Visual Studio ma kilka narzędzi i projektantów, współpracujących za pomocą narzędzia ADO.NET w celu łatwiejszego nawiązania połączenia z bazami danych, manipulowania danymi i prezentowania danych użytkownika. W dokumentacji w tej sekcji opisano sposób używania tych narzędzi. Ponadto można programować bezpośrednio w odniesieniu do obiektów poleceń ADO.NET. Aby uzyskać więcej informacji na temat bezpośrednie wywoływanie interfejsów API ADO.NET, zobacz [ADO.NET](/dotnet/framework/data/adonet/index).

Aby uzyskać dokumentację dostęp do danych związane z programem ASP.NET, zobacz [Praca z danymi](https://www.asp.net/web-forms/overview/presenting-and-managing-data) w witrynie programu ASP.NET. Samouczek dotyczący używający narzędzia Entity Framework z platformą ASP.NET MVC, zobacz [wprowadzenie do programu Entity Framework 6 Code First wykorzystaniem MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

Uniwersalnych platformy Windows (UWP) w języku C# lub Visual Basic można użyć zestawu Microsoft Azure SDK dla platformy .NET, dostęp do usługi Azure Storage i innymi usługami platformy Azure. Klasa Windows.Web.HttpClient umożliwia komunikację z dowolnej usługi RESTful. Aby uzyskać więcej informacji, zobacz [sposób nawiązywania połączeń z serwerem HTTP przy użyciu Windows.Web.Http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

Do przechowywania danych na komputerze lokalnym Zalecanym podejściem jest użycie bazy danych SQLite, która jest uruchamiana w tym samym procesie co aplikacja. Jeśli wymagana jest warstwa Mapowania obiektowo relacyjny (ORM), można użyć programu Entity Framework. Aby uzyskać więcej informacji, zobacz [dostęp do danych](/windows/uwp/data-access/index) w Centrum deweloperów Windows.

Jeśli łączysz się z usługami platformy Azure, pamiętaj pobrać najnowsze [zestawu Azure SDK tools](https://azure.microsoft.com/downloads/).

### <a name="data-providers"></a>Dostawcy danych

Aby baza danych jest w użyciu w ADO.NET, musi mieć niestandardową *dostawcy danych ADO.NET* lub inne musi ujawniać interfejsu ODBC lub OLE DB. Firma Microsoft udostępnia [listę dostawców danych ADO.NET](https://docs.microsoft.com/dotnet/framework/data/adonet/ado-net-overview) dla produktów programu SQL Server, a także dostawcami ODBC i OLE DB.

### <a name="data-modeling"></a>Modelowanie danych

Na platformie .NET dostępne są trzy możliwości do modelowania i manipulowanie danymi w pamięci po jej pobraniu ze źródła danych:

[Entity Framework](../data-tools/entity-data-model-tools-in-visual-studio.md) preferowaną technologię ORM firmy Microsoft. Umożliwia ona Programowanie w relacyjnej bazie danych jako najwyższej klasy obiektów platformy .NET. Gdy model jest wymagany dla nowych aplikacji, powinno być pierwszy wybór domyślny. Wymaga ona dodatkowej pomocy technicznej od podstawowego dostawcy ADO.NET.

[LINQ do SQL](../data-tools/linq-to-sql-tools-in-visual-studio2.md) maper obiektowo relacyjny starszej generacji. Działa dobrze sprawdza się w mniej złożonych scenariuszy, ale nie jest już aktywnie.

[Zestawy danych](../data-tools/dataset-tools-in-visual-studio.md) najstarsze trzy technologie modelowania. Jest ona przeznaczona przede wszystkim do szybkiego opracowywania aplikacji "formularzy nad danymi", w których są nie przetwarzanie ogromnych ilości danych lub wykonywania kwerend złożonych lub przekształcenia. Obiekt DataSet składa się z elementu DataTable i DataRow obiektów, które logicznie znacznie więcej niż obiekty .NET podobne obiekty bazy danych SQL. Stosunkowo proste aplikacje oparte na SQL źródła danych zestawy danych nadal może być dobrym wyborem.

Nie istnieje wymóg, aby użyć dowolnego z tych technologii. W niektórych scenariuszach, szczególnie w przypadku, gdy wydajność ma kluczowe znaczenie, po prostu służy obiekt DataReader do odczytu z bazy danych, a następnie skopiuj wartości, które należy do obiektu kolekcji, takich jak lista\<T >.

## <a name="native-c"></a>Natywnych języka C++

Skorzystaj z aplikacji w języku C++, które połączenia z serwerem SQL [® sterownik Microsoft ODBC 13.1 dla programu SQL Server](https://www.microsoft.com/download/details.aspx?id=53339) w większości przypadków. Jeśli serwery są połączone, a następnie zachodzi OLE DB i do tego użyć [SQL Server Native Client](/sql/relational-databases/native-client/sql-server-native-client). Dostęp do innych baz danych przy użyciu [ODBC](https://docs.microsoft.com/sql/odbc/microsoft-open-database-connectivity-odbc?view=sql-server-2017) lub bezpośrednio sterownikami OLE DB. ODBC jest bieżącego interfejsu database w warstwie standardowa, ale większość systemów bazy danych dostarczają niestandardowych funkcjonalności, które nie są dostępne za pośrednictwem interfejsu ODBC. OLE DB jest technologią starszą dostęp do danych modelu COM, która jest w dalszym ciągu obsługiwany, ale nie jest zalecane dla nowych aplikacji. Aby uzyskać więcej informacji, zobacz [dostęp do danych w programie Visual C++](/cpp/data/data-access-in-cpp).

Programy w języku C++, korzystanie z usług REST, które można użyć [C++ REST SDK](https://github.com/Microsoft/cpprestsdk).

Programy w języku C++, które działają z usługą Microsoft Azure Storage można użyć [Microsoft Azure Storage Client](https://www.nuget.org/packages/Microsoft.Azure.Storage.CPP).

Modelowanie danych&mdash;programu Visual Studio nie zapewnia warstwę ORM dla języka C++. [ODB](https://www.codesynthesis.com/products/odb/) to popularne ORM typu open source dla języka C++.

Aby dowiedzieć się więcej na temat nawiązywania połączenia z bazami danych z aplikacji C++, zobacz [narzędzia danych programu Visual Studio dla języka C++](../data-tools/visual-studio-data-tools-for-cpp.md). Aby uzyskać więcej informacji na temat technologii dostępu do danych w usłudze starszej wersji Visual C++, zobacz [dostęp do danych](/cpp/data/data-access-in-cpp).

## <a name="javascript"></a>JavaScript

[Język JavaScript w programie Visual Studio](/scripting/javascript/javascript-language-reference) do najważniejszych języków do tworzenia aplikacji dla wielu platform, aplikacje platformy uniwersalnej systemu Windows, usług w chmurze, witryn sieci Web i aplikacji sieci web. Bower, Grunt, Gulp, npm i NuGet z poziomu programu Visual Studio można użyć do zainstalowania z ulubionych bibliotek JavaScript i produktów w bazie danych. Podłączanie do usługi Azure storage i usług, pobierając zestawy SDK dostępne w [witryny sieci Web Azure](https://azure.microsoft.com/). Edge.js jest bibliotekę, która łączy JavaScript po stronie serwera (Node.js) do źródeł danych ADO.NET.

## <a name="python"></a>Python

Zainstaluj [obsługi języka Python w programie Visual Studio](../python/overview-of-python-tools-for-visual-studio.md) do tworzenia aplikacji Python. Dokumentacja usługi Azure składa się kilka samouczków na temat łączenia się z danymi, takie jak następujące:

- [Django i bazy danych SQL na platformie Azure](/azure/app-service/app-service-web-get-started-python)
- [Django i MySQL na platformie Azure](/azure/app-service-web/web-sites-python-ptvs-django-mysql)
- Praca z [obiektów blob](/azure/storage/blobs/storage-quickstart-blobs-python), [pliki](/azure/storage/files/storage-python-how-to-use-file-storage), [kolejek](/azure/storage/queues/storage-python-how-to-use-queue-storage), i [tabel (baza danych kosmetyczka)](/azure/cosmos-db/table-storage-how-to-use-python).

## <a name="related-topics"></a>Tematy pokrewne

[Platforma Microsoft AI](https://azure.microsoft.com/overview/ai-platform/?v=17.42w)&mdash;zawiera wprowadzenie do inteligentnej chmury firmy Microsoft, łącznie z pakietu Cortana Analytics i pomoc techniczna dla Internetu rzeczy.

[Usługa Microsoft Azure Storage](/azure/storage/)&mdash;zawiera opis usługi Azure Storage, a także jak tworzyć aplikacje przy użyciu obiektów blob platformy Azure, tabel, kolejek i plików.

[Usługa Azure SQL Database](/azure/sql-database/)&mdash;opisano, jak połączyć się z usługi Azure SQL Database, relacyjnej bazy danych jako usługa.

[SQL Server Data Tools](/sql/ssdt/download-sql-server-data-tools-ssdt)&mdash;opisano narzędzia, które upraszczają projektowanie i eksploracji, testowania i wdrażania aplikacji połączonych z usługą danych i baz danych.

[ADO.NET](/dotnet/framework/data/adonet/index)&mdash;w tym artykule opisano architekturę ADO.NET oraz jak używać klas ADO.NET do zarządzania danymi aplikacji i wchodzić w interakcje z źródła danych i XML.

[ADO.NET Entity Framework](https://docs.microsoft.com/ef/ef6/)&mdash;w tym artykule opisano sposób tworzenia aplikacji do danych, które umożliwiają deweloperom programować przy użyciu modelu koncepcyjnego zamiast bezpośrednio w odniesieniu do relacyjnej bazy danych.

[4.5 usług danych WCF](/dotnet/framework/data/wcf/index)&mdash;w tym artykule opisano sposób używania [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] do wdrożenia usług danych w Internecie lub intranecie, które implementują [Open Data Protocol (OData)](https://www.odata.org/).

[Dane w rozwiązaniach pakietu Office](../vsto/data-in-office-solutions.md)&mdash;zawiera łącza do tematów, które wyjaśniają jak działają dane w rozwiązaniach pakietu Office. W tym informacje dotyczące programowania schematycznego, buforowania danych i dostęp do danych po stronie serwera.

[LINQ (Language-Integrated Query)](/dotnet/csharp/linq/)&mdash;w tym artykule opisano możliwości zapytań wbudowane w języku C# i Visual Basic i wspólnego modelu wykonywania zapytań relacyjnych baz danych, dokumentów XML, zestawów danych i kolekcji w pamięci.

[Narzędzia XML w programie Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)&mdash;zawiera omówienie pracy z funkcjami .NET XML danych debugowania XSLT XML i architektury zapytanie w języku XML.

[Dokumenty i dane XML](/dotnet/standard/data/xml/index)&mdash;zawiera omówienie kompleksowego i zintegrowanego zestawu klas, które działają z dokumentów XML i dane na platformie .NET.
