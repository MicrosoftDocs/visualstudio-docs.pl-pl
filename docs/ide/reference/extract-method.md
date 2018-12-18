---
title: Wyodrębnij metodę
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: b80b5053022b9e42bb6cfd30e3c76a72bef70746
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064617"
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnij także refaktoryzację — metoda

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** pozwala włączyć fragment kodu do własnej metody.

**Kiedy:** masz fragmentu istniejący kod w jakiejś metodzie, która musi zostać wywołana z innej metody.

**Dlaczego:** można kopiujesz/wklejasz kod, ale, co może spowodować dublowania. Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do jego własnej metody, która może być wywoływany za darmo przez jakąkolwiek inną metodę.

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