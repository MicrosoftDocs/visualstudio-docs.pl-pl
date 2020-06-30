---
title: 'CA2141: Metody przezroczyste nie mogą spełniać LinkDemands | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bee810ed938d316e92095ad47062ed5ad9cd456f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546448"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>Metody CA2141:Transparent nie mogą spełniać LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta pod względem zabezpieczeń wywołuje metodę w zestawie, który nie jest oznaczony <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutem (APTCA) lub metoda przezroczysta zabezpieczeń spełnia <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` dla typu lub metody.

## <a name="rule-description"></a>Opis reguły
 Spełnienie LinkDemand jest operacją z uwzględnieniem zabezpieczeń, co może spowodować niepożądane podwyższenie poziomu uprawnień. Kod przezroczysty zabezpieczeń nie może spełniać LinkDemands, ponieważ nie podlega tym samym wymaganiom inspekcji zabezpieczeń co kod krytyczny dla bezpieczeństwa. Jawne metody w regułach zabezpieczeń zestaw na poziomie 1 spowodują, że wszystkie LinkDemands ich spełniają wszystkie wymagania w czasie wykonywania, co może spowodować problemy z wydajnością. W przypadku zestawów reguł zabezpieczeń z zestawem 2 poziom przezroczystych metod nie będzie kompilować w kompilatorze just-in-Time (JIT), jeśli spróbuje spełnić LinkDemand.

 W zestawach, które uSee poziom 2 zabezpieczeń, próbuje za pomocą przejrzystej metody zabezpieczeń, aby zaspokoić LinkDemand lub wywołać metodę w zestawie innym niż APTCA, podnosi a <xref:System.MethodAccessException> ; w zestawach poziomu 1, LinkDemand staną się pełnym zapotrzebowaniem.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, oznacz metodę dostępu przy użyciu <xref:System.Security.SecurityCriticalAttribute> atrybutu lub lub <xref:System.Security.SecuritySafeCriticalAttribute> Usuń LinkDemand z metody, do której uzyskano dostęp.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W tym przykładzie metoda przezroczysta próbuje wywołać metodę, która ma LinkDemand. Ta reguła zostanie włączona na tym kodzie.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
