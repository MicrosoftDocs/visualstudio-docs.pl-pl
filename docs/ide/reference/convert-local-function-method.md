---
title: Konwertowanie funkcji lokalnej na metodę
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "71301695"
---
# <a name="convert-a-local-function-to-a-method"></a>Konwertowanie funkcji lokalnej na metodę

Ten refaktoryzator ma zastosowanie do:

- C#

**Co:** Konwertuj funkcję lokalną na metodę.

**Kiedy:** Masz funkcję lokalną, którą chcesz zdefiniować poza bieżącym kontekstem lokalnym.

**Dlaczego?** Chcesz przekonwertować funkcję lokalną na metodę, dzięki czemu można wywołać ją poza kontekstem lokalnym. Można przekonwertować na metodę, gdy funkcja lokalna jest coraz zbyt długo. Podczas definiowania funkcji w oddzielnej metody, kod jest łatwiejsze do odczytania.

## <a name="convert-local-function-to-method-refactoring"></a>Konwertowanie funkcji lokalnej na refaktoryzowanie metody

1. Umieść kursor w funkcji lokalnej.

    ![Konwertowanie funkcji lokalnej na przykład kodu metody](media/convert-local-function-to-method.png)

2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

    ![Konwertowanie funkcji lokalnej na przykład poprawki kodu metody](media/convert-local-function-to-method-codefix.png)

2. Naciśnij klawisz Enter, aby zaakceptować refaktoryzowanie.

    ![Konwertowanie funkcji lokalnej na przykład wyników metody](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
