---
title: Metoda wbudowana
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
ms.openlocfilehash: 0cc619ea61a7fd4d7f4bc542b946e298933a8f73
ms.sourcegitcommit: f4b49f1fc50ffcb39c6b87e2716b4dc7085c7fb5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2020
ms.locfileid: "93402299"
---
# <a name="inline-method"></a>Metoda wbudowana

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

    ![Ustaw abstrakcyjną klasę](media/inline-method-remove-declaration.png)

   Wybierz pozycję **Umieść w tekście i zachowaj element `<QualifiedMethodName>`** , aby zachować oryginalną deklarację metody: 

    ![Ustaw abstrakcyjną klasę](media/inline-method-preserve-declaration.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
