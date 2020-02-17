---
title: Konwertuj instrukcję if, aby przełączyć instrukcję lub wyrażenie Switch
ms.date: 02/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cb0c06fe0493f973ea9cf0a566ffda45a49eeeff
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2020
ms.locfileid: "77280783"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Konwertuj instrukcję if, aby przełączyć instrukcję lub wyrażenie Switch

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Przekonwertuj instrukcję if na [instrukcję Switch](/dotnet/csharp/language-reference/keywords/switch) lub C# [wyrażenie przełącznika](/dotnet/csharp/whats-new/csharp-8#switch-expressions)8,0.

**Kiedy:** Chcesz przekonwertować instrukcję `if` do instrukcji `switch` lub wyrażenia `switch` i na odwrót. 

**Dlaczego:** Jeśli używasz instrukcji `if`, to Refaktoryzacja umożliwia łatwe przejście do `switch` instrukcji lub wyrażeń `switch`.

## <a name="how-to"></a>Porady

1. Umieść kursor w słowie kluczowym `if`.
2. Naciśnij klawisz **Ctrl**+ **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz pozycję **Konwertuj na instrukcję "switch"** .

   ![Konwertuj instrukcję if, aby przełączyć instrukcję lub wyrażenie Switch](media/convert-if-statement-to-switch-statement-or-switch-expression.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
