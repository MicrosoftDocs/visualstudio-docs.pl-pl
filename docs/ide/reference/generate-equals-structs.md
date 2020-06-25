---
title: Generuj operatory IEquatable dla struktur
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ccc5be9debbdc2b4901d4aad15a0dc4d2bf1bb9f
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85290569"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Generuj operatory IEquatable podczas generowania elementu Equals dla struktur

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** Umożliwia generowanie operatorów **Equals** i **IEquatable** dla [struktur](https://docs.microsoft.com/dotnet/csharp/language-reference/builtin-types/struct).

**Kiedy:** Masz już strukturę, w której zostanie automatycznie dodany IEquatable oraz operator równości i nierówności.

**Zalet**

- W przypadku implementowania typu wartości należy rozważyć Zastępowanie metody **Equals** , aby uzyskać większą wydajność w porównaniu z domyślną implementacją metody Equals dla elementu ValueType.

- Implementacja interfejsu IEquatable implementuje specyficzną dla typu metodę Equals ().

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym miejscu w wierszu deklaracji struktury.

2. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij kartę ![śrubokręt](../media/screwdriver-icon.png) ikona wyświetlana na lewym marginesie.

   ![Generuj IEquatable i Equals dla struktur](media/generate-equals-structs.png)

3. Wybierz pozycję **Generuj wartość Equals (obiekt)** z menu rozwijanego.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
