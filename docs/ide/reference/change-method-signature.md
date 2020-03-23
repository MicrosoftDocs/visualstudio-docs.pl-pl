---
title: Zmiana sygnatury metody
description: Usuń lub zmień kolejność parametrów metody. Kliknij prawym przyciskiem myszy metodę, wybierz szybkie akcje i refaktoryzowania, a następnie wybierz pozycję Zmień podpis.
ms.date: 01/26/2018
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 97c03c798732b5d722b2dc49f3ec7ffa490b4f06
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68711262"
---
# <a name="change-a-method-signature-refactoring"></a>Zmienianie refaktoryzacji podpisu metody

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia usunięcie lub zmianę kolejności parametrów metody.

**Kiedy:** Chcesz przenieść lub usunąć parametr metody, który jest obecnie używany w różnych lokalizacjach.

**Dlaczego?** Można ręcznie usunąć i ponownie uporządkować parametry, a następnie znaleźć wszystkie wywołania tej metody i zmienić je jeden po drugim, ale może to prowadzić do błędów.  To narzędzie refaktoryzacji wykona zadanie automatycznie.

## <a name="how-to"></a>Porady

1. Wyróżnij lub umieść kursor tekstowy wewnątrz nazwy metody modyfikacji lub jednego z jej użycia:

   - C#:

       ![Wyróżniony kod C #](media/changesignature-highlight-cs.png)

   - Vb:

       ![Wyróżniony kod Visual Basic](media/changesignature-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze Ctrl+R**, a następnie **klawisze Ctrl+V**.  (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania,** a następnie wybrać **pozycję Zmień podpis** w oknie podglądu.
   - **Mysz**
      - Wybierz **pozycję Edytuj > refaktoryzatora > usuń parametry**.
      - Wybierz **pozycję Edytuj > refaktoryzator > ponownie zamów parametry**.
      - Kliknij prawym przyciskiem myszy kod, wybierz menu **Szybkie akcje i Refaktoryzowania** i wybierz polecenie **Zmień podpis** w oknie podglądu.

3. W oknie dialogowym **Zmień podpis,** które się pojawia, można użyć przycisków po prawej stronie, aby zmienić podpis metody:

   ![Okno dialogowe Zmienianie podpisu](media/changesignature-dialog-cs.png)

   | Button | Opis
   | ------ | ---
   | **W górę/w dół** | Przenoszenie zaznaczonego parametru w górę i w dół listy
   | **Usuń** | Usuwanie zaznaczonego parametru z listy
   | **Przywracanie** | Przywracanie zaznaczonego, przekreślony parametr do listy

   > [!TIP]
   > Użyj **pola wyboru Zmiany odwołania w wersji zapoznawczej,** aby [zobaczyć, jaki będzie wynik](../../ide/preview-changes.md) przed zatwierdzeniem go.

4. Po zakończeniu naciśnij przycisk **OK,** aby wprowadzić zmiany.

   - C#:

      ![Zmiana wyniku podpisu - C #](media/changesignature-result-cs.png)

   - Visual Basic:

      ![Wynik zmień podpis — Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)