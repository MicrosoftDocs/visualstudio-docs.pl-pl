---
title: 'CA1031: Nie przechwytuj typów wyjątków ogólnych | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3133ea902717f4fea15cfb66b8d0050f7a538940
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54780100"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj typów wyjątków ogólnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Ogólny wyjątek, takie jak <xref:System.Exception?displayProperty=fullName> lub <xref:System.SystemException?displayProperty=fullName> padł w `catch` instrukcji lub Ogólna klauzula catch takich jak `catch()` jest używany.

## <a name="rule-description"></a>Opis reguły
 Ogólne wyjątki nie powinny być przechwytywane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, przechwycić wyjątek bardziej precyzyjny lub Zgłoś ponownie ogólny wyjątek jako ostatnią instrukcję w `catch` bloku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Przechwytywanie typów wyjątków ogólnych może ukryć problemów w czasie wykonywania przed użytkownikiem biblioteki oraz może utrudnić debugowanie.

> [!NOTE]
>  Począwszy od [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], środowisko uruchomieniowe języka wspólnego (CLR) dostarcza już wyjątki uszkodzony, które występują w systemie operacyjnym i kodu zarządzanego, takie jak naruszenia zasad dostępu w [!INCLUDE[TLA#tla_mswin](../includes/tlasharptla-mswin-md.md)], aby zostać obsłużony przez kod zarządzany. Jeśli chcesz skompilować aplikację w [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] lub nowszy i obsługa obsługi wyjątków uszkodzony, możesz zastosować <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu do metody, która obsługuje wyjątek stanie uszkodzenia.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, który narusza tę regułę i typu, który implementuje prawidłowo `catch` bloku.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cpp/FxCop.Design.ExceptionAndSystemException.cpp#1)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/cs/FxCop.Design.ExceptionAndSystemException.cs#1)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ExceptionAndSystemException/vb/FxCop.Design.ExceptionAndSystemException.vb#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2200: Ponownie, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)
