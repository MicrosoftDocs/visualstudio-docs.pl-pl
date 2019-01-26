---
title: Wyodrębnij metodę
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 15025f531108851b55e04399a532ba6e10ad231a
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54981002"
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnij także refaktoryzację — metoda

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Pozwala włączyć fragment kodu do własnej metody.

**Kiedy:** Masz fragmentu istniejący kod w jakiejś metodzie, która musi zostać wywołana z innej metody.

**Dlaczego:** Można kopiujesz/wklejasz kod, ale, co może spowodować dublowania. Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do jego własnej metody, która może być wywoływany za darmo przez jakąkolwiek inną metodę.

## <a name="how-to"></a>Instrukcje

1. Wyróżnij kod w celu wyodrębnienia:

   - C#:

       ![Wyróżnione kodu-C#](media/extractmethod-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/extractmethod-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + M**. (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
      - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu, a następnie wybierz **Wyodrębnij metodę** z menu podręcznego okna podglądu.
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