---
title: Refaktoryzacja zmiany nazwy
ms.date: 01/26/2018
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d1b4ff448f04ff6f683fac06cbc0b31797edf587
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186579"
---
# <a name="rename-a-code-symbol-refactoring"></a>Zmień nazwę symbolu kodu refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Whatman** Umożliwia zmianę nazw identyfikatorów dla symboli kodu, takich jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typy.

**Czasie** Chcesz bezpiecznie zmienić nazwę elementu bez konieczności znajdowania wszystkich wystąpień, a następnie skopiuj/wklej nową nazwę.

**Zalet** Kopiowanie i wklejanie nowej nazwy w całym projekcie prawdopodobnie spowoduje błędy. To narzędzie refaktoryzacji dokładnie wykona akcję zmiany nazwy.

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

## <a name="remarks"></a>Uwagi

- Począwszy od programu Visual Studio 2019 w wersji 16,3, gdy zmieniasz nazwę typu, który pasuje do nazwy pliku, w którym znajduje się, zostanie wyświetlone pole wyboru umożliwiające zmianę nazwy pliku w tym samym czasie. Ta opcja jest wyświetlana w przypadku zmiany nazwy klasy, interfejsu lub wyliczenia. Ta opcja nie jest obsługiwana w przypadku typów częściowych z wieloma definicjami.

   ![Zmień nazwę animacji z plikiemC#](media/rename-with-file-animated-cs.gif)
   
- Jeśli używasz nazwę, która już istnieje która może spowodować konflikt, **Zmień nazwę** wyświetli ostrzeżenie, pole.

   ![Zmień nazwę konflikt](media/rename-conflict-cs.png)

- Innym sposobem zmiany nazwy symbolu jest zmiana jego nazwy w edytorze. Następnie za pomocą kursora w nazwie symbolu naciśnij klawisz **Ctrl**+ **.** lub po prostu rozwiń wyświetlone menu ikony żarówki, a następnie wybierz pozycję **Zmień \<nazwę starej nazwy > na \<nową >** .

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
