---
title: Ściąganie członków
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62969183"
---
# <a name="pull-members-up"></a>Ściąganie członków

To Refaktoryzacja dotyczy:

- C#

- Visual Basic

**Co:** Umożliwia ściąganie członków do typu podstawowego.

**Kiedy:** Zaimplementowano interfejs i chcesz przenieść element członkowski do typu podstawowego.

**Dlaczego:** Ściąganie członków pozwala na inne implementacje interfejsu w celu dziedziczenia tych członków.

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym członku zaimplementowanego interfejsu.
2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   ![Ściąganie członków](media/pull-members-up.png)

2. Wybierz pozycję **Pobierz składowe do typu podstawowego**.

3. W oknie dialogowym Wybierz elementy, które chcesz dodać do wybranego interfejsu.

   ![Ściąganie członków](media/pull-members-up-dialog.png)

4. Wybierz przycisk **OK**. Wybrane elementy członkowskie są ściągane do interfejsu.

   ![Ukończono ściąganie członków](media/pull-members-up-completed.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
