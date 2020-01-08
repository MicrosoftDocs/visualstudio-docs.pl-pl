---
title: Przenieś deklarację zmiennej blisko odwołania
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 35735009a5b813ca29159f276fe2d5abb734be0e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585287"
---
# <a name="move-declaration-near-reference-refactoring"></a>Przenoszenie deklaracji blisko odwołania refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

**Co:** pozwala na przechodzenie bliżej deklaracje zmiennych do ich użycia.

**Kiedy:** masz deklaracji zmiennych, które mogą znajdować się w węższy zakres.

**Dlaczego:** może ona pozostaw, ponieważ istnieje, ale mogą powodować problemy czytelność lub ukrywanie informacji. Jest to możliwość refaktoryzacji w celu poprawienia czytelności.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w deklaracji zmiennej.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **przenoszenie deklaracji blisko odwołania** z menu podręcznego okna podglądu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **przenoszenie deklaracji blisko odwołania** z menu podręcznego okna podglądu.

1. Po zakończeniu zmiany, naciśnij klawisz **Enter** lub kliknij poprawki w menu, a zmiany zostaną zatwierdzone.

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

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
