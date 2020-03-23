---
title: Generowanie pola, właściwości, zmiennej lokalnej
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: b554aa5586150942c0fc7d7aeada9356a67029ca
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595608"
---
# <a name="generate-a-field-property-or-local-variable-in-visual-studio"></a>Generowanie pola, właściwości lub zmiennej lokalnej w programie Visual Studio

To generowanie kodu dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia natychmiastowe wygenerowanie kodu dla wcześniej niezadeklarowanego pola, właściwości lub lokalnego.

**Kiedy:** Podczas pisania wprowadzasz nowe pole, właściwość lub lokalne i chcesz automatycznie je poprawnie zadeklarować.

**Dlaczego?** Przed użyciem można zadeklarować pole, właściwość lub lokalną, jednak ta funkcja wygeneruje deklarację i wpisz automatycznie.

## <a name="how-to"></a>Porady

1. Umieść kursor na linii, w której znajduje się czerwona falista. Czerwony squiggle wskazuje pole, lokalne lub właściwość, która jeszcze nie istnieje.

   - C#:

       ![Wyróżniony kod C #](media/field-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod VB](media/field-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Najedź kursorem na czerwoną falosę i kliknij przycisk ![błąd żarówki](media/error-bulb.png) pojawi się ikona.
      - Kliknij ikonę ![błąd żarówki](media/error-bulb.png) ikonę, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w wierszu z czerwoną faliczkiem.

      ![Generowanie pola/właściwości/podglądu lokalnego](media/field-preview-cs.png)

3. Wybierz jedną z opcji generowania z menu rozwijanego.

   > [!TIP]
   > Użyj łącza **Podgląd zmian** u dołu okna podglądu, [aby wyświetlić wszystkie zmiany,](../../ide/preview-changes.md) które zostaną wprowadzone przed dokonaniem wyboru.

   Zostanie utworzone pole, właściwość lub lokal lokalny z typem wywnioskowane z jego użycia.

   - C#:

       ![Generowanie wyniku metody C #](media/field-result-cs.png)

   - Visual Basic:

       ![Generowanie wyniku metody VB](media/field-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
