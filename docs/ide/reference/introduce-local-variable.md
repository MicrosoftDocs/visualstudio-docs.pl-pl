---
title: Wprowadzanie zmiennej lokalnej
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 14a595de3b80635ad6974f2abb94bd9645d5a7f7
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483813"
---
# <a name="introduce-a-local-variable-in-visual-studio"></a>Wprowadzanie zmiennej lokalnej w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** Pozwala natychmiast wygenerować zmienną lokalną, aby zastąpić istniejące wyrażenia.

**Kiedy:** Masz kod, który można łatwo wykorzystać także później, jakby był w zmiennej lokalnej.

**Dlaczego:** Możesz skopiować i Wklej kod wiele razy z niej korzystać w różnych miejscach, jednak byłoby lepiej wykonać tę operację jeszcze raz, przechowuje wynik w zmiennej lokalnej i użyć zmiennej lokalnej przez cały.

## <a name="how-to"></a>Instrukcje

1. Zaznacz wyrażenie, które chcesz przypisać do zmiennej lokalnej.

   - C#:

       ![Wyróżniony kod C#](media/local-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony Kod VB](media/local-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Kliknij ikonę ![śrubokręt](media/screwdriver.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w wierszu za pomocą wyrażenia wyróżnione.

   ![Wprowadzenie lokalnego (wersja zapoznawcza)](media/local-preview-cs.png)

3. Wybierz **wprowadź element lokalny dla (wszystkich wystąpień), "wyrażenia"** z menu rozwijanego.

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