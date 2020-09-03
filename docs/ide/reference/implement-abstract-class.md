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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568909"
---
# <a name="implement-an-abstract-class-in-visual-studio"></a>Implementowanie klasy abstrakcyjnej w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu wymaganego do zaimplementowania klasy abstrakcyjnej.

**Kiedy:** Chcesz dziedziczyć z klasy abstrakcyjnej.

**Dlaczego:** Można ręcznie zaimplementować wszystkie abstrakcyjne elementy członkowskie jeden do jednego, jednak ta funkcja będzie automatycznie generować wszystkie podpisy metod.

## <a name="how-to"></a>Porady

1. Umieść kursor w wierszu, w którym znajduje się czerwona zygzakowata, która wskazuje, że dziedziczysz z klasy abstrakcyjnej, ale nie zaimplementowano wszystkich wymaganych elementów członkowskich.

   - C#:

       ![Wyróżniony kod C #](media/abstract-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/abstract-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij pozycję ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

   ![Implementuj Podgląd klasy](media/abstract-preview-cs.png)

3. Wybierz opcję **Implementuj klasę abstrakcyjną** z menu rozwijanego.

   > [!TIP]
   > - Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.
   > - Użyj linków **dokumentu**, **projektu**i **rozwiązania** w dolnej części okna Podgląd, aby utworzyć odpowiednie sygnatury metod dla wielu klas, które dziedziczą z klasy abstrakcyjnej.

   Sygnatury metod abstrakcyjnych są tworzone i są gotowe do zaimplementowania.

   - C#:

       ![Implementuj wynik klasy C #](media/abstract-result-cs.png)

   - Visual Basic:

       ![Implementowanie wyniku klasy VB](media/abstract-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
