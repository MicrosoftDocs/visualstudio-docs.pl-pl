---
title: Entity Framework Tools
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 53b87ce39f0eb5b1455f0a38b2aea7cc6b604342
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648527"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools w programie Visual Studio

Entity Framework jest technologią mapowania obiektów relacyjnych, która umożliwia deweloperom platformy .NET współdziałanie z danymi relacyjnymi przy użyciu obiektów specyficznych dla domeny. Dzięki temu większa część kodu dostępu do danych, który programiści muszą zwykle tworzyć, nie jest już potrzebna. Entity Framework to zalecana technologia modelowania obiektów (ORM) dla nowych aplikacji platformy .NET.

Entity Framework Tools zaprojektowano w celu ułatwienia tworzenia aplikacji Entity Framework (EF). Kompletna dokumentacja Entity Framework jest dostępna w tym miejscu: [Przegląd-EF 6](/ef/ef6/).

  > [!NOTE]
  > Entity Framework Tools opisana na tej stronie służy do generowania plików *. edmx* , które nie są obsługiwane w programie EF Core. Aby wygenerować model EF Core na podstawie istniejącej bazy danych, zobacz Odtwarzanie w [EF Core](/ef/core/managing-schemas/scaffolding). Aby uzyskać więcej informacji na temat różnic między EF 6 i EF Core, zobacz [porównanie EF 6 i EF Core](/ef/efcore-and-ef6/).

Za pomocą Entity Framework Tools można utworzyć *model koncepcyjny* z istniejącej bazy danych, a następnie graficznie wizualizować i edytować model koncepcyjny. Można też utworzyć graficznie model koncepcyjny, a następnie wygenerować bazę danych, która obsługuje model. W obu przypadkach można automatycznie aktualizować model, gdy bazowa baza danych ulegnie zmianie i automatycznie generuje kod warstwy obiektu dla aplikacji. Generowanie bazy danych i generowanie kodu warstwy obiektu można dostosowywać.

Narzędzia Entity Framework są instalowane w ramach obciążenia związanego z **magazynowaniem i przetwarzaniem danych** w Instalator programu Visual Studio. Można je również zainstalować jako pojedynczy składnik w kategorii **zestawy SDK, biblioteki i struktury** .

Są to określone narzędzia, które tworzą Entity Framework narzędzia w programie Visual Studio:

- Można użyć **projektanta [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] (**Entity Designer**) do wizualnego tworzenia i modyfikowania jednostek, skojarzeń, mapowań i relacji dziedziczenia. **Entity Designer** generuje również [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] lub [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] kod warstwy obiektu.

- Za pomocą **kreatora [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** można wygenerować model koncepcyjny z istniejącej bazy danych i dodać do aplikacji informacje o połączeniu z bazą danych.

- Możesz użyć **Kreatora tworzenia bazy danych** , aby najpierw utworzyć model koncepcyjny, a następnie utworzyć bazę danych, która obsługuje model.

- **Kreatora aktualizacji modelu** można użyć do aktualizowania modelu koncepcyjnego, modelu magazynu i mapowań, gdy wprowadzono zmiany w źródłowej bazie danych.

  > [!NOTE]
  > Począwszy od programu Visual Studio 2010 narzędzia Entity Framework nie obsługują [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Narzędzia generują lub modyfikują plik *. edmx* . Ten plik *. edmx* zawiera informacje opisujące model koncepcyjny, model magazynu oraz mapowania między nimi. Aby uzyskać więcej informacji, zobacz [edmx](https://docs.microsoft.com/ef/ef6/).

[Entity Framework narzędziach](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) ułatwiają tworzenie aplikacji korzystających z Entity Data Model. Narzędzia energetyczne mogą generować model koncepcyjny, sprawdzać istniejący model, tworzyć pliki kodu źródłowego zawierające klasy obiektów na podstawie modelu koncepcyjnego i generować pliki kodu źródłowego, które zawierają widoki generowane przez ten model. Aby uzyskać szczegółowe informacje, zobacz [wstępnie generowane widoki mapowania](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| - | - |
| [Program Entity Framework na platformie ADO.NET](/dotnet/framework/data/adonet/ef/index) | Opisuje, jak używać narzędzi [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], które [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] oferuje do tworzenia aplikacji. |
| [Model danych jednostki](/dotnet/framework/data/adonet/entity-data-model) | Zawiera linki i informacje dotyczące pracy z danymi, które są używane przez aplikacje oparte na [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Dokumentacja Entity Framework (EF))](https://docs.microsoft.com/ef/ef6/get-started) | Zawiera indeks filmów wideo, samouczków i zaawansowanej dokumentacji, które ułatwiają optymalne wykorzystanie Entity Framework. |
| [ASP.NET 5 aplikacji do nowej bazy danych](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Opisuje sposób tworzenia nowej aplikacji ASP.NET 5 przy użyciu programu Entity Framework 7. |

## <a name="see-also"></a>Zobacz także

- [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)