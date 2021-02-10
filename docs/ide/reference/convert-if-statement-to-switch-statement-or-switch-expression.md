---
title: Konwertuj instrukcję if, aby przełączać instrukcję lub wyrażenie
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje, aby przekonwertować instrukcję if na instrukcję Switch lub wyrażenie przełącznika języka C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 0d857338eb1c9b5bb66ccb89e20e6f892944d608
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99936833"
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
