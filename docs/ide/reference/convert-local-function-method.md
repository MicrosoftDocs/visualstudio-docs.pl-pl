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
ms.openlocfilehash: a580077528c87e62f81e840ed6dee76ff1eac57f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62968295"
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
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
