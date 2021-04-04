---
title: Używanie instrukcji new()
description: Dowiedz się, jak korzystać z programu `new()` `var` .
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 889be18ab342f515bf5add266088a7ee69c087c1
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106218077"
---
# <a name="use-new"></a>Korzystanie z polecenia `new()`

Dotyczy to:

- C#

**Co:** Użyj `new()` .

**Kiedy:** Masz pole, którego nie można użyć `var` lub preferencja stylu kodu nie jest używana `var` .

**Dlaczego:** Aby nie trzeba było pisać powtarzanego kodu przez powtórzenie tego typu dwa razy.

## <a name="how-to"></a>Porady

1. Umieść karetkę na deklaracji pola.

2. Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

3. Wybierz pozycję **Użyj "New (...)"**:

    ![Użyj "New (...)"](media/use-new.png)

## <a name="see-also"></a>Zobacz też

- [Refaktoryzacja](../refactoring-in-visual-studio.md)
