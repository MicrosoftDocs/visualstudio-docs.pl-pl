---
title: 'CA1031: nie Przechwytuj typów wyjątków ogólnych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 520c9a066a4a902d5e9243baf1a8d8dec1b78e29
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542405"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj typów wyjątków ogólnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Ogólny wyjątek, taki jak <xref:System.Exception?displayProperty=fullName> lub, <xref:System.SystemException?displayProperty=fullName> jest przechwytywany w `catch` instrukcji lub Ogólna klauzula catch, taka jak `catch()` .

## <a name="rule-description"></a>Opis reguły
 Ogólne wyjątki nie powinny być przechwytywane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Przechwyć bardziej szczegółowy wyjątek lub ponownie Zgłoś wyjątek ogólny jako ostatnią instrukcję w `catch` bloku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Przechwytywanie typów wyjątków ogólnych może spowodować ukrycie problemów w czasie wykonywania z poziomu użytkownika biblioteki i utrudnienie debugowania.

> [!NOTE]
> Począwszy od [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)] , środowisko uruchomieniowe języka wspólnego (CLR) nie dostarcza już wyjątków uszkodzonych stanu, które występują w systemie operacyjnym i kodzie zarządzanym, takich jak naruszenia zasad dostępu w programie [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)] , do obsługi przez kod zarządzany. Jeśli chcesz skompilować aplikację w programie [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub nowszym i zachować obsługę wyjątków uszkodzonych Stanów, możesz zastosować <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybut do metody, która obsługuje wyjątek uszkodzony stan.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę i typ, który poprawnie implementuje `catch` blok.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2200: Ponowie zgłoś wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
