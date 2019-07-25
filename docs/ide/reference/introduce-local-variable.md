---
title: Wprowadzanie zmiennej lokalnej
description: Wygeneruj zmienną lokalną, aby zastąpić istniejące wyrażenie. Zaznacz wyrażenie, kliknij prawym przyciskiem myszy i wybierz menu szybkie akcje i refaktoryzacje, wybierz pozycję Wprowadź wartość lokalna dla (wszystkie wystąpienia) wyrażenia "Expression".
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 43f54072d495cfdd6607ccb033ffd1a1713ad8bb
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483696"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Wprowadzanie zmiennej lokalnej w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Whatman** Umożliwia natychmiastowe wygenerowanie zmiennej lokalnej w celu zastąpienia istniejącego wyrażenia.

**Czasie** Masz kod, który może być łatwo ponownie wykorzystany później, jeśli był w zmiennej lokalnej.

**Zalet** Można kopiować i wklejać kod wielokrotnie, aby używać go w różnych lokalizacjach, jednak lepszym rozwiązaniem jest wykonanie operacji raz, zapisanie wyniku w zmiennej lokalnej i użycie zmiennej lokalnej w całym.

## <a name="how-to"></a>Instrukcje

1. Zaznacz wyrażenie, które chcesz przypisać do zmiennej lokalnej.

   - C#:

       ![Wyróżniony kod C#](media/local-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony Kod VB](media/local-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Kliknij ikonę ![śrubokręt](media/screwdriver.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z wyróżnionym wyrażeniem.

   ![Wprowadzenie lokalnego (wersja zapoznawcza)](media/local-preview-cs.png)

3. Wybierz pozycję **wprowadź lokalne dla (wszystkie wystąpienia)** z menu rozwijanego.

   > [!TIP]
   > Użyj **podgląd zmian** link w dolnej części okna podglądu [Aby wyświetlić wszystkie zmiany](../../ide/preview-changes.md) , zostaną wprowadzone przed dokonaniem wyboru.

   Zmienna lokalna jest tworzony z typem wywnioskować na podstawie jej użycie. Nadaj nowej zmiennej lokalnej nową nazwę.

   - C#:

       ![Implementuj interfejs wynik C#](media/local-result-cs.png)

   - Visual Basic:

       ![Implementuj interfejs wynik VB](media/local-result-vb.png)

   > [!NOTE]
   > Możesz użyć **.. wyświetlacze wystąpień...**  opcję menu, aby zastąpić każde wystąpienie wybranego wyrażenia, a nie tylko jedną, specjalnie wyróżnioną pozycją.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)