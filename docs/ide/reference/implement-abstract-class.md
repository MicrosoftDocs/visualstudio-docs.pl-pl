---
title: Implementowanie klasy abstrakcyjnej
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6fcfdc06a055df28159f9d1ddc440aaf113f3264
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568909"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementowanie klasy abstrakcyjnej w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu wymaganego do zaimplementowania klasy abstrakcyjnej.

**Kiedy:** Chcesz dziedziczyć z klasy abstrakcyjnej.

**Dlaczego?** Można ręcznie zaimplementować wszystkie abstrakcyjne elementy członkowskie jeden po drugim, jednak ta funkcja automatycznie wygeneruje wszystkie podpisy metod.

## <a name="how-to"></a>Porady

1. Umieść kursor w wierszu, w którym znajduje się czerwona falista, która wskazuje, że zostały odziedziczone z klasy abstrakcyjnej, ale nie zaimplementowano wszystkich wymaganych elementów członkowskich.

   - C#:

       ![Wyróżniony kod C #](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/abstract-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Najedź kursorem na czerwoną falosę i kliknij przycisk ![błąd żarówki](media/error-bulb.png) pojawi się ikona.
      - Kliknij ikonę ![błąd żarówki](media/error-bulb.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z czerwoną faliczkiem.

   ![Implementowanie podglądu klasy](media/abstract-preview-cs.png)

3. Z menu rozwijanego **wybierz pozycję Implementuj klasę abstrakcyjną.**

   > [!TIP]
   > - Użyj łącza **Podgląd zmian** u dołu okna podglądu, [aby wyświetlić wszystkie zmiany,](../../ide/preview-changes.md) które zostaną wprowadzone przed dokonaniem wyboru.
   > - Użyj **łącza Dokumentu,** **Projektu**i **Rozwiązania** u dołu okna podglądu, aby utworzyć odpowiednie podpisy metod w wielu klasach, które dziedziczą z klasy abstrakcyjnej.

   Podpisy metody abstrakcyjnej są tworzone i są gotowe do zaimplementowania.

   - C#:

       ![Zaimplementowanie wyniku klasy C #](media/abstract-result-cs.png)

   - Visual Basic:

       ![Implementowanie wyniku klasy VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
