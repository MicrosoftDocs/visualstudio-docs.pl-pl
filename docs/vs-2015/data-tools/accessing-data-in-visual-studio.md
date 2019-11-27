---
title: Uzyskiwanie dostępu do danych
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- "80025080"
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [Visual Studio]
- data access [Visual Studio]
- data [C#]
- ADO.NET, data access
ms.assetid: 9812a6d5-23d2-4427-8b98-70a2abfec3bc
caps.latest.revision: 103
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 158bc4c2fc7734957c7d3e946390ab1339a322ba
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299430"
---
# <a name="accessing-data-in-visual-studio"></a>Uzyskiwanie dostępu do danych w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio, można utworzyć aplikacji, które łączą się z danymi w praktycznie dowolnego produktu bazy danych lub usługi, w dowolnym formacie, dowolnym miejscu — na komputerze lokalnym, w sieci lokalnej lub w chmurze prywatnej, publicznej lub hybrydowej.

 Dla aplikacji JavaScript, Python, PHP, Ruby lub C++ możesz łączyć się dane tak jak dowolne inne, uzyskując bibliotek i pisania kodu. Dla aplikacji .NET Visual Studio udostępnia narzędzia, które umożliwia poznawanie źródeł danych, tworzyć modele obiektów do przechowywania i manipulowanie danymi w pamięci i powiązać dane z interfejsu użytkownika.     Microsoft Azure udostępnia zestawy SDK for .NET, Java, Node.js, PHP, Python, Ruby i aplikacje mobilne i narzędzi w programie Visual Studio do łączenia się z usługi Azure Storage.

 Poniższej przedstawiono kilka wiele systemów bazy danych i magazynu, które mogą być używane w programie Visual Studio. Oferty [Microsoft Azure](https://azure.microsoft.com/) to usługi danych, które obejmują wszystkie aprowizacji i administrowanie bazowym magazynem danych.  [Narzędzia systemu Azure dla programu Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) to opcjonalny składnik, który umożliwia współpracę z magazynami danych platformy Azure bezpośrednio z programu Visual Studio. Większość innych języków SQL i NoSQL bazy danych produktów, które są wymienione w tym miejscu mogą być hostowane na komputerze lokalnym, w sieci lokalnej lub w systemie Microsoft Azure na maszynie wirtualnej. W tym scenariuszu jesteś odpowiedzialny za zarządzanie sama baza danych.

 **Microsoft Azure**

||||
|-|-|-|
|Baza danych SQL|Baza danych DocumentDB|Storage (obiekty BLOB, tabel, kolejek, plików)|
|SQL Data Warehouse|SQL Server Stretch Database|Usługi StorSimple|

 i więcej...

 **SQL**

||||
|-|-|-|
|SQL Server 2005 — 2016, w tym Express i LocalDB|Firebird|MariaDB|
|MySQL|Oracle|PostgreSQL|
|Bazy danych SQLite|||

 i więcej...

 **NoSQL**

||||
|-|-|-|
|Apache Cassandra|CouchDB|MongoDB|
|Lokalizacji|OrientDB|RavenDB|
|VelocityDB|||

 i więcej...

 Wielu dostawców bazy danych i innych firm obsługuje integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z ofertami w witrynie nuget.org lub za pomocą Menedżera pakietów NuGet w programie Visual Studio (**narzędzia** > **menedżerze pakietów NuGet** > **Zarządzanie pakietami NuGet dla rozwiązania**). Inne produkty bazy danych Integracja z programem Visual Studio jako rozszerzenie.   Możesz przeglądać te oferty w galerii programu Visual Studio, przechodząc do pozycji **narzędzia** > **rozszerzenia i aktualizacje** , a następnie wybierając pozycję **online** w lewym okienku okna dialogowego.  Aby uzyskać więcej informacji, zobacz [Instalowanie systemów baz danych, narzędzi i przykładów](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Rozszerzona pomoc techniczna dla programu SQL Server 2005 zakończona w dniu 12 kwietnia 2016 r.   Nie ma żadnej gwarancji, że narzędzia danych w programie Visual Studio 2015 i nowszych wersjach będą w dalszym ciągu działać przy użyciu programu SQL Server 2005 po tej dacie. Aby uzyskać więcej informacji, zobacz [anons końca pomocy technicznej dla SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Języków .NET
 .NET dostępu do wszystkich danych, w tym programie .NET Core jest oparty na ADO.NET, zestaw klas, który definiuje interfejs do uzyskiwania dostępu do dowolnego rodzaju źródła danych relacyjnych i nierelacyjnych. Program Visual Studio ma kilka narzędzi i projektantów, współpracujących za pomocą narzędzia ADO.NET w celu łatwiejszego nawiązania połączenia z bazami danych, manipulowania danymi i prezentowania danych użytkownika. W dokumentacji w tej sekcji opisano sposób używania tych narzędzi. Ponadto można programować bezpośrednio w odniesieniu do obiektów poleceń ADO.NET. Aby uzyskać więcej informacji na temat bezpośredniego wywoływania interfejsów API ADO.NET, zobacz [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) w bibliotece MSDN.

 Aby uzyskać dokumentację dostępu do danych, która odnosi się w odniesieniu do ASP.NET, zobacz [Praca z danymi](https://docs.microsoft.com/aspnet/web-forms/overview/presenting-and-managing-data/) w witrynie ASP.NET. Aby zapoznać się z samouczkiem dotyczącym używania Entity Framework z ASP.NET MVC, zobacz [wprowadzenie z Entity Framework 6 Code First przy użyciu MVC 5](https://docs.microsoft.com/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Uniwersalnych platformy Windows (UWP) w języku C# lub Visual Basic można użyć zestawu Microsoft Azure SDK dla platformy .NET, dostęp do usługi Azure Storage i innymi usługami platformy Azure. Klasa Windows.Web.HttpClient umożliwia komunikację z dowolnej usługi RESTful. Aby uzyskać więcej informacji, zobacz [jak nawiązać połączenie z serwerem HTTP przy użyciu systemu Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 Do przechowywania danych na komputerze lokalnym Zalecanym podejściem jest użycie bazy danych SQLite, która jest uruchamiana w tym samym procesie co aplikacja. Jeśli wymagana jest warstwa Mapowania obiektowo relacyjny (ORM), można użyć programu Entity Framework. Aby uzyskać więcej informacji, zobacz [dostęp do danych](https://msdn.microsoft.com/windows/uwp/data-access/index) w centrum deweloperów systemu Windows.

 Jeśli łączysz się z usługami platformy Azure, pamiętaj o pobraniu najnowszych [narzędzi zestawu Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Dostawcy danych
 Aby można było korzystać z bazy danych w programie ADO.NET, musi ona mieć niestandardowego *dostawcę danych ADO.NET* lub musi uwidaczniać interfejs ODBC lub OLE DB. Firma Microsoft udostępnia [listę dostawców danych ADO.NET](https://msdn.microsoft.com/data/dd363565) dla produktów SQL Server, a także dostawców ODBC i OLE DB.

#### <a name="data-modeling"></a>Modelowanie danych
 Na platformie .NET dostępne są trzy możliwości do modelowania i manipulowanie danymi w pamięci po jej pobraniu ze źródła danych:

 Entity Framework preferowaną technologię ORM firmy Microsoft. Umożliwia ona Programowanie w relacyjnej bazie danych jako najwyższej klasy obiektów platformy .NET. Gdy model jest wymagany dla nowych aplikacji, powinno być pierwszy wybór domyślny. Wymaga ona dodatkowej pomocy technicznej od podstawowego dostawcy ADO.NET.

 LINQ do SQL maper obiektowo relacyjny starszej generacji. Działa dobrze sprawdza się w mniej złożonych scenariuszy, ale nie jest już aktywnie.

 Zestawy danych najstarsze trzy technologie modelowania. Jest ona przeznaczona przede wszystkim do szybkiego opracowywania aplikacji "formularzy nad danymi", w których są nie przetwarzanie ogromnych ilości danych lub wykonywania kwerend złożonych lub przekształcenia. Obiekt DataSet składa się z elementu DataTable i DataRow obiektów, które logicznie znacznie więcej niż obiekty .NET podobne obiekty bazy danych SQL. Stosunkowo proste aplikacje oparte na SQL źródła danych zestawy danych nadal może być dobrym wyborem.

 Nie istnieje wymóg, aby użyć dowolnego z tych technologii. W niektórych scenariuszach, szczególnie w przypadku, gdy wydajność jest krytyczna, można po prostu użyć obiektu DataReader do odczytu z bazy danych i skopiować wartości, które są potrzebne do obiektu kolekcji, takiego jak list\<T >.

### <a name="native-c"></a>Natywnych języka C++
 C++aplikacje łączące się z SQL Server powinny używać [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Możesz uzyskać dostęp do innych baz danych za pomocą [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) lub sterowników OLE DB bezpośrednio. ODBC jest bieżącego interfejsu database w warstwie standardowa, ale większość systemów bazy danych dostarczają niestandardowych funkcjonalności, które nie są dostępne za pośrednictwem interfejsu ODBC.  OLE DB jest technologią starszą dostęp do danych modelu COM, która jest w dalszym ciągu obsługiwany, ale nie jest zalecane dla nowych aplikacji.  Aby uzyskać więcej informacji, zobacz [dostęp do danych](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 C++programy korzystające z usług REST mogą korzystać z [ C++ zestawu SDK REST](https://github.com/Microsoft/cpprestsdk).

 C++programy, które współpracują z Microsoft Azure Storage mogą korzystać z [klienta Microsoft Azure Storage](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelowanie danych
 Program Visual Studio nie zapewnia warstwę ORM dla języka C++.  [ODB](https://www.codesynthesis.com/products/odb/) to popularny obiekt ORM typu open source dla C++programu.

 Aby uzyskać więcej informacji na temat C++ starszych technologii dostępu do danych wizualnych, zobacz [dostęp do danych](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 Język [JavaScript w programie Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) to pierwsza klasa języka do tworzenia aplikacji dla wielu platform, aplikacji platformy UWP, usług Cloud Services, witryn sieci Web i aplikacji internetowych. Bower, Grunt, Gulp, npm i NuGet z poziomu programu Visual Studio można użyć do zainstalowania z ulubionych bibliotek JavaScript i produktów w bazie danych. Połącz się z usługą Azure Storage i usługami, pobierając zestawy SDK z [witryny sieci Web systemu Azure](https://azure.microsoft.com/).  Edge.js jest bibliotekę, która łączy JavaScript po stronie serwera (Node.js) do źródeł danych ADO.NET.

### <a name="python"></a>Python
 Zainstaluj [Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) wraz z ulubioną strukturą języka Python, aby tworzyć aplikacje CPython lub IronPython (.NET).  Witryna sieci Web Python Tools for Visual Studio zawiera kilka samouczków dotyczących łączenia się z danymi, w tym [Django i SQL Database na platformie Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django i MySQL na platformie Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) oraz [w butelkach i MongoDB na platformie Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>W tej sekcji
 [Instalowanie systemów baz danych, narzędzi i przykładów](../data-tools/installing-database-systems-tools-and-samples.md) W tym artykule omówiono sposób uzyskiwania produktów bazy danych oraz rozszerzeń lub sterowników programu Visual Studio, które je obsługują, a także znajdowania przykładowych baz danych na potrzeby eksperymentowania i uczenia się.

 [Visual Studio Data Tools dla platformy .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Opisuje sposób używania okien narzędzi programu Visual Studio do łączenia się ze źródłami danych, tworzenia zestawów danych lub modeli Entity Framework i powiązania danych z kontrolkami interfejsu użytkownika.

## <a name="related-topics"></a>Tematy pokrewne
 [Dane, urządzenia i analiza](https://msdn.microsoft.com/data-and-devices) Zawiera wprowadzenie do inteligentnej chmury firmy Microsoft, w tym pakietu Cortana Analytics Suite i pomocy technicznej dla Internet rzeczy.

 [Microsoft Azure Storage](/azure/storage/) Opisuje usługę Azure Storage oraz sposób tworzenia aplikacji przy użyciu obiektów blob, tabel, kolejek i plików platformy Azure.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) Opisuje sposób nawiązywania połączenia z Azure SQL Database, relacyjną bazą danych jako usługą.

 [Narzędzia danych SQL Server](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Zawiera opis narzędzi, które upraszczają projektowanie, eksplorację, testowanie i wdrażanie aplikacji połączonych z danymi oraz baz danych.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) W tym artykule opisano architekturę ADO.NET oraz sposób używania klas ADO.NET do zarządzania danymi aplikacji i współdziałania ze źródłami danych i XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) Zawiera opis sposobu tworzenia aplikacji do danych, które umożliwiają deweloperom programowanie w modelu koncepcyjnym, a nie bezpośrednio w odniesieniu do relacyjnej bazy danych.

 [Usługi danych programu WCF 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Opisuje, jak używać [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] do wdrażania usług danych w sieci Web lub intranet, które implementują [protokół Open Data Protocol (OData)](https://go.microsoft.com/fwlink/?LinkID=182204).

 [Dane w rozwiązaniach pakietu Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Zawiera łącza do tematów, które wyjaśniają, jak dane działają w rozwiązaniach pakietu Office. W tym informacje dotyczące programowania schematycznego, buforowania danych i dostęp do danych po stronie serwera.

 [LINQ (zapytanie zintegrowane z językiem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Opisuje możliwości zapytania wbudowane w C# i Visual Basic oraz wspólny model służący do wykonywania zapytań dotyczących relacyjnych baz danych, dokumentów XML, zestawów danych i kolekcji w pamięci.

 [Narzędzia XML w programie Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) W tym artykule omówiono pracę z danymi XML, debugowanie XSLT, .NET Framework funkcje XML i architekturę kwerendy XML.

 [Dokumenty i dane XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Zawiera omówienie kompleksowego i zintegrowanego zestawu klas, które współpracują z dokumentami XML i danymi w .NET Framework.
