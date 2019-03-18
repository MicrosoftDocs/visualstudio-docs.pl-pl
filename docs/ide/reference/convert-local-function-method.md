---
title: Konwertowanie funkcji lokalnej na metodę
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
ms.openlocfilehash: 96064b16e53081e0456ed43275acd5edf7ead468
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58152957"
---
# <a name="convert-local-function-to-method"></a>Konwertowanie funkcji lokalnej na metodę

Ta Refaktoryzacja mają zastosowanie do:

- C#
- Visual Basic

**Co:** Konwertuj funkcją lokalną do metody

**Kiedy:** Masz lokalne funkcja, która ma zostać zdefiniowana poza bieżący kontekst lokalnego.

**Dlaczego:** Może chcesz przekonwertować funkcją lokalną do metody, można więc wywoływać go poza lokalnego kontekstu. Możesz konwertować do metody, pobierając lokalnych funkcji jest zbyt długa. Zdefiniowaniem go w oddzielnych metodach sprawia, że Twój kod łatwiejsza do odczytania.

## <a name="convert-local-function-to-method-refactoring"></a>Konwertuj funkcję lokalnego do refaktoryzacji — metoda

1. Umieść kursor w funkcji lokalnej.

    ![Konwertowanie funkcji lokalnej na metodę](media/convert-local-function-to-method.png)

2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

    ![Konwertuj funkcję lokalnego do poprawki kodu — metoda](media/convert-local-function-to-method-codefix.png)

2. Naciśnij klawisz **Enter** do akceptowania refaktoryzacji.

    ![Konwertuj funkcję lokalnego do wyniku — metoda](media/convert-local-function-to-method-result.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
