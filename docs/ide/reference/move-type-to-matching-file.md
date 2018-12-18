---
title: Przeniesienie typu do pasującego refaktoryzacji pliku
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 997cf31d14acd65abd003bcb00cce4a9797b394a
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059642"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Przeniesienie typu do pasującego pliku refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** umożliwia przeniesienie wybranego typu do osobnego pliku o takiej samej nazwie.

**Kiedy:** masz wiele klas, struktur, interfejsów, itp. w tym samym pliku, który chcesz oddzielić.

**Dlaczego:** umieszczenie różnych typów, w tym samym pliku może utrudnić można znaleźć tych typów. Przenosząc typów plików o takiej samej nazwie, kod staje się bardziej czytelny i łatwiejszą nawigacją.

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
