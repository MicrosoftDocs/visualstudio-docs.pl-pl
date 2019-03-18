---
title: Generowanie deconstructor szybka akcja
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8887f4cd6b4dcd7f08e808f1271f5d546d6a224c
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58159182"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generowanie deconstructor w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** Pozwala natychmiast generowania szkieletu metody dla nowych deconstructor.

**Kiedy:** Chcesz automatycznie prawidłowo dekonstruować danego typu.

**Dlaczego:** Możesz ręcznie wpisać deconstructor, jednak ta funkcja wygeneruje klasy zastępczej dla Ciebie przy użyciu prawidłowych parametrów out.

## <a name="generate-deconstructor"></a>Generowanie dekonstruktora

1. Zadeklaruj nowy typ z określonymi parametrami żądany limit. Ta deklaracja spowoduje błąd, gdy żadne wystąpienie dekonstrukcji można znaleźć dopasowania swojej deklaracji.

   ![Błąd braku deconstructor](media/deconstruct.png)

2. Następnie wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Kursor w swojej deklaracji, naciśnij **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Kliknij ikonę ![śrubokręt](media/screwdriver.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w pustym wierszu w klasie.

      ![Generowanie deconstructor poprawki kodu](media/deconstruct-codefix.png)

3. Wybierz **Generuj metodę "MyInternalClass.Deconstruct"** do generowania deconstructor.

   ![Wynikowy kod deconstructor](media/deconstruct-result.png)


## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)