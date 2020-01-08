---
title: Zamień na wartość Zmienna tymczasowa
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8f0199436f5f9b1013a4c49cfb5909e760c73dcc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568870"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Wbudowanej zmiennej tymczasowej refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

- Język Visual Basic

**Co:** pozwala usunąć zmienną tymczasową i zamienić ją na jej wartość.

**Kiedy:** wykorzystanie zmiennej tymczasowej sprawia, że kod jest trudniejsze do zrozumienia.

**Dlaczego:** usuwanie zmiennej tymczasowej może poprawić czytelność kodu.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekstu w zmiennej tymczasowej, aby był śródwierszowy:

   - C#:

       ![Wyróżniony kod-C#](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/inline-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
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
