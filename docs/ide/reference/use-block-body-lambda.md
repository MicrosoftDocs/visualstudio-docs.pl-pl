---
title: Używanie wyrażenia lambda lub treści bloku
ms.date: 02/14/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 5c46506e81e5334efea9060e957269e92e9d49cc
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531916"
---
# <a name="use-expression-body-or-block-body-for-lambda-expressions"></a>Używanie treści wyrażenia lub treści bloku dla wyrażeń lambda

Ten refaktoryzator ma zastosowanie do:

- C#

**Co:** Umożliwia refaktoryzator wyrażenie lambda, aby użyć treści wyrażenia lub obiektu bloku.

**Kiedy:** Wolisz wyrażenia lambda, aby używać treści wyrażenia lub obiektu bloku.

**Dlaczego?** Wyrażenia Lambda mogą być refaktoryzowane w celu poprawy czytelności zgodnie z preferencjami użytkownika.

## <a name="lambda-expression-body-or-block-body-refactoring"></a>Refaktoryzowanie treści wyrażenia Lambda lub refaktoryzacji korpusu bloku

1. Umieść kursor po prawej stronie operatora lambda.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

  ![Użyj wyrażenia lambda/korpusu bloku](media/block-body-lambda.png)

3. Wybierz **opcję Użyj treści bloku dla wyrażeń lambda** lub Użyj treści wyrażenia dla **wyrażeń lambda**.

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
- [Wskazówki dla deweloperów platformy .NET](../csharp-developer-productivity.md)