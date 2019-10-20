---
title: Wprowadź zmienną lokalną
description: Wygeneruj zmienną lokalną, aby zastąpić istniejące wyrażenie. Zaznacz wyrażenie, kliknij prawym przyciskiem myszy i wybierz menu szybkie akcje i refaktoryzacje, wybierz pozycję Wprowadź wartość lokalna dla (wszystkie wystąpienia) wyrażenia "Expression".
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 6407810b4143d5edacecf42990ae5b6d63497be2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668753"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Wprowadzanie zmiennej lokalnej w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie zmiennej lokalnej w celu zastąpienia istniejącego wyrażenia.

**Kiedy:** Masz kod, który może być łatwo ponownie wykorzystany później, jeśli był w zmiennej lokalnej.

**Dlaczego:** Można kopiować i wklejać kod wielokrotnie, aby używać go w różnych lokalizacjach, jednak lepszym rozwiązaniem jest wykonanie operacji raz, zapisanie wyniku w zmiennej lokalnej i użycie zmiennej lokalnej w całym.

## <a name="how-to"></a>Instrukcje

1. Zaznacz wyrażenie, które ma zostać przypisane do nowej zmiennej lokalnej.

   - C#:

       ![Wyróżniony kodC#](media/local-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/local-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Kliknij ikonę ![śrubokręt](media/screwdriver.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z wyróżnionym wyrażeniem.

   ![Wprowadź lokalną wersję zapoznawczą](media/local-preview-cs.png)

3. Wybierz pozycję **wprowadź lokalne dla (wszystkie wystąpienia)** z menu rozwijanego.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.

   Zostanie utworzona zmienna lokalna z typem wywnioskowanym na podstawie jego użycia. Nadaj nowej nazwie nową zmienną lokalną.

   - C#:

       ![Zaimplementuj wynik interfejsuC#](media/local-result-cs.png)

   - Visual Basic:

       ![Implementuj wyniki interfejsu VB](media/local-result-vb.png)

   > [!NOTE]
   > Możesz użyć.. **. wszystkie wystąpienia...** opcja menu, aby zamienić każde wystąpienie wybranego wyrażenia, a nie tylko te, które zostały specjalnie wyróżnione.

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)