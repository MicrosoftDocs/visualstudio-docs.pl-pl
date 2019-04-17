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
ms.openlocfilehash: 2ca2d3a0c174fa4c7d0f66d3abc440b8c9aa93cf
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658815"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generowanie deconstructor w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** Pozwala natychmiast generowania szkieletu metody dla nowych deconstructor.

**Kiedy:** Chcesz automatycznie prawidłowo dekonstruować danego typu.

**Dlaczego:** Można ręcznie wpisać deconstructor, ale ta funkcja generuje klasy zastępczej dla Ciebie przy użyciu prawidłowych parametrów out.

## <a name="generate-a-deconstructor"></a>Generowanie deconstructor

1. Zadeklaruj nowy typ z określonymi parametrami żądany limit. Ta deklaracja spowoduje błąd, gdy można znaleźć żadnego wystąpienia dekonstrukcji dopasowania swojej deklaracji.

   ![Błąd braku deconstructor](media/deconstruct.png)

2. Wykonaj jedną z następujących czynności:

   - **Keyboard**
      - Jeśli kursor znajduje się w swojej deklaracji wybierz klawisze Ctrl +. wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
   - **Myszy**
      - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.
      - Wybierz pozycję ![śrubokręt](media/screwdriver.png) Ikona wyświetlana na lewym marginesie, jeśli kursor tekstu jest już w pustym wierszu w klasie.

      ![Generowanie deconstructor poprawki kodu](media/deconstruct-codefix.png)

3. Wybierz **Generuj metodę "MyInternalClass.Deconstruct"** do generowania deconstructor.

   ![Wynikowy kod deconstructor](media/deconstruct-result.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)