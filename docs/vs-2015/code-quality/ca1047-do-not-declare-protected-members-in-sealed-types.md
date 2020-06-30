---
title: 'CA1047: Nie deklaruj chronionych składowych w typach zapieczętowanych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotDeclareProtectedMembersInSealedTypes
- CA1047
helpviewer_keywords:
- CA1047
- DoNotDeclareProtectedMembersInSealedTypes
ms.assetid: 829033b5-a9d8-4f26-a719-45494c9dd035
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e115b4d327f1ac45673de491ceaffc90941e1111
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546786"
---
# <a name="ca1047-do-not-declare-protected-members-in-sealed-types"></a>CA1047: Nie deklaruj chronionych składowych w typach zapieczętowanych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotDeclareProtectedMembersInSealedTypes|
|CheckId|CA1047|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Typ publiczny to `sealed` ( `NotInheritable` w języku Visual Basic) i deklaruje chroniony element członkowski lub chroniony Typ zagnieżdżony. Ta reguła nie raportuje naruszeń <xref:System.Object.Finalize%2A> metod, które muszą być zgodne z tym wzorcem.

## <a name="rule-description"></a>Opis reguły
 Chronione elementy członkowskie są zadeklarowane w typach tak, aby typy dziedziczące miały dostęp do elementu członkowskiego i mogły go zastąpić. Według definicji nie można dziedziczyć z typu zapieczętowanego, co oznacza, że nie można wywołać metod chronionych na typach zapieczętowanych.

 Kompilator języka C# emituje Ostrzeżenie dla tego błędu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień poziom dostępu elementu członkowskiego na prywatny lub ustaw typ dziedziczenia.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Pozostawienie tego typu w bieżącym stanie może spowodować problemy z konserwacją i nie zapewnia żadnych korzyści.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę.

 [!code-csharp[FxCop.Design.SealedNoProtected#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/cs/FxCop.Design.SealedNoProtected.cs#1)]
 [!code-vb[FxCop.Design.SealedNoProtected#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.SealedNoProtected/vb/FxCop.Design.SealedNoProtected.vb#1)]
