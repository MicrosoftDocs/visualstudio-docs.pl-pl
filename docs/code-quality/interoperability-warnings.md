---
title: Ostrzeżenia dotyczące przenośności i współdziałania
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 306c2477e6e5f731ed6dbf20b2cf4d03d4556467
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509916"
---
# <a name="portability-and-interoperability-warnings"></a>Ostrzeżenia dotyczące przenośności i współdziałania

Ostrzeżenia dotyczące przenośności obsługują przenośność na różnych platformach. Ostrzeżenia dotyczące współdziałania obsługują interakcję z klientami modelu COM.

## <a name="in-this-section"></a>W tej sekcji

| Reguła | Opis |
| - | - |
| [CA1401: P/Invoke nie powinna być widoczna](../code-quality/ca1401.md) | Metoda publiczna lub chroniona w typie publicznym ma atrybut System.Runtime.InteropServices.DllImportAttribute (również zaimplementowany przez słowo kluczowe Declare w Visual Basic). Takie metody nie powinny być udostępniane. |
| [CA1417: nie należy używać `OutAttribute` w parametrach ciągu dla elementu P/Invoke](../code-quality/ca1417.md) | Parametry ciągu przesyłane przez wartość z `OutAttribute` mogą destabilizację środowiska uruchomieniowego, jeśli ciąg jest ciągiem z stażystami. |