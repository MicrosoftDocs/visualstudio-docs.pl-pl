---
title: Instalowanie systemów baz danych, narzędzi i przykładów | Microsoft Docs
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
- sample databases
- databases, samples
ms.assetid: 821de34b-eaa9-40af-b9aa-b8305de16899
caps.latest.revision: 31
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 091338e411369e40f19e028cd19b6cb2e697718c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74299601"
---
# <a name="installing-database-systems-tools-and-samples"></a>Instalowanie systemów baz danych, narzędzi i przykładów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio nie zawiera żadnych systemów baz danych innych niż używane wewnętrznie. Do tworzenia aplikacji połączonych danych w programie Visual Studio, zazwyczaj instaluje system bazy danych na lokalnej maszynie do programowania, a następnie wdrażanie aplikacji i baz danych w środowisku produkcyjnym kiedy będą gotowe. Aby można było uzyskać dostęp do systemu bazy danych z aplikacji .NET i były one widoczne w oknach narzędzi danych programu Visual Studio, musi on mieć dostawcę danych ADO.NET. Dostawca musi obsługiwać specjalnie Entity Framework, jeśli planowane jest użycie jednostki danych modeli w aplikacji .NET.     Wielu dostawców jest oferowany za pomocą Menedżera pakietów NuGet lub Galerii programu Visual Studio.

 W przypadku programowania w języku SQL upewnij się, że masz narzędzia do SQL Server danych zainstalowane w programie Visual Studio. Kliknij menu **Widok** . Jeśli nie widzisz Eksplorator obiektów SQL Server, przejdź do panelu sterowania i zmień program Visual Studio. W instalatorze wybierz pozycję **Narzędzia danych Microsoft SQL Server**.

 Jeśli używasz interfejsów API usługi Azure Storage, zainstaluj emulatory usługi Azure Storage na maszynie lokalnej podczas opracowywania, aby uniknąć naliczania opłat do momentu, aż wszystko będzie gotowe do wdrożenia w środowisku produkcyjnym. Aby uzyskać więcej informacji, zobacz [Używanie emulatora usługi Azure Storage do programowania i testowania](https://azure.microsoft.com/documentation/articles/storage-use-emulator/).

 Poniższa lista zawiera niektóre z najpopularniejszych systemów bazy danych, które mogą być używane w projektach programu Visual Studio. Lista nie jest wyczerpująca. Aby zapoznać się z listą innych dostawców, którzy oferują ADO.NET dostawcy danych, którzy umożliwiają ścisłą integrację z narzędziami programu Visual Studio, zobacz [ADO.NET dostawcy danych](https://msdn.microsoft.com/library/dd363565.aspx).

### <a name="microsoft-sql-server"></a>Microsoft SQL Server
 SQL Server jest baza danych programu Microsoft sztandarowe oferty. SQL Server 2016 zapewnia przełomową wydajność, zabezpieczeniami zaawansowanymi i rozbudowane, zintegrowane raportowania i analizy. Jest on dostarczany w różnych wersjach, które są przeznaczone do różnych celów: z analiz biznesowych o wysokim stopniu skalowalności, wysokiej wydajności, do użycia na jednym komputerze. SQL Server Express jest w pełni funkcjonalna wersja programu SQL Server, które są dopasowane do ponownej dystrybucji i osadzania.  LocalDB to Uproszczona wersja programu SQL Server Express, która nie wymaga konfigurowania i działa w procesie aplikacji. Możesz pobrać albo oba produkty ze [strony pobierania SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express). Wiele przykładów SQL w tej sekcji Użyj programu SQL Server LocalDB. SQL Server Management Studio (SSMS) to aplikacja do zarządzania autonomicznej bazy danych, który ma więcej funkcji niż podana w Eksploratorze obiektów serwera SQL programu Visual Studio. Możesz pobrać program SSMS z poprzedniej konsolidacji.

### <a name="oracle"></a>Oracle
 Na stronie [sieci technologii Oracle](http://www.oracle.com/technetwork/database/enterprise-edition/downloads/index-092322.html) można pobrać płatną lub bezpłatną wersję bazy danych Oracle. Aby zapewnić obsługę Entity Framework i TableAdapters, konieczne będzie [Narzędzia deweloperskie Oracle dla programu Visual Studio](https://www.oracle.com/database/technologies/developer-tools/visual-studio/). Inne oficjalne produktów Oracle, w tym błyskawiczne wersję klienta Oracle, są dostępne za pośrednictwem Menedżera pakietów NuGet.  Przykładowe schematy programu Oracle można pobrać, postępując zgodnie z instrukcjami w [dokumentacji usługi Oracle online](https://docs.oracle.com/cd/E11882_01/server.112/e10831/toc.htm).

### <a name="mysql"></a>MySQL
 MySQL to system popularnych bazy danych typu open source, który jest powszechnie używana w przedsiębiorstwach i witryn sieci Web. Pliki do pobrania dla programu MySQL, MySQL dla programu Visual Studio i powiązane produkty są dostępne w witrynie [MySQL w systemie Windows](https://www.mysql.com/why-mysql/windows/).  Trzecim oferują różne rozszerzenia programu Visual Studio i zarządzania autonomicznej aplikacji pod kątem MySQL. Oferty można przeglądać w Menedżerze pakietów NuGet (**narzędzia** > **menedżerze pakietów NuGet** > **Zarządzanie pakietami NuGet dla rozwiązania**).

### <a name="postgresql"></a>PostgreSQL
 PostgreSQL jest systemem relacyjnej bazy danych obiektu bezpłatny, open source. Aby zainstalować ją w systemie Windows, można pobrać ją ze [strony pobierania PostgreSQL](http://www.postgresql.org/download/windows/).  Można także utworzyć PostgreSQL z kodu źródłowego.  PostgreSQL podstawowego systemu obejmuje interfejs języka C. Wiele firm Obejmij pakietów NuGet za pomocą PostgreSQL z poziomu aplikacji .NET.  Oferty można przeglądać w Menedżerze pakietów NuGet (**narzędzia** > **menedżerze pakietów NuGet** > **Zarządzanie pakietami NuGet dla rozwiązania**). Być może najpopularniejszy pakiet jest dostarczany przez [npgsql.org](http://www.npgsql.org/).

### <a name="sqlite"></a>Bazy danych SQLite
 Bazy danych SQLite jest osadzony aparat bazy danych SQL działa w procesie własnych aplikacji. Można go pobrać ze [strony pobierania oprogramowania SQLite](http://www.sqlite.org/download.html). Dostępne są także wiele innych pakietów NuGet dla bazy danych SQLite. Oferty można przeglądać w Menedżerze pakietów NuGet (**narzędzia** > **menedżerze pakietów NuGet** > **Zarządzanie pakietami NuGet dla rozwiązania**).

### <a name="firebird"></a>Firebird
 Firebird to system bazy danych SQL typu open source. Można go pobrać ze [strony pobierania Firebird](http://firebirdsql.org/en/downloads/). Dostawca danych programu ADO.NET jest dostępna za pośrednictwem Menedżera pakietów NuGet.

## <a name="see-also"></a>Zobacz też
 [Jak określić wersję i wydanie SQL Server i jej składników](https://support.microsoft.com/help/321185/how-to-determine-the-version-edition-and-update-level-of-sql-server-an)
