---
title: Wyodrębnianie funkcji lokalnej
description: Przekształcenie fragmentu kodu w własną funkcję, wybierając kod i wpisując CTRL + R, Ctrl + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129461"
---
# <a name="extract-local-function-refactoring"></a>Oddzielanie refaktoryzacji funkcji lokalnych

To Refaktoryzacja dotyczy:

- C#

**Co:** Umożliwia włączenie fragmentu kodu z istniejącej metody do funkcji lokalnej.

**Kiedy:** Istnieje fragment istniejącego kodu w pewnej metodzie, który musi zostać wywołany z funkcji lokalnej.

**Dlaczego:** Można skopiować/wkleić ten kod, ale może to prowadzić do duplikacji. Lepszym rozwiązaniem jest Refaktoryzacja tego fragmentu do własnej funkcji lokalnej.

## <a name="how-to"></a>Porady

1. Zaznacz kod, który ma zostać wyodrębniony.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** . 

3. Wybierz pozycję **Wyodrębnij funkcję lokalną**.

    ![Zrzut ekranu przedstawiający okno programu Visual Studio Code z wyróżnionym wierszem. Menu szybkie akcje i refaktoryzacje jest otwarte i zaznaczona jest funkcja Wyodrębnij funkcję lokalną.](media/extract-local-function.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
