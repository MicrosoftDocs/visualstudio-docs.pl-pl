---
title: Narzędzia danych dla platformy .NET
description: Przejrzyj narzędzia danych programu Visual Studio dla platformy .NET, które zapewniają obsługę interfejsów API i narzędzi do łączenia się z bazami danych, modelowania danych w pamięci i wyświetlania danych w interfejsie użytkownika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: a095d0fc026634c13ee9f74c8568e199e09f49db
ms.sourcegitcommit: 72a49c10a872ab45ec6c6d7c4ac7521be84526ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/20/2020
ms.locfileid: "94998281"
---
# <a name="visual-studio-data-tools-for-net"></a>Narzędzia do obsługi danych programu Visual Studio dla platformy .NET

Programy Visual Studio i .NET wspólnie zapewniają szeroką obsługę interfejsów API i narzędzi do łączenia się z bazami danych, modelowania danych w pamięci i wyświetlania danych w interfejsie użytkownika. Klasy .NET, które zapewniają funkcje dostępu do danych, są nazywane [ADO.NET](/dotnet/framework/data/adonet/index). Program ADO.NET, wraz z narzędziami do obsługi danych w programie Visual Studio, został zaprojektowany głównie z uwzględnieniem relacyjnych baz danych i XML. W tych dniach wiele dostawców baz danych NoSQL lub innych firm oferuje dostawców ADO.NET.

[Platforma .NET Core](/dotnet/core/) obsługuje ADO.NET, z wyjątkiem zestawów danych i ich powiązanych typów. Jeśli celem jest platforma .NET Core i wymagana jest warstwa mapowania obiektów (ORM), użyj [Entity Framework Core](/ef/core/).

Na poniższym diagramie przedstawiono uproszczony widok podstawowej architektury:

![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typowy przepływ pracy

Typowy przepływ pracy to:

1. Zainstaluj programistyczną lub testową bazę danych na komputerze lokalnym. Zobacz [Instalowanie systemów baz danych, narzędzi i przykładów](../data-tools/installing-database-systems-tools-and-samples.md). Jeśli używasz usługi danych platformy Azure, ten krok nie jest konieczny.

2. Przetestuj połączenie z bazą danych (lub usługą lub plikiem lokalnym) w programie Visual Studio. Zobacz [Dodawanie nowych połączeń](../data-tools/add-new-connections.md).

3. Obowiązkowe Użyj narzędzi, aby wygenerować i skonfigurować nowy model. Modele oparte na Entity Framework są domyślnymi zaleceniami dla nowych aplikacji. Model, w zależności od tego, który jest używany, to źródło danych, z którym aplikacja działa. Model jest rozmieszczony logicznie między bazą danych lub usługą a aplikacją. Zobacz [Dodawanie nowych źródeł danych](../data-tools/add-new-data-sources.md).

4. Przeciągnij źródło danych z okna **źródła danych** na Windows Forms, ASP.NET lub Windows Presentation Foundation powierzchni projektowej w celu wygenerowania kodu powiązania danych, który będzie wyświetlał dane dla użytkownika w sposób określony przez użytkownika. Zobacz [powiązane kontrolki z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Dodaj niestandardowy kod dla elementów, takich jak reguły biznesowe, wyszukiwanie i sprawdzanie poprawności danych, lub, aby skorzystać z funkcji niestandardowych, które uwidacznia bazowa baza danych.

Możesz pominąć krok 3 i program aplikacji .NET, aby wydać polecenia bezpośrednio do bazy danych, zamiast korzystać z modelu. W takim przypadku znajdziesz odpowiednią dokumentację tutaj: [ADO.NET](/dotnet/framework/data/adonet/index). Należy pamiętać, że nadal można użyć **Kreatora konfiguracji źródła danych** i projektantów do generowania kodu powiązania danych podczas wypełniania własnych obiektów w pamięci, a następnie do tych obiektów formantów interfejsu użytkownika powiązanych z danymi.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
