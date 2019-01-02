---
title: 'CA2142: Przezroczysty kod nie powinien być chroniony za pomocą żądań Linkdemand'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 508d9606b07798a1aaa788d3d7ee87da4797dcad
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53899905"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Przezroczysty kod nie powinien być chroniony za pomocą żądań Linkdemand

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta pod względem wymaga <xref:System.Security.Permissions.SecurityAction> lub inne żądanie zabezpieczeń.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na przezroczystych metodach, które wymaga elementu LinkDemands uzyskiwać do nich dostęp. Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Ponieważ metody przezroczyste powinna być zabezpieczeń neutralne, ich powinna nie ustawienie wszystkie decyzje dotyczące bezpieczeństwa. Ponadto bezpieczny kod krytyczny, który decyzje dotyczące zabezpieczeń, nie należy polegać na przejrzysty kod będzie mieć wcześniej podjętych decyzji.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, usuń zapotrzebowania na łącza na metoda przezroczysta pod względem lub oznaczyć metody <xref:System.Security.SecuritySafeCriticalAttribute> sprawdza atrybut, jeśli działa zabezpieczeń, takie jak żądania kontroli zabezpieczeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie reguła jest uruchamiana na metodzie, ponieważ metoda jest przejrzysta i jest oznaczona za pomocą LinkDemand <xref:System.Security.PermissionSet> zawierający <xref:System.Security.Permissions.SecurityAction>.

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

 Nie pomijaj ostrzeżeń dla tej reguły.