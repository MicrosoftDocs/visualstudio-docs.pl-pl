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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531675"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Odwrócone wyrażenia warunkowe i operatory warunkowe I/OR

Ten refaktoryzator ma zastosowanie do:

- C#
- Visual Basic

**Co:** Umożliwia odwrócenie wyrażenia warunkowego lub operatora warunkowego I/OR.

**Kiedy:** Masz wyrażenie warunkowe lub warunkowe I/OR operatora, które byłyby lepiej zrozumiałe, jeśli odwrócone.

**Dlaczego?** Odwracanie wyrażenia lub warunkowego operatora AND/OR ręcznie może trwać znacznie dłużej i ewentualnie powodować błędy. Ta poprawka kodu pomaga wykonać tę refaktoryzacji automatycznie.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Odwrócone wyrażenia warunkowe i refaktoryzatory warunkowe i/lub operatorów

1. Umieść kursor w wyrażeniu warunkowym lub w uwarunkowatym operatorze I/OR.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
3. Wybierz **opcję Odwróć warunek** lub **zamień "&&" na "||"**

    ![Odwrócony warunkowy](media/invert-conditional.png)

    ![Odwrócony warunkowy](media/invert-logical-operator.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)
