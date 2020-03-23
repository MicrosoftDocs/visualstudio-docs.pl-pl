---
title: Przenoszenie deklaracji zmiennej w pobliżu odwołania
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
ms.openlocfilehash: 1339f4a9d151ef41d9a35c5aac0a96f220a297b3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093990"
---
# <a name="move-declaration-near-reference-refactoring"></a>Przenoszenie deklaracji w pobliżu refaktoryzacji odwołania

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia przeniesienie deklaracji zmiennych bliżej ich użycia.

**Kiedy:** Masz deklaracje zmiennych, które mogą znajdować się w węższym zakresie.

**Dlaczego?** Możesz pozostawić go w takim stanie, w jakim jest, ale może to spowodować problemy z czytelnością lub ukrywanie informacji. Jest to szansa na refaktoryzator w celu poprawy czytelności.

## <a name="how-to"></a>Porady

1. Umieść kursor w deklaracji zmiennej.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania,** a następnie wybrać **polecenie Przenieś deklarację w pobliżu odwołania** z okna podglądu.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzuje** i wybierz polecenie **Przenieś deklarację w pobliżu odwołania** z okna podglądu.

1. Gdy ze zmiany będziesz zadowolony, naciśnij klawisz **Enter** lub kliknij poprawkę w menu, a zmiany zostaną wprowadzone.

Przykład:

```csharp
// Before
int x;
if (condition)
{
    x = 1;
    Console.WriteLine(x);
}

// Move declaration near reference

// After
if (condition)
{
    int x = 1;
    Console.WriteLine(x);
}
```

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
