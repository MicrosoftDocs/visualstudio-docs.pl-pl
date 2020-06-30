---
title: 'CA2142: kod przezroczysty nie powinien być chroniony za pomocą LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2142
ms.assetid: 6dc59053-5dd9-4583-bf10-5f339107e59f
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: aa6bd9dcacc5fb863199c740a71c824f14739052
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546435"
---
# <a name="ca2142-transparent-code-should-not-be-protected-with-linkdemands"></a>CA2142: Kod przezroczysty nie powinien być chroniony za pomocą żądań LinkDemand
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparentMethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2142|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta wymaga <xref:System.Security.Permissions.SecurityAction> lub innego żądania zabezpieczeń.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na przezroczystych metodach wymagających żądania LinkDemands, aby uzyskać do nich dostęp. Przezroczysty kod zabezpieczeń nie powinien być odpowiedzialny za weryfikację zabezpieczeń operacji, a zatem nie powinien wymagać uprawnień. Ze względu na to, że przejrzyste metody mają być neutralne pod względem zabezpieczeń, nie powinny podejmować żadnych decyzji dotyczących zabezpieczeń. Ponadto bezpieczny kod krytyczny, który podejmuje decyzje w zakresie bezpieczeństwa, nie powinien polegać na przezroczystym kodzie, który wcześniej wprowadził takie rozstrzygnięcie.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy usunąć żądanie linku dla przezroczystej metody lub oznaczyć metodę <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem Attribute, jeśli wykonuje kontrolę zabezpieczeń, na przykład wymagania dotyczące zabezpieczeń.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie reguła jest uruchamiana na metodzie, ponieważ metoda jest przezroczysta i jest oznaczona za pomocą LinkDemand <xref:System.Security.PermissionSet> , która zawiera <xref:System.Security.Permissions.SecurityAction> .

 [!code-csharp[FxCop.Security.CA2142.TransparentMethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2142.transparentmethodsshouldnotbeprotectedwithlinkdemands/cs/ca2142 -transparentmethodsshouldnotbeprotectedwithlinkdemands.cs#1)]

 Nie pomijaj ostrzeżeń dla tej reguły.
