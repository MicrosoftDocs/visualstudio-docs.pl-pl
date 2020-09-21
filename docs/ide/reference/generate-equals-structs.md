---
title: Generowanie operatorów IEquatable dla struktur
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 5ee695169f52036858fc70598f81f375638ab03f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808119"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Generuj operatory IEquatable podczas generowania elementu Equals dla struktur

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** Umożliwia generowanie operatorów **Equals** i **IEquatable** dla [struktur](/dotnet/csharp/language-reference/builtin-types/struct).

**Kiedy:** Masz już strukturę, w której zostanie automatycznie dodany IEquatable oraz operator równości i nierówności.

**Zalet**

- W przypadku implementowania typu wartości należy rozważyć Zastępowanie metody **Equals** , aby uzyskać większą wydajność w porównaniu z domyślną implementacją metody Equals dla elementu ValueType.

- Implementacja interfejsu IEquatable implementuje specyficzną dla typu metodę Equals ().

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym miejscu w wierszu deklaracji struktury.

2. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij pozycję ![śrubokręt](../media/screwdriver-icon.png) ikona wyświetlana na lewym marginesie.

   ![Generuj IEquatable i Equals dla struktur](media/generate-equals-structs.png)

3. Wybierz pozycję **Generuj wartość Equals (obiekt)** z menu rozwijanego.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)