---
title: Przeniesienie typu do pasującego refaktoryzacji pliku
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 1cdb84af563afaf5b51d3c378d7a9e06d67a9e76
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55039088"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Przeniesienie typu do pasującego pliku refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia przeniesienie wybranego typu do osobnego pliku o takiej samej nazwie.

**Kiedy:** W tym samym pliku, który chcesz oddzielić masz wiele klas, struktur, interfejsów, itp.

**Dlaczego:** Wprowadzenie do wielu typów, w tym samym pliku może utrudnić znaleźć tych typów. Przenosząc typów plików o takiej samej nazwie, kod staje się bardziej czytelny i łatwiejszą nawigacją.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor wewnątrz nazwę typu, w którym jest zdefiniowana. Na przykład:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl**+**.**
   - Kliknij prawym przyciskiem myszy nazwę typu, a następnie wybierz pozycję **szybkie akcje i operacje refaktoryzacji**

1. Wybierz **przeniesienie typu do *TypeName*.cs** z menu, gdzie *TypeName* jest nazwa typu, który wybrano.

   Typ jest przenoszona do nowego pliku w projekcie, który ma taką samą nazwę jak typ.

   - C#:

      ![Wynik wbudowane-C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowane - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
