---
title: Przenieś typ do zgodnego refaktoryzacji pliku
description: Przenieś typ do oddzielnego pliku o tej samej nazwie. Kliknij prawym przyciskiem myszy typ, wybierz polecenie szybkie akcje i refaktoryzacje, a następnie wybierz pozycję Przenieś typ do <TypeName> . cs.
ms.date: 01/26/2018
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 728b9e176a40d2bfd7ae36a329409cb27f80fc86
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927964"
---
# <a name="move-a-type-to-a-matching-file-refactoring"></a>Przenoszenie typu do zgodnego refaktoryzacji pliku

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia przeniesienie wybranego typu do oddzielnego pliku o tej samej nazwie.

**Kiedy:** Istnieje wiele klas, struktur, interfejsów itp. w tym samym pliku, który ma zostać rozdzielony.

**Dlaczego:** Umieszczenie wielu typów w tym samym pliku może utrudnić znalezienie tych typów. Przenosząc typy do plików o tej samej nazwie, kod będzie bardziej czytelny i łatwiejszy do nawigowania.

## <a name="how-to"></a>Porady

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

      ![Wynik wbudowany-C #](media/movetype-result-cs.png)

   - Visual Basic:

      ![Wynik wbudowany — Visual Basic](media/movetype-result-vb.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
