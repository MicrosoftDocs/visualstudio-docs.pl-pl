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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094147"
---
# <a name="convert-if-statement-to-switch-statement-or-switch-expression"></a>Konwertowanie instrukcji if na instrukcję switch lub wyrażenie switch

Ten refaktoryzator ma zastosowanie do:

- C#

**Co:** Konwertuj instrukcję if na [instrukcję switch](/dotnet/csharp/language-reference/keywords/switch) lub na [wyrażenie przełącznika](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8.0 .

**Kiedy:** Chcesz przekonwertować instrukcję `if` na instrukcję `switch` `switch` lub wyrażenie i odwrotnie. 

**Dlaczego?** Jeśli używasz `if` instrukcji, to refaktoryzowanie `switch` umożliwia `switch` łatwe przejście do instrukcji lub wyrażeń.

## <a name="how-to"></a>Porady

1. Umieść kursor w `if` słowie kluczowym.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
3. Wybierz jedną z następujących dwóch opcji: 

    Wybierz **opcję Konwertuj na instrukcję "przełącz"**.

   ![Konwertuj, aby instrukcja if przełączyć instrukcję](media/convert-if-to-switch-statement.png) 

    Wybierz **opcję Konwertuj na wyrażenie "przełącz"**. 

    ![Konwertuj, aby instrukcja if przełączyć wyrażenie](media/convert-if-to-switch-expression.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
