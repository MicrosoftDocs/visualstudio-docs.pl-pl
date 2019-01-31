---
title: Generowanie metody
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 86ade7bac365c5566c79d3cb1364670b23f0d3d9
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483838"
---
# <a name="generate-a-method-in-visual-studio"></a>Generuj metodę w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe dodanie metody do klasy.

**Kiedy:** Wprowadzenie nowej metody i aby poprawnie Zadeklaruj go automatycznie.

**Dlaczego:** Można zadeklarować metody i parametrów przed użyciem, ale tej funkcji będzie generowana automatycznie deklaracji.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w wierszu gdzie znajduje się czerwona fala. Czerwona fala wskazuje metodę, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C#](media/method-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony Kod VB](media/method-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Umieść kursor nad czerwona fala, a następnie kliknij przycisk ![Błąd żarówka](media/error-bulb.png) Ikona wyświetlana.
      - Kliknij ikonę ![Błąd żarówka](media/error-bulb.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym czerwona fala.

      ![Generowanie podglądu — metoda](media/method-preview-cs.png)

3. Wybierz **Generuj metodę** z menu rozwijanego.

   > [!TIP]
   > Użyj **podgląd zmian** link w dolnej części okna podglądu [Aby wyświetlić wszystkie zmiany](../../ide/preview-changes.md) , zostaną wprowadzone przed dokonaniem wyboru.

   Metoda jest tworzony z parametrów wywnioskować na podstawie jej użycie.

   - C#:

       ![Generowanie metody powodują C#](media/method-result-cs.png)

   - Visual Basic:

       ![Generowanie metody powodują VB](media/method-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)