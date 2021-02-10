---
title: Ściąganie członków
description: Dowiedz się, jak używać menu szybkie akcje i refaktoryzacje do ściągania elementów członkowskich do typu podstawowego.
ms.custom: SEO-VS-2020
ms.date: 02/13/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: ee5776e9fc39b77f8059146848d847e0976a5664
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958287"
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
