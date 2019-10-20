---
title: Usuwanie nieosiągalnego refaktoryzacji kodu
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 1e5bdab773cf70963e1d0f485a7779e57084c8a0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655606"
---
# <a name="remove-unreachable-code-refactoring"></a>Usuwanie nieosiągalnego refaktoryzacji kodu

To Refaktoryzacja dotyczy:

- C#

**Co:** Usuwa kod, który nigdy nie będzie wykonywany.

**Kiedy:** Program nie ma ścieżki do fragmentu kodu, dzięki czemu fragment kodu nie jest zbędny.

**Dlaczego:** Zwiększ czytelność i łatwość utrzymania, usuwając kod, który jest zbędny i nigdy nie będzie wykonywany.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w dowolnym miejscu w nieosiągalnym kodzie:

![Wyblakły nieosiągalny kod](media/unreachablecode-faded-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Usuń nieosiągalny kod** z okna podręcznego w oknie podglądu.
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Usuń nieosiągalny kod** z okna podręcznego w oknie podglądu.

1. Po zakończeniu zmiany naciśnij klawisz **Enter** lub kliknij poprawkę w menu, a zmiany zostaną zatwierdzone.

Przykład:

```csharp
// Before
private void Method()
{
    throw new Exception(nameof(Method));
    Console.WriteLine($"Exception for method {nameof(Method)}");
}

// Remove unreachable code

// After
private void Method()
{
    throw new Exception(nameof(Method));
}
```

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)