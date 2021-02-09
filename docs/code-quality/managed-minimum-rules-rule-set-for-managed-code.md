---
title: Zarządzany minimalny zestaw reguł dla kodu zarządzanego
ms.date: 11/04/2016
description: Poznaj reguły dotyczące zarządzanych reguł minimalnych w programie Visual Studio, które koncentrują się na zabezpieczeniach, niezawodności i innych problemach krytycznych. Zobacz opisy reguł.
ms.custom: SEO-VS-2020
ms.topic: reference
ms.assetid: 44a50c54-8dd3-42b2-8387-532a150e5a6c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 8711fd0a265618a5aaf4f84edcf7dd2b081b16a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99859817"
---
# <a name="managed-minimum-rules-rule-set-for-managed-code"></a>Zarządzany minimalny zestaw reguł dla kodu zarządzanego

Zarządzane reguły minimalne koncentrują się na najważniejszych problemach w kodzie, takich jak potencjalne luki w zabezpieczeniach, awarie aplikacji oraz inne ważne błędy logiki i projektowania. Dołącz ten zestaw reguł do dowolnego niestandardowego zestawu reguł tworzonego dla projektów.

|Reguła|Opis|
|----------|-----------------|
|[CA1001](/dotnet/fundamentals/code-analysis/quality-rules/ca1001)|Typy, do których należą pola możliwe do likwidacji, powinny być możliwe do likwidacji|
|[CA1821](/dotnet/fundamentals/code-analysis/quality-rules/ca1821)|Usuwaj puste finalizatory|
|[CA2213](/dotnet/fundamentals/code-analysis/quality-rules/ca2213)|Pola możliwe do likwidacji należy likwidować|
|[CA2231](/dotnet/fundamentals/code-analysis/quality-rules/ca2231)|Operator przeciążenia jest równy przy zastępowaniu `ValueType.Equals`|
