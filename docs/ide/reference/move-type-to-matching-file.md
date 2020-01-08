---
title: Przeniesienie typu do pasującego refaktoryzacji pliku
description: Przenieś typ do oddzielnego pliku o tej samej nazwie. Kliknij prawym przyciskiem myszy typ, wybierz polecenie szybkie akcje i refaktoryzacje, a następnie wybierz pozycję Przenieś typ do <TypeName>. cs.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ba082e90c2447d1da7510ce16f888f67a52b5ac0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75585274"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Przeniesienie typu do pasującego pliku refaktoryzacji

Ta Refaktoryzacja mają zastosowanie do:

- Język C#

- Język Visual Basic

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

   - Naciśnij klawisz **Ctrl**+ **.**
   - Kliknij prawym przyciskiem myszy nazwę typu, a następnie wybierz pozycję **szybkie akcje i operacje refaktoryzacji**

1. Wybierz **przeniesienie typu do *TypeName*.cs** z menu, gdzie *TypeName* jest nazwa typu, który wybrano.

   Typ jest przenoszona do nowego pliku w projekcie, który ma taką samą nazwę jak typ.

   - C#:

      ![Wynik wbudowane-C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowane - Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
