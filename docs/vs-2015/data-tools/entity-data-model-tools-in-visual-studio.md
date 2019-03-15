---
title: Narzędzia modelu danych jednostki
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5f44b44cb0aa2d574d81fd63ef8541c25a4c2453
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57872735"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Narzędzia modelu danych jednostki w programie Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Entity Framework to technologii mapowania obiektowo relacyjny, który umożliwia deweloperom platformy .NET pracować z danymi relacyjnymi przy użyciu obiektów specyficznych dla domeny. Dzięki temu większa część kodu dostępu do danych, który programiści muszą zwykle tworzyć, nie jest już potrzebna. Entity Framework jest zalecane mapowania obiektowo relacyjny (ORM), modelowanie technologii nowych aplikacji .NET.

 Począwszy od marca 2016 r. jest aktualna wersja wydana [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) jest w wersji wstępnej.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Narzędzia są przeznaczone do tworzenia [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] aplikacji. Pełną dokumentację dla [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] narzędzi jest tutaj: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Za pomocą [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] narzędzia, możesz utworzyć *modelu koncepcyjnego* z istniejącej bazy danych, następnie graficznie wizualizowanie i edytować model koncepcyjny. Alternatywnie można graficznie najpierw utworzyć model koncepcyjny, a następnie wygeneruj bazy danych, która obsługuje model. W obu przypadkach można automatycznie aktualizować modelu, gdy podstawowe zmiany bazy danych i automatycznie wygenerować kod warstwy obiektu dla aplikacji. Generowanie bazy danych i generowania kodu warstwy obiektu są możliwe do dostosowania.

 Są one określone narzędzia, które tworzą narzędzia modelu danych jednostki w programie Visual Studio 2015:

- Możesz użyć [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] projektanta** (**Projektant jednostki**) aby wizualnie tworzyć i modyfikować jednostek, skojarzeń, mapowania i relacjami dziedziczenia. **Projektant jednostki** generuje również [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] lub [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] kod warstwy obiektu.

- Możesz użyć  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] kreatora** Generowanie modelu koncepcyjnego z istniejącej bazy danych i Dodaj informacje o połączeniu bazy danych do aplikacji.

- Możesz użyć **Kreatora tworzenia bazy danych** najpierw utworzyć model koncepcyjny, a następnie utworzenie bazy danych, która obsługuje model.

- Możesz użyć **Kreatora aktualizacji modelu** można zaktualizować swoje modelu koncepcyjnego, model magazynu i mapowania, jeśli wprowadzono zmiany do podstawowej bazy danych.

  > [!NOTE]
  >  Począwszy od programu Visual Studio 2010, [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] narzędzia nie obsługują [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Narzędzia Generowanie lub modyfikowanie pliku edmx. Ten plik zawiera informacje opisujące modelu koncepcyjnego, model magazynu i mapowania między nimi. Aby uzyskać więcej informacji, zobacz [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools pomagają Ci tworzyć aplikacje, które używają modelu Entity Data Model. Narzędzia można wygenerować model koncepcyjny, sprawdzania poprawności istniejącego modelu, generuje pliki kodu źródłowego, które zawierają klas obiektów opartych na modelu koncepcyjnego i tworzenia plików kodu źródłowego, które zawierają widoki, które generuje modelu. Aby uzyskać szczegółowe informacje, zobacz [Pre-Generated mapowanie widoków](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Program Entity Framework na platformie ADO.NET](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Opisuje sposób używania [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] narzędzia, które [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] oferuje do tworzenia aplikacji.|
|[Model danych jednostki](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Zawiera linki i informacje dotyczące pracy z danymi, które jest wykorzystywane przez aplikacje oparte na [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Wprowadzenie do na pełnej platformie .NET (Konsola, WinForms, WPF, itd.)](/ef/ef6/get-started)|Zawiera samouczki na temat tworzenia aplikacji klasycznych .NET, korzystających z programu Entity Framework 7.|
|[Program ASP.NET 5 aplikację do nowej bazy danych](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|W tym artykule opisano sposób tworzenia nowej aplikacji platformy ASP.NET 5 za pomocą programu Entity Framework 7.|

## <a name="see-also"></a>Zobacz też
 [Narzędzia do obsługi danych programu Visual Studio dla platformy .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
