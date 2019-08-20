---
title: Zawijanie i wyrównywanie łańcuchów wywołań
description: Dowiedz się, jak zawijać i wyrównywać łańcuchy wywołań metod.
ms.date: 08/13/2019
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 2a5b6bea4c915e029ca3ae448444decce0d7b041
ms.sourcegitcommit: b83fefa8177c5554cbe2c59c4d102cbc534f7cc6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69619739"
---
# <a name="wrap-and-align-call-chains"></a>Zawijanie i wyrównywanie łańcuchów wywołań

Ta Refaktoryzacja mają zastosowanie do:

- C#

**Whatman** Umożliwia Zawijanie i wyrównywanie łańcuchów wywołań metod.

**Czasie** Istnieje długi łańcuch składający się z kilku wywołań metod w jednej instrukcji.

**Zalet** Odczytywanie długiej listy jest łatwiejsze, gdy są one opakowane lub wcięte zgodnie z preferencjami użytkownika.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w dowolnym łańcuchu wywołań.
2. Naciśnij klawisz **Ctrl**+ **.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.
3. Wybierz opcję **Zawijaj łańcuch wywołań** lub **Otocz i Wyrównaj łańcuch wywołań** , aby zaakceptować refaktoryzację.

   ![Zawijanie i wyrównywanie łańcuchów wywołań](media/wrap-call-chain.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
