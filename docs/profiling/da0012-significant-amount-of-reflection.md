---
title: 'DA0012: Znaczna ilość refleksji | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1c1b96e9a73b488ba9c9920e8ea43e27f78f67ed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777676"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Znaczne odbicie

|||
|-|-|
|Identyfikator reguły|DA0012|
|Kategoria|Użycie programu .NET Framework|
|Metody profilowania|Próbkowanie|
|Komunikat|Być może używasz refleksu nadmiernie. Jest to kosztowna operacja.|
|Typ reguły|Ostrzeżenie|

## <a name="cause"></a>Przyczyna
 Wywołania System.Reflection metody, takie jak InvokeMember i GetMember lub typ metody, takie jak MemberInvoke są znaczną część danych profilowania. Jeśli to możliwe, należy rozważyć zastąpienie tych metod wczesnym wiązaniem z metodami zestawów zależnych.

## <a name="rule-description"></a>Opis reguły
 Odbicie jest elastyczne obiektu .NET Framework, który może służyć do wykonywania późnego wiązania aplikacji do zestawu w czasie wykonywania zależne lub do tworzenia i dynamicznie wykonywać nowe typy w czasie wykonywania. Jednak te techniki mogą zmniejszyć wydajność, jeśli są one często używane lub wywoływane w ciasnych pętlach.

 Aby uzyskać więcej informacji, zobacz [sekcji Odbicie i późne powiązanie](/previous-versions/msp-n-p/ff647790(v=pandp.10)#reflection-and-late-binding) rozdziału 5 — poprawa wydajności kodu zarządzanego w zwiększaniu wydajności aplikacji .NET i skalowalności biblioteki wzorców i praktyk w usłudze MSDN.

## <a name="how-to-investigate-a-warning"></a>Jak zbadać ostrzeżenie
 Kliknij dwukrotnie komunikat w oknie Lista błędów, aby przejść do [widoku szczegóły funkcji](../profiling/function-details-view.md) danych profilowania. Sprawdź funkcje wywołujące System.Type lub System.Reflection metody, aby znaleźć sekcje programu, które najczęściej korzystają z interfejsów API odbicie .NET. Należy unikać używania metod, które zwracają metadane. Gdy wydajność aplikacji jest krytyczna, może być konieczne unikanie używania późnego wiązania i dynamicznego tworzenia typów w czasie wykonywania.
