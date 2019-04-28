---
title: Przenieś deklarację zmiennej blisko odwołania
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e23c5c8d6ea0895f9e5a78e726bb7a7cede071bb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62540599"
---
# <a name="move-declaration-near-reference-refactoring"></a>Przenoszenie deklaracji blisko odwołania refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Pozwala na przechodzenie bliżej deklaracje zmiennych do ich użycia.

**Kiedy:** Masz deklaracji zmiennych, które mogą znajdować się w węższy zakres.

**Dlaczego:** Można go pozostaw, ponieważ istnieje, ale mogą powodować problemy czytelność lub ukrywanie informacji. Jest to możliwość refaktoryzacji w celu poprawienia czytelności.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w deklaracji zmiennej.

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **przenoszenie deklaracji blisko odwołania** z menu podręcznego okna podglądu.
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