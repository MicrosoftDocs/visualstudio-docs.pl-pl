---
title: Generuj pole, właściwość, zmienna lokalna
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje do generowania kodu dla niezadeklarowanego pola, właściwości lub lokalnego.
ms.custom: SEO-VS-2020
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 57e6490b9375e3f59e0d214ae3f5300f2276964d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99914902"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generowanie pola, właściwości lub zmiennej lokalnej w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla wcześniej niezadeklarowanego pola, właściwości lub lokalnego.

**Kiedy:** Wprowadzasz nowe pole, właściwość lub wartość lokalna podczas pisania i chcę prawidłowo zadeklarować ją automatycznie.

**Dlaczego:** Można zadeklarować pole, właściwość lub wartość lokalną przed użyciem, jednak ta funkcja będzie generować deklarację i pisać automatycznie.

## <a name="how-to"></a>Porady

1. Umieść kursor w wierszu, w którym znajduje się czerwona zygzakowata. Czerwona zygzakowata wskazuje pole, lokalne lub właściwość, które jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C #](media/field-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/field-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .
      - Umieść kursor na czerwono, a następnie kliknij przycisk ![Żarówka błędów](media/error-bulb.png) zostanie wyświetlona ikona.
      - Kliknij pozycję ![Żarówka błędów](media/error-bulb.png) ikona wyświetlana na lewym marginesie, jeśli kursor tekstu znajduje się już w wierszu z czerwonym obramowaniem.

      ![Generuj Podgląd pola/właściwości/lokalnego podglądu](media/field-preview-cs.png)

3. Wybierz jedną z opcji generacji z menu rozwijanego.

   > [!TIP]
   > Użyj linku **Podgląd zmian** w dolnej części okna Podgląd, [Aby zobaczyć wszystkie zmiany](../../ide/preview-changes.md) , które zostaną wprowadzone przed dokonaniem wyboru.

   Pole, właściwość lub wartość lokalna są tworzone z typem wywnioskowanym na podstawie jego użycia.

   - C#:

       ![Generuj wynik metody C #](media/field-result-cs.png)

   - Visual Basic:

       ![Generuj wynik metody VB](media/field-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
