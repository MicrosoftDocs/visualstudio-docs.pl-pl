---
title: Usuwanie nieosiągalnego kodu refaktoryzacji
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 89b203dfb0e8f748f1e6ec11ba3c15927ee669d2
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54917048"
---
# <a name="remove-unreachable-code-refactoring"></a>Usuwanie nieosiągalnego kodu refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Usunięcie kodu, która nigdy nie zostanie wykonana.

**Kiedy:** Program nie ma ścieżki do fragmentu kodu, co ten fragment kodu jest niepotrzebne.

**Dlaczego:** Zwiększ czytelność i łatwość konserwacji przez usunięcie kodu, który jest zbędny i nigdy nie zostanie wykonana.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w dowolnym miejscu w rozmytą się kod, który jest niedostępny:

![Rozmytą nieosiągalnego kodu](media/unreachablecode-faded-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **usuwanie nieosiągalnego kodu** z menu podręcznego okna podglądu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **usuwanie nieosiągalnego kodu** z menu podręcznego okna podglądu.

1. Po zakończeniu zmiany, naciśnij klawisz **Enter** lub kliknij poprawki w menu, a zmiany zostaną zatwierdzone.

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