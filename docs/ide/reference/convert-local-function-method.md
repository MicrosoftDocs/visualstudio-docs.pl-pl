---
title: Konwertuj funkcję lokalną na metodę
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 3572682fe68d9b0b1bc4adee537de5cd056a8906
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71301695"
---
# <a name="convert-a-local-function-to-a-method"></a>Konwertuj funkcję lokalną na metodę

To Refaktoryzacja dotyczy:

- C#

**Co:** Konwertuj funkcję lokalną na metodę.

**Kiedy:** Masz funkcję lokalną, którą chcesz zdefiniować poza bieżącym kontekstem lokalnym.

**Dlaczego:** Chcesz skonwertować funkcję lokalną na metodę, aby można było ją wywołać poza kontekstem lokalnym. Możesz chcieć skonwertować na metodę, gdy funkcja lokalna jest zbyt długa. Podczas definiowania funkcji w osobnej metodzie kod jest łatwiejszy do odczytania.

## <a name="convert-local-function-to-method-refactoring"></a>Konwertuj funkcję lokalną na refaktoryzację metody

1. Umieść kursor w funkcji lokalnej.

    ![Konwertowanie funkcji lokalnej na przykład kodu metody](media/convert-local-function-to-method.png)

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

    ![Konwertuj funkcję lokalną na przykład naprawy kodu metody](media/convert-local-function-to-method-codefix.png)

2. Naciśnij klawisz ENTER, aby zaakceptować refaktoryzację.

    ![Przykład konwersji funkcji lokalnej na wynik metody](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Porady dla deweloperów platformy .NET](../csharp-developer-productivity.md)
