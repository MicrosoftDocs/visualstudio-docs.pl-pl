---
title: Konwertowanie instrukcji if na instrukcję switch lub wyrażenie switch
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 93ad96809c77d5644b13e6221a41f0b182fb448f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "79094147"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Konwertowanie instrukcji if na instrukcję switch lub wyrażenie switch

To Refaktoryzacja dotyczy:

- C#

**Co:** Przekonwertuj instrukcję if na [instrukcję Switch](/dotnet/csharp/language-reference/keywords/switch) lub [wyrażenie przełącznika](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Kiedy:** Chcesz przekonwertować `if` instrukcję do `switch` instrukcji lub `switch` wyrażenia i na odwrót. 

**Dlaczego:** Jeśli używasz `if` instrukcji, to Refaktoryzacja umożliwia łatwe przejście do `switch` instrukcji lub `switch` wyrażeń.

## <a name="how-to"></a>Porady

1. Umieść kursor w `if` słowie kluczowym.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz jedną z dwóch następujących opcji: 

    Wybierz pozycję **Konwertuj na instrukcję "switch"**.

   ![Konwertuj instrukcję if, aby instrukcji switch](media/convert-if-to-switch-statement.png) 

    Wybierz pozycję **Konwertuj na wyrażenie "switch"**. 

    ![Konwertuj instrukcję if, aby przełączać wyrażenie](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
