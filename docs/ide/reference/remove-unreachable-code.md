---
title: Usuwanie nieosiągalnego refaktoryzacji kodu
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby usunąć kod, który nigdy nie będzie wykonywany.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a7ce04b38c13b0994d47974488b90114a63495e6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958118"
---
# <a name="remove-unreachable-code-refactoring"></a>Usuwanie nieosiągalnego refaktoryzacji kodu

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Usuwa kod, który nigdy nie będzie wykonywany.

**Kiedy:** Program nie ma ścieżki do fragmentu kodu, dzięki czemu fragment kodu nie jest zbędny.

**Dlaczego:** Zwiększ czytelność i łatwość utrzymania, usuwając kod, który jest zbędny i nigdy nie będzie wykonywany.

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym miejscu w nieosiągalnym kodzie:

![Wyblakły nieosiągalny kod](media/unreachablecode-faded-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Usuń nieosiągalny kod** z okna podręcznego w oknie podglądu.
   - **Mysz**
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

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
