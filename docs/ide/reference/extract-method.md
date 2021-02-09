---
title: Wyodrębnij metodę
description: Zmień fragment kodu na własny metodę, wybierając kod i wpisując CTRL + R, Ctrl + M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b39112a696611103828d862c7f7adf04784e6222
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861000"
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnianie metody refaktoryzacji

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia włączenie fragmentu kodu w osobnym metodzie.

**Kiedy:** Istnieje fragment istniejącego kodu w pewnej metodzie, który musi zostać wywołany z innej metody.

**Dlaczego:** Można skopiować/wkleić ten kod, ale może to prowadzić do duplikacji. Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do własnej metody, która może być wywoływana swobodnie przez jakąkolwiek inną metodę.

## <a name="how-to"></a>Porady

1. Zaznacz kod, który ma zostać wyodrębniony:

   - C#:

       ! Zrzut ekranu przedstawiający kod C# dla klasy program. W funkcji Main tej klasy, wiersz kodu wyróżniony.] (nośnik/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Zrzut ekranu przedstawiający kod Visual Basic dla głównego elementu podrzędnego. W tym elemencie zostanie wyróżniony wiersz kodu.](media/extractmethod-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Klawiatura**
      - Naciśnij klawisze **Ctrl + R**, a następnie **Ctrl + M**. (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
      - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i refaktoryzacje** , a następnie wybierz polecenie **Wyodrębnij metodę** z menu podręcznego okna podglądu.
   - **Mysz**
      - Wybierz pozycję **edytuj > refaktoryzacja > Metoda wyodrębnienia**.
      - Kliknij prawym przyciskiem myszy kod i wybierz pozycję **refaktoryzacja > wyodrębnij > metodę wyodrębnienia**.
      - Kliknij prawym przyciskiem myszy kod, zaznacz menu **szybkie akcje i refaktoryzacje** i wybierz polecenie **Wyodrębnij metodę** w menu podręcznym okna podglądu.

   Metoda zostanie natychmiast utworzona. W tym miejscu możesz teraz zmienić nazwę metody po prostu, wpisując nową nazwę.

   > [!TIP]
   > Możesz również zaktualizować Komentarze i inne ciągi, aby użyć tej nowej nazwy, a także [wyświetlić podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, używając pól wyboru w polu **Zmień nazwę** wyświetlaną w prawym górnym rogu środowiska IDE.

   - C#:

      ![Zrzut ekranu przedstawiający kod C# dla klasy program. Nazwa metody zostanie wyróżniona, a okno podręczne Zmień nazwę jest otwarte.](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Zrzut ekranu przedstawiający kod Visual Basic dla głównego elementu podrzędnego. Nazwa metody zostanie wyróżniona, a okno podręczne Zmień nazwę jest otwarte.](media/extractmethod-rename-vb.png)

3. Po zakończeniu wprowadzania zmian wybierz przycisk **Zastosuj** lub naciśnij klawisz **Enter** , a zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
