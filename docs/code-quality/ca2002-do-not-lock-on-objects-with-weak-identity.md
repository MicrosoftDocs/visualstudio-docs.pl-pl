---
title: 'CA2002: Nie blokuj obiektów o słabej tożsamości'
ms.date: 01/31/2018
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: c10eb0a37f24b4fe36b2e1afde8d3bec16e5896a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954998"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Nie blokuj obiektów o słabej tożsamości

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Kategoria|Microsoft.Reliability|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Wątek próbuje uzyskać blokadę na obiekcie o słabej tożsamości.

## <a name="rule-description"></a>Opis reguły

Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.

Następujące typy ma słabą tożsamość i są oznaczone przez regułę:

- <xref:System.String>

- Tablice typów wartości, w tym [typów całkowitych](/dotnet/csharp/language-reference/keywords/integral-types-table), [typów zmiennoprzecinkowych](/dotnet/csharp/language-reference/keywords/floating-point-types-table), i <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, użyj obiektu z typem, który nie ma na liście w sekcji Opis.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły

[CA2213: Pola możliwe do rozporządzania należy rozporządzać](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Przykład

Poniższy przykład przedstawia niektóre blokady obiektu, które naruszają reguły.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Monitor>
- <xref:System.AppDomain>
- [Lock — instrukcja (C#)](/dotnet/csharp/language-reference/keywords/lock-statement)
- [SyncLock — instrukcja (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)