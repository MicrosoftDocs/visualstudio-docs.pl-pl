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
ms.openlocfilehash: 4d7f680107790143f4022722ed60e2a7f1000a06
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232174"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Kategoria|Microsoft.Security|
|Zmiana podziału|Kluczowa|

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