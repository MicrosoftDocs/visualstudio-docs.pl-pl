---
title: 'CA2131: Typy krytyczne dla zabezpieczeń nie mogą brać udziału w równoważeniu typu | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2131
ms.assetid: 4170f3b1-6086-430d-8fba-837d5538c573
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6fba07fbfd7f0c36681b7567ad01359df1be88f6
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65700527"
---
# <a name="ca2131-security-critical-types-may-not-participate-in-type-equivalence"></a>CA2131: Typy krytyczne pod względem zabezpieczeń nie mogą brać udziału w określaniu równoważności typów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CriticalTypesMustNotParticipateInTypeEquivalence|
|CheckId|CA2131|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Typ uczestniczy w równoważeniu typu i albo sam typ lub element członkowski lub pole o typie, jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na wszystkich typach krytycznych lub typach zawierających metody krytyczne lub pola, które uczestniczą w równoważeniu typu. Gdy CLR wykryje taki typ, nie jest on ładować je za pomocą <xref:System.TypeLoadException> w czasie wykonywania. Zazwyczaj ta reguła uruchamiana jest tylko wtedy, gdy użytkownicy implementują równoważenie typu ręcznie, zamiast wykonać je, opierając się na otokach tlbimp i kompilatorach.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, usuń atrybut SecurityCritical.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższych przykładach pokazano interfejs, metody i pola, które spowodują wyzwolenie tej reguły.

 [!code-csharp[FxCop.Security.CA2131.CriticalTypesMustNotParticipateInTypeEquivalence#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2131.criticaltypesmustnotparticipateintypeequivalence/cs/ca2131 - criticaltypesmustnotparticipateintypeequivalence.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Kod o przezroczystym poziomie bezpieczeństwa, poziom 2](https://msdn.microsoft.com/library/4d05610a-0da6-4f08-acea-d54c9d6143c0)
