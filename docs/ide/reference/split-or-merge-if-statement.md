---
title: Dzielenie i scalanie instrukcji if
ms.date: 06/12/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 405ccd4bc0197ce06aa14982a16dc02f6d13a537
ms.sourcegitcommit: d4920babfc3d24a3fe1d4bf446ed3fe73b344467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2019
ms.locfileid: "67160721"
---
# <a name="split-or-merge-if-statements"></a>Dzielenie i scalanie instrukcji if

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** **Co:** Dzielenie i scalanie [Jeśli](/dotnet/csharp/language-reference/keywords/if-else) instrukcji.

**Kiedy:** Chcesz podzielić `if` instrukcję, która używa `&&` lub `||` operatorów w zagnieżdżonych `if` instrukcji lub scalania `if` instrukcji z zewnętrznym `if` instrukcji.

**Dlaczego:** Jest kwestią preferencji stylu.  

## <a name="how-to"></a>Instrukcje

Jeśli chcesz podzielić `if` instrukcji:

1. Umieść kursor w `if` oświadczenie `&&` lub `||` operatora.

2. Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

    ![Podziel If — instrukcja](../media/split-if-statement.png)

3. Wybierz **podzielić zagnieżdżonymi instrukcji**.

    ![Jeśli dzielenie pełną instrukcję](../media/split-if-statement-complete.png)

Jeśli chcesz scalić wewnętrzny `if` instrukcję, określając zewnętrzny `if` instrukcji: 

1. Umieść kursor w wewnętrzny `if` — słowo kluczowe.

2. Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

    ![Scal, jeśli instrukcja](../media/merge-if-statement.png)

3. Wybierz **łączyć się z zewnętrznym, jeśli instrukcja**.

    ![Scal, jeśli instrukcja ukończone](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)