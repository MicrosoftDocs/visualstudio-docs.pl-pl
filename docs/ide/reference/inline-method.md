---
title: Metoda śródwierszowa
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje w programie Visual Studio do refaktoryzacji deklaracji metody wbudowanej i zapewnienia wyraźniejszej składni.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 80313cf0dd9b828c9602fdf8ebff022342faa0fb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852365"
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
