---
title: Refaktoryzuj podpis metody
description: Usuń lub Zmień kolejność parametrów metody. Kliknij prawym przyciskiem myszy metodę, wybierz pozycję szybkie akcje i refaktoryzacje, a następnie wybierz pozycję Zmień sygnaturę.
ms.date: 01/26/2018
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
ms.openlocfilehash: 7e8332cb8fb39c47f4e46a7d306b2673ff61b9e9
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483745"
---
# <a name="change-a-method-signature-refactoring"></a>Zmień podpis metody refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Whatman** Umożliwia usunięcie lub zmianę kolejności parametrów metody.

**Czasie** Chcesz przenieść lub usunąć parametr metody, który jest aktualnie używany w różnych lokalizacjach.

**Zalet** Można ręcznie usunąć i zmienić kolejność parametrów, a następnie znaleźć wszystkie wywołania tej metody i wprowadzić je jeden do jednego, ale może to prowadzić do błędów.  To narzędzie refaktoryzacji będzie automatycznie wykonywać zadania.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekstu w nazwie metody, aby zmodyfikować lub jednego z jego użycia:

   - C#:

       ![Wyróżniony kod C#](media/changesignature-highlight-cs.png)

   - VB:

       ![Wyróżniony kod języka Visual Basic](media/changesignature-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **klawisze Ctrl + V**.  (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Zmień podpis** z menu podręcznego okna podglądu.
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