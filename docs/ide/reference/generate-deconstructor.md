---
title: Generowanie szybkiej akcji dekonstruktora
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5a3a89d15d05b44575fede98d3043d706b24c1d9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531886"
---
# <a name="generate-a-deconstructor-in-visual-studio"></a>Generowanie dekonstruktora w programie Visual Studio

To generowanie kodu dotyczy:

- C#

**Co:** Umożliwia natychmiastowe wygenerowanie skrótu metody dla nowego dekonstruktora.

**Kiedy:** Chcesz automatycznie zdekonstruować typ.

**Dlaczego?** Można ręcznie wpisać dekonstruktora, ale ta funkcja generuje skrót dla Ciebie z poprawnymi parametrami out.

## <a name="generate-a-deconstructor"></a>Generowanie dekonstruktora

1. Zadeklaruj nowy typ z określonymi żądanymi parametrami. Ta deklaracja spowoduje błąd, gdy nie można znaleźć wystąpienia dekonstrukcji pasującego do deklaracji.

   ![Brak błędu dekonstruktora](media/deconstruct.png)

2. Wykonać jeden z następujących kroków:

   - **Klawiatura**
      - Za pomocą kursora w deklaracji wybierz pozycję Ctrl+. , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
   - **Mysz**
      - Kliknij prawym przyciskiem myszy i wybierz menu **Szybkie akcje i Refaktoryzowania.**
      - Wybierz ikonę ![Śrubokręt](media/screwdriver.png) ikona, która pojawia się na lewym marginesie, jeśli kursor tekstowy znajduje się już w pustym wierszu w klasie.

      ![Generowanie poprawki kodu dekonstruktora](media/deconstruct-codefix.png)

3. Wybierz **opcję Wygeneruj metodę "MyInternalClass.Deconstruct",** aby wygenerować dekonstruktora.

   ![Wynikowy kod dekonstruktora](media/deconstruct-result.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)