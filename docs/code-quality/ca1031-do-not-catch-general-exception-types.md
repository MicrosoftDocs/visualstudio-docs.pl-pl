---
title: 'CA1031: Nie przechwytuj wyjątków typów ogólnych'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
helpviewer_keywords:
- CA1031
- DoNotCatchGeneralExceptionTypes
ms.assetid: cbc283ae-2a46-4ec0-940e-85aa189b118f
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 844f6686205f7aaa6c1b8b8c198eb4240d6d1fab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878302"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj wyjątków typów ogólnych

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
> Począwszy od [!INCLUDE[net_v40_long](../code-quality/includes/net_v40_long_md.md)], środowisko uruchomieniowe języka wspólnego (CLR) dostarcza już wyjątki uszkodzony, które występują w systemie operacyjnym i kodu zarządzanego, takie jak naruszenia zasad dostępu w [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], aby zostać obsłużony przez kod zarządzany. Jeśli chcesz skompilować aplikację w [!INCLUDE[net_v40_short](../code-quality/includes/net_v40_short_md.md)] lub nowszy i obsługa obsługi wyjątków uszkodzony, możesz zastosować <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu do metody, która obsługuje wyjątek stanie uszkodzenia.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, który narusza tę regułę i typu, który implementuje prawidłowo `catch` bloku.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2200: Ponownie, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)