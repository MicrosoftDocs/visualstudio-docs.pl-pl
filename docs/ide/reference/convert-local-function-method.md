---
title: Konwertuj funkcją lokalną do metody
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ccddc3aef24ba14245dc568ca5f369e38ce8eba0
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531639"
---
# <a name="convert-a-local-function-to-a-method"></a>Konwertuj funkcją lokalną do metody

Ta Refaktoryzacja mają zastosowanie do:

- C#
- Visual Basic

**Co:** Konwertuj funkcją lokalną do metody.

**Kiedy:** Masz lokalne funkcja, która ma zostać zdefiniowana poza bieżący kontekst lokalnego.

**Dlaczego:** Chcesz przekonwertować funkcją lokalną do metody, aby wywołując poza lokalnego kontekstu. Można przekonwertować do metody, pobierając lokalnych funkcji jest zbyt długa. Po zdefiniowaniu funkcji w oddzielnych metodach kod jest łatwiejsza do odczytania.

## <a name="convert-local-function-to-method-refactoring"></a>Konwertuj funkcję lokalnego do refaktoryzacji — metoda

1. Umieść kursor w funkcji lokalnej.

    ![Konwertuj funkcją lokalną do przykładowego kodu — metoda](media/convert-local-function-to-method.png)

2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

    ![Konwertuj funkcję lokalnych na przykład poprawki kodu — metoda](media/convert-local-function-to-method-codefix.png)

2. Naciśnij klawisz Enter, aby zaakceptować refaktoryzacji.

    ![Konwertuj funkcję lokalnego próbkę wynik, metoda](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
