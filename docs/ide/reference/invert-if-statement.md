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
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531587"
---
# <a name="invert-if-statement"></a>Odwracanie instrukcji If

To Refaktoryzacja dotyczy:

- C#
- Visual Basic

**Co:** Pozwala odwrócić `if` instrukcję or `if else` bez zmiany znaczenia kodu.

**Kiedy:** Jeśli masz `if` `if else` instrukcję lub, która będzie lepiej zrozumiała po odwrócenia.

**Dlaczego:** Odwracanie `if` `if else` instrukcji or może zająć dużo czasu i może spowodować błędy. Ta poprawka kodu ułatwia automatyczne przeprowadzenie tego refaktoryzacji.

## <a name="invert-if-statement-refactoring"></a>Odwróć Jeśli Refaktoryzacja instrukcji

1. Umieść kursor w `if` `if else` instrukcji or.

    ![Odwróć Jeśli else](media/invert-if.png)

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

    ![Odwróć, Jeśli poprawka kodu else](media/invert-if-codefix.png)

3. Wybierz pozycję **Odwróć, jeśli**.

    ![Odwróć, jeśli wynik jest inny](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
