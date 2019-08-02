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
ms.sourcegitcommit: b56dc6fadc6c924beed36bb4c2ccc16cf6bcfa1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/02/2019
ms.locfileid: "68740063"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Konwertowanie instrukcji switch na wyrażenie switch

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Whatman** Konwertuj [instrukcję Switch](/dotnet/csharp/language-reference/keywords/switch) na C# [wyrażenie przełącznika](/dotnet/csharp/whats-new/csharp-8#switch-expressions)8,0.

**Czasie** Chcesz przekonwertować `switch` instrukcję `switch` na wyrażenie i na odwrót. 

**Zalet** Jeśli używasz tylko wyrażeń, to Refaktoryzacja umożliwia łatwe przejście z tradycyjnych `switch` instrukcji.

## <a name="how-to"></a>Instrukcje

1. W pliku projektu [Ustaw wersję językową na podgląd](/dotnet/csharp/language-reference/configure-language-version#edit-the-project-file) , ponieważ `switch` wyrażenia są nową C# funkcją 8,0.
2. Umieść kursor `switch` w słowie kluczowym i naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
3. Wybierz pozycję **Konwertuj instrukcję Switch na wyrażenie**.

   ![Konwertowanie instrukcji switch na wyrażenie switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
