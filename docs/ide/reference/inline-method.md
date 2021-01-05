---
title: Metoda śródwierszowa
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje w programie Visual Studio do refaktoryzacji deklaracji metody wbudowanej i zapewnienia wyraźniejszej składni.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 655c6dad03b05b257aec3d92199321a0e0e93d22
ms.sourcegitcommit: 3c571f44bfd6402efea5187af43df287bac5b6ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/24/2020
ms.locfileid: "97761423"
---
# <a name="inline-method"></a>Metoda śródwierszowa

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Refaktoryzacja metody wbudowanej. 

**Kiedy:** Chcesz zastąpić użycie metody static, instance i Extension w ramach jednej treści instrukcji z opcją usunięcia oryginalnej deklaracji metody.

**Dlaczego:**  Ta refaktoryzacja zapewni bardziej przejrzystą składnię.

## <a name="how-to"></a>Porady

1. Umieść karetkę przy użyciu metody.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

3. Wybierz jedną z następujących opcji: 
    
   Wybierz pozycję **Umieść w tekście element `<QualifiedMethodName>`** , aby usunąć deklarację metody wbudowanej: 

    ![Screeenshot z menu szybkie akcje i refaktoryzacje w programie Visual Studio z pokazanymi zmianami kodu w języku C# ().](media/inline-method-remove-declaration.png)

   Wybierz pozycję **Umieść w tekście i zachowaj element `<QualifiedMethodName>`** , aby zachować oryginalną deklarację metody: 

    ![Screeenshot z menu szybkie akcje i refaktoryzacje w programie Visual Studio z opcją Konwertuj wartość "inline i Keep".](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
