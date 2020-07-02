---
title: 'CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 35cc152998b15a2fd4c4ff02e4730cdfae5366cb
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546500"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta pod względem bezpieczeństwa wywołuje metodę, która jest oznaczona za pomocą <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.

## <a name="rule-description"></a>Opis reguły
 Ta zasada jest uruchamiana dla dowolnej przezroczystej metody, która wywołuje bezpośrednio do kodu natywnego, na przykład za pomocą wywołania P/Invoke (wywołania platformy). Metody P/Invoke i COM międzyoperacyjności, które są oznaczone <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutem, powodują, że LinkDemand jest wykonywane względem metody wywołującej. Ponieważ przezroczysty kod zabezpieczeń nie może spełnić LinkDemands, kod nie może również wywołać metod, które są oznaczone atrybutem SuppressUnmanagedCodeSecurity, lub metod klasy, które są oznaczone atrybutem SuppressUnmanagedCodeSecurity. Metoda zakończy się niepowodzeniem lub żądanie zostanie przekonwertowane na pełne żądanie.

 Naruszenia tej reguły prowadzą do <xref:System.MethodAccessException> modelu przezroczystości zabezpieczeń poziomu 2 oraz pełnych wymagań dotyczących <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> modelu przezroczystości poziomu 1.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybut i oznacz metodę <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem or.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2138.transparentmethodsmustnotcallsuppressunmanagedcodesecuritymethods/cs/ca2138.cs#1)]
