---
title: Wyodrębnianie funkcji lokalnej
description: Zmień fragment kodu na własny metodę, wybierając kod i wpisując CTRL + R, Ctrl + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77515331"
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

    ![Wyodrębnianie funkcji lokalnej](media/extract-local-function.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
