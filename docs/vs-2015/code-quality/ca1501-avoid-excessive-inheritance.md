---
title: 'CA1501: Unikaj nadmiernego dziedziczenia | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1501
- AvoidExcessiveInheritance
helpviewer_keywords:
- AvoidExcessiveInheritance
- CA1501
ms.assetid: 9e934746-1a4d-492a-91e4-085201abafa4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: cf797ad67b7df2eb1f3ba1246e965ed6ebbd586d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547865"
---
# <a name="ca1501-avoid-excessive-inheritance"></a>CA1501: Unikaj nadmiernego dziedziczenia
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidExcessiveInheritance|
|CheckId|CA1501|
|Kategoria|Microsoft. łatwość obsługi|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ jest głęboki na więcej niż cztery poziomy w hierarchii dziedziczenia.

## <a name="rule-description"></a>Opis reguły
 Hierarchie typów głęboko zagnieżdżonych mogą być trudne do śledzenia, zrozumienia i utrzymania. Ta reguła ogranicza analizę do hierarchii w tym samym module.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, należy utworzyć typ z typu podstawowego, który jest mniej głębokie w hierarchii dziedziczenia, lub wyeliminować niektóre pośrednie typy podstawowe.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak kod może być trudniejszy do utrzymania. Należy pamiętać, że w zależności od widoczności typów podstawowych Rozwiązywanie naruszeń tej reguły może spowodować istotne zmiany. Na przykład usunięcie publicznych typów podstawowych jest istotną zmianą.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza regułę.

 [!code-csharp[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/cs/FxCop.Maintainability.ExcessiveInheritance.cs#1)]
 [!code-vb[FxCop.Maintainability.ExcessiveInheritance#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Maintainability.ExcessiveInheritance/vb/FxCop.Maintainability.ExcessiveInheritance.vb#1)]
