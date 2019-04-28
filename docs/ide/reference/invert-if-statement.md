---
title: Odwracanie instrukcji If
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 5a809eee1eb5460e245f64156385f759870adbd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62970276"
---
# <a name="invert-if-statement"></a>Odwracanie instrukcji If

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

    ![Odwróć, jeśli program tworzący poprawki kodu else](media/invert-if-codefix.png)

3. Wybierz **Odwróć Jeśli**.

    ![Odwróć, jeśli inny wynik](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
