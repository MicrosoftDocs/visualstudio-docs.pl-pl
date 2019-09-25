---
title: 'CA2142: Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ab0f6aaae97a510b0521e10ad607a86988c345a3
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232082"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand

|||
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda przezroczysta wymaga <xref:System.Security.Permissions.SecurityAction> lub innego żądania zabezpieczeń.

## <a name="rule-description"></a>Opis reguły
Ta zasada jest uruchamiana na przejrzystych metodach, które wymagają LinkDemands dostępu do nich. Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Ze względu na to, że przejrzyste metody mają być neutralne pod względem zabezpieczeń, nie powinny podejmować żadnych decyzji dotyczących zabezpieczeń. Ponadto bezpieczny kod krytyczny, który podejmuje decyzje w zakresie bezpieczeństwa, nie powinien polegać na przezroczystym kodzie, który wcześniej wprowadził takie rozstrzygnięcie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, należy usunąć żądanie linku dla przezroczystej metody lub oznaczyć metodę atrybutem Attribute <xref:System.Security.SecuritySafeCriticalAttribute> , jeśli wykonuje kontrolę zabezpieczeń, na przykład wymagania dotyczące zabezpieczeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W poniższym przykładzie reguła jest uruchamiana na metodzie, ponieważ metoda jest przezroczysta i jest oznaczona za pomocą LinkDemand <xref:System.Security.PermissionSet> , która <xref:System.Security.Permissions.SecurityAction>zawiera.

[!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../code-quality/codesnippet/CSharp/ca2142-transparent-code-should-not-be-protected-with-linkdemands_1.cs)]

Nie pomijaj ostrzeżeń dla tej reguły.