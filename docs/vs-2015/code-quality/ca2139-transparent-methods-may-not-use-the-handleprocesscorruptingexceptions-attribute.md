---
title: 'CA2139: Metody przezroczyste nie mogą używać atrybutu HandleProcessCorruptingExceptions | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2139
ms.assetid: 45a0328a-add7-40f9-8934-dff59beb02b3
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 821598d7708fa8681f1dbc5fee65978d7498dbb5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72603002"
---
# <a name="ca2139-transparent-methods-may-not-use-the-handleprocesscorruptingexceptions-attribute"></a>CA2139: Jawne metody mogą nie używać atrybutu HandleProcessCorruptingExceptions
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|TransparentMethodsMustNotHandleProcessCorruptingExceptions|
|CheckId|CA2139|
|Kategoria|Microsoft.Security|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda przezroczysta jest oznaczona atrybutem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>.

## <a name="rule-description"></a>Opis reguły
 Ta zasada wyzwala każdą metodę, która jest niewidoczna i próbuje obsłużyć wyjątek powodujący uszkodzenie procesu przy użyciu atrybutu <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>. Wyjątek powodujący uszkodzenie procesu to klasyfikacja wyjątków w środowisku CLR w wersji 4,0 wyjątków takich jak <xref:System.AccessViolationException>. Atrybut HandleProcessCorruptedStateExceptionsAttribute może być używany tylko przez metody krytyczne pod względem bezpieczeństwa i będzie ignorowany, jeśli zostanie zastosowany do metody przezroczystej. Aby obsłużyć wyjątki uszkadzające proces, ta metoda musi stać się krytycznym zabezpieczeniami lub bezpiecznymi zabezpieczeniami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Usuń atrybut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> lub oznacz metodę za pomocą atrybutu <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute>.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły.

## <a name="example"></a>Przykład
 W tym przykładzie przezroczysta Metoda jest oznaczona atrybutem <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> i spowoduje niepowodzenie reguły. Metoda powinna być również oznaczona przy użyciu atrybutu <xref:System.Security.SecurityCriticalAttribute> lub <xref:System.Security.SecuritySafeCriticalAttribute>.

 [!code-csharp[FxCop.Security.CA2139.TransparentMethodsMustNotHandleProcessCorruptingExceptions#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2139.transparentmethodsmustnothandleprocesscorruptingexceptions/cs/ca2139 - transparentmethodsmustnothandleprocesscorruptingexceptions.cs#1)]
