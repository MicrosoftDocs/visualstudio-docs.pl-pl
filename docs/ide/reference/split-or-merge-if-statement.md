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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093672"
---
# <a name="split-or-merge-if-statements"></a>Dzielenie i scalanie instrukcji if

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** **co:** podział lub scalanie [if](/dotnet/csharp/language-reference/keywords/if-else) instrukcji.

**Kiedy:** Chcesz podzielić instrukcję używającą `if` `&&` `||` operatorów or do instrukcji zagnieżdżonych `if` lub scalić `if` instrukcję z zewnętrzną `if` instrukcją.

**Dlaczego:** Jest to kwestia preferencji stylu.  

## <a name="how-to"></a>Porady

Jeśli chcesz podzielić `if` instrukcję:

1. Umieść kursor w `if` instrukcji przez `&&` `||` operator or.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

    ![Split if — instrukcja](../media/split-if-statement.png)

3. Wybierz pozycję **Podziel na zagnieżdżone instrukcje if**.

    ![Instrukcja Split if Complete](../media/split-if-statement-complete.png)

Jeśli chcesz scalić wewnętrzną `if` instrukcję z instrukcją zewnętrzną `if` : 

1. Umieść kursor w wewnętrznym `if` słowie kluczowym.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

    ![Merge if — instrukcja](../media/merge-if-statement.png)

3. Wybierz pozycję **Scal z zewnętrzną instrukcją If**.

    ![Scalanie po zakończeniu wykonywania instrukcji](../media/merge-if-statement-complete.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)