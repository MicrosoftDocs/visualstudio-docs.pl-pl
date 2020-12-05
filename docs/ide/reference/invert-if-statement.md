---
title: Odwracanie instrukcji If
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby odwrócić instrukcję if lub if else bez zmiany znaczenia kodu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 71b3a11e053b6a600d0b33db7c52a91c4950bf5b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616983"
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

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
