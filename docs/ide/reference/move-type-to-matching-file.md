---
title: Przenieś typ do zgodnego refaktoryzacji pliku
description: Przenieś typ do oddzielnego pliku o tej samej nazwie. Kliknij prawym przyciskiem myszy typ, wybierz polecenie szybkie akcje i refaktoryzacje, a następnie wybierz pozycję Przenieś typ do <TypeName>. cs.
ms.date: 01/26/2018
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ba822981ade5ebdc191732e0a32b02a9a4005fb4
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666489"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Przenoszenie typu do zgodnego refaktoryzacji pliku

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia przeniesienie wybranego typu do oddzielnego pliku o tej samej nazwie.

**Kiedy:** Istnieje wiele klas, struktur, interfejsów itp. w tym samym pliku, który ma zostać rozdzielony.

**Dlaczego:** Umieszczenie wielu typów w tym samym pliku może utrudnić znalezienie tych typów. Przenosząc typy do plików o tej samej nazwie, kod będzie bardziej czytelny i łatwiejszy do nawigowania.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor wewnątrz nazwy typu, w którym jest zdefiniowany. Na przykład:

   ```csharp
   class Person
   ```

   ```vb
   Class Person
   ```

2. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl** + **.**
   - Kliknij prawym przyciskiem myszy nazwę typu i wybierz polecenie **szybkie akcje i refaktoryzacje**

1. Wybierz pozycję **Przenieś typ do *TypeName*. cs** z menu, gdzie *TypeName* jest nazwą wybranego typu.

   Typ jest przenoszony do nowego pliku w projekcie, który ma taką samą nazwę jak typ.

   - C#:

      ![Wynik wbudowany —C#](media/movetype-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowany — Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
