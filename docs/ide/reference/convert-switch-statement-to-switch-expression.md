---
title: Konwertowanie instrukcji switch na wyrażenie switch
description: Dowiedz się, jak użyć menu szybkie akcje i refaktoryzacje w celu przekonwertowania instrukcji switch na wyrażenie przełącznika języka C# 8,0.
ms.custom: SEO-VS-2020
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 56a1b20854cdd2c1821490bb4972d67bbe912056
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99919664"
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
