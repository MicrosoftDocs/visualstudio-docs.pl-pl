---
title: Ostrzeżenia dotyczące przenośności i współdziałania
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- rules, portability
- interoperability rules
- rules, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8a456f4a24339b6cba5aeec2c9fe64ad3ee278b
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808603"
---
# <a name="portability-and-interoperability-rules"></a>Przenośność i reguły współdziałania

Reguły przenośności obsługują przenośność na różnych platformach. Reguły współdziałania obsługują interakcję z klientami COM.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1401: P/Invoke nie powinna być widoczna](../code-quality/ca1401.md) | Metoda publiczna lub chroniona w typie publicznym ma atrybut System.Runtime.InteropServices.DllImportAttribute (również zaimplementowany przez słowo kluczowe Declare w Visual Basic). Takie metody nie powinny być udostępniane. |
| [CA1416: Weryfikowanie zgodności platformy](../code-quality/ca1416.md) | Korzystanie z interfejsów API zależnych od platformy w składniku sprawia, że kod przestaje działać na wszystkich platformach. |
| [CA1417: nie należy używać `OutAttribute` w parametrach ciągu dla elementu P/Invoke](../code-quality/ca1417.md) | Parametry ciągu przesyłane przez wartość z `OutAttribute` mogą destabilizację środowiska uruchomieniowego, jeśli ciąg jest ciągiem z stażystami. |
