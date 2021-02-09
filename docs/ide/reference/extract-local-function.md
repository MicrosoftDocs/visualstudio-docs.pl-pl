---
title: Wyodrębnianie funkcji lokalnej
description: Przekształcenie fragmentu kodu w własną funkcję, wybierając kod i wpisując CTRL + R, Ctrl + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860974"
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

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
