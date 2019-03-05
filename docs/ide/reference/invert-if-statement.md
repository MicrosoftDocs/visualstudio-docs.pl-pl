---
title: Odwróć, jeśli instrukcja
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a6dd0a3ebdb41243734850cea4f4b43604ebb94b
ms.sourcegitcommit: 11337745c1aaef450fd33e150664656d45fe5bc5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/04/2019
ms.locfileid: "57325277"
---
# <a name="invert-if-statement"></a>Odwróć, jeśli instrukcja

Ta Refaktoryzacja mają zastosowanie do:

- C#
- Visual Basic

**Co:** Umożliwia Odwróć `if` lub `if else` instrukcji bez zmiany znaczenia kodu.

**Kiedy:** Jeśli masz `if` lub `if else` instrukcję, która będzie lepiej rozumieć, gdy odwrócony.

**Dlaczego:** Odwracanie `if` lub `if else` instrukcji ręcznie może trwać dłużej i ewentualnie wprowadzał błędy. Ta poprawka kodu pomaga to osiągnąć, automatycznie tej refaktoryzacji.

## <a name="invert-if-statement-refactoring"></a>Odwróć, jeśli instrukcja refaktoryzacji

1. Umieść kursor w `if` lub `if else` instrukcji.

    ![Odwróć Jeśli else](media/invert-if.png)

2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

    ![Odwróć, jeśli inne poprawki kodu](media/invert-if-codefix.png)

3. Wybierz **Odwróć Jeśli**.

    ![Odwróć, jeśli inny wynik](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
