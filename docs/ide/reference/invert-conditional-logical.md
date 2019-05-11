---
title: Odwracanie wyrażeń warunkowych i operacji logicznych
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 3931ae53fc29b0ffd8b8b6e96951a0f4786ff756
ms.sourcegitcommit: 614d5b99576ea27a41957cd94062dc95cbd29c1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2019
ms.locfileid: "65531675"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Odwróć wyrażenia warunkowe i warunkowego i/lub operatorów

Ta Refaktoryzacja mają zastosowanie do:

- C#
- Visual Basic

**Co:** Umożliwia Odwróć wyrażenia warunkowego lub warunkowe i/lub operatora.

**Kiedy:** Wyrażenia warunkowego lub warunkowe i/lub operator, który będzie lepszym rozumieć, jeśli odwrócony.

**Dlaczego:** Odwracanie wyrażenie lub warunkowe i/lub operator ręcznie może trwać dłużej i ewentualnie wprowadzał błędy. Ta poprawka kodu pomaga to osiągnąć, automatycznie tej refaktoryzacji.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Odwróć wyrażenia warunkowe i warunkowego i/lub refaktoryzacji operatorów

1. Umieść kursor w wyrażeniu warunkowym lub warunkowe i/lub operatora.
2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
3. Wybierz **warunkowe Odwróć** lub **Zastąp "& &" z "||"**

    ![Odwróć warunkowe](media/invert-conditional.png)

    ![Odwróć warunkowe](media/invert-logical-operator.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
