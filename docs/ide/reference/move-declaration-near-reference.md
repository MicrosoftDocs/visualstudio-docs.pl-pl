---
title: Przenieś deklarację zmiennej blisko odwołania
description: Dowiedz się, jak za pomocą menu szybkie akcje i refabryki przenieść deklaracje zmiennych bliżej ich użycia.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 188907b4f1b6630e95ab435d588878b16c763f4a
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616931"
---
# <a name="move-declaration-near-reference-refactoring"></a>Przenieś deklarację do refaktoryzacji odwołania

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia przenoszenie deklaracji zmiennych bliżej ich użycia.

**Kiedy:** Istnieją deklaracje zmiennych, które mogą znajdować się w węższym zakresie.

**Dlaczego:** Można go pozostawić w taki sposób, ale może to spowodować problemy z odczytem lub ukrywanie informacji. Jest to szansa, aby można było poprawić czytelność.

## <a name="how-to"></a>Porady

1. Umieść kursor w deklaracji zmiennej.

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** i wybrać pozycję **Przenieś deklarację blisko odwołania** w oknie podręcznym okna podglądu.
   - **Mysz**
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
