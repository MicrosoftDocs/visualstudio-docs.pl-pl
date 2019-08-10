---
title: 'CA2139: Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f6808c5e9b5d35ab6ec8d4012f08e15cba9a159d
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68920566"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda przezroczysta jest oznaczona <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutem.

## <a name="rule-description"></a>Opis reguły
Ta zasada wyzwala każdą metodę, która jest niewidoczna i próbuje obsłużyć wyjątek powodujący uszkodzenie <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> procesu przy użyciu atrybutu. Wyjątek powodujący uszkodzenie procesu jest klasyfikacją wyjątków w środowisku CLR w wersji 4,0 <xref:System.AccessViolationException>, takich jak. Atrybut HandleProcessCorruptedStateExceptionsAttribute może być używany tylko przez metody krytyczne pod względem bezpieczeństwa i będzie ignorowany, jeśli zostanie zastosowany do metody przezroczystej. Aby obsłużyć wyjątki uszkadzające proces, ta metoda musi stać się krytycznym zabezpieczeniami lub bezpiecznymi zabezpieczeniami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, Usuń <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybut lub oznacz metodę <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> atrybutem or.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
W tym przykładzie przezroczysta Metoda jest oznaczona <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutem i spowoduje niepowodzenie reguły. Metoda powinna być również oznaczona przy użyciu <xref:System.Security.SecurityCriticalAttribute> <xref:System.Security.SecuritySafeCriticalAttribute> lub atrybutu.

[!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../code-quality/codesnippet/CSharp/ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute_1.cs)]