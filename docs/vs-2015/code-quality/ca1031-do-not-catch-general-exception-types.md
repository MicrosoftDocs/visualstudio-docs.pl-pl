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
ms.openlocfilehash: 2696446ee2b257b78559909c0cba672cded39943
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661896"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj wyjątków typów ogólnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
 Ogólny wyjątek, taki jak <xref:System.Exception?displayProperty=fullName> lub <xref:System.SystemException?displayProperty=fullName>, jest przechwytywany w instrukcji `catch` lub jest używana Ogólna klauzula catch, taka jak `catch()`.

## <a name="rule-description"></a>Opis reguły
 Ogólne wyjątki nie powinny być przechwytywane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, Przechwyć bardziej szczegółowy wyjątek lub ponownie Zgłoś wyjątek ogólny jako ostatnią instrukcję w bloku `catch`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Przechwytywanie typów wyjątków ogólnych może spowodować ukrycie problemów w czasie wykonywania z poziomu użytkownika biblioteki i utrudnienie debugowania.

> [!NOTE]
> Począwszy od [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], środowisko uruchomieniowe języka wspólnego (CLR) nie dostarcza już wyjątków uszkodzonych stanu występujących w systemie operacyjnym i kodzie zarządzanym, takich jak naruszenia zasad dostępu w [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], do obsługi przez kod zarządzany. Jeśli chcesz skompilować aplikację w [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub nowszych wersjach i zachować obsługę wyjątków uszkodzonych Stanów, można zastosować atrybut <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> do metody, która obsługuje wyjątek uszkodzonego stanu.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje typ, który narusza tę regułę i typ, który poprawnie implementuje blok `catch`.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2200: Zgłoś ponownie wyjątek, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
