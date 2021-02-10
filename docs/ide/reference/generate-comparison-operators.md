---
title: Generowanie operatorów porównania dla elementu IComparable
ms.custom: SEO-VS-2020
description: Aby zwiększyć wydajność, Generuj operatory porównania dla typów, które implementują interfejs IComparable.
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: ee0ac916bcc13e6bc89485171b2ce145b31dd919
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932569"
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
