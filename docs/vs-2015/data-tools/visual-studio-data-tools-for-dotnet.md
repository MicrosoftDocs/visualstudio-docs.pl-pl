---
title: Visual Studio Data Tools dla platformy .NET | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670098"
---
# <a name="visual-studio-data-tools-for-net"></a>Narzędzia do obsługi danych programu Visual Studio dla platformy .NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Program Visual Studio i .NET Framework razem zapewniają szeroką obsługę interfejsów API i narzędzi do łączenia się z bazami danych, modelowania danych w pamięci i wyświetlania danych w interfejsie użytkownika.  Klasy .NET Framework, które zapewniają funkcje dostępu do danych, są znane jako [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). ADO.NET, wraz z narzędziami do obsługi danych w programie Visual Studio, została pierwotnie zaprojektowana głównie w celu obsługiwania relacyjnych baz danych i XML. W tych dniach wiele dostawców baz danych NoSQL lub innych firm oferuje dostawców ADO.NET.

 Program Visual Studio 2015 Update 2 zawiera najnowsze aktualizacje [narzędzi SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx), które umożliwiają obsługę najnowszych funkcji usługi Azure [SQL Database](https://azure.microsoft.com/services/sql-database/) i [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016). [Platforma .NET Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) obsługuje ADO.NET, z wyjątkiem zestawów danych i powiązanych typów. Jeśli celem jest platforma .NET Core i wymagana jest warstwa mapowania obiektów (ORM), użyj [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx).

 Na poniższym diagramie przedstawiono uproszczony widok podstawowej architektury:

 ![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png "Diagram architektury raddata ADO.NET")

 Typowy przepływ pracy to:

1. Zainstaluj programistyczną lub testową bazę danych na komputerze lokalnym. Zobacz [Instalowanie systemów baz danych, narzędzi i przykładów](../data-tools/installing-database-systems-tools-and-samples.md). Jeśli używasz usługi danych platformy Azure, ten krok nie jest konieczny.

2. Przetestuj połączenie z bazą danych (lub usługą lub plikiem lokalnym) w programie Visual Studio. Zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

3. Obowiązkowe Użyj narzędzi, aby wygenerować i skonfigurować nowy model. Modele oparte na Entity Framework są domyślnymi zaleceniami dla nowych aplikacji. Używanym modelem jest źródło danych, z którego korzysta aplikacja. Model jest rozmieszczony logicznie między bazą danych lub usługą a aplikacją.  Zobacz [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).

4. Przeciągnij źródło danych z okna **źródła danych** na Windows Forms, ASP.NET lub Windows Presentation Foundation powierzchni projektowej w celu wygenerowania kodu powiązania danych, który będzie wyświetlał dane dla użytkownika w sposób określony przez użytkownika. Zobacz [powiązane kontrolki z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Dodaj niestandardowy kod dla elementów, takich jak reguły biznesowe, wyszukiwanie i sprawdzanie poprawności danych, lub, aby skorzystać z funkcji niestandardowych, które uwidacznia bazowa baza danych.

   Możesz pominąć krok 3 i program aplikacji .NET, aby wydać polecenia bezpośrednio do bazy danych, zamiast korzystać z modelu. W takim przypadku znajdziesz odpowiednią dokumentację tutaj: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx). Należy pamiętać, że nadal można użyć Kreatora konfiguracji źródła danych i projektantów do generowania kodu powiązania danych podczas wypełniania własnych obiektów w pamięci, a następnie do tych obiektów formantów interfejsu użytkownika powiązanych z danymi.

## <a name="in-this-section"></a>W tej sekcji

- [Tworzenie prostej aplikacji do obsługi danych za pomocą pakietu ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [Dodawanie nowych połączeń](../data-tools/add-new-connections.md)

- [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md)

- [Narzędzia modelu Entity Data Model w programie Visual Studio](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Narzędzia zestawów danych w programie Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

- [Narzędzia LINQ to SQL Tools w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)

- [Wiązanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [Dodatkowe zasoby dla rozwiązywania problemów z błędami dostępu do danych](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Tworzenie baz danych i aplikacji warstw danych oraz zarządzanie nimi w programie Visual Studio](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [Dodatkowe zasoby dla rozwiązywania problemów z błędami dostępu do danych](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>Zobacz też
 [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
