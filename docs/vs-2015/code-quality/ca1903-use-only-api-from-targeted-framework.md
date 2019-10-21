---
title: 'CA1903: Używaj tylko interfejsu API z platformy dostosowanej | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseOnlyAPIFromTargetedFramework
- CA1903
helpviewer_keywords:
- UseOnlyApiFromTargetedFramework
- CA1903
ms.assetid: efdb5cc7-bbd8-4fa7-9fff-02b91e59350e
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7dec130e4a4704bea347f94ff57d354a4465ddd6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604976"
---
# <a name="ca1903-use-only-api-from-targeted-framework"></a>CA1903: Używaj tylko API z frameworku docelowego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby uzyskać najnowszą dokumentację programu Visual Studio, zobacz [CA1903: Używaj tylko interfejsu API z platformy dostosowanej](https://docs.microsoft.com/visualstudio/code-quality/ca1903-use-only-api-from-targeted-framework).

|||
|-|-|
|TypeName|UseOnlyApiFromTargetedFramework|
|CheckId|CA1903|
|Kategoria|Microsoft. przenośność|
|Zmiana kluczowa|Przerywanie — gdy jest uruchamiany z podpisem widocznego na zewnątrz elementu członkowskiego lub typu.<br /><br /> Rozdzielenie — gdy jest uruchamiany w treści metody.|

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

 Aby zmienić platformę docelową projektu, zobacz [Określanie docelowej wersji .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md).

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby usunąć zależność od dodatku Service Pack, należy usunąć wszystkie użycia nowego elementu członkowskiego lub typu. Jeśli jest to zależność celowa, Pomiń ostrzeżenie lub wyłącz tę regułę.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżenia z tej reguły, jeśli nie jest to oczekiwana zależność od określonego dodatku Service Pack. W takiej sytuacji działanie aplikacji może się nie powieść w systemach, w których nie zainstalowano tego dodatku Service Pack. Pomiń ostrzeżenie lub wyłącz tę regułę, jeśli była to celowa zależność.

## <a name="example"></a>Przykład
 Poniższy przykład przedstawia klasę, która używa typu DateTimeOffset, który jest dostępny tylko w programie .NET 2,0 z dodatkiem Service Pack 1. Ten przykład wymaga wybrania .NET Framework 2,0 na liście rozwijanej platformy docelowej we właściwościach projektu.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework.cs#1)]

## <a name="example"></a>Przykład
 W poniższym przykładzie zostały poprawione opisane wcześniej naruszenia, zastępując użycie typu DateTimeOffset typem DateTime.

 [!code-csharp[FxCop.Portability.UseOnlyApiFromTargetedFramework2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Portability.UseOnlyApiFromTargetedFramework2/CS/FxCop.Portability.UseOnlyApiFromTargetedFramework2.cs#1)]

## <a name="see-also"></a>Zobacz też
 [Ostrzeżenia dotyczące przenośności](../code-quality/portability-warnings.md) [ukierunkowane na określoną .NET Framework wersję](../ide/targeting-a-specific-dotnet-framework-version.md)
