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
ms.sourcegitcommit: 9a3972eb85de5443ac2bc03964c5a251c39b2921
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2019
ms.locfileid: "71301695"
---
# <a name="convert-a-local-function-to-a-method"></a>Konwertuj funkcję lokalną na metodę

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Whatman** Konwertuj funkcję lokalną na metodę.

**Czasie** Masz funkcję lokalną, którą chcesz zdefiniować poza bieżącym kontekstem lokalnym.

**Zalet** Chcesz skonwertować funkcję lokalną na metodę, aby można było ją wywołać poza kontekstem lokalnym. Możesz chcieć skonwertować na metodę, gdy funkcja lokalna jest zbyt długa. Podczas definiowania funkcji w osobnej metodzie kod jest łatwiejszy do odczytania.

## <a name="convert-local-function-to-method-refactoring"></a>Konwertuj funkcję lokalną na refaktoryzację metody

1. Umieść kursor w funkcji lokalnej.

    ![Konwertowanie funkcji lokalnej na przykład kodu metody](media/convert-local-function-to-method.png)

2. Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

    ![Konwertuj funkcję lokalną na przykład naprawy kodu metody](media/convert-local-function-to-method-codefix.png)

2. Naciśnij klawisz ENTER, aby zaakceptować refaktoryzację.

    ![Przykład konwersji funkcji lokalnej na wynik metody](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
