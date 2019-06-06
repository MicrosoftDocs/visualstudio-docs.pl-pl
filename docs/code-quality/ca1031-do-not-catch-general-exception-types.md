---
title: 'CA1031: Nie przechwytuj typów wyjątków ogólnych'
ms.date: 11/04/2016
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
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: e9746119c746679817076c86e3d5a9080cec30d9
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66744683"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj typów wyjątków ogólnych

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
> Począwszy od programu .NET Framework 4 środowisko uruchomieniowe języka wspólnego (CLR) nie jest już dostarcza wyjątki uszkodzony, które występują w systemie operacyjnym i kodu zarządzanego, takie jak naruszenia zasad dostępu w [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)], aby zostać obsłużony przez kod zarządzany. Jeśli do kompilacji aplikacji w programie .NET Framework 4 lub nowszy, a obsługa obsługą wyjątków uszkodzony, możesz zastosować <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybutu do metody, która obsługuje wyjątek stanie uszkodzenia.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia typ, który narusza tę regułę i typu, który implementuje prawidłowo `catch` bloku.

 [!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
 [!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
 [!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA2200: Ponownie, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)