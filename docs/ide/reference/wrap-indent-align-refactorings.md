---
title: Zawijanie, wcięcie i wyrównywanie refaktoryzacji
description: Dowiedz się, jak zawijać i wyrównywać łańcuchy wywołań metod.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093877"
---
# <a name="wrap-indent-and-align-refactorings"></a>Zawijanie, wcięcie i wyrównywanie refaktoryzacji

## <a name="wrap-and-align-call-chains"></a>Zawijanie i wyrównywanie łańcuchów wywołań

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia zawijanie i wyrównywanie łańcuchów wywołań metody.

**Kiedy:** Masz długi łańcuch składający się z kilku wywołań metody w jednej instrukcji.

**Dlaczego?** Czytanie długiej listy jest łatwiejsze, gdy są one zawinięte lub wcięte zgodnie z preferencjami użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym łańcuchu połączeń.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
3. Wybierz **wrap łańcucha wywołania** lub **Zawijanie i wyrównać łańcuch wywołań,** aby zaakceptować refaktoryzacji.

   ![Zawijanie i wyrównywanie łańcuchów wywołań](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Zawijanie, wcięcie i wyrównywanie parametrów lub argumentów

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia zawijanie, wcięcie i wyrównywanie parametrów lub argumentów.

**Kiedy:** Masz deklarację metody lub wywołanie, które ma wiele parametrów lub argumentów.

**Dlaczego?** Czytanie długiej listy parametrów lub argumentów jest łatwiejsze, gdy są one zawijane lub wcięte zgodnie z preferencjami użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor na liście parametrów.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   ![Zawijanie, Wcięcie i Wyrównywanie parametrów](media/wrap-parameters.png)

3. Wybierz **Owijania każdego parametru,** aby zaakceptować refaktoryzacji.

## <a name="wrap-binary-expressions"></a>Zawijanie wyrażeń binarnych

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia zawijanie wyrażeń binarnych.

**Kiedy:** Masz wyrażenie binarne.

**Dlaczego?** Odczytywanie wyrażenia binarnego jest łatwiejsze, gdy jest zawijane do preferencji użytkownika.

### <a name="how-to"></a>Porady

1. Umieść kursor w wyrażeniu binarnym.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**
3. Wybierz **wrap wyrażenie,** aby zaakceptować refaktoryzacji.

   ![Zawijanie i wyrównywanie łańcuchów wywołań](media/wrap-binary-expression.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
