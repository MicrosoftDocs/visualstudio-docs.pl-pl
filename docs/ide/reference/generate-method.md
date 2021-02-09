---
title: Generuj metodę
description: Dowiedz się, jak natychmiast dodać metodę do klasy przy użyciu menu szybkie akcje i refaktoryzacje.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: c6f4a25e3cda10e74c344cb7eef879b78f60a1de
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903905"
---
# <a name="generate-a-method-in-visual-studio"></a>Generowanie metody w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe dodanie metody do klasy.

**Kiedy:** Należy wprowadzić nową metodę i chcieć ją prawidłowo zadeklarować automatycznie.

**Dlaczego:** Można zadeklarować metodę i parametry przed użyciem, jednak ta funkcja będzie generować deklarację automatycznie.

## <a name="how-to"></a>Porady

1. Umieść kursor w wierszu, w którym znajduje się czerwona zygzakowata. Czerwona zygzakowata wskazuje metodę, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C #](media/method-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/method-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij pozycję ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

      ![Generuj Podgląd metody](media/method-preview-cs.png)

3. Wybierz pozycję **Generuj metodę** z menu rozwijanego.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.

   Metoda jest tworzona z dowolnymi parametrami wywnioskowanymi z użycia.

   - C#:

       ![Generuj wynik metody C #](media/method-result-cs.png)

   - Visual Basic:

       ![Generuj wynik metody VB](media/method-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
