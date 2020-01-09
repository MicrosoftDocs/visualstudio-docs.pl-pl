---
title: Generowanie metody
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f166c31a1615c951170367223a5b19ab93811b5d
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75595595"
---
# <a name="generate-a-method-in-visual-studio"></a>Generuj metodę w programie Visual Studio

Dotyczy to generowanie kodu:

- Język C#

- Język Visual Basic

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
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Umieść kursor nad czerwona fala, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) Ikona wyświetlana.
      - Kliknij ikonę ![Żarówka błędów](media/error-bulb.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym czerwona fala.

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
