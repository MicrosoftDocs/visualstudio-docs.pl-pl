---
title: Zastąp zmienną tymczasową jej wartością
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568870"
---
# <a name="inline-a-temporary-variable-refactoring"></a>Wbudowana tymczasowa zmienna refaktoryzująca

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia usunięcie zmiennej tymczasowej i zastąpienie jej jej wartością.

**Kiedy:** Użycie zmiennej tymczasowej sprawia, że kod trudniejsze do zrozumienia.

**Dlaczego?** Usunięcie zmiennej tymczasowej może ułatwić odczytanie kodu.

## <a name="how-to"></a>Porady

1. Podświetl lub umieść kursor tekstowy wewnątrz zmiennej tymczasowej, która ma być inlined:

   - C#:

       ![Wyróżniony kod - C #](media/inline-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — visual basic](media/inline-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy kod i wybierz menu **Szybkie akcje i Refaktoryzowania.**

3. Z okna podglądu **wybierz opcję Zmienna tymczasowa w** linii wbudowanej.

   Zmienna jest usuwana, a jej użycia zastąpione wartością zmiennej.

   - C#:

      ![Wynik wbudowany - C #](media/inline-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowany — visual basic](media/inline-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
