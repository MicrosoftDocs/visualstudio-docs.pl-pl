---
title: Zmiana nazwy elementu refaktoryzacji
description: Dowiedz się, jak za pomocą funkcji refaktoryzacji Zmień nazwy identyfikatorów dla symboli kodu, takich jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typy.
ms.custom: SEO-VS-2020
ms.date: 05/04/2020
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2e3d4d5d0abc335cfb857e5a4de9c5189a1ca5cc
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958105"
---
# <a name="rename-a-code-symbol-refactoring"></a>Zmiana nazwy refaktoryzacji symbolu kodu

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia zmianę nazw identyfikatorów dla symboli kodu, takich jak pola, zmienne lokalne, metody, przestrzenie nazw, właściwości i typy.

**Kiedy:** Chcesz bezpiecznie zmienić nazwę elementu bez konieczności znajdowania wszystkich wystąpień, a następnie skopiuj/wklej nową nazwę.

**Dlaczego:** Kopiowanie i wklejanie nowej nazwy w całym projekcie prawdopodobnie spowoduje błędy. To narzędzie refaktoryzacji dokładnie przeprowadzi akcję zmiany nazwy.

## <a name="how-to"></a>Porady

1. Podświetl lub umieść kursor tekstu wewnątrz elementu, którego nazwę chcesz zmienić:

   - C#:

       ![Wyróżniony kod — C #](media/rename-highlight-cs.png)

   - Visual Basic:

       ![Wyróżniony kod — Visual Basic](media/rename-highlight-vb.png)

2. Następnie użyj klawiatury lub myszy w następujący sposób:

   - **Klawiatura**
      - Naciśnij klawisze **Ctrl + r**, a następnie **Ctrl + r**. (Pamiętaj, że skrót klawiaturowy może się różnić w zależności od wybranego profilu).
   - **Mysz**
      - Wybierz pozycję **edytuj > refaktoryzacja > Zmień nazwę**.
      - Kliknij prawym przyciskiem myszy kod i wybierz polecenie **Zmień nazwę**.

3. Zmień nazwę elementu po prostu, wpisując nową nazwę.

   - C#:

      ![Zmień nazwę animacji-C #](media/rename-animated-cs.gif)

   - Visual Basic:

      ![Zmień nazwę — VB](media/rename-rename-vb.png)

   > [!TIP]
   > Możesz również zaktualizować Komentarze i inne ciągi, aby użyć tej nowej nazwy, a także [wyświetlić podgląd zmian](../../ide/preview-changes.md) przed zapisaniem, używając pól wyboru w polu **Zmień nazwę** wyświetlaną w prawym górnym rogu edytora.

4. Po zakończeniu wprowadzania zmian wybierz przycisk **Zastosuj** lub naciśnij klawisz **Enter** , a zmiany zostaną zatwierdzone.

## <a name="remarks"></a>Uwagi

- Począwszy od programu Visual Studio 2019 w wersji 16,3, gdy zmieniasz nazwę typu, który pasuje do nazwy pliku, w którym znajduje się, zostanie wyświetlone pole wyboru umożliwiające zmianę nazwy pliku w tym samym czasie. Ta opcja jest wyświetlana w przypadku zmiany nazwy klasy, interfejsu lub wyliczenia. Ta opcja nie jest obsługiwana w przypadku typów częściowych z wieloma definicjami.

   ![Zmień nazwę animacji z plikiem C #](media/rename-with-file-animated-cs.gif)

- Jeśli użyjesz już nazwy, która może spowodować konflikt, w polu **Zmień nazwę** zostanie wyświetlone ostrzeżenie.

   ![Konflikt zmiany nazwy](media/rename-conflict-cs.png)

- Innym sposobem zmiany nazwy symbolu jest zmiana jego nazwy w edytorze. Następnie za pomocą kursora w nazwie symbolu naciśnij klawisz **Ctrl** + **.** lub po prostu rozwiń wyświetlone menu ikony żarówki i wybierz polecenie **Zmień \<old name> nazwę \<new name> na**.

   ![Zmień nazwę w edytorze](media/rename-with-editor-cs.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
