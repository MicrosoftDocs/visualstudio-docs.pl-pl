---
title: Wyodrębnianie funkcji lokalnej
description: Przeksztą fragment kodu do własnej metody, wybierając kod i wpisując Ctrl+R, Ctrl+M.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515331"
---
# <a name="extract-local-function-refactoring"></a>Wyodrębnianie refaktoryzacji funkcji lokalnych

Ten refaktoryzator ma zastosowanie do:

- C#

**Co:** Umożliwia przekształcenie fragmentu kodu z istniejącej metody w funkcję lokalną.

**Kiedy:** Masz fragment istniejącego kodu w jakiejś metodzie, która musi być wywoływana z funkcji lokalnej.

**Dlaczego?** Można skopiować/wkleić ten kod, ale to prowadzi do powielania. Lepszym rozwiązaniem jest refaktoryzator tego fragmentu do własnej funkcji lokalnej.

## <a name="how-to"></a>Porady

1. Wyróżnij kod, który ma zostać wyodrębniony.

2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.** 

3. Wybierz pozycję **Wyodrębnij funkcję lokalną**.

    ![Wyodrębnianie funkcji lokalnej](media/extract-local-function.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
