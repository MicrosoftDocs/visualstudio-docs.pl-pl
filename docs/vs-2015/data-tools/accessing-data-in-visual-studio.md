---
title: Dostęp do danych
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
ms.openlocfilehash: 78d950b777d866835ef516c4910180b21de295e9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545005"
---
# <a name="accessing-data-in-visual-studio"></a>Uzyskiwanie dostępu do danych w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio można tworzyć aplikacje, które łączą się z danymi praktycznie dowolnego produktu lub usługi bazy danych, w dowolnym formacie, w dowolnym miejscu — na komputerze lokalnym, w sieci lokalnej lub w chmurze publicznej, prywatnej lub hybrydowej.

 W przypadku aplikacji w językach JavaScript, Python, PHP, Ruby lub C++ możesz łączyć się z danymi, takimi jak coś innego, pobierając biblioteki i pisząc kod. W przypadku aplikacji .NET program Visual Studio udostępnia narzędzia umożliwiające Eksplorowanie źródeł danych, tworzenie modeli obiektów do przechowywania i manipulowanie danymi w pamięci oraz Powiązywanie danych z interfejsem użytkownika.     Microsoft Azure udostępnia zestawy SDK dla aplikacji .NET, Java, Node.js, PHP, Python, Ruby i Mobile oraz narzędzia w programie Visual Studio do łączenia się z usługą Azure Storage.

 Na poniższych listach przedstawiono zaledwie kilka systemów baz danych i pamięci masowej, które mogą być używane w programie Visual Studio. Oferty [Microsoft Azure](https://azure.microsoft.com/) to usługi danych, które obejmują wszystkie aprowizacji i administrowanie bazowym magazynem danych.  [Narzędzia systemu Azure dla programu Visual Studio](https://www.visualstudio.com/features/azure-tools-vs.aspx) to opcjonalny składnik, który umożliwia współpracę z magazynami danych platformy Azure bezpośrednio z programu Visual Studio. Większość innych produktów baz danych SQL i NoSQL, które są wymienione w tym miejscu, mogą być hostowane na komputerze lokalnym, w sieci lokalnej lub w Microsoft Azure na maszynie wirtualnej. W tym scenariuszu użytkownik jest odpowiedzialny za zarządzanie bazą danych.

 **Microsoft Azure**

- Baza danych SQL

- DocumentDB

-Storage (obiekty blob, tabele, kolejki, pliki)

- SQL Data Warehouse

- SQL Server Stretch Database

- Magazyn StorSimple

 I nie tylko...

 **SQL**

- SQL Server 2005 — 2016, w tym Express i LocalDB
- Firebird
- MariaDB
- MySQL
- Oracle
- PostgreSQL
- SQLite

 I nie tylko...

 **NoSQL**

- Apache Cassandra
- CouchDB
- MongoDB
- NDatabase
- OrientDB
- RavenDB
- VelocityDB

 I nie tylko...

 Wielu dostawców baz danych i inne firmy obsługują integrację z programem Visual Studio przez pakiety NuGet. Możesz zapoznać się z ofertami w witrynie NuGet.org lub za pomocą Menedżera pakietów NuGet w programie Visual Studio (**Narzędzia**  >  **Menedżer pakietów NuGet**zarządzanie pakietami  >  **NuGet dla rozwiązania**). Inne produkty bazy danych integrują się z programem Visual Studio jako rozszerzeniem.   Możesz przeglądać te oferty w galerii programu Visual Studio, przechodząc do pozycji **Narzędzia**  >  **rozszerzenia i aktualizacje** , a następnie wybierając pozycję **online** w lewym okienku okna dialogowego.  Aby uzyskać więcej informacji, zobacz [Instalowanie systemów baz danych, narzędzi i przykładów](../data-tools/installing-database-systems-tools-and-samples.md).

> [!NOTE]
> Rozszerzona pomoc techniczna dla SQL Server 2005 zakończyła się 12 kwietnia 2016.   Nie ma gwarancji, że narzędzia danych w programie Visual Studio 2015 i nowszych będą nadal działały z SQL Server 2005 po tej dacie. Aby uzyskać więcej informacji, zobacz [anons końca pomocy technicznej dla SQL Server 2005](https://www.microsoft.com/sql-server/sql-server-2005).

### <a name="net-languages"></a>Języki .NET
 Wszystkie funkcje dostępu do danych platformy .NET, w tym na platformie .NET Core, bazują na ADO.NET, zestawie klas, który definiuje interfejs do uzyskiwania dostępu do dowolnego rodzaju źródła danych, zarówno relacyjnych, jak i nierelacyjnych. Program Visual Studio zawiera kilka narzędzi i projektantów, które współpracują z usługą ADO.NET, aby ułatwić łączenie się z bazami danych, manipulowanie danymi oraz prezentowanie danych użytkownikom. W dokumentacji w tej sekcji opisano sposób korzystania z tych narzędzi. Możesz również programować bezpośrednio w odniesieniu do obiektów poleceń ADO.NET. Aby uzyskać więcej informacji na temat bezpośredniego wywoływania interfejsów API ADO.NET, zobacz [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx) w bibliotece MSDN.

 Aby uzyskać dokumentację dostępu do danych, która odnosi się w odniesieniu do ASP.NET, zobacz [Praca z danymi](/aspnet/web-forms/overview/presenting-and-managing-data/) w witrynie ASP.NET. Aby zapoznać się z samouczkiem dotyczącym używania Entity Framework z ASP.NET MVC, zobacz [wprowadzenie z Entity Framework 6 Code First przy użyciu MVC 5](/aspnet/mvc/overview/getting-started/getting-started-with-ef-using-mvc/creating-an-entity-framework-data-model-for-an-asp-net-mvc-application).

 Aplikacje platforma uniwersalna systemu Windows (platformy UWP) w języku C# lub Visual Basic mogą używać Zestaw Microsoft Azure SDK dla platformy .NET do uzyskiwania dostępu do usługi Azure Storage i innych usług platformy Azure. Klasa Windows. Web. HttpClient umożliwia komunikację z dowolną usługą RESTful. Aby uzyskać więcej informacji, zobacz [jak nawiązać połączenie z serwerem HTTP przy użyciu systemu Windows. Web. http](https://msdn.microsoft.com/library/windows/apps/dn469430.aspx).

 W przypadku przechowywania danych na komputerze lokalnym zalecanym rozwiązaniem jest użycie oprogramowania SQLite, które jest uruchamiane w tym samym procesie co aplikacja. Jeśli wymagana jest warstwa mapowania obiektów relacyjnych (ORM), można użyć Entity Framework. Aby uzyskać więcej informacji, zobacz [dostęp do danych](https://msdn.microsoft.com/windows/uwp/data-access/index) w centrum deweloperów systemu Windows.

 Jeśli łączysz się z usługami platformy Azure, pamiętaj o pobraniu najnowszych [narzędzi zestawu Azure SDK](https://azure.microsoft.com/downloads/).

#### <a name="data-providers"></a>Dostawcy danych
 Aby można było korzystać z bazy danych w programie ADO.NET, musi ona mieć niestandardowego *dostawcę danych ADO.NET* lub musi uwidaczniać interfejs ODBC lub OLE DB. Firma Microsoft udostępnia [listę dostawców danych ADO.NET](https://msdn.microsoft.com/data/dd363565) dla produktów SQL Server, a także dostawców ODBC i OLE DB.

#### <a name="data-modeling"></a>Modelowanie danych
 W programie .NET dostępne są trzy opcje modelowania i manipulowania danymi w pamięci po pobraniu ich ze źródła danych:

 Entity Framework preferowaną technologię Microsoft ORM. Można jej używać do programowania danych relacyjnych jako obiektów pierwszej klasy .NET. W przypadku nowych aplikacji powinien być pierwszym wyborem, gdy wymagany jest model. Wymaga to obsługi niestandardowej od bazowego dostawcy ADO.NET.

 LINQ to SQL mapowania obiektu starszej generacji. Dobrze sprawdza się w przypadku mniej złożonych scenariuszy, ale nie jest już aktywnym programowaniem.

 Ustawia najstarsze z trzech technologii modelowania. Jest ona zaprojektowana głównie do szybkiego opracowywania aplikacji "Forms na dane", w których nie są przetwarzane ogromne ilości danych ani wykonywanie złożonych zapytań lub transformacji. Obiekt DataSet składa się z obiektów DataTable i DataRow, które logicznie przypominają obiekty bazy danych SQL znacznie więcej niż obiekty .NET. W przypadku stosunkowo prostej aplikacji opartej na źródłach danych SQL, nadal może być to dobry wybór.

 Korzystanie z tych technologii nie jest wymagane. W niektórych scenariuszach, szczególnie w przypadku, gdy wydajność jest krytyczna, można po prostu użyć obiektu DataReader do odczytu z bazy danych i skopiować wartości, które są potrzebne do obiektu kolekcji, takiego jak List \<T> .

### <a name="native-c"></a>Natywny język C++
 Aplikacje C++, które łączą się z SQL Server powinny używać [SQL Server Native Client](https://msdn.microsoft.com/sqlserver/aa937733.aspx). Możesz uzyskać dostęp do innych baz danych za pomocą [ODBC](https://msdn.microsoft.com/library/ms710252\(v=vs.85\).aspx) lub sterowników OLE DB bezpośrednio. ODBC jest bieżącym standardowym interfejsem bazy danych, ale większość systemów baz danych oferuje niestandardowe funkcje, do których nie można uzyskać dostępu za pośrednictwem interfejsu ODBC.  OLE DB to Starsza technologia dostępu do danych COM, która jest nadal obsługiwana, ale nie jest zalecana w przypadku nowych aplikacji.  Aby uzyskać więcej informacji, zobacz [dostęp do danych](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b).

 Programy c++ korzystające z usług REST mogą korzystać z [zestawu SDK REST języka c++](https://github.com/Microsoft/cpprestsdk).

 Programy w języku C++, które współpracują z Microsoft Azure Storage mogą korzystać z [klienta Microsoft Azure Storage](https://www.nuget.org/packages/wastorage).

#### <a name="data-modeling"></a>Modelowanie danych
 Program Visual Studio nie udostępnia warstwy ORM dla języka C++.  [ODB](https://www.codesynthesis.com/products/odb/) to popularne ORM typu open source dla języka C++.

 Aby uzyskać więcej informacji na temat starszych technologii dostępu do danych Visual C++, zobacz [dostęp do danych](https://msdn.microsoft.com/library/a9455752-39c4-4457-b14e-197772d3df0b)

### <a name="javascript"></a>JavaScript
 Język [JavaScript w programie Visual Studio](https://msdn.microsoft.com/library/hh334522.aspx) to pierwsza klasa języka do tworzenia aplikacji dla wielu platform, aplikacji platformy UWP, usług Cloud Services, witryn sieci Web i aplikacji internetowych. Możesz użyć Bower, grunt, Gulp, npm i NuGet z poziomu programu Visual Studio, aby zainstalować Ulubione biblioteki JavaScript i produkty bazy danych. Połącz się z usługą Azure Storage i usługami, pobierając zestawy SDK z [witryny sieci Web systemu Azure](https://azure.microsoft.com/).  Edge.js to biblioteka, która łączy kod JavaScript po stronie serwera (Node.js) ze źródłami danych ADO.NET.

### <a name="python"></a>Python
 Zainstaluj [Python Tools for Visual Studio](http://microsoft.github.io/PTVS/) wraz z ulubioną strukturą języka Python, aby tworzyć aplikacje CPython lub IronPython (.NET).  Witryna sieci Web Python Tools for Visual Studio zawiera kilka samouczków dotyczących łączenia się z danymi, w tym [Django i SQL Database na platformie Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-SQL-Database-on-Azure), [Django i MySQL na platformie Azure](https://github.com/Microsoft/PTVS/wiki/Django-and-MySQL-on-Azure) oraz [w butelkach i MongoDB na platformie Azure](https://github.com/Microsoft/PTVS/wiki/Bottle-and-MongoDB-on-Azure).

## <a name="in-this-section"></a>W tej sekcji
 [Instalowanie systemów baz danych, narzędzi i przykładów](../data-tools/installing-database-systems-tools-and-samples.md) W tym artykule omówiono sposób uzyskiwania produktów bazy danych oraz rozszerzeń lub sterowników programu Visual Studio, które je obsługują, a także znajdowania przykładowych baz danych na potrzeby eksperymentowania i uczenia się.

 [Visual Studio Data Tools dla platformy .NET](https://msdn.microsoft.com/6b145922-2f00-47db-befc-bf351b4809a1) Opisuje sposób używania okien narzędzi programu Visual Studio do łączenia się ze źródłami danych, tworzenia zestawów danych lub modeli Entity Framework i powiązania danych z kontrolkami interfejsu użytkownika.

## <a name="related-topics"></a>Powiązane tematy
 [Dane, urządzenia i analiza](https://msdn.microsoft.com/data-and-devices) Zawiera wprowadzenie do inteligentnej chmury firmy Microsoft, w tym pakietu Cortana Analytics Suite i pomocy technicznej dla Internet rzeczy.

 [Microsoft Azure Storage](/azure/storage/) Opisuje usługę Azure Storage oraz sposób tworzenia aplikacji przy użyciu obiektów blob, tabel, kolejek i plików platformy Azure.

 [Azure SQL Database](https://azure.microsoft.com/documentation/services/sql-database/) Opisuje sposób nawiązywania połączenia z Azure SQL Database, relacyjną bazą danych jako usługą.

 [Narzędzia danych SQL Server](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx) Zawiera opis narzędzi, które upraszczają projektowanie, eksplorację, testowanie i wdrażanie aplikacji połączonych z danymi oraz baz danych.

 [ADO.NET](https://msdn.microsoft.com/library/5b96ed06-9759-4966-a797-a1d5f6ee50ca) W tym artykule opisano architekturę ADO.NET oraz sposób używania klas ADO.NET do zarządzania danymi aplikacji i współdziałania ze źródłami danych i XML.

 [ADO.NET Entity Framework](https://msdn.microsoft.com/data/ef) Zawiera opis sposobu tworzenia aplikacji do danych, które umożliwiają deweloperom programowanie w modelu koncepcyjnym, a nie bezpośrednio w odniesieniu do relacyjnej bazy danych.

 [Usługi danych programu WCF 4,5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a) Opisuje, jak używać [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] programu do wdrażania usług danych w sieci Web lub intranecie implementujących [protokół Open Data Protocol (OData)](https://www.odata.org/).

 [Dane w rozwiązaniach pakietu Office](https://msdn.microsoft.com/library/8478c095-864b-4ed3-8a70-1fc19b411c6a) Zawiera łącza do tematów, które wyjaśniają, jak dane działają w rozwiązaniach pakietu Office. Obejmuje to informacje o programowaniu zorientowanym na schematach, buforowaniu danych i dostępie do danych po stronie serwera.

 [LINQ (zapytanie zintegrowane z językiem)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) Opisuje możliwości zapytania wbudowane w Języki C# i Visual Basic oraz wspólny model służący do wykonywania zapytań dotyczących relacyjnych baz danych, dokumentów XML, zestawów danych i kolekcji w pamięci.

 [Narzędzia XML w programie Visual Studio](../xml-tools/xml-tools-in-visual-studio.md) W tym artykule omówiono pracę z danymi XML, debugowanie XSLT, .NET Framework funkcje XML i architekturę kwerendy XML.

 [Dokumenty i dane XML](https://msdn.microsoft.com/library/e695047f-3c0f-4045-8708-5baea91cc380) Zawiera omówienie kompleksowego i zintegrowanego zestawu klas, które współpracują z dokumentami XML i danymi w .NET Framework.
