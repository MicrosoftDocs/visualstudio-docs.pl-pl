---
title: Konwertuj między ciągami regularnymi i Verbatim literałów ciągu
ms.date: 06/08/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 7e8e239f53f92727072a2fcd6573d6957b7cd3ec
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290572"
---
# <a name="convert-between-regular-string-and-verbatim-string-literals-refactoring"></a>Konwersja między zwykłym ciągiem i Verbatim literałów ciągów

To Refaktoryzacja dotyczy:

- C#

**Co:** Umożliwia konwertowanie między zwykłym ciągiem i literałami ciągu Verbatim.

**Kiedy:** Chcesz zaoszczędzić miejsce lub zwiększyć przejrzystość kodu.

**Dlaczego:** Konwertowanie literału ciągu Verbatim na zwykły literał ciągu może pomóc zaoszczędzić miejsce. Konwertowanie zwykłego literału ciągu na literał ciągu Verbatim może zapewnić większą przejrzystość.

## <a name="how-to"></a>Porady

1. Umieść karetkę na zwykłym ciągu lub literale ciągu Verbatim:

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

3. Wybierz jedną z następujących opcji: 

    Wybierz pozycję **Konwertuj na zwykły ciąg**.

    ![Konwertuj na ciąg zwykły](media/convert-to-regular-string.png)

    Wybierz pozycję **Konwertuj na ciąg dosłowny**.

    ![Konwertuj na ciąg Verbatim](media/convert-to-verbatim-string.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)