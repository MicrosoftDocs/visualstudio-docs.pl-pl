---
title: Narzędzia Entity Data Model
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672394"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Narzędzia modelu Entity Data Model w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework jest technologią mapowania obiektów relacyjnych, która umożliwia deweloperom platformy .NET współdziałanie z danymi relacyjnymi przy użyciu obiektów specyficznych dla domeny. Dzięki temu większa część kodu dostępu do danych, który programiści muszą zwykle tworzyć, nie jest już potrzebna. Entity Framework to zalecana technologia modelowania obiektów (ORM) dla nowych aplikacji platformy .NET.

 Począwszy od marca 2016, Najnowsza wydana wersja to [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) jest w wersji wstępnej.

 Narzędzia [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] są przeznaczone do tworzenia aplikacji [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)]. Kompletna dokumentacja narzędzi [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] są następujące: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Za pomocą [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] narzędzi można utworzyć *model koncepcyjny* z istniejącej bazy danych, a następnie graficznie wizualizować i edytować model koncepcyjny. Można też utworzyć graficznie model koncepcyjny, a następnie wygenerować bazę danych, która obsługuje model. W obu przypadkach można automatycznie aktualizować model, gdy bazowa baza danych ulegnie zmianie i automatycznie generuje kod warstwy obiektu dla aplikacji. Generowanie bazy danych i generowanie kodu warstwy obiektu można dostosowywać.

 Są to określone narzędzia, które tworzą Entity Data Model narzędzia w programie Visual Studio 2015:

- Można użyć **projektanta [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** [!INCLUDE[vstecado](../includes/vstecado-md.md)] (**Entity Designer**) do wizualnego tworzenia i modyfikowania jednostek, skojarzeń, mapowań i relacji dziedziczenia. **Entity Designer** generuje również [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kod warstwy obiektu.

- Za pomocą **kreatora [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]** można wygenerować model koncepcyjny z istniejącej bazy danych i dodać do aplikacji informacje o połączeniu z bazą danych.

- Możesz użyć **Kreatora tworzenia bazy danych** , aby najpierw utworzyć model koncepcyjny, a następnie utworzyć bazę danych, która obsługuje model.

- **Kreatora aktualizacji modelu** można użyć do aktualizowania modelu koncepcyjnego, modelu magazynu i mapowań, gdy wprowadzono zmiany w źródłowej bazie danych.

  > [!NOTE]
  > Począwszy od programu Visual Studio 2010 narzędzia [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] nie obsługują [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Narzędzia generują lub modyfikują plik. edmx. Ten plik zawiera informacje opisujące model koncepcyjny, model magazynu oraz mapowania między nimi. Aby uzyskać więcej informacji, zobacz [edmx](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework narzędziach ułatwiają tworzenie aplikacji korzystających z Entity Data Model. Narzędzia mogą generować model koncepcyjny, sprawdzać istniejący model, tworzyć pliki kodu źródłowego zawierające klasy obiektów na podstawie modelu koncepcyjnego i generować pliki kodu źródłowego, które zawierają widoki generowane przez ten model. Aby uzyskać szczegółowe informacje, zobacz [wstępnie generowane widoki mapowania](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Program Entity Framework na platformie ADO.NET](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Opisuje, jak używać narzędzi [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)], które [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] oferuje do tworzenia aplikacji.|
|[Model danych jednostki](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Zawiera linki i informacje dotyczące pracy z danymi, które są używane przez aplikacje oparte na [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Wprowadzenie na pełnym platformie .NET (konsole, WinForms, WPF itp.)](/ef/ef6/get-started)|Zawiera samouczki dotyczące tworzenia aplikacji klasycznych platformy .NET, które używają Entity Framework 7.|
|[ASP.NET 5 aplikacji do nowej bazy danych](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Opisuje sposób tworzenia nowej aplikacji ASP.NET 5 przy użyciu programu Entity Framework 7.|

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
