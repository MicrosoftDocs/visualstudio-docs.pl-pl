---
title: 'CA2135: zestawy Level 2 nie powinny zawierać LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2135
ms.assetid: 7a775285-42d2-4f13-8434-3fdb0deeebe6
caps.latest.revision: 12
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1248ac41a757ba2fc26ef0659c0f93ee325bc605
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72602946"
---
# <a name="ca2135-level-2-assemblies-should-not-contain-linkdemands"></a>CA2135: Zestawy poziomu 2 nie powinny zawierać LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands|
|CheckId|CA2135|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Klasa lub członek klasy używa <xref:System.Security.Permissions.SecurityAction> w aplikacji, która korzysta z zabezpieczeń poziomu 2.

## <a name="rule-description"></a>Opis reguły
 LinkDemands są przestarzałe w zestawie reguł zabezpieczeń poziomu 2. Zamiast używać LinkDemands, aby wymusić zabezpieczenia w czasie kompilacji just-in-Time (JIT), Oznacz metody, typy i pola atrybutem <xref:System.Security.SecurityCriticalAttribute>.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Usuń <xref:System.Security.Permissions.SecurityAction> i Oznacz typ lub element członkowski atrybutem <xref:System.Security.SecurityCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W poniższym przykładzie należy usunąć <xref:System.Security.Permissions.SecurityAction>, a metoda oznaczona atrybutem <xref:System.Security.SecurityCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2135.SecurityRuleSetLevel2MethodsShouldNotBeProtectedWithLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2135.securityrulesetlevel2methodsshouldnotbeprotectedwithlinkdemands/cs/ca2135.cs#1)]
