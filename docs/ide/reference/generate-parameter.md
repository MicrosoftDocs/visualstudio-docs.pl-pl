---
title: Generowanie parametr refaktoryzacji
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e95e76c35afdb8cdbe38c8b33329734ba68361b1
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329101"
---
# <a name="generate-parameter"></a>Generowanie parametr

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Automatycznie generuje parametrem metody.

**Kiedy:** Możesz odwoływać się do zmiennej w metodzie, która nie istnieje w bieżącym kontekście i komunikat o błędzie; Możesz wygenerować parametr jako poprawki kodu. 

**Dlaczego:** Można szybko zmodyfikować podpis metody bez utraty kontekstu.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w zmiennej nazwę i naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
1. Wybierz **Generowanie parametr**.

   ![Generowanie parametr](media/generate-parameter.png) 

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
