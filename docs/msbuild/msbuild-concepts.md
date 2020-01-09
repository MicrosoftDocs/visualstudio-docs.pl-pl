---
title: Koncepcje programu MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aed8c97702989bdbdfd0f09c3cf99391c12fe9bd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589282"
---
# <a name="msbuild-concepts"></a>Pojęcia dotyczące programu MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] udostępnia podstawowy schemat XML, którego można użyć do kontrolowania sposobu, w jaki platforma kompilacji kompiluje oprogramowanie. Aby określić składniki w kompilacji i sposób ich kompilowania, Użyj tych czterech części programu MSBuild: właściwości, elementów, zadań i obiektów docelowych.

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| - | - |
| [Właściwości programu MSBuild](../msbuild/msbuild-properties.md) | Wprowadza właściwości i kolekcje właściwości. Właściwości to pary klucz/wartość, których można użyć do konfigurowania kompilacji. |
| [Elementy programu MSBuild](../msbuild/msbuild-items.md) | Zawiera wprowadzenie do elementów i kolekcji elementów. Elementy są wejściami do systemu kompilacji i zazwyczaj reprezentują pliki. |
| [Obiekty docelowe w programie MSBuild](../msbuild/msbuild-targets.md) | Wyjaśnia, w jaki sposób grupować zadania w określonej kolejności i włączać sekcje procesu kompilacji do wywołania w wierszu polecenia. |
| [Zadania programu MSBuild](../msbuild/msbuild-tasks.md) | Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, która może być używana przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania niepodzielnych operacji kompilacji. |
| [Porównywanie właściwości i elementów](../msbuild/comparing-properties-and-items.md) | Porównuje właściwości i elementy programu MSBuild. Oba są używane do przekazywania informacji do zadań, obliczania warunków i przechowywania wartości, do których można się odwoływać w całym pliku projektu. |
| [Znaki specjalne w MSBuild](../msbuild/msbuild-special-characters.md) | Wyjaśnia, w jaki sposób można wypróbować niektóre znaki, które [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezerwy do specjalnego użycia w określonych kontekstach. |
| [Przewodnik: Tworzenie pliku projektu MSBuild od podstaw](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Pokazuje, jak utworzyć podstawowy plik projektu przyrostowo, używając tylko edytora tekstu. |
| [Przewodnik: Używanie programu MSBuild](../msbuild/walkthrough-using-msbuild.md) | Wprowadza bloki konstrukcyjne programu MSBuild i pokazuje, jak pisać, manipulować i debugować projekty MSBuild bez zamykania zintegrowanego środowiska programistycznego (IDE) programu Visual Studio. |
| [Dokumentacja programu MSBuild](../msbuild/msbuild-reference.md) | Linki do dokumentów zawierających informacje referencyjne. |
| [MSBuild](../msbuild/msbuild.md) | Przedstawia Omówienie schematu XML dla pliku projektu i pokazuje, w jaki sposób kontroluje procesy, które kompilują oprogramowanie. |
