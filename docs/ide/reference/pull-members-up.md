---
title: Obudowach elementów członkowskich
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 2d1f7deb7aca1fed7b75b66b17ce2e4d63768a0d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969183"
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
