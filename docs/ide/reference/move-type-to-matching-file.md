---
title: Przenoszenie typu do pasującego refaktoryzacji plików
description: Przenieś typ do oddzielnego pliku o tej samej nazwie. Kliknij prawym przyciskiem myszy typ, wybierz szybkie akcje i refaktoryzowania, a następnie wybierz polecenie Przenieś typ do <TypeName>cs.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585274"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Przenoszenie typu do pasującego refaktoryzacji plików

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia przeniesienie zaznaczonego typu do oddzielnego pliku o tej samej nazwie.

**Kiedy:** Masz wiele klas, struktur, interfejsów itp w tym samym pliku, który chcesz oddzielić.

**Dlaczego?** Umieszczenie wielu typów w tym samym pliku może utrudnić znalezienie tych typów. Przenosząc typy do plików o tej samej nazwie, kod staje się bardziej czytelny i łatwiejszy w nawigacji.

## <a name="how-to"></a>Porady

1. Umieść kursor wewnątrz nazwy typu, w którym jest zdefiniowany. Przykład:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij **klawisze Ctrl**+**.**
   - Kliknij prawym przyciskiem myszy nazwę typu i wybierz **szybkie akcje i refaktoryzowania**

1. Z menu **wybierz polecenie Przenieś typ do nazwy *typu*.cs,** w którym *nazwa typename* jest nazwą wybranego typu.

   Typ jest przenoszony do nowego pliku w projekcie, który ma taką samą nazwę jak typ.

   - C#:

      ![Wynik wbudowany - C #](media/movetype-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowany — visual basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
