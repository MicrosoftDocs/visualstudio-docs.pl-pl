---
title: Refaktoryzacja zmiany nazwy
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 02b08f3218ab6f1380884d2385899d6dd486bb81
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063156"
---
# <a name="rename-a-code-symbol-refactoring"></a>Zmień nazwę symbolu kodu refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** umożliwia zmianę nazwy identyfikatorów w celu symbole kodu, takie jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typów.

**Kiedy:** chcesz bezpiecznie zmienić coś bez konieczności Znajdź wszystkie wystąpienia i kopiowanie/wklejanie nowej nazwy.

**Dlaczego:** kopiowanie i wklejanie nową nazwę dla całego projektu, prawdopodobnie będą powodować błędy. To narzędzie refaktoryzacji dokładnie wykona akcję zmiany nazwy.

## <a name="how-to"></a>Instrukcje

1. Zaznacz lub umieść kursor tekstu w można zmienić nazwy elementu:

   - C#:

       ![Wyróżniony kod-C#](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod - języka Visual Basic](media/rename-highlight-vb.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Naciśnij klawisz **Ctrl + R**, następnie **Ctrl + R**. (Należy pamiętać, że skrót klawiaturowy może różnić się w oparciu o profilu, który wybrano.)
   - **Myszy**
      - Wybierz **Edytuj > Refaktoryzuj > Zmień nazwę**.
      - Kliknij prawym przyciskiem myszy ten kod, a następnie wybierz pozycję **Zmień nazwę**.

3. Zmień nazwę elementu, po prostu wpisując nową nazwę.

   - C#:

      ![Zmień nazwę Animacja —C#](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Rename - VB](media/rename-rename-vb.png)

   > [!TIP]
   > Możesz także zaktualizować komentarze i innych ciągów, aby użyć tej nowej nazwy także [podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, za pomocą pola wyboru w **Zmień nazwę** wyświetlonym u góry bezpośrednio z edytora.

4. Po zakończeniu zmiany wybierz **Zastosuj** przycisk lub naciśnij klawisz **Enter** i zmiany zostaną zatwierdzone.

> [!NOTE]
> Jeśli używasz nazwę, która już istnieje która może spowodować konflikt, **Zmień nazwę** wyświetli ostrzeżenie, pole.
>
> ![Zmień nazwę konflikt](media/rename-conflict-cs.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
