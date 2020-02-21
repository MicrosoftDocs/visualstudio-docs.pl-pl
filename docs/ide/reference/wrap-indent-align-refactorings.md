---
title: Zawijanie, wcięcie i wyrównywanie refaktoryzacji
description: Dowiedz się, jak zawijać i wyrównywać łańcuchy wywołań metod.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 349f2eeccfea4fea03967929b01114c0de1af155
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527669"
---
# <a name="wrap-indent-and-align-refactorings"></a>Zawijanie, wcięcie i wyrównywanie refaktoryzacji

## <a name="wrap-and-align-call-chains"></a>Zawijanie i wyrównywanie łańcuchów wywołań

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Umożliwia Zawijanie i wyrównywanie łańcuchów wywołań metod.

**Kiedy:** Istnieje długi łańcuch składający się z kilku wywołań metod w jednej instrukcji.

**Dlaczego:** Odczytywanie długiej listy jest łatwiejsze, gdy są one opakowane lub wcięte zgodnie z preferencjami użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym łańcuchu wywołań.
2. Naciśnij klawisz **Ctrl**+ **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz opcję **Zawijaj łańcuch wywołań** lub **Otocz i Wyrównaj łańcuch wywołań** , aby zaakceptować refaktoryzację.

   ![Zawijanie i wyrównywanie łańcuchów wywołań](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Zawijanie, wcięcie i wyrównywanie parametrów lub argumentów

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia Zawijanie, wcinanie i wyrównywanie parametrów lub argumentów.

**Kiedy:** Masz deklarację metody lub wywołanie, które ma wiele parametrów lub argumentów.

**Dlaczego:** Odczytywanie długiej listy parametrów lub argumentów jest łatwiejsze, gdy są one opakowane lub wcięte zgodnie z preferencjami użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor na liście parametrów.
2. Naciśnij klawisz **Ctrl**+ **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Zawijanie, wcięcie i wyrównywanie parametrów](media/wrap-parameters.png)

3. Wybierz opcję **Zawijaj każdy parametr** , aby zaakceptować refaktoryzację.

## <a name="wrap-binary-expressions"></a>Zawijanie wyrażeń binarnych

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Co:** Umożliwia Zawijanie wyrażeń binarnych.

**Kiedy:** Masz wyrażenie binarne.

**Dlaczego:** Odczytywanie wyrażenia binarnego jest łatwiejsze, gdy jest opakowane do preferencji użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor w wyrażeniu binarnym.
2. Naciśnij klawisz **Ctrl**+ **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .
3. Wybierz opcję **Otocz wyrażenie** , aby zaakceptować refaktoryzację.

   ![Zawijanie i wyrównywanie łańcuchów wywołań](media/wrap-binary-expression.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
