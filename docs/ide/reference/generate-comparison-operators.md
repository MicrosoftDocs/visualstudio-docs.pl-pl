---
title: Generowanie operatorów porównania dla elementu IComparable
ms.custom: SEO-VS-2020
description: Aby zwiększyć wydajność, Generuj operatory porównania dla typów, które implementują interfejs IComparable.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 289562b1aebe981b0829a1adac107a607163a859
ms.sourcegitcommit: f1bb1b66ed141837e992b3352ce68ff24c11f53e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2020
ms.locfileid: "93102600"
---
# <a name="generate-comparison-operators-for-types-that-implement-icomparable"></a>Generuj operatory porównania dla typów, które implementują interfejs IComparable

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** Umożliwia generowanie operatorów **porównania** dla typów, które implementują interfejs IComparable.

**Kiedy:** Masz typ, który implementuje interfejs IComparable, dodamy automatycznie operatory porównania.

**Dlaczego:** W przypadku implementowania typu wartości należy rozważyć Zastępowanie metody **Equals** , aby uzyskać większą wydajność w porównaniu z domyślną implementacją metody Equals dla elementu ValueType.

## <a name="how-to"></a>Porady

1. Umieść kursor wewnątrz klasy lub na słowie kluczowym IComparable.

2. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij pozycję ![śrubokręt](../media/screwdriver-icon.png) ikona wyświetlana na lewym marginesie.

   ![Generowanie operatorów porównania](media/generate-comparison-operators.png)

3. Wybierz pozycję **Generuj wartość Equals (obiekt)** z menu rozwijanego.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
