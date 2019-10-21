---
title: Kompatybilność wersji dla zasad ewidencjonowania analizy kodu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8385e2b36d09f029c4b8625e58cd99ecc06ea226
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72649028"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatybilność wersji dla zasad ewidencjonowania analizy kodu

Jeśli musisz oszacować i utworzyć zasady ewidencjonowania analizy kodu przy użyciu różnych wersji [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], musisz znać różnice w sposobie [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] i [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] oszacowania zasad ewidencjonowania.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Zgodność wersji do oceny zasad ewidencjonowania

- Gdy zasady ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], wszystkie reguły, które istniały w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], ale nie istnieją w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], są ignorowane.

- Gdy zasady ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], wszystkie nowe reguły, które mają wyłączność [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], zostaną zignorowane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoruje wszystkie reguły, które są określone przez zestawy, które nie są rozpoznawane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, których [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nie rozpoznaje, zostanie wyświetlony komunikat.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Zgodność wersji dla zasad ewidencjonowania autorstwa

- Jeśli utworzono zasady zaewidencjonowania analizy kodu przy użyciu [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] wersji [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)], nie można użyć [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]j wersji [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] do jej modyfikacji. Ponadto [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nie może oszacować zasad.

- Jeśli utworzono zasady ewidencjonowania analizy kodu przy użyciu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], można użyć [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], aby je zmodyfikować, a zasady można także ocenić przez [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)]. Po zmodyfikowaniu zasad przy użyciu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] nie będzie można edytować zasad przy użyciu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)]. [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] może oszacować zasady bez problemów z niezgodnymi silnymi nazwami.

- Aby utworzyć zasady ewidencjonowania analizy kodu przy użyciu ustawień reguły, które dotyczą zarówno [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], jak i [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], należy utworzyć zasady w [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)], wprowadzić wszystkie wymagane zmiany i zapisać zasady. Jeśli zmiany reguł istnieją tylko w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)], należy zmodyfikować i zapisać zasady w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)].

   Po zapisaniu zasad w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] nie można już zmieniać ustawień reguł istniejących w programie [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)].
