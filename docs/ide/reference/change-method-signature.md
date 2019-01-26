---
title: Refaktoryzuj podpis metody
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.remove
- vs.csharp.refactoring.reorder
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: bc40f71db956e42a566cf3a49b924c601fbe28d1
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54971263"
---
# <a name="change-a-method-signature-refactoring"></a>Zmień podpis metody refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia usunięcie lub zmiana kolejności parametrów metody.

**Kiedy:** Chcesz przenieść lub usunąć parametr metody, która jest obecnie używana w różnych lokalizacjach.

**Dlaczego:** Możesz można ręcznie usuń i kolejność parametrów, a następnie Znajdź wszystkie wywołania do tej metody i zmień je pojedynczo, ale która może prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekstu w nazwie metody, aby zmodyfikować lub jednego z jego użycia:

   - C#:

       ![Wyróżniony kod C#](media/changesignature-highlight-cs.png)

   - VB:

       ![Wyróżniony kod języka Visual Basic](media/changesignature-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **klawisze Ctrl + V**.  (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień podpis** z menu podręcznego okna podglądu.
   - **Myszy**
      - Wybierz **Edytuj > Refaktoryzuj > Usuń parametry**.
      - Wybierz **Edytuj > Refaktoryzuj > Zmień kolejność parametrów**.
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień podpis** z menu podręcznego okna podglądu.

3. W **Zmień podpis** okna dialogowego, które się pojawi, umożliwia przyciski po prawej stronie Zmień sygnaturę metody:

   ![Zmień podpis w oknie dialogowym](media/changesignature-dialog-cs.png)

   | Przycisk | Opis
   | ------ | ---
   | **Góra/dół** | Przenieś wybrany parametr w górę i w dół listy
   | **Usuń** | Usuń wybrany parametr z listy
   | **Przywróć** | Przywróć wybrane, przekreślonym parametru do listy

   > [!TIP]
   > Użyj **podgląd zmian odwołania** pole wyboru, aby [Zobacz, jaki będzie wynik](../../ide/preview-changes.md) przed zatwierdzeniem do niego.

4. Gdy skończysz, naciśnij klawisz **OK** , aby wprowadzić zmiany.

   - C#:

      ![Wynik podpisu — zmianyC#](media/changesignature-result-cs.png)

   - Visual Basic:

      ![Zmień podpis wynik - Visual Basic](media/changesignature-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)