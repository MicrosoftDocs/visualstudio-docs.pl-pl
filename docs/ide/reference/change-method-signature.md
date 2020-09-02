---
title: Zmiana sygnatury metody
description: Dodaj, Usuń lub Zmień kolejność parametrów metody. Kliknij prawym przyciskiem myszy metodę, wybierz pozycję szybkie akcje i refaktoryzacje, a następnie wybierz pozycję Zmień sygnaturę.
ms.date: 07/20/2020
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
ms.openlocfilehash: 2d91406b65950515afb3659c0d5918841465b2fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "86869571"
---
# <a name="change-a-method-signature-refactoring"></a>Zmiana refaktoryzacji sygnatury metody

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia usunięcie lub zmianę kolejności parametrów metody.

**Kiedy:** Chcesz przenieść lub usunąć parametr metody, który jest aktualnie używany w różnych lokalizacjach.

**Dlaczego:** Można ręcznie usunąć i zmienić kolejność parametrów, a następnie znaleźć wszystkie wywołania tej metody i wprowadzić je jeden do jednego, ale może to prowadzić do błędów.  To narzędzie refaktoryzacji wykona zadanie automatycznie.

## <a name="how-to"></a>Porady

1. Zaznacz lub umieść kursor tekstu w nazwie metody do zmodyfikowania lub jeden z jego użycia:

   - C#:

       ![Wyróżniony kod C #](media/changesignature-highlight-cs.png)

   - VB

       ![Wyróżniony Visual Basic kodu](media/changesignature-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij **klawisze CTRL + R**, a następnie **Ctrl + V**.  (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz pozycję **Zmień sygnaturę** w menu podręcznym okna podglądu.
   - **Mysz**
      - Wybierz pozycję **edytuj > refaktoryzację > Usuń parametry**.
      - Wybierz pozycję **edytuj > refaktoryzacja > Zmień kolejność parametrów**.
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Zmień sygnaturę** w menu podręcznym okna podglądu.

3. W oknie dialogowym **Zmienianie podpisu** , które się pojawia, możesz użyć przycisków z prawej strony, aby zmienić sygnaturę metody:

   ![Okno dialogowe Zmienianie sygnatury](media/change-signature.png)

   | Przycisk | Opis
   | ------ | ---
   | **W górę/w dół** | Przenieś wybrany parametr w górę i w dół listy
   | **Dodaj** | Dodaj nowy parametr do listy
   | **Usuń** | Usuń wybrany parametr z listy
   | **Przywróć** | Przywróć wybrany, przekroczenie parametru do listy

   > [!TIP]
   > Użyj pola wyboru **Podgląd zmian odwołań** , aby [zobaczyć, co wynik będzie](../../ide/preview-changes.md) przed jego zatwierdzeniem.

4. Wybranie pozycji **Dodaj** w oknie dialogowym **Zmienianie podpisu** spowoduje otwarcie okna dialogowego **Dodawanie parametru** . Okno dialogowe **Dodawanie parametru** umożliwia dodanie nazwy typu i nazwy parametru. Można określić, że parametr jest wymagany lub jest opcjonalny z wartością domyślną. Następnie można dodać wartość w miejscu wywołania i wybrać nazwany argument dla tej wartości albo można wprowadzić zmienną TODO. Zmienna TODO umożliwia umieszczenie elementu TODO w kodzie, aby można było odwiedzać poszczególne błędy oraz przechodzić niezależnie do poszczególnych lokalizacji wywołań i decydować, co należy przekazać. W przypadku parametrów opcjonalnych można całkowicie pomijać lokalizację wywołania.

    ![Okno dialogowe Dodawanie parametru-C #](media/add-parameter-dialog.png)

5. Po zakończeniu dodawania parametru naciśnij przycisk **OK** , aby wyświetlić podgląd zmian.

    ![Okno dialogowe Zmienianie sygnatury](media/change-signature.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)