---
title: Data tools dla platformy .NET
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 1dcd8c256259baeef36939e19ce785e5efe7c80b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586045"
---
# <a name="visual-studio-data-tools-for-net"></a>Narzędzia do obsługi danych programu Visual Studio dla platformy .NET

Programy Visual Studio i .NET wspólnie zapewniają szeroką obsługę interfejsów API i narzędzi do łączenia się z bazami danych, modelowania danych w pamięci i wyświetlania danych w interfejsie użytkownika. Klasy .NET, które zapewniają funkcje dostępu do danych, są nazywane [ADO.NET](/dotnet/framework/data/adonet/index). ADO.NET, wraz z danymi narzędzi w programie Visual Studio został zaprojektowany głównie w celu obsługi relacyjnych baz danych i XML. Te dni wielu dostawców bazy danych NoSQL lub stronom trzecim, oferują dostawcy ADO.NET.

[Platforma .NET Core](/dotnet/core/) obsługuje ADO.NET, z wyjątkiem zestawów danych i ich powiązanych typów. Jeśli celem jest platforma .NET Core i wymagana jest warstwa mapowania obiektów (ORM), użyj [Entity Framework Core](/ef/core/).

Na poniższym diagramie przedstawiono uproszczony widok podstawowej architektury:

![Architektura ADO.NET](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>Typowy przepływ pracy

Typowy przepływ pracy to:

1. Zainstaluj rozwoju lub bazy danych testów na komputerze lokalnym. Zobacz [instalowanie systemów baz danych, narzędzia i przykłady](../data-tools/installing-database-systems-tools-and-samples.md). Jeśli używasz usługi danych platformy Azure, ten krok nie jest konieczne.

2. Przetestuj połączenie z bazą danych (lub usługi lub plik lokalny) w programie Visual Studio. Zobacz [dodać nowe połączenia](../data-tools/add-new-connections.md).

3. (Opcjonalnie) Narzędzia do generowania i skonfigurować nowy model. Modele oparte na platformie Entity Framework są określenia domyślnego zalecenia w przypadku nowych aplikacji. Model, niezależnie od jednej z nich, jest źródłem danych, za pomocą którego aplikacja wchodzi w interakcje. Model logicznie znajduje się pomiędzy bazy danych lub usługi i aplikacji. Zobacz [dodasz nowe źródła danych](../data-tools/add-new-data-sources.md).

4. Przeciągnij źródła danych z **źródeł danych** okna na powierzchni projektowej Windows Forms, ASP.NET lub Windows Presentation Foundation do generowania kodu wiązania danych, które będą wyświetlane dane użytkownika w taki sposób, który określisz. Zobacz [powiązywanie kontrolek z danymi w programie Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).

5. Dodawanie kodu niestandardowego, w przypadku elementów, takich jak reguły biznesowe, wyszukiwania i sprawdzanie poprawności danych lub skorzystaj z zalet funkcji niestandardowych, który udostępnia w źródłowej bazie danych.

Można pominąć krok 3 i programowania aplikacji .NET w celu wydawania poleceń, bezpośrednio do bazy danych, a nie przy użyciu modelu. W takim przypadku możesz znaleźć odpowiednią dokumentację: [ADO.NET](/dotnet/framework/data/adonet/index). Należy zauważyć, że nadal można używać **Kreatora konfiguracji źródła danych** i projektantów, aby wygenerować kod powiązania danych, podczas wypełniania obiektów w pamięci, a następnie powiązanie danych kontrolki interfejsu użytkownika do tych obiektów.

## <a name="see-also"></a>Zobacz także

- [Uzyskiwanie dostępu do danych w programie Visual Studio](../data-tools/accessing-data-in-visual-studio.md)
