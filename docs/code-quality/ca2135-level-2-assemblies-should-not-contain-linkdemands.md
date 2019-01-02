---
title: 'CA2135: Zestawy poziomu 2 nie powinny zawierać LinkDemands'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 61f41a47b7fbb27e1811bd2c9888baf01143a50f
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53904106"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Zestawy poziomu 2 nie powinny zawierać LinkDemands

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Używa klasy ani składowej klasy <xref:System.Security.Permissions.SecurityAction> w aplikacji, która używa zabezpieczenia na poziomie 2.

## <a name="rule-description"></a>Opis reguły
 LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast używania LinkDemands do wymuszenia zabezpieczeń w czasie kompilacji programu just-in-time (JIT), należy oznaczyć metody, typy i pola za pomocą <xref:System.Security.SecurityCriticalAttribute> atrybutu.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń <xref:System.Security.Permissions.SecurityAction> i oznacz typ lub element członkowski o <xref:System.Security.SecurityCriticalAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie <xref:System.Security.Permissions.SecurityAction> powinny zostać usunięte, a metoda oznaczona atrybutem <xref:System.Security.SecurityCriticalAttribute> atrybutu.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]