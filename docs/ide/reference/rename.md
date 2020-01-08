---
title: Refaktoryzacja zmiany nazwy
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 4dbccd4732f56d671fd74f59916885ea338136f8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565464"
---
# <a name="rename-a-code-symbol-refactoring"></a>Zmień nazwę symbolu kodu refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

- Język Visual Basic

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

## <a name="remarks"></a>Uwagi

- Począwszy od programu Visual Studio 2019 w wersji 16,3, gdy zmieniasz nazwę typu, który pasuje do nazwy pliku, w którym znajduje się, zostanie wyświetlone pole wyboru umożliwiające zmianę nazwy pliku w tym samym czasie. Ta opcja jest wyświetlana w przypadku zmiany nazwy klasy, interfejsu lub wyliczenia. Ta opcja nie jest obsługiwana w przypadku typów częściowych z wieloma definicjami.

   ![Zmień nazwę animacji z plikiemC#](media/rename-with-file-animated-cs.gif)

- Jeśli używasz nazwę, która już istnieje która może spowodować konflikt, **Zmień nazwę** wyświetli ostrzeżenie, pole.

   ![Zmień nazwę konflikt](media/rename-conflict-cs.png)

- Innym sposobem zmiany nazwy symbolu jest zmiana jego nazwy w edytorze. Następnie przy użyciu kursora w nazwie symbolu naciśnij klawisz **Ctrl**+ **.** lub po prostu rozwiń wyświetlone menu ikony żarówki i wybierz polecenie **Zmień nazwę \<stara nazwa >, aby \<nową nazwę >** .

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
