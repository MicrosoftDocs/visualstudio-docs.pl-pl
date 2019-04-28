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
ms.openlocfilehash: 4e302c9e8cc74d461dc67237bd62b34097c0aceb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62542186"
---
# <a name="ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute"></a>CA2138: Metody przezroczyste nie mogą wywoływać metod z atrybutem SuppressUnmanagedCodeSecurity

|||
|-|-|
|TypeName|TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods|
|CheckId|CA2138|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta pod względem bezpieczeństwa wywołuje metodę, która jest oznaczona za pomocą <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu.

## <a name="rule-description"></a>Opis reguły
 Ta reguła jest uruchamiana na każdej przezroczystej metody metodę, która wywołuje bezpośrednio kod natywny, na przykład za pomocą metody P/Invoke (Wywołanie platformy) wywołań. P/Invoke i COM międzyoperacyjny metody, które są oznaczone <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu wynik na liście LinkDemand wykonywana względem wywoływania metody. Ponieważ przezroczysty kod zabezpieczeń nie mogą spełniać LinkDemands, kod również nie można wywołać metody, które są oznaczone atrybutem SuppressUnmanagedCodeSecurity lub metody klasy, która jest oznaczona atrybutem SuppressUnmanagedCodeSecurity. Metoda zakończy się niepowodzeniem lub żądanie zostaną przekonwertowane na pełnego żądania.

 Naruszenie tej zasady prowadzi do <xref:System.MethodAccessException> zabezpieczeń na poziomie 2 modelu przezroczystości i pełnego żądania dla <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> w modelu przezroczystości poziomu 1.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> atrybutu i oznacz metodę z <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute> atrybutu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 [!code-csharp[FxCop.Security.CA2138.TransparentMethodsMustNotCallSuppressUnmanagedCodeSecurityMethods#1](../code-quality/codesnippet/CSharp/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute_1.cs)]