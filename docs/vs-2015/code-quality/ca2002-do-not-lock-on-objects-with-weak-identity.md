---
title: 'CA2002: nie blokuj obiektów o słabej tożsamości | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotLockOnObjectsWithWeakIdentity
- CA2002
helpviewer_keywords:
- CA2002
- DoNotLockOnObjectsWithWeakIdentity
ms.assetid: 16100b39-c6fc-452b-8fca-8b459a26c286
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 557f91d8b00274642accbbfc05b4a60789615bfc
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667748"
---
# <a name="ca2002-do-not-lock-on-objects-with-weak-identity"></a>CA2002: Nie należy blokować obiektów z słabą tożsamością
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotLockOnObjectsWithWeakIdentity|
|CheckId|CA2002|
|Kategoria|Microsoft. niezawodność|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Wątek próbuje uzyskać blokadę dla obiektu, który ma słabą tożsamość.

## <a name="rule-description"></a>Opis reguły
 Obiekt ma słabą tożsamość, gdy można uzyskać do niego bezpośredni dostęp poza granicami domeny aplikacji. Wątek, który próbuje uzyskać blokadę na obiekcie o słabej tożsamości, może zostać zablokowany przez drugi wątek w domenie innej aplikacji, która ma blokady dla tego samego obiektu. Następujące typy mają słabą tożsamość i są oflagowane przez regułę:

- <xref:System.MarshalByRefObject>

- <xref:System.ExecutionEngineException>

- <xref:System.OutOfMemoryException>

- <xref:System.StackOverflowException>

- <xref:System.String>

- <xref:System.Reflection.MemberInfo>

- <xref:System.Reflection.ParameterInfo>

- <xref:System.Threading.Thread>

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, użyj obiektu z typu, który nie znajduje się na liście w sekcji opis.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="related-rules"></a>Powiązane reguły
 [CA2213: Pola możliwe do likwidacji powinny zostać zlikwidowane](../code-quality/ca2213-disposable-fields-should-be-disposed.md)

## <a name="example"></a>Przykład
 W poniższym przykładzie przedstawiono niektóre blokady obiektów, które naruszają daną regułę.

 [!code-csharp[FxCop.Reliability.LockWeakObjects#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/cs/FxCop.Reliability.LockWeakObjects.cs#1)]
 [!code-vb[FxCop.Reliability.LockWeakObjects#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Reliability.LockWeakObjects/vb/FxCop.Reliability.LockWeakObjects.vb#1)]

## <a name="see-also"></a>Zobacz też
 <xref:System.Threading.Monitor><xref:System.AppDomain>
 instrukcja [lock instrukcji](https://msdn.microsoft.com/library/656da1a4-707e-4ef6-9c6e-6d13b646af42) " [SyncLock](https://msdn.microsoft.com/library/14501703-298f-4d43-b139-c4b6366af176) "
