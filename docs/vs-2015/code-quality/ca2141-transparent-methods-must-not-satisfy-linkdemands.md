---
title: 'CA2141: metody przezroczyste nie mogą spełniać LinkDemands | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2141
ms.assetid: 2957f5f7-c511-4180-ba80-752034f10a77
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d9cdd35a640c333bef4f13b3c6123ba894b7ef65
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827093"
---
# <a name="ca2141transparent-methods-must-not-satisfy-linkdemands"></a>Metody CA2141:Transparent nie mogą spełniać LinkDemands
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotSatisfyLinkDemands|
|CheckId|CA2141|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta pod względem bezpieczeństwa wywołuje metodę w zestawie, który nie jest oznaczony atrybutem <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atrybutu (APTCA) lub metoda przezroczysta pod względem zabezpieczeń spełnia <xref:System.Security.Permissions.SecurityAction> `.LinkDemand` dla typu lub metody.

## <a name="rule-description"></a>Opis reguły
 Spełnia LinkDemand jest operacją poufnych zabezpieczeń, co może spowodować niezamierzone podniesienie uprawnień. Przezroczysty kod zabezpieczeń nie mogą spełniać LinkDemands, ponieważ nie podlega ona te same wymagania inspekcji zabezpieczeń, jak kodu krytycznego dla zabezpieczeń. Metody w zestawy poziomu 1 zestaw reguł zabezpieczeń spowoduje, że wszystkie LinkDemands, że spełniają one do przekonwertowania w pełnych żądań w czasie wykonywania, co może powodować problemy z wydajnością. W zestawy poziomu 2 zestaw reguł zabezpieczeń metody przezroczyste zakończy się niepowodzeniem skompilować w kompilator just-in-time (JIT), przy próbie spełnia LinkDemand.

 W zestawach zgłasza ten usee zabezpieczenia na poziomie 2, próby ustalenia przez metoda przezroczysta pod względem zabezpieczeń spełnia żądanie LinkDemand lub wywołanie metody w zestawie APTCA bez <xref:System.MethodAccessException>; w zestawach poziomu 1 żądanie LinkDemand staje się pełnego żądania.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy oznaczyć metody uzyskiwania dostępu do <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybut lub Usuń żądanie LinkDemand z metody dostępu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W tym przykładzie metoda przezroczysta pod względem próbuje wywołać metodę, która ma żądanie LinkDemand. Ta reguła zostanie zastosowana dla tego kodu.

 [!code-csharp[FxCop.Security.CA2141.TransparentMethodsMustNotSatisfyLinkDemands#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2141.transparentmethodsmustnotsatisfylinkdemands/cs/ca2141 - transparentmethodsmustnotsatisfylinkdemands.cs#1)]
