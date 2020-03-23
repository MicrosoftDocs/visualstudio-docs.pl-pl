---
title: Implementowanie interfejsu
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7d420bd0d42e89476696966f7eda94a19893fc23
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595556"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementowanie interfejsu w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu wymaganego do zaimplementowania interfejsu.

**Kiedy:** Chcesz dziedziczyć z interfejsu.

**Dlaczego?** Można ręcznie zaimplementować cały interfejs jeden po drugim, jednak ta funkcja automatycznie wygeneruje wszystkie podpisy metod.

## <a name="how-to"></a>Porady

1. Umieść kursor w wierszu, w którym znajduje się czerwona falista, która wskazuje, że odwołujesz się do interfejsu, ale nie zaimplementowano wszystkich wymaganych elementów członkowskich.

   - C#:

       ![Wyróżniony kod C #](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/interface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Najedź kursorem na czerwoną falosę i kliknij przycisk ![błąd żarówki](media/error-bulb.png) pojawi się ikona.
      - Kliknij ikonę ![błąd żarówki](media/error-bulb.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z czerwoną faliczkiem.

3. Z menu rozwijanego **wybierz pozycję Zaimplementuj interfejs.**

   ![Implementowanie podglądu interfejsu](media/interface-preview-cs.png)

   > [!TIP]
   > - Użyj łącza **Podgląd zmian** u dołu okna podglądu, [aby wyświetlić wszystkie zmiany,](../../ide/preview-changes.md) które zostaną wprowadzone przed dokonaniem wyboru.
   > - Użyj **łącza Dokumentu,** **Projektu**i **Rozwiązania** u dołu okna podglądu, aby utworzyć odpowiednie podpisy metod w wielu klasach, które implementują interfejs.

   Podpisy metody interfejsu jest tworzony i jest gotowy do zaimplementowania.

   - C#:

       ![Implementowanie wyniku interfejsu C #](media/interface-result-cs.png)

   - Visual Basic:

       ![Implementowanie wyniku interfejsu VB](media/interface-result-vb.png)

   > [!TIP]
   > (tylko C#) Użyj **implement interfejsu jawnie** opcja poprzecznie każdej wygenerowanej metody z nazwą interfejsu, aby uniknąć kolizji nazw.
   >
   > ![Implementowanie interfejsu jawnie wynik](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
