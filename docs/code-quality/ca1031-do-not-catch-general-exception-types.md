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
ms.openlocfilehash: c1dc1e5ed18ddcd42d42c96f3f853808c58ade48
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236067"
---
# <a name="ca1031-do-not-catch-general-exception-types"></a>CA1031: Nie przechwytuj typów wyjątków ogólnych

|||
|-|-|
|TypeName|DoNotCatchGeneralExceptionTypes|
|CheckId|CA1031|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna
Ogólny wyjątek, taki jak <xref:System.Exception?displayProperty=fullName> lub <xref:System.SystemException?displayProperty=fullName> , jest przechwytywany `catch` w instrukcji lub Ogólna klauzula catch, taka jak `catch()` .

## <a name="rule-description"></a>Opis reguły
Ogólne wyjątki nie powinny być przechwytywane.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, Przechwyć bardziej szczegółowy wyjątek lub ponownie Zgłoś wyjątek ogólny jako ostatnią instrukcję w `catch` bloku.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżeń dla tej reguły. Przechwytywanie typów wyjątków ogólnych może spowodować ukrycie problemów w czasie wykonywania z poziomu użytkownika biblioteki i utrudnienie debugowania.

> [!NOTE]
> Począwszy od .NET Framework 4, środowisko uruchomieniowe języka wspólnego (CLR) nie dostarcza już wyjątków uszkodzonych stanu występujących w systemie operacyjnym i kodzie zarządzanym, na przykład naruszeń dostępu [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)]w, do obsługi przez kod zarządzany. Jeśli chcesz skompilować aplikację w .NET Framework 4 lub nowszej wersji i zachować obsługę wyjątków uszkodzonych Stanów, możesz zastosować <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute> atrybut do metody, która obsługuje wyjątek uszkodzony stan.

## <a name="example"></a>Przykład
Poniższy przykład pokazuje typ, który narusza tę regułę i typ, który poprawnie implementuje `catch` blok.

[!code-cpp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CPP/ca1031-do-not-catch-general-exception-types_1.cpp)]
[!code-vb[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/VisualBasic/ca1031-do-not-catch-general-exception-types_1.vb)]
[!code-csharp[FxCop.Design.ExceptionAndSystemException#1](../code-quality/codesnippet/CSharp/ca1031-do-not-catch-general-exception-types_1.cs)]

## <a name="related-rules"></a>Powiązane reguły
[CA2200: Zgłoś ponownie, aby zachować szczegóły stosu](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)