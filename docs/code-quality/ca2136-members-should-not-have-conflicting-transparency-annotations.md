---
title: 'CA2136: Adnotacje przezroczystości składowych nie powinny powodować konfliktu'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2127
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2136
helpviewer_keywords:
- SecurityTransparentAssembliesShouldNotContainSecurityCriticalCode
- CA2127
ms.assetid: ff5a1d18-7c52-4da5-8990-60be83a8ea81
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7f9455e83d7cb128a34696ae5e849fd0901f1891
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232218"
---
# <a name="ca2136-members-should-not-have-conflicting-transparency-annotations"></a>CA2136: Adnotacje przezroczystości składowych nie powinny powodować konfliktu

|||
|-|-|
|TypeName|TransparencyAnnotationsShouldNotConflict|
|CheckId|CA2136|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Ta zasada jest wyzwalana, gdy element członkowski typu jest <xref:System.Security> oznaczony atrybutem zabezpieczeń, który ma inną przezroczystość niż atrybut zabezpieczeń kontenera elementu członkowskiego.

## <a name="rule-description"></a>Opis reguły
Atrybuty przezroczystości są stosowane od elementów kodu o większym zakresie do elementów o mniejszym zakresie. Atrybuty przezroczystości elementów kodu z większym zakresem mają pierwszeństwo przed atrybutami przejrzystości elementów kodu, które są zawarte w pierwszym elemencie. Na przykład Klasa, która jest oznaczona za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu, nie może zawierać metody oznaczonej <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby rozwiązać ten problem, Usuń atrybut Security z elementu kodu, który ma niższy zakres, lub zmień jego atrybut na taki sam jak element kodu zawierającego.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń z tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie metoda jest oznaczona <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem i jest składową klasy, która jest oznaczona <xref:System.Security.SecurityCriticalAttribute> atrybutem. Bezpieczny atrybut zabezpieczeń powinien zostać usunięty.

[!code-csharp[FxCop.Security.CA2136.TransparencyAnnotationsShouldNotConflict#1](../code-quality/codesnippet/CSharp/ca2136-members-should-not-have-conflicting-transparency-annotations_1.cs)]