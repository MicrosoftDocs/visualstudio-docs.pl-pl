---
title: Przenieś deklarację zmiennej blisko odwołania
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: c0a82b48a556e26866393661d4b87836db765abb
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666500"
---
# <a name="move-declaration-near-reference-refactoring"></a>Przenieś deklarację do refaktoryzacji odwołania

To Refaktoryzacja dotyczy:

- C#

**Co:** Umożliwia przenoszenie deklaracji zmiennych bliżej ich użycia.

**Kiedy:** Istnieją deklaracje zmiennych, które mogą znajdować się w węższym zakresie.

**Dlaczego:** Można go pozostawić w taki sposób, ale może to spowodować problemy z odczytem lub ukrywanie informacji. Jest to szansa, aby można było poprawić czytelność.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w deklaracji zmiennej.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** i wybrać pozycję **Przenieś deklarację blisko odwołania** w oknie podręcznym okna podglądu.
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Przenieś deklarację blisko odwołania** w oknie podręcznym okna podglądu.

1. Po zakończeniu zmiany naciśnij klawisz **Enter** lub kliknij poprawkę w menu, a zmiany zostaną zatwierdzone.

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