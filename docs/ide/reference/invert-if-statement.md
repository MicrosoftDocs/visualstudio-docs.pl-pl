---
title: Odwracanie instrukcji If
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby odwrócić instrukcję if lub if else bez zmiany znaczenia kodu.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cf4ad7c25030e4a331ee67f4957ddac59afdd966
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852235"
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
