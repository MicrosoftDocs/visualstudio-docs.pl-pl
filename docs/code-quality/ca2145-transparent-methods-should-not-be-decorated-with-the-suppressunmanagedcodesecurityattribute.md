---
title: 'CA2145: Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2145
ms.assetid: 81970700-b438-4b3b-9239-16887e16f7b7
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3cca385c346a7daa8aaddb377f999506ffb1abaa
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232052"
---
# <a name="ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute"></a>CA2145: Metody przezroczyste nie powinny być dekorowane za pomocą atrybutu SuppressUnmanagedCodeSecurityAttribute

|||
|-|-|
|TypeName|TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity|
|CheckId|CA2145|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda przezroczysta, metoda oznaczona przy użyciu <xref:System.Security.SecuritySafeCriticalAttribute> metody lub typ, który zawiera metodę, jest oznaczona <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutem.

## <a name="rule-description"></a>Opis reguły

Metody oznaczone <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutem mają niejawny LinkDemand umieszczany dla każdej metody wywołującej ją. Ten element LinkDemand wymaga, aby kod wywołujący był krytyczny dla bezpieczeństwa. Oznaczenie metody, która używa SuppressUnmanagedCodeSecurity z atrybutem, <xref:System.Security.SecurityCriticalAttribute> sprawia, że to wymaganie jest bardziej oczywiste dla wywołujących metod.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, oznacz metodę lub typ <xref:System.Security.SecurityCriticalAttribute> atrybutem.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

### <a name="code"></a>Kod

[!code-csharp[FxCop.Security.CA2145.TransparentMethodsShouldNotUseSuppressUnmanagedCodeSecurity#1](../code-quality/codesnippet/CSharp/ca2145-transparent-methods-should-not-be-decorated-with-the-suppressunmanagedcodesecurityattribute_1.cs)]