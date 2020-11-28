---
title: Konwertuj funkcję lokalną na metodę
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby przekonwertować funkcję lokalną na metodę.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 64a46fc6221f00e6bb130be8010cb2544a00dcc8
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305573"
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
