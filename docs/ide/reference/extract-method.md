---
title: Wyodrębnij metodę
description: Zmień fragment kodu na własny metodę, wybierając kod i wpisując CTRL + R, Ctrl + M.
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a1ec6ca273f873c82a1bb2c730a9288b5e2ae4ed
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654392"
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnianie metody refaktoryzacji

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia włączenie fragmentu kodu w osobnym metodzie.

**Kiedy:** Istnieje fragment istniejącego kodu w pewnej metodzie, który musi zostać wywołany z innej metody.

**Dlaczego:** Można skopiować/wkleić ten kod, ale może to prowadzić do duplikacji. Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do własnej metody, która może być wywoływana swobodnie przez jakąkolwiek inną metodę.

## <a name="how-to"></a>Instrukcje

1. Zaznacz kod, który ma zostać wyodrębniony:

   - C#:

       ![Wyróżniony kod —C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/extractmethod-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatury**
      - Naciśnij klawisze **Ctrl + R**, a następnie **Ctrl + M**. (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Wyodrębnij metodę** z menu podręcznego okna podglądu.
   - **Wskaźnik**
      - Wybierz pozycję **edytuj > refaktoryzacja > Metoda wyodrębnienia**.
      - Kliknij prawym przyciskiem myszy kod i wybierz pozycję **refaktoryzacja > wyodrębnij > metodę wyodrębnienia**.
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Wyodrębnij metodę** w menu podręcznym okna podglądu.

   Metoda zostanie natychmiast utworzona. W tym miejscu możesz teraz zmienić nazwę metody po prostu, wpisując nową nazwę.

   > [!TIP]
   > Możesz również zaktualizować Komentarze i inne ciągi, aby użyć tej nowej nazwy, a także [wyświetlić podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, używając pól wyboru w polu **Zmień nazwę** wyświetlaną w prawym górnym rogu środowiska IDE.

   - C#:

      ![Zmień nazwę metody-C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Zmień nazwę metody-Visual Basic](media/extractmethod-rename-vb.png)

3. Po zakończeniu wprowadzania zmian wybierz przycisk **Zastosuj** lub naciśnij klawisz **Enter** , a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)