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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609319"
---
# <a name="version-compatibility-for-code-analysis-check-in-policies"></a>Kompatybilność wersji dla zasad ewidencjonowania analizy kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jeśli musisz oszacować i utworzyć zasady ewidencjonowania analizy kodu przy użyciu różnych wersji [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], musisz znać różnice w sposobie [!INCLUDE[vstsTfsOrcasLong](../includes/vststfsorcaslong-md.md)] i [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] oszacowania zasad ewidencjonowania.

## <a name="version-compatibility-for-evaluating-check-in-policies"></a>Zgodność wersji do oceny zasad ewidencjonowania

- Gdy zasady ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], wszystkie reguły, które istniały w [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], ale nie istnieją w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], są ignorowane.

- Gdy zasady ewidencjonowania analizy kodu są oceniane w [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], wszystkie nowe reguły, które mają wyłączność [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], zostaną zignorowane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] ignoruje wszystkie reguły, które są określone przez zestawy, które nie są rozpoznawane.

- Jeśli zasady ewidencjonowania analizy kodu określają zestawy reguł, których [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nie rozpoznaje, zostanie wyświetlony komunikat.

## <a name="version-compatibility-for-authoring-check-in-policies"></a>Zgodność wersji dla zasad ewidencjonowania autorstwa

- Jeśli utworzono zasady zaewidencjonowania analizy kodu przy użyciu [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] wersji [!INCLUDE[esprtfc](../includes/esprtfc-md.md)], nie można użyć [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]j wersji [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] do jej modyfikacji. Ponadto [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] nie może oszacować zasad.

- Jeśli utworzono zasady ewidencjonowania analizy kodu przy użyciu [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] w [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], można użyć [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], aby je zmodyfikować, a zasady można także ocenić przez [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)]. Po zmodyfikowaniu zasad przy użyciu [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] nie będzie można edytować zasad przy użyciu [!INCLUDE[esprtfc](../includes/esprtfc-md.md)] w [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)]. [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)] może oszacować zasady bez problemów z niezgodnymi silnymi nazwami.

- Aby utworzyć zasady ewidencjonowania analizy kodu przy użyciu ustawień reguły, które dotyczą zarówno [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], jak i [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], należy utworzyć zasady w [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)], wprowadzić wszystkie wymagane zmiany i zapisać zasady. Jeśli zmiany reguł istnieją tylko w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)], należy zmodyfikować i zapisać zasady w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)].

     Po zapisaniu zasad w [!INCLUDE[vstsTfsOrcasShort](../includes/vststfsorcasshort-md.md)] nie można już zmieniać ustawień reguł istniejących w programie [!INCLUDE[vstsTfsRosarioShort](../includes/vststfsrosarioshort-md.md)].
