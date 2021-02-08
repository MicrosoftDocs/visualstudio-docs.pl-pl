---
title: Typowe metadane elementu MSBuild | Microsoft Docs
description: Dowiedz się więcej o opcjonalnych metadanych elementów mających znaczenie dla niektórych zestawów SDK lub obiektów docelowych programu MSBuild, ale nie są domyślnie ustawiane dla każdego elementu.
ms.custom: SEO-VS-2020
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8dda627f748773bc4cb5598b133ac05597ffe1d4
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839312"
---
# <a name="common-msbuild-item-metadata"></a>Wspólne metadane elementów programu MSBuild

W poniższej tabeli opisano opcjonalne metadane elementów, których znaczenie dotyczy niektórych zestawów SDK lub obiektów docelowych MSBuild, ale które nie są domyślnie ustawione dla każdego elementu. Można ustawić te ustawienia, aby mieć wpływ na zachowanie kompilacji, ale tylko wtedy, gdy plik zestawu SDK lub plików docelowych jest rozpoznawany przez użytkownika.

| Metadane elementu | Zestawy SDK | Opis |
|---------------| ------- | -------------|
|% (Link)| Wszystko |System projektu programu Visual Studio używa `Link` metadanych (jeśli istnieją) w celu zmiany elementów wyświetlanych w drzewie projektu. plik można umieścić w innej logicznej strukturze folderów w **Eksplorator rozwiązań**.<br />Ponadto `AssignTargetPath` zadanie sprawdza, `Link` czy w katalogu wyjściowym skopiowano plik do, jeśli jest to jeden z elementów, które zostały skopiowane.|
|% (Baza łączy)| Zestaw .NET Core SDK | Służy do ustawiania folderu, który ma być używany dla `Link` metadanych dla grup elementów. |

## <a name="see-also"></a>Zobacz też

- [Wspólne właściwości projektów MSBuild](../msbuild/common-msbuild-project-properties.md)
- [Wspólne elementy projektów MSBuild](../msbuild/common-msbuild-project-items.md)
- [Dobrze znane metadane elementów programu MSBuild](msbuild-well-known-item-metadata.md)