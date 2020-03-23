---
title: Pociągnij członków w górę
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62969183"
---
# <a name="pull-members-up"></a>Pociągnij członków w górę

Ten refaktoryzator ma zastosowanie do:

- C#

- Visual Basic

**Co:** Umożliwia wyciągnięcie elementów członkowskich do typu podstawowego.

**Kiedy:** Zaimplementowano interfejs i chcesz przenieść element członkowski do typu podstawowego.

**Dlaczego?** Ciągnięcie członków w górę umożliwia inne implementacje interfejsu do dziedziczenia tych elementów członkowskich, jak również.

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym elementów członkowskich zaimplementowanego interfejsu.
2. Naciśnij **klawisze Ctrl**+**.** , aby wyzwolić menu **Szybkie akcje i Refaktoryzowania.**

   ![Pociągnij członków w górę](media/pull-members-up.png)

2. Wybierz **opcję Pociągnij elementy członkowskie do typu bazowego**.

3. W oknie dialogowym wybierz elementy członkowskie, które chcesz dodać do wybranego interfejsu.

   ![Pociągnij członka w górę](media/pull-members-up-dialog.png)

4. Wybierz pozycję **OK**. Wybrane elementy członkowskie są ściągane do interfejsu.

   ![Pociągnij element członkowski w górę ukończony](media/pull-members-up-completed.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
