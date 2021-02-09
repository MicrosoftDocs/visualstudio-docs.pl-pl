---
title: Dzielenie i scalanie instrukcji if
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby podzielić lub scalić instrukcje if.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 30ec77382cf404bc74f2ff5fed71cff360b9f28e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893389"
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