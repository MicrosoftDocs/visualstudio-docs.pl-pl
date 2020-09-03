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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68740063"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Konwertowanie instrukcji switch na wyrażenie switch

To Refaktoryzacja dotyczy:

- C#

**Co:** Konwertuj [instrukcję Switch](/dotnet/csharp/language-reference/keywords/switch) na [wyrażenie przełącznika](/dotnet/csharp/whats-new/csharp-8#switch-expressions)C# 8,0.

**Kiedy:** Chcesz przekonwertować `switch` instrukcję na `switch` wyrażenie i na odwrót. 

**Dlaczego:** Jeśli używasz tylko wyrażeń, to Refaktoryzacja umożliwia łatwe przejście z tradycyjnych `switch` instrukcji.

## <a name="how-to"></a>Porady

1. W pliku projektu [Ustaw wersję językową na podgląd](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) , ponieważ `switch` wyrażenia są nową funkcją języka C# 8,0.
2. Umieść kursor w `switch` słowie kluczowym i naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz pozycję **Konwertuj instrukcję Switch na wyrażenie**.

   ![Konwertowanie instrukcji switch na wyrażenie switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
