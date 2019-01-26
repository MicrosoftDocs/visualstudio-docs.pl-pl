---
title: 'CA1903: Używaj tylko interfejsu API platformy docelowej'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 2483ebbaab2009d514ecb1ecec31f8ac78d35b6a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54943997"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Używaj tylko interfejsu API platformy docelowej

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategoria|Microsoft.Portability|
|Zmiana kluczowa|Przerywanie — gdy wywoływane przed podpis widocznego na zewnątrz elementu członkowskiego lub typu.<br /><br /> Bez podziału — gdy wywoływane w treści metody.|

## <a name="cause"></a>Przyczyna
 Element członkowski lub typ używa elementu członkowskiego lub typu, która została wprowadzona w dodatku service pack, który nie był dołączony do platformy docelowej projektu.

## <a name="rule-description"></a>Opis reguły
 Nowi członkowie i typy zostały uwzględnione w .NET Framework 2.0 z dodatkiem Service Pack 1 i 2, .NET Framework 3.0 z dodatkiem Service Pack 1 i 2 i .NET Framework 3.5 Service Pack 1. Projekty przeznaczone dla wersji głównych programu .NET Framework przypadkowo może zależności na te nowe interfejsy API. Aby uniknąć tej zależności, ta reguła jest uruchamiana na użycia żadnych nowych elementów członkowskich i typy, które nie zostały uwzględnione domyślnie platforma docelowa projektu.

 **Platforma docelowa i zależności pakietu usługi**

|||
|-|-|
|Gdy jest platforma docelowa|Uruchamiany na użycia elementów członkowskich wprowadzone w systemie|
|.NET Framework 2.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2|
|.NET Framework 3.0|.NET Framework 2.0 SP1, .NET Framework 2.0 SP2, .NET Framework 3.0 SP1, .NET Framework 3.0 SP2|
|Program .NET Framework 3,5|.NET Framework 3.5 SP1|
|Program .NET Framework 4|Brak|

 Aby zmienić platformę docelową projektu, zobacz [przeznaczonych dla określonej wersji programu .NET Framework](../ide/visual-studio-multi-targeting-overview.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć zależność od dodatku service pack, należy usunąć wszystkie użycia nowego elementu członkowskiego lub typu. Jeśli jest to zamierzone zależności, ostrzeżenia lub wyłącz tę regułę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły, jeśli nie jest to zamierzone zależności określonej z dodatkiem Service Pack. W takiej sytuacji aplikacja może zakończyć się niepowodzeniem działające w systemach bez tego dodatku service pack, zainstalowane. Pomijaj ostrzeżenia lub wyłącz tę regułę, jeśli jest to zamierzone zależności.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia klasę, która używa typu DateTimeOffset, która jest dostępna tylko w dodatku Service Pack 1 dla platformy .NET w wersji 2.0. W tym przykładzie wymaga, że na liście rozwijanej platformy docelowej we właściwościach projektu wybrano .NET Framework 2.0.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_1.cs)]

## <a name="example"></a>Przykład
 Poniższy przykład naprawia naruszenie opisany wcześniej, zastępując użycia typu DateTimeOffset typu DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../code-quality/codesnippet/CSharp/ca1903-use-only-api-from-targeted-framework_2.cs)]

## <a name="see-also"></a>Zobacz także

- [Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md)
- [Określanie konkretnej wersji programu .NET Framework jako docelowej](../ide/visual-studio-multi-targeting-overview.md)