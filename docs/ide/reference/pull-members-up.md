---
title: Obudowach elementów członkowskich
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kendrahavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 65ce1b44063fd6152fc300e32e7dd075fa8afcbf
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/18/2019
ms.locfileid: "56335960"
---
# <a name="pull-members-up"></a>Obudowach elementów członkowskich

Ta Refaktoryzacja mają zastosowanie do:

- C#

- Visual Basic

**Co:** Pozwala na ściąganie członków typu podstawowego.

**Kiedy:** Udało Ci się wdrożyć interfejs i chcesz przenieść element członkowski do typu podstawowego.

**Dlaczego:** Ściąganie elementów członkowskich w umożliwia inne implementacje interfejsu dziedziczy tych członków, a także.

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w dowolnym członkiem zaimplementowany interfejs.
2. Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

   ![Obudowach elementów członkowskich](media/pull-members-up.png)

2. Wybierz **pobierania członków typu podstawowego**.

3. W oknie dialogowym Wybierz elementy członkowskie, które chcesz dodać do wybranego interfejsu.

   ![Obudowach element członkowski](media/pull-members-up-dialog.png)

4. Wybierz **OK**. Zaznaczone elementy członkowskie są pobierane w do interfejsu.

   ![Obudowach element członkowski ukończone](media/pull-members-up-completed.png)

## <a name="see-also"></a>Zobacz także

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
