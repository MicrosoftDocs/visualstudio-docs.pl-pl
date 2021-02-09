---
title: Implementowanie interfejsu
description: Dowiedz się, jak za pomocą menu szybkie akcje i refaktoryzacje natychmiast wygenerować kod wymagany do zaimplementowania interfejsu.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 37adee082f5356180b4e1d58007db48a7f9bb60e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852495"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementowanie interfejsu w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu wymaganego do zaimplementowania interfejsu.

**Kiedy:** Chcesz dziedziczyć z interfejsu.

**Dlaczego:** Można ręcznie zaimplementować wszystkie interfejsy jeden po sobie, jednak ta funkcja będzie automatycznie generować wszystkie podpisy metod.

## <a name="how-to"></a>Porady

1. Umieść kursor w wierszu, w którym znajduje się czerwony zygzak wskazujący, że odwołuje się do interfejsu, ale nie zaimplementowano wszystkich wymaganych członków.

   - C#:

       ![Wyróżniony kod C #](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/interface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij pozycję ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

3. Z menu rozwijanego wybierz pozycję **Implementuj interfejs** .

   ![Implementuj wersję zapoznawczą interfejsu](media/interface-preview-cs.png)

   > [!TIP]
   > - Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.
   > - Użyj linków **dokumentu**, **projektu** i **rozwiązania** w dolnej części okna Podgląd, aby utworzyć odpowiednie sygnatury metod dla wielu klas, które implementują interfejs.

   Sygnatury metod interfejsu są tworzone i gotowe do zaimplementowania.

   - C#:

       ![Zaimplementuj wynik interfejsu C #](media/interface-result-cs.png)

   - Visual Basic:

       ![Implementuj wyniki interfejsu VB](media/interface-result-vb.png)

   > [!TIP]
   > (Tylko w języku C#) Użyj opcji **Zaimplementuj interfejs jawnie** , aby przede wszystkim wygenerowanej metody uzyskać nazwę interfejsu, aby uniknąć kolizji nazw.
   >
   > ![Zaimplementuj interfejs jawnie](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
