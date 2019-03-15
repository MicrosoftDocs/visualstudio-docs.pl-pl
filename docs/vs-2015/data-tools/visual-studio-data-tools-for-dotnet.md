---
title: Narzędzia Visual Studio data tools dla platformy .NET | Dokumentacja firmy Microsoft
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: da5578321e9c637b12ffbb253a9c0d4c4f87dfe9
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57870501"
---
# <a name="visual-studio-data-tools-for-net"></a>Narzędzia do obsługi danych programu Visual Studio dla platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio i .NET Framework razem zapewniają szeroką interfejsu API i narzędzia do obsługi łączenie z bazami danych, modelowania danych w pamięci i wyświetlanie danych w interfejsie użytkownika.  Klasy .NET Framework, które oferują funkcje dostępu do danych są znane jako [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, wraz z danymi narzędzi w programie Visual Studio został pierwotnie zaprojektowany głównie w celu obsługi relacyjnych baz danych i XML. Te dni wielu dostawców bazy danych NoSQL lub stronom trzecim, oferują dostawcy ADO.NET.  
  
 Visual Studio 2015 Update 2 zawiera najnowsze aktualizacje programu [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), umożliwiają one obsługę najnowszych funkcji platformy Azure [bazy danych SQL](https://azure.microsoft.com/services/sql-database/) i [programu SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [.NET core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) obsługuje ADO.NET, z wyjątkiem zestawy danych i powiązanych typów. Jeśli są przeznaczone dla platformy .NET Core i wymagają warstwy mapowania obiektowo relacyjny (ORM), użyj [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).  
  
 Na poniższym diagramie przedstawiono uproszczony widok podstawowej architektury:  
  
 ![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata Diagram architektury ADO.NET")  
  
 Typowy przepływ pracy to:  
  
1. Zainstaluj rozwoju lub bazy danych testów na komputerze lokalnym. Zobacz [instalowanie systemów baz danych, narzędzia i przykłady](../data-tools/installing-database-systems-tools-and-samples.md). Jeśli używasz usługi danych platformy Azure, ten krok nie jest konieczne.  
  
2. Przetestuj połączenie z bazą danych (lub usługi lub plik lokalny) w programie Visual Studio. Zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).  
  
3. (Opcjonalnie) Narzędzia do generowania i skonfigurować nowy model. Modele oparte na platformie Entity Framework są określenia domyślnego zalecenia w przypadku nowych aplikacji. Model, niezależnie od jednej z nich, jest źródło danych, które aplikacja wchodzi w interakcje z. Model logicznie znajduje się pomiędzy bazy danych lub usługi i aplikacji.  Zobacz [dodasz nowe źródła danych](../data-tools/add-new-data-sources.md).  
  
4. Przeciągnij źródła danych z **źródeł danych** okna na powierzchni projektowej Windows Forms, ASP.NET lub Windows Presentation Foundation do generowania kodu wiązania danych, które będą wyświetlane dane użytkownika w taki sposób, który określisz. Zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
5. Dodawanie kodu niestandardowego, w przypadku elementów, takich jak reguły biznesowe, wyszukiwania i sprawdzanie poprawności danych lub skorzystaj z zalet funkcji niestandardowych, który udostępnia w źródłowej bazie danych.  
  
   Można pominąć krok 3 i programowania aplikacji .NET w celu wydawania poleceń, bezpośrednio do bazy danych, a nie przy użyciu modelu. W tym przypadku znajdziesz tutaj odpowiedniej dokumentacji: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Pamiętaj, że nadal można używać Kreatora konfiguracji źródła danych i projektantów do generowania kodu wiązania danych, podczas wypełniania obiektów w pamięci, a następnie powiązanie danych kontrolki interfejsu użytkownika do tych obiektów.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
-   [Tworzenie prostej aplikacji do obsługi danych za pomocą pakietu ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)  
  
-   [Dodawanie nowych połączeń](../data-tools/add-new-connections.md)  
  
-   [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)  
  
-   [Narzędzia modelu Entity Data Model w programie Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)  
  
-   [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)  
  
-   [Narzędzia LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)  
  
-   [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)  
  
-   [Dodatkowe zasoby dla rozwiązywania problemów z błędami dostępu do danych](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
-   [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)  
  
-   [Tworzenie baz danych i aplikacji warstw danych oraz zarządzanie nimi w programie Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)  
  
-   [Dodatkowe zasoby dla rozwiązywania problemów z błędami dostępu do danych](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
