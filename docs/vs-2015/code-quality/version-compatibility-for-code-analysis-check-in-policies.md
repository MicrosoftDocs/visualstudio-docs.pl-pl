---
title: Zgodność wersji dla zasad zaewidencjonowania analizy kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- version compatibility, code analysis check-in policy
- check-in policies, version compatibility for code analysis
ms.assetid: 1af376e3-3be7-4445-803b-76a858567a5b
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 075981569cbee05e90afe17b3afc9558d7bbb270
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72609319"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatybilność wersji dla zasad ewidencjonowania analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli trzeba oszacować i utworzyć zasady ewidencjonowania analizy kodu przy użyciu różnych wersji programu [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , należy znać różnice w zakresie [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] i [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ocenie zasad ewidencjonowania.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Zgodność wersji do oceny zasad ewidencjonowania

- Gdy zasady ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , wszystkie reguły, które istniały w, [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] ale nie istnieją, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] są ignorowane.

- Gdy są oceniane zasady ewidencjonowania analizy kodu [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , wszystkie nowe reguły, które są wyłączność, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] są ignorowane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, program [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignoruje wszystkie reguły, które są określone przez zestawy, które nie są rozpoznawane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, które [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nie są rozpoznawane, zostanie wyświetlony komunikat.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Zgodność wersji dla zasad ewidencjonowania autorstwa

- Jeśli utworzono zasady zaewidencjonowania analizy kodu przy użyciu [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] wersji programu [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] , nie można [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] jej modyfikować za pomocą wersji programu. Ponadto program [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nie może oszacować zasad.

- Jeśli zasady ewidencjonowania analizy kodu zostały utworzone za pomocą [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] programu w programie [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , można użyć [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] programu w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] celu jego zmodyfikowania, a zasady można także ocenić przez [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] . Po zmodyfikowaniu zasad przy użyciu [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] programu w programie [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] nie można już edytować zasad przy użyciu [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] programu w programie [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] . [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] program może oszacować zasady bez problemów z niezgodnymi silnymi nazwami.

- Aby utworzyć zasady ewidencjonowania analizy kodu przy użyciu ustawień reguły, które są stosowane do obu [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] i [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , należy utworzyć zasady w programie [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] , wprowadzić wszystkie wymagane zmiany i zapisać zasady. Jeśli zmiany reguł istnieją tylko w programie [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] , należy zmodyfikować i zapisać zasady w programie [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] .

     Po zapisaniu zasad w programie [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] nie można już zmieniać ustawień reguł, które istnieją tylko w programie [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] .
