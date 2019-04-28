---
title: Zamień na wartość Zmienna tymczasowa
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a7c691efcc507212aa0649b6c4b4179fb8288f06
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423200"
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