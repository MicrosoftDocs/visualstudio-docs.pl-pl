---
title: Wprowadź zmienną lokalną
description: Wygeneruj zmienną lokalną, aby zastąpić istniejące wyrażenie. Zaznacz wyrażenie, kliknij prawym przyciskiem myszy i wybierz menu szybkie akcje i refaktoryzacje, wybierz pozycję Wprowadź wartość lokalna dla (wszystkie wystąpienia) wyrażenia "Expression".
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0fbd5ed752b28cc3f8c0dd734ed2b3ce09e80b78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75568818"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Wprowadzanie zmiennej lokalnej w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie zmiennej lokalnej w celu zastąpienia istniejącego wyrażenia.

**Kiedy:** Masz kod, który może być łatwo ponownie wykorzystany później, jeśli był w zmiennej lokalnej.

**Dlaczego:** Można kopiować i wklejać kod wielokrotnie, aby używać go w różnych lokalizacjach, jednak lepszym rozwiązaniem jest wykonanie operacji raz, zapisanie wyniku w zmiennej lokalnej i użycie zmiennej lokalnej w całym.

## <a name="how-to"></a>Porady

1. Zaznacz wyrażenie, które ma zostać przypisane do nowej zmiennej lokalnej.

   - C#:

       ![Wyróżniony kod C #](media/local-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/local-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Kliknij pozycję ![śrubokręt](media/screwdriver.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z wyróżnionym wyrażeniem.

   ![Wprowadź lokalną wersję zapoznawczą](media/local-preview-cs.png)

3. Wybierz pozycję **wprowadź lokalne dla (wszystkie wystąpienia)** z menu rozwijanego.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.

   Zostanie utworzona zmienna lokalna z typem wywnioskowanym na podstawie jego użycia. Nadaj nowej nazwie nową zmienną lokalną.

   - C#:

       ![Zaimplementuj wynik interfejsu C #](media/local-result-cs.png)

   - Visual Basic:

       ![Implementuj wyniki interfejsu VB](media/local-result-vb.png)

   > [!NOTE]
   > Możesz użyć.. **. wszystkie wystąpienia...** opcja menu, aby zamienić każde wystąpienie wybranego wyrażenia, a nie tylko te, które zostały specjalnie wyróżnione.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
