---
title: Generowanie operatorów IEquatable dla struktur
description: Dowiedz się, jak za pomocą menu szybkie akcje i refabryki wygenerować operatory Equals i IEquatable dla struktur.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 05792636e1094c53869f0235145aec73b26deea9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99952983"
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