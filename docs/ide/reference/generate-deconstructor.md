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
ms.openlocfilehash: f24fa988cf14bbf48fe157e2b9ee538d3eff2f35
ms.sourcegitcommit: cd91a8a4f6086cda9ba6948be25864fc7d6b8e44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59537533"
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