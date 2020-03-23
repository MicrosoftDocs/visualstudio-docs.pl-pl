---
title: Dzielenie i scalanie instrukcji if
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a3b42f83faacda6be34b282150cf4fb4c0f379f1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093672"
---
# <a name="split-or-merge-if-statements"></a>Dzielenie i scalanie instrukcji if

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co: Co:** **What:** Podziel lub scal [jeśli](/dotnet/csharp/language-reference/keywords/if-else) instrukcje.

**Kiedy:** Chcesz `if` podzielić instrukcję, która `&&` używa `||` lub operatorów `if` do instrukcji `if` zagnieżdżonej lub scalić instrukcję z zewnętrznej `if` instrukcji.

**Dlaczego?** To kwestia preferencji stylu.  

## <a name="how-to"></a>Porady

Jeśli chcesz podzielić `if` instrukcję:

1. Umieść kursor w `if` instrukcji przez `&&` `||` lub operatora.

2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

    ![Instrukcja Podziel if](../media/split-if-statement.png)

3. Wybierz **opcję Podziel na zagnieżdżone, jeśli instrukcje**.

    ![Instrukcja Podziel, jeśli została ukończona](../media/split-if-statement-complete.png)

Jeśli chcesz scalić `if` wewnętrzną `if` instrukcję z instrukcją zewnętrzną: 

1. Umieść kursor w wewnętrznym `if` słowie kluczowym.

2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

    ![Scal, jeśli instrukcja](../media/merge-if-statement.png)

3. Wybierz **pozycję Scal z zewnętrzną instrukcją if**.

    ![Scal, jeśli instrukcja została ukończona](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)