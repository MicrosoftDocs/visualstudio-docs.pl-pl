---
title: Generowanie c# równych i przesłonia metody GetHashCode
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f9b1a639dd655f4f75b21555396866858b144010
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569286"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generowanie zastępów metody Equals i GetHashCode w programie Visual Studio

To generowanie kodu dotyczy:

- C#

**Co:** Umożliwia **generowanie equals** i **GetHashCode** metody.

**Kiedy:** Wygeneruj te zastąpienia, gdy masz typ, który powinien być porównywany przez jedno lub więcej pól, a nie przez lokalizację obiektu w pamięci.

**Dlaczego:**

- Jeśli implementujesz typ wartości, należy rozważyć zastąpienie **Equals** metody, aby uzyskać zwiększoną wydajność w porównaniu z domyślną implementacją Equals metody valuetype.

- Jeśli implementujesz typ odwołania, należy rozważyć zastąpienie **Equals** metody, jeśli typ wygląda jak typ podstawowy, takich jak Punkt, String, BigNumber i tak dalej.

- Zastąpuj **GetHashCode** metody, aby umożliwić typ do poprawnego działania w tabeli mieszania. Przeczytaj więcej wskazówek dotyczących [operatorów równości](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Porady

1. Umieść kursor gdzieś w wierszu deklaracji typu.

   ![Wyróżniony kod](media/overrides-highlight-cs.png)

   > [!TIP]
   > Nie klikaj dwukrotnie nazwy typu lub opcja menu nie będzie dostępna. Wystarczy umieścić kursor gdzieś na linii.

1. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**

   - Kliknij ikonę ![Śrubokręt](../media/screwdriver-icon.png) ikonę wyświetlaną na lewym marginesie.

   ![Generowanie podglądu zastępowania](media/overrides-preview-cs.png)

1. Z menu rozwijanego **wybierz polecenie Generuj equals(object)** lub **Generuj equals i GetHashCode.**

1. W oknie dialogowym **Wybieranie członków** wybierz elementy członkowskie, dla których chcesz wygenerować metody:

    ![Okno dialogowe Generowanie zastępowania](media/overrides-dialog-cs.png)

    > [!TIP]
    > Można również wybrać opcję generowania operatorów z tego okna dialogowego przy użyciu pola wyboru w dolnej części okna dialogowego.

   I `Equals` `GetHashCode` metody są generowane z domyślnych implementacji.

   ![Generowanie wyniku metody](media/overrides-result-cs.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
