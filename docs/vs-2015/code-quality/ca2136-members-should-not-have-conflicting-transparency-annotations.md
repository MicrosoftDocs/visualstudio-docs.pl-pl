---
title: 'CA2136: elementy członkowskie nie powinny mieć sprzecznych adnotacji przezroczystości | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f2fbb856ff53552ab99dabd4f650e9fd7f62a088
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602968"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Elementy członkowskie nie powinny mieć skonfliktowanych adnotacji przezroczystości
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta zasada jest wyzwalana, gdy element członkowski typu jest oznaczony atrybutem zabezpieczeń <xref:System.Security>, który ma inną przezroczystość niż atrybut zabezpieczeń kontenera elementu członkowskiego.

## <a name="rule-description"></a>Opis reguły
 Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu z większym zakresem mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład Klasa, która jest oznaczona za pomocą atrybutu <xref:System.Security.SecurityCriticalAttribute> nie może zawierać metody oznaczonej atrybutem <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, Usuń atrybut Security z elementu kodu, który ma niższy zakres, lub zmień jego atrybut na taki sam jak element kodu zawierającego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń z tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie metoda jest oznaczona atrybutem <xref:System.Security.SecuritySafeCriticalAttribute> i jest składową klasy, która jest oznaczona atrybutem <xref:System.Security.SecurityCriticalAttribute>. Bezpieczny atrybut zabezpieczeń powinien zostać usunięty.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
