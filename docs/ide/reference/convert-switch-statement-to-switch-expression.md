---
title: Konwertuj instrukcję switch, aby wyrażenie switch
ms.date: 06/19/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: ecb7750301101a2607c17e68b5e919623a03caba
ms.sourcegitcommit: 7eb2fb21805d92f085126f3a820ac274f2216b4e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2019
ms.locfileid: "67329103"
---
# <a name="convert-switch-statement-to-switch-expression"></a>Konwertuj instrukcję switch, aby wyrażenie switch

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Konwertuj [switch, instrukcja](/dotnet/csharp/language-reference/keywords/switch) do C# 8.0 [wyrażenie switch](/dotnet/csharp/whats-new/csharp-8#switch-expressions).

**Kiedy:** Chcesz przekonwertować `switch` instrukcję, aby `switch` wyrażenia i na odwrót. 

**Dlaczego:** Jeśli używane są tylko wyrażenia, tej refaktoryzacji umożliwia łatwe przejście od tradycyjnych `switch` instrukcji.

## <a name="how-to"></a>Instrukcje

1. W pliku projektu [Ustaw wersję języka, aby wyświetlić podgląd](/dotnet/csharp/language-reference/configure-language-version#set-the-language-version-in-visual-studio) ponieważ `switch` wyrażenia są nowe C# funkcji 8.0.
2. Umieść kursor w `switch` — słowo kluczowe, a następnie naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
3. Wybierz **instrukcji switch przekonwertować na wyrażenie**.

   ![Konwertuj instrukcję switch, aby wyrażenie switch](media/convert-switch-statement-to-switch-expression.png) 

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
