---
title: Zarządzany minimalny zestaw reguł dla kodu zarządzanego
ms.date: 11/04/2016
description: Poznaj reguły dotyczące zarządzanych reguł minimalnych w programie Visual Studio, które koncentrują się na zabezpieczeniach, niezawodności i innych problemach krytycznych. Zobacz opisy reguł.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5a0e5c59621f948cbb7465a6726fa8c3003480d4
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/10/2020
ms.locfileid: "94435394"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Zarządzany minimalny zestaw reguł dla kodu zarządzanego

Zarządzane reguły minimalne koncentrują się na najważniejszych problemach w kodzie, takich jak potencjalne luki w zabezpieczeniach, awarie aplikacji oraz inne ważne błędy logiki i projektowania. Dołącz ten zestaw reguł do dowolnego niestandardowego zestawu reguł tworzonego dla projektów.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Usuwaj puste finalizatory|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Pola możliwe do likwidacji należy likwidować|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Operator przeciążenia jest równy przy zastępowaniu `ValueType.Equals`|
