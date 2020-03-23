---
title: Wprowadzenie zmiennej lokalnej
description: Wygeneruj zmienną lokalną, aby zastąpić istniejące wyrażenie. Zaznacz wyrażenie, kliknij prawym przyciskiem myszy i wybierz menu Szybkie akcje i Refaktoryzowania, wybierz polecenie Wprowadzenie lokalnego dla (wszystkich wystąpień) wyrażenia.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0fbd5ed752b28cc3f8c0dd734ed2b3ce09e80b78
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568818"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Wprowadzenie zmiennej lokalnej w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie zmiennej lokalnej w celu zastąpienia istniejącego wyrażenia.

**Kiedy:** Masz kod, który można łatwo ponownieżyć później, jeśli były w zmiennej lokalnej.

**Dlaczego?** Można skopiować i wkleić kod wiele razy, aby użyć go w różnych lokalizacjach, jednak lepiej byłoby wykonać operację raz, przechowywać wynik w zmiennej lokalnej i używać zmiennej lokalnej w całym.

## <a name="how-to"></a>Porady

1. Wyróżnij wyrażenie, które chcesz przypisać do nowej zmiennej lokalnej.

   - C#:

       ![Wyróżniony kod C #](media/local-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/local-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Kliknij ikonę ![Śrubokręt](media/screwdriver.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z wyróżnionym wyrażeniem.

   ![Wprowadzenie lokalnej wersji zapoznawczej](media/local-preview-cs.png)

3. Z menu **rozwijanego wybierz opcję Wprowadzenie lokalnego dla (wszystkich wystąpień) wyrażenia.**

   > [!TIP]
   > Użyj łącza **Podgląd zmian** u dołu okna podglądu, [aby wyświetlić wszystkie zmiany,](../../ide/preview-changes.md) które zostaną wprowadzone przed dokonaniem wyboru.

   Zmienna lokalna jest tworzona, z typem wywnioskowane z jego użycia. Nadaj nowej zmiennej lokalnej nową nazwę.

   - C#:

       ![Implementowanie wyniku interfejsu C #](media/local-result-cs.png)

   - Visual Basic:

       ![Implementowanie wyniku interfejsu VB](media/local-result-vb.png)

   > [!NOTE]
   > Możesz użyć **... wszystkie wystąpienia...** opcja menu, aby zastąpić każde wystąpienie wybranego wyrażenia, a nie tylko to, które zostało wyraźnie wyróżnione.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
