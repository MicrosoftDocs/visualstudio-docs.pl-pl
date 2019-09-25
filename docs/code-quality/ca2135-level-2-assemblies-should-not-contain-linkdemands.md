---
title: 'CA2135: Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 66b9e7cb0eba06b00b30c2b7d00fac78206d222f
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232247"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Zestawy poziomu 2 nie powinny zawierać żądań LinkDemand

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Klasa lub członek klasy używa <xref:System.Security.Permissions.SecurityAction> w aplikacji, która korzysta z zabezpieczeń poziomu 2.

## <a name="rule-description"></a>Opis reguły
LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast używać LinkDemands, aby wymusić zabezpieczenia w czasie kompilacji just-in-Time (JIT), Oznacz metody, typy i pola <xref:System.Security.SecurityCriticalAttribute> atrybutem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej reguły, Usuń <xref:System.Security.Permissions.SecurityAction> i Oznacz typ lub składową <xref:System.Security.SecurityCriticalAttribute> z atrybutem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie <xref:System.Security.Permissions.SecurityAction> należy usunąć, a metoda oznaczona <xref:System.Security.SecurityCriticalAttribute> atrybutem.

[!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2135-level-2-assemblies-should-not-contain-linkdemands_1.cs)]