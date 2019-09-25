---
title: 'CA2002: Nie blokuj obiektów o słabej tożsamości'
ms.date: 01/31/2018
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
ms.openlocfilehash: fc4504e917daeadc93963c6d6870c00515a5065a
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233163"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Nie blokuj obiektów o słabej tożsamości

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Kategoria|Microsoft.Reliability|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Wątek próbuje uzyskać blokadę dla obiektu, który ma słabą tożsamość.

## <a name="rule-description"></a>Opis reguły

Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu.

Następujące typy mają słabą tożsamość i są oflagowane przez regułę:

- <xref:System.String>

- Tablice typów wartości, w tym [Typy całkowite](/dotnet/csharp/language-reference/keywords/integral-types-table), [typy zmiennoprzecinkowe](/dotnet/csharp/language-reference/keywords/floating-point-types-table)i <xref:System.Boolean>.

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, użyj obiektu z typu, który nie znajduje się na liście w sekcji opis.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły

[CA2213 Pola jednorazowe powinny zostać usunięte](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono niektóre blokady obiektów, które naruszają daną regułę.

[!code-vb[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/VisualBasic/ca2002-do-not-lock-on-objects-with-weak-identity_1.vb)]
[!code-csharp[FxCop.Reliability.LockWeakObjects#1](../code-quality/codesnippet/CSharp/ca2002-do-not-lock-on-objects-with-weak-identity_1.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Monitor>
- <xref:System.AppDomain>
- [Lock — instrukcjaC#()](/dotnet/csharp/language-reference/keywords/lock-statement)
- [SyncLock — instrukcja (Visual Basic)](/dotnet/visual-basic/language-reference/statements/synclock-statement)