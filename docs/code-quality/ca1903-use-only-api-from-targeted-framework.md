---
title: 'CA1903: Używaj tylko interfejsu API platformy docelowej'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 704972127130cc7be991213249ff41212fa40676
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233268"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Używaj tylko interfejsu API platformy docelowej

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategoria|Microsoft. przenośność|
|Zmiana podziału|Przerywanie — gdy jest uruchamiany z podpisem widocznego na zewnątrz elementu członkowskiego lub typu.<br /><br /> Rozdzielenie — gdy jest uruchamiany w treści metody.|

## <a name="cause"></a>Przyczyna
Element członkowski lub typ używa elementu członkowskiego lub typu, który został wprowadzony w dodatku Service Pack, który nie został dołączony do platformy dostosowanej projektu.

## <a name="rule-description"></a>Opis reguły
Nowe elementy członkowskie i typy zostały uwzględnione w .NET Framework 2,0 z dodatkiem Service Pack 1 i 2, .NET Framework 3,0 z dodatkiem Service Pack 1 i 2 oraz .NET Framework 3,5 z dodatkiem Service Pack 1. Projekty przeznaczone dla głównych wersji .NET Framework mogą przypadkowo przyjmować zależności od tych nowych interfejsów API. Aby zapobiec tej zależności, ta reguła jest wyzwalana w przypadku użycia wszelkich nowych elementów członkowskich i typów, które nie zostały uwzględnione domyślnie w strukturze docelowej projektu.

**Zależności platformy docelowej i dodatku Service Pack**

|||
|-|-|
|Gdy platformą docelową jest|Generowane w przypadku użycia elementów członkowskich wprowadzonych w|
|.NET Framework 2.0|.NET Framework 2,0 z dodatkiem SP1, .NET Framework 2,0 SP2|
|.NET Framework 3.0|.NET Framework 2,0 z dodatkiem SP1, .NET Framework 2,0 SP2, .NET Framework 3,0 SP1, .NET Framework 3,0 SP2|
|Program .NET Framework 3,5|.NET Framework 3.5 SP1|
|Program .NET Framework 4|Brak|

Aby zmienić platformę docelową projektu, [zobacz How to: Docelowa wersja platformy](../ide/how-to-target-a-version-of-the-dotnet-framework.md).NET.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby usunąć zależność od dodatku Service Pack, należy usunąć wszystkie użycia nowego elementu członkowskiego lub typu. Jeśli jest to zależność celowa, Pomiń ostrzeżenie lub wyłącz tę regułę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Nie pomijaj ostrzeżenia z tej reguły, jeśli nie jest to oczekiwana zależność od określonego dodatku Service Pack. W takiej sytuacji działanie aplikacji może się nie powieść w systemach, w których nie zainstalowano tego dodatku Service Pack. Pomiń ostrzeżenie lub wyłącz tę regułę, jeśli była to celowa zależność.

## <a name="example"></a>Przykład
Poniższy przykład przedstawia klasę, która używa typu DateTimeOffset, który jest dostępny tylko w programie .NET 2,0 z dodatkiem Service Pack 1. Ten przykład wymaga wybrania .NET Framework 2,0 na liście rozwijanej platformy docelowej we właściwościach projektu.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Przykład
W poniższym przykładzie zostały poprawione opisane wcześniej naruszenia, zastępując użycie typu DateTimeOffset typem DateTime.

[!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)
- [Omówienie określania celu platformy](../ide/visual-studio-multi-targeting-overview.md)