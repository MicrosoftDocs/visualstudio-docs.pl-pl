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
ms.openlocfilehash: a3a17a0db7dd4ad1c57d23104a313a78cd1289ed
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547696"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Adnotacje przezroczystości składowych nie powinny powodować konfliktu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Ta zasada jest wyzwalana, gdy element członkowski typu jest oznaczony <xref:System.Security> atrybutem zabezpieczeń, który ma inną przezroczystość niż atrybut zabezpieczeń kontenera elementu członkowskiego.

## <a name="rule-description"></a>Opis reguły
 Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu z większym zakresem mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład Klasa, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu, nie może zawierać metody oznaczonej <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby rozwiązać ten problem, Usuń atrybut Security z elementu kodu, który ma niższy zakres, lub zmień jego atrybut na taki sam jak element kodu zawierającego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń z tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie metoda jest oznaczona <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem i jest składową klasy, która jest oznaczona <xref:System.Security.SecurityCriticalAttribute> atrybutem. Bezpieczny atrybut zabezpieczeń powinien zostać usunięty.

 [!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2136.transparencyannotationsshouldnotconflict/cs/ca2136 - transparencyannotationsshouldnotconflict.cs#1)]
