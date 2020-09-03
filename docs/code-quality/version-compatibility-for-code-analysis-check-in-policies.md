---
title: Kompatybilność wersji dla zasad ewidencjonowania analizy kodu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4757b3a105ff02a92944d9b45e645e2c63a8b81c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75587163"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatybilność wersji dla zasad ewidencjonowania analizy kodu

Jeśli trzeba oszacować i utworzyć zasady ewidencjonowania analizy kodu przy użyciu różnych wersji programu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , należy znać różnice w zakresie [!INCLUDE[vstsTfsOrcasLong](../code-quality/includes/vststfsorcaslong_md.md)] i [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ocenie zasad ewidencjonowania.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Zgodność wersji do oceny zasad ewidencjonowania

- Gdy zasady ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , wszystkie reguły, które istniały w, [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] ale nie istnieją, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] są ignorowane.

- Gdy są oceniane zasady ewidencjonowania analizy kodu [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , wszystkie nowe reguły, które są wyłączność, [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] są ignorowane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, program [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] ignoruje wszystkie reguły, które są określone przez zestawy, które nie są rozpoznawane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, które [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nie są rozpoznawane, zostanie wyświetlony komunikat.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Zgodność wersji dla zasad ewidencjonowania autorstwa

- Jeśli utworzono zasady zaewidencjonowania analizy kodu przy użyciu [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] wersji programu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] , nie można [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] jej modyfikować za pomocą wersji programu. Ponadto program [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] nie może oszacować zasad.

- Jeśli zasady ewidencjonowania analizy kodu zostały utworzone za pomocą [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] programu w programie [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , można użyć [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] programu w [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] celu jego zmodyfikowania, a zasady można także ocenić przez [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] . Po zmodyfikowaniu zasad przy użyciu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] programu w programie [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] nie można już edytować zasad przy użyciu [!INCLUDE[esprtfc](../code-quality/includes/esprtfc_md.md)] programu w programie [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] . [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] program może oszacować zasady bez problemów z niezgodnymi silnymi nazwami.

- Aby utworzyć zasady ewidencjonowania analizy kodu przy użyciu ustawień reguły, które są stosowane do obu [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] i [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , należy utworzyć zasady w programie [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] , wprowadzić wszystkie wymagane zmiany i zapisać zasady. Jeśli zmiany reguł istnieją tylko w programie [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] , należy zmodyfikować i zapisać zasady w programie [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] .

   Po zapisaniu zasad w programie [!INCLUDE[vstsTfsOrcasShort](../code-quality/includes/vststfsorcasshort_md.md)] nie można już zmieniać ustawień reguł, które istnieją tylko w programie [!INCLUDE[vstsTfsRosarioShort](../code-quality/includes/vststfsrosarioshort_md.md)] .
