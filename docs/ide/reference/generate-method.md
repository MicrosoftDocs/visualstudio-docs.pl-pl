---
title: Generowanie metody
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f166c31a1615c951170367223a5b19ab93811b5d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595595"
---
# <a name="generate-a-method-in-visual-studio"></a>Generowanie metody w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe dodanie metody do klasy.

**Kiedy:** Wprowadzasz nową metodę i chcesz poprawnie ją zadeklarować, automatycznie.

**Dlaczego?** Można zadeklarować metodę i parametry przed użyciem go, jednak ta funkcja wygeneruje deklarację automatycznie.

## <a name="how-to"></a>Porady

1. Umieść kursor na linii, w której znajduje się czerwona falista. Czerwony squiggle wskazuje metodę, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C #](media/method-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/method-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Najedź kursorem na czerwoną falosę i kliknij przycisk ![błąd żarówki](media/error-bulb.png) pojawi się ikona.
      - Kliknij ikonę ![błąd żarówki](media/error-bulb.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z czerwoną faliczkiem.

      ![Generowanie podglądu metody](media/method-preview-cs.png)

3. Z menu rozwijanego **wybierz opcję Generuj metodę.**

   > [!TIP]
   > Użyj łącza **Podgląd zmian** u dołu okna podglądu, [aby wyświetlić wszystkie zmiany,](../../ide/preview-changes.md) które zostaną wprowadzone przed dokonaniem wyboru.

   Metoda jest tworzona z dowolnymi parametrami wywnioskowane z jej użycia.

   - C#:

       ![Generowanie wyniku metody C #](media/method-result-cs.png)

   - Visual Basic:

       ![Generowanie wyniku metody VB](media/method-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
