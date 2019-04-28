---
title: Pojęcia dotyczące programu MSBuild | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, concepts
ms.assetid: 083b8ba3-e4ad-45af-bb5d-3bc81d406131
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 12f0c8f2235db4c5eb332d52a454bd0093a34b68
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62842792"
---
# <a name="msbuild-concepts"></a>Pojęcia dotyczące programu MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] zawiera podstawowe schematu XML, który służy do kontrolowania, jak platforma kompilacji tworzy oprogramowanie. Aby określić składniki w kompilacji i jak są one ma zostać utworzony, należy użyć tych czterech części programu MSBuild: właściwości, elementy, zadania i elementy docelowe.

## <a name="related-topics"></a>Tematy pokrewne

| Tytuł | Opis |
| - | - |
| [Właściwości programu MSBuild](../msbuild/msbuild-properties.md) | Wprowadza właściwości i kolekcje właściwości. Właściwości to pary klucz/wartość, które służą do konfigurowania kompilacji. |
| [Elementy programu MSBuild](../msbuild/msbuild-items.md) | Wprowadza elementy i kolekcji elementów. Elementy to wejścia do systemu kompilacji i zazwyczaj reprezentują pliki. |
| [Obiekty docelowe w programie MSBuild](../msbuild/msbuild-targets.md) | Wyjaśnia, jak grupować zadania razem w określonej kolejności i włączyć sekcje procesu kompilacji, który ma być wywoływana w wierszu polecenia. |
| [Zadania programu MSBuild](../msbuild/msbuild-tasks.md) | Pokazuje, jak utworzyć jednostkę kodu wykonywalnego, który może być używany przez [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] do wykonywania niepodzielnych operacji kompilacji. |
| [Porównanie właściwości i elementów](../msbuild/comparing-properties-and-items.md) | Porównanie właściwości programu MSBuild i elementów. Oba są używane do przekazywania informacji do zadań, oceny warunków i przechowywania wartości, które można się odwoływać w całym pliku projektu. |
| [Znaki specjalne w MSBuild](../msbuild/msbuild-special-characters.md) | Wyjaśnia, jak jako znak ucieczki dla niektórych znaków, które [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] rezerwy dla specjalnych użycia w określonych kontekstach. |
| [Przewodnik: Tworzenie pliku projektu MSBuild od zera](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md) | Przedstawia sposób tworzenia podstawowego pliku projektu przyrostowo, używając tylko tekst edytora. |
| [Przewodnik: korzystanie z programu MSBuild](../msbuild/walkthrough-using-msbuild.md) | Wprowadza bloki konstrukcyjne programu MSBuild i pokazuje, jak napisać, modyfikowania i debugowania projektów programu MSBuild bez zamknięcia programu Visual Studio zintegrowane środowisko programistyczne (IDE). |
| [Odwołanie do narzędzia MSBuild](../msbuild/msbuild-reference.md) | Zawiera łącza do dokumentów, które zawierają informacje odniesienia. |
| [MSBuild](../msbuild/msbuild.md) | Przedstawia omówienie schematu XML w pliku projektu i pokazuje, jak kontroluje procesów, które tworzy oprogramowanie. |
