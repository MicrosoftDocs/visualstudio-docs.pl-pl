---
title: Generuj metodę
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: c85e3f849d7d74f326c1cf330b0e2c338d78fc6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668331"
---
# <a name="generate-a-method-in-visual-studio"></a>Generowanie metody w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe dodanie metody do klasy.

**Kiedy:** Należy wprowadzić nową metodę i chcieć ją prawidłowo zadeklarować automatycznie.

**Dlaczego:** Można zadeklarować metodę i parametry przed użyciem, jednak ta funkcja będzie generować deklarację automatycznie.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w wierszu, w którym znajduje się czerwona zygzakowata. Czerwona zygzakowata wskazuje metodę, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kodC#](media/method-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/method-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Wskaźnik**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij ikonę ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

      ![Generuj Podgląd metody](media/method-preview-cs.png)

3. Wybierz pozycję **Generuj metodę** z menu rozwijanego.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.

   Metoda jest tworzona z dowolnymi parametrami wywnioskowanymi z użycia.

   - C#:

       ![Generowanie wyniku metodyC#](media/method-result-cs.png)

   - Visual Basic:

       ![Generuj wynik metody VB](media/method-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)