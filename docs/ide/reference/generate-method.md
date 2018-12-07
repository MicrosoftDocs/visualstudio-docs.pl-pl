---
title: Generowanie metody
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 1e5cf156c6c17e8a9bf1fb9f40f75c1e72b7be94
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53057181"
---
# <a name="generate-a-method-in-visual-studio"></a>Generuj metodę w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** umożliwia natychmiastowe dodanie metody do klasy.

**Kiedy:** wprowadzają nową metodę i aby poprawnie Zadeklaruj go, automatycznie.

**Dlaczego:** można zadeklarować metody i parametrów przed użyciem, ale tej funkcji będzie generowana automatycznie deklaracji.

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
      - Umieść kursor nad czerwona fala, a następnie kliknij przycisk ![Żarówka](media/bulb-cs.png) Ikona wyświetlana.
      - Kliknij ikonę ![Żarówka](media/bulb-cs.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym czerwona fala.

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