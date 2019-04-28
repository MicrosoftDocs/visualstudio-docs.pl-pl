---
title: Zarządzany minimalny zestaw reguł dla kodu zarządzanego
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: eb9078050b42998bb88ad71580ecd506b9049f86
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62825380"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Zarządzany minimalny zestaw reguł dla kodu zarządzanego

Zarządzane Minimum rules skoncentrować się na najważniejszych problemów w kodzie, w tym potencjalnych luk w zabezpieczeniach, awarii aplikacji i inne istotne błędy logiki i projektowania. Obejmują ten zestaw reguł każdego niestandardowego zestawu reguł tworzonego dla projektów.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Usuwaj puste finalizatory|
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|Pola możliwe do likwidacji należy likwidować|
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Przeciążaj operator równości w przypadku przesłaniania metody ValueType.Equals|
