---
title: Zamień na wartość Zmienna tymczasowa
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 37a70dd119cf94bf79796cdc0684c8dbee47032c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54991265"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Wbudowanej zmiennej tymczasowej refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Pozwala usunąć zmienną tymczasową i zamienić ją na jej wartość.

**Kiedy:** Użycie zmiennej tymczasowej sprawia, że kod jest trudniejsze do zrozumienia.

**Dlaczego:** Usuwanie zmiennej tymczasowej może czytelność kodu.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekstu w zmiennej tymczasowej, aby był śródwierszowy:

   - C#:

       ![Wyróżniony kod-C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/inline-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy ten kod, a następnie wybierz pozycję **szybkie akcje i Refaktoryzacje** menu.

3. Wybierz **wstawiona zmienna tymczasowa** z menu podręcznego okna podglądu.

   Zmienna zostanie usunięty, a jego użycia zastępuje wartość zmiennej.

   - C#:

      ![Wynik wbudowane-C#](media/inline-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowane - Visual Basic](media/inline-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)