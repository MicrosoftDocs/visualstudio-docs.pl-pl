---
title: Wyodrębnij metodę
description: Zmień fragment kodu na własny metodę, wybierając kod i wpisując CTRL + R, Ctrl + M.
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a764fd0d95696866e914ec76a560a49d641acb47
ms.sourcegitcommit: 0f5f7955076238742f2071d286ad8e896f3a6cad
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2019
ms.locfileid: "68483671"
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnij także refaktoryzację — metoda

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Whatman** Umożliwia włączenie fragmentu kodu w osobnym metodzie.

**Czasie** Istnieje fragment istniejącego kodu w pewnej metodzie, który musi zostać wywołany z innej metody.

**Zalet** Można skopiować/wkleić ten kod, ale może to prowadzić do duplikacji. Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do jego własnej metody, która może być wywoływany za darmo przez jakąkolwiek inną metodę.

## <a name="how-to"></a>Instrukcje

1. Wyróżnij kod w celu wyodrębnienia:

   - C#:

       ![Wyróżnione kodu-C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/extractmethod-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + M**. (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
      - Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij metodę** z menu podręcznego okna podglądu.
   - **Myszy**
      - Wybierz **Edytuj > Refaktoryzuj > Wyodrębnij metodę**.
      - Kliknij prawym przyciskiem myszy ten kod, a następnie wybierz pozycję **Refaktoryzuj > Wyodrębnianie > Wyodrębnij metodę**.
      - Kliknij prawym przyciskiem myszy ten kod, wybierz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij metodę** z menu podręcznego okna podglądu.

   Metoda zostanie utworzona natychmiast. W tym miejscu można teraz zmienić nazwę metody po prostu wpisując nową nazwę.

   > [!TIP]
   > Możesz także zaktualizować komentarze i innych ciągów, aby użyć tej nowej nazwy, jak i [podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, za pomocą pola wyboru w **Zmień nazwę** wyświetlonym u góry rogu zintegrowanego środowiska Projektowego.

   - C#:

      ![Zmień nazwę metody-C#](media/extractmethod-rename-cs.png)

   - Visual Basic:

      ![Zmień nazwę metody - Visual Basic](media/extractmethod-rename-vb.png)

3. Po zakończeniu zmiany wybierz **Zastosuj** przycisk lub naciśnij klawisz **Enter** i zmiany zostaną zatwierdzone.

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)