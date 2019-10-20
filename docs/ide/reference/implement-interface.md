---
title: Implementowanie interfejsu
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 45265c10677b8d3eadc27eb3b6e22c69bb5299be
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658915"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementowanie interfejsu w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu wymaganego do zaimplementowania interfejsu.

**Kiedy:** Chcesz dziedziczyć z interfejsu.

**Dlaczego:** Można ręcznie zaimplementować wszystkie interfejsy jeden po sobie, jednak ta funkcja będzie automatycznie generować wszystkie podpisy metod.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w wierszu, w którym znajduje się czerwony zygzak wskazujący, że odwołuje się do interfejsu, ale nie zaimplementowano wszystkich wymaganych członków.

   - C#:

       ![Wyróżniony kodC#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/interface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij ikonę ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

3. Z menu rozwijanego wybierz pozycję **Implementuj interfejs** .

   ![Implementuj wersję zapoznawczą interfejsu](media/interface-preview-cs.png)

   > [!TIP]
   > - Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.
   > - Użyj linków **dokumentu**, **projektu**i **rozwiązania** w dolnej części okna Podgląd, aby utworzyć odpowiednie sygnatury metod dla wielu klas, które implementują interfejs.

   Sygnatury metod interfejsu są tworzone i gotowe do zaimplementowania.

   - C#:

       ![Zaimplementuj wynik interfejsuC#](media/interface-result-cs.png)

   - Visual Basic:

       ![Implementuj wyniki interfejsu VB](media/interface-result-vb.png)

   > [!TIP]
   > (C# tylko) Użyj opcji **Zaimplementuj interfejs jawnie** , aby przede wszystkim wygenerowanej metody uzyskać nazwę interfejsu, aby uniknąć kolizji nazw.
   >
   > ![Zaimplementuj interfejs jawnie](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)