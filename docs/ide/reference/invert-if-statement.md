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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531587"
---
# <a name="invert-if-statement"></a>Odwracanie instrukcji If

Ten refaktoryzator ma zastosowanie do:

- C#
- Visual Basic

**Co:** Umożliwia odwrócenie `if` lub `if else` instrukcji bez zmiany znaczenia kodu.

**Kiedy:** Gdy masz `if` lub `if else` instrukcji, które byłyby lepiej zrozumiałe, gdy odwrócone.

**Dlaczego?** Odwracanie lub `if` `if else` instrukcja ręcznie może trwać znacznie dłużej i ewentualnie wprowadzić błędy. Ta poprawka kodu pomaga wykonać tę refaktoryzacji automatycznie.

## <a name="invert-if-statement-refactoring"></a>Odwróć, jeśli refaktoryzuje instrukcję

1. Umieść kursor w `if` instrukcji `if else` lub instrukcji.

    ![Odwróć, jeśli inaczej](media/invert-if.png)

2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

    ![Popraw kod Odwróć, jeśli inaczej](media/invert-if-codefix.png)

3. Wybierz **opcję Odwróć, jeśli**.

    ![Odwróć, jeśli wynik w przeciwnym razie](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
