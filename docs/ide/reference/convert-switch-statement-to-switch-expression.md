---
title: Konwertowanie instrukcji switch na wyrażenie switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: cc13cffe8352d9fb57f5bb991c3af615eddb2a14
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "68740063"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Konwertowanie instrukcji switch na wyrażenie switch

Ten refaktoryzator ma zastosowanie do:

- C#

**Co:** Konwertuj [instrukcję switch](/dotnet/csharp/language-reference/keywords/switch) na [wyrażenie przełącznika](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8.0 .

**Kiedy:** Chcesz przekonwertować instrukcję `switch` na `switch` wyrażenie i odwrotnie. 

**Dlaczego?** Jeśli używasz tylko wyrażeń, to refaktoryzowanie umożliwia łatwe przejście od tradycyjnych `switch` instrukcji.

## <a name="how-to"></a>Porady

1. W pliku projektu [ustaw wersję językową na podgląd,](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) ponieważ `switch` wyrażenia są nową funkcją języka C# 8.0.
2. Umieść kursor w `switch` słowie kluczowym i naciśnij klawisz **Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
3. Wybierz **pozycję Konwertuj instrukcję przełączania na wyrażenie**.

   ![Konwertowanie instrukcji switch na wyrażenie switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
