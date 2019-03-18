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
ms.openlocfilehash: 7d59b61cff622a9ba305ebfa86f7c0ebe3c00fe3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2019
ms.locfileid: "58157363"
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
- [Wskazówki dla deweloperów platformy .NET](../../ide/visual-studio-2017-for-dotnet-developers.md)
