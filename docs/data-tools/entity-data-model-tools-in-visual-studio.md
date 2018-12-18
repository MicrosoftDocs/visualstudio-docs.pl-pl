---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 14a0e5b6b746356e38dfc71c26f53ced5a470e34
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066806"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools w programie Visual Studio

Entity Framework to technologii mapowania obiektowo relacyjny, który umożliwia deweloperom platformy .NET pracować z danymi relacyjnymi przy użyciu obiektów specyficznych dla domeny. Dzięki temu większa część kodu dostępu do danych, który programiści muszą zwykle tworzyć, nie jest już potrzebna. Entity Framework jest zalecane mapowania obiektowo relacyjny (ORM), modelowanie technologii nowych aplikacji .NET.

Entity Framework Tools są przeznaczone do tworzenia aplikacji Entity Framework (EF). Pełną dokumentację programu Entity Framework jest już dostępny: [programu EF Core i programem EF 6](/ef/).

Za pomocą narzędzi Entity Framework Tools można utworzyć *modelu koncepcyjnego* z istniejącej bazy danych, następnie graficznie wizualizowanie i edytować model koncepcyjny. Alternatywnie można graficznie najpierw utworzyć model koncepcyjny, a następnie wygeneruj bazy danych, która obsługuje model. W obu przypadkach można automatycznie aktualizować modelu, gdy podstawowe zmiany bazy danych i automatycznie wygenerować kod warstwy obiektu dla aplikacji. Generowanie bazy danych i generowania kodu warstwy obiektu są możliwe do dostosowania.

Narzędzia platformy Entity Framework są zainstalowane jako część **przechowywanie i przetwarzanie danych** obciążenie w Instalatorze programu Visual Studio. Można również zainstalować jako poszczególnych składników, w obszarze **zestawów SDK, bibliotek i struktur** kategorii.

Poniżej przedstawiono określonych narzędziach, które tworzą Entity Framework tools w programie Visual Studio:

- Możesz użyć [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] projektanta** (**Projektant jednostki**) aby wizualnie tworzyć i modyfikować jednostek, skojarzeń, mapowania i relacjami dziedziczenia. **Projektant jednostki** generuje również [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kod warstwy obiektu.

- Możesz użyć  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] kreatora** Generowanie modelu koncepcyjnego z istniejącej bazy danych i Dodaj informacje o połączeniu bazy danych do aplikacji.

- Możesz użyć **Kreatora tworzenia bazy danych** najpierw utworzyć model koncepcyjny, a następnie utworzenie bazy danych, która obsługuje model.

- Możesz użyć **Kreatora aktualizacji modelu** można zaktualizować swoje modelu koncepcyjnego, model magazynu i mapowania, jeśli wprowadzono zmiany do podstawowej bazy danych.

  > [!NOTE]
  > Począwszy od programu Visual Studio 2010 narzędzia Entity Framework nie obsługują [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Narzędzia Generowanie lub modyfikowanie *edmx* pliku. To *edmx* plik zawiera informacje opisujące modelu koncepcyjnego, model magazynu i mapowania między nimi. Aby uzyskać więcej informacji, zobacz [EDMX](https://docs.microsoft.com/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) pomagają Ci tworzyć aplikacje, które używają modelu Entity Data Model. Narzędzia zasilania można Generowanie modelu koncepcyjnego, sprawdzania poprawności istniejącego modelu, generuje pliki kodu źródłowego, które zawierają klas obiektów opartych na modelu koncepcyjnego i tworzenia plików kodu źródłowego, które zawierają widoki, które generuje modelu. Aby uzyskać szczegółowe informacje, zobacz [Pre-Generated mapowanie widoków](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| - | - |
| [Program Entity Framework na platformie ADO.NET](/dotnet/framework/data/adonet/ef/index) | Opisuje sposób używania [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] narzędzia, które [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] oferuje do tworzenia aplikacji. |
| [Model danych jednostki](/dotnet/framework/data/adonet/entity-data-model) | Zawiera linki i informacje dotyczące pracy z danymi, które jest wykorzystywane przez aplikacje oparte na [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Dokumentacja programu Entity Framework (EF))](https://docs.microsoft.com/ef/ef6/get-started) | Dostarcza indeks filmów wideo, samouczki i zaawansowane dokumentację, aby pomóc Państwu jak najlepiej wykorzystać możliwości platformy Entity Framework. |
| [Program ASP.NET 5 aplikację do nowej bazy danych](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | W tym artykule opisano sposób tworzenia nowej aplikacji platformy ASP.NET 5 za pomocą programu Entity Framework 7. |

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)