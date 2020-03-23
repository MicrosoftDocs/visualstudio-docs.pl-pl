---
title: Usuwanie nieosiągalnego refaktoryzacji kodu
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
ms.openlocfilehash: cd827870f07fb3161674d287d20f266942e61afe
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093981"
---
# <a name="remove-unreachable-code-refactoring"></a>Usuwanie nieosiągalnego refaktoryzacji kodu

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Usuwa kod, który nigdy nie zostanie wykonany.

**Kiedy:** Program nie ma ścieżki do fragmentu kodu, co sprawia, że fragment kodu niepotrzebne.

**Dlaczego?** Zwiększ czytelność i łatwość konserwacji, usuwając kod, który jest zbędny i nigdy nie zostanie wykonany.

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym miejscu w wyblakłym kodzie, który jest nieosiągalny:

![Wyblakły nieosiągalny kod](media/unreachablecode-faded-cs.png)

1. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania,** a następnie wybrać **Usuń nieosiągalny kod** z okna podglądu.
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz polecenie **Usuń nieosiągalny kod** z okna podglądu.

1. Gdy ze zmiany będziesz zadowolony, naciśnij klawisz **Enter** lub kliknij poprawkę w menu, a zmiany zostaną wprowadzone.

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
