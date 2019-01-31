---
title: Implementowanie interfejsu
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 63f33d80a89a35d78e1c4465c9367f0674f73f18
ms.sourcegitcommit: e3d96b20381916bf4772f9db52b22275763bb603
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483851"
---
# <a name="implement-an-interface-in-visual-studio"></a>Implementowanie interfejsu w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe generowanie kodu wymaganego do implementacji interfejsu.

**Kiedy:** Chcesz dziedziczyć z interfejsu.

**Dlaczego:** Można ręcznie implementują interfejs wszystkich jeden po drugim, jednak ta funkcja będzie generowana automatycznie wszystkich podpisów metody.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w wierszu gdzie znajduje się czerwona fala wskazującą ma odwołanie do interfejsu, ale nie zaimplementowano wszystkich wymaganych elementów członkowskich.

   - C#:

       ![Wyróżniony kod C#](media/interface-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony Kod VB](media/interface-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Umieść kursor nad czerwona fala, a następnie kliknij przycisk ![Błąd żarówka](media/error-bulb.png) Ikona wyświetlana.
      - Kliknij ikonę ![Błąd żarówka](media/error-bulb.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w wierszu zawierającym czerwona fala.

3. Wybierz **implementuj interfejs** z menu rozwijanego.

   ![Implementuj interfejs w wersji zapoznawczej](media/interface-preview-cs.png)

   > [!TIP]
   > - Użyj **podgląd zmian** link w dolnej części okna podglądu [Aby wyświetlić wszystkie zmiany](../../ide/preview-changes.md) , zostaną wprowadzone przed dokonaniem wyboru.
   > - Użyj **dokumentu**, **projektu**, i **rozwiązania** linki na dole okna (wersja zapoznawcza) do tworzenia podpisów właściwej metody w wielu klas, które implementują interfejs.

   Podpisy metod interfejsu jest tworzony i jest gotowa do zaimplementowania.

   - C#:

       ![Implementuj interfejs wynik C#](media/interface-result-cs.png)

   - Visual Basic:

       ![Implementuj interfejs wynik VB](media/interface-result-vb.png)

   > [!TIP]
   > (C# tylko) Użyj **implementuj interfejs jawnie** opcję, aby każdy poprzedzony wygenerowanej metody o nazwie interfejsu, aby uniknąć konfliktów nazw.
   >
   > ![Implementuj interfejs jawnie wyniku.](media/interface-explicitresult-cs.png);

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)