---
title: 'CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2138
ms.assetid: a14c4d32-f079-4f3a-956c-a1657cde0f66
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 316aef3b0f1f715857fde8eaf2a6e74b1a49e40f
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920579"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda przezroczysta pod względem bezpieczeństwa wywołuje metodę, która jest oznaczona <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> za pomocą atrybutu.

## <a name="rule-description"></a>Opis reguły
Ta zasada jest uruchamiana dla dowolnej przezroczystej metody, która wywołuje bezpośrednio do kodu natywnego, na przykład przy użyciu wywołania P/Invoke (wywołania platformy). Metody P/Invoke i com międzyoperacyjności, które są <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> oznaczone atrybutem, powodują, że LinkDemand jest wykonywane względem metody wywołującej. Ponieważ przezroczysty kod zabezpieczeń nie może spełnić LinkDemands, kod nie może również wywołać metod, które są oznaczone atrybutem SuppressUnmanagedCodeSecurity, lub metod klasy, które są oznaczone atrybutem SuppressUnmanagedCodeSecurity. Metoda zakończy się niepowodzeniem lub żądanie zostanie przekonwertowane na pełne żądanie.

Naruszenia tej reguły prowadzą do <xref:System.MethodAccessException> modelu przezroczystości zabezpieczeń poziomu 2 oraz pełnych wymagań dotyczących <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> modelu przezroczystości poziomu 1.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, Usuń <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybut i oznacz metodę <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem or.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
[!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]