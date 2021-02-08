---
title: Opakowywanie, wcięcia i wyrównywanie refaktoryzacji
description: Dowiedz się, jak zawijać i wyrównywać łańcuchy wywołań metod.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7c218d914bc234533af674fc5d138a1c102d85c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836271"
---
# <a name="wrap-indent-and-align-refactorings"></a>Opakowywanie, wcięcia i wyrównywanie refaktoryzacji

## <a name="wrap-and-align-call-chains"></a>Zawijanie i wyrównywanie łańcuchów wywołań

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia Zawijanie i wyrównywanie łańcuchów wywołań metod.

**Kiedy:** Istnieje długi łańcuch składający się z kilku wywołań metod w jednej instrukcji.

**Dlaczego:** Odczytywanie długiej listy jest łatwiejsze, gdy są one opakowane lub wcięte zgodnie z preferencjami użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym łańcuchu wywołań.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz opcję **Zawijaj łańcuch wywołań** lub **Otocz i Wyrównaj łańcuch wywołań** , aby zaakceptować refaktoryzację.

   ![Screeenshot z menu szybkie akcje i refaktoryzacje w programie Visual Studio z wybranym łańcuchem wywołań Warap i wyświetlanymi zmianami kodu w języku C#.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Zawijanie, wcięcie i wyrównywanie parametrów lub argumentów

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia Zawijanie, wcinanie i wyrównywanie parametrów lub argumentów.

**Kiedy:** Masz deklarację metody lub wywołanie, które ma wiele parametrów lub argumentów.

**Dlaczego:** Odczytywanie długiej listy parametrów lub argumentów jest łatwiejsze, gdy są one opakowane lub wcięte zgodnie z preferencjami użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor na liście parametrów.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Zawijanie, wcięcie i wyrównywanie parametrów](media/wrap-parameters.png)

3. Wybierz opcję **Zawijaj każdy parametr** , aby zaakceptować refaktoryzację.

## <a name="wrap-binary-expressions"></a>Zawijanie wyrażeń binarnych

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia Zawijanie wyrażeń binarnych.

**Kiedy:** Masz wyrażenie binarne.

**Dlaczego:** Odczytywanie wyrażenia binarnego jest łatwiejsze, gdy jest opakowane do preferencji użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor w wyrażeniu binarnym.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz opcję **Otocz wyrażenie** , aby zaakceptować refaktoryzację.

   ![Screeenshot z menu szybkie akcje i refaktoryzacje w programie Visual Studio z wybranym wyrażeniem Warap i wyświetlanymi zmianami kodu w języku C#.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
