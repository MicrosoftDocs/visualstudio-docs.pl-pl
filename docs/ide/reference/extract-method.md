---
title: Wyodrębnij metodę
description: Zmień fragment kodu na własny metodę, wybierając kod i wpisując CTRL + R, Ctrl + M.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 50f14cc2a7eafe5d65e0c6a6af54bafa2ebb5a1f
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75569702"
---
# <a name="extract-a-method-refactoring"></a>Wyodrębnij także refaktoryzację — metoda

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

- Język Visual Basic

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
