---
title: Generowanie C# Equals i GetHashCode — metoda przesłonięcia
ms.date: 01/26/2018
ms.prod: visual-studio-dev15
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: e7b1f2f196e8cb737d179e12e49d829b1651c5d5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53960907"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generowanie elementu Equals i GetHashCode — metoda zastępuje w programie Visual Studio

Dotyczy to generowanie kodu:

- C#

**Co:** Umożliwia wygenerowanie **jest równa** i **GetHashCode** metody.

**Kiedy:** W przypadku typów, które powinny być porównywane według jedną lub więcej pól, a nie według lokalizacji obiektu w pamięci, należy wygenerować te zastąpienia.

**Dlaczego:**

- Przed zaimplementowaniem typ wartości, należy rozważyć zastępowanie **jest równa** metodę, aby uzyskać większą wydajność przez Domyślna implementacja metody Equals na ValueType.

- Przed zaimplementowaniem Typ referencyjny, należy rozważyć zastępowanie **jest równa** metodę, jeśli danego typu wygląda typu podstawowego, takie jak punkt, ciąg, BigNumber i tak dalej.

- Zastąp **GetHashCode** metodę, aby zezwolić na typ, który ma działać poprawnie w tabeli wyznaczania wartości skrótu. Dowiedz się więcej wskazówek na [Operatory równości](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Instrukcje

1. Umieść kursor w jakimś miejscu w wierszu swojej deklaracji typu.

   ![Wyróżniony kod](media/overrides-highlight-cs.png)

   > [!TIP]
   > Czy nie, kliknij dwukrotnie wybierz nazwę typu lub nie będzie można skorzystać z opcji menu. Po prostu umieść kursor w wierszu w jakimś miejscu.

1. Następnie wykonaj jedną z następujących czynności:

   - Naciśnij klawisz **Ctrl**+**.** wyzwalacz **szybkie akcje i Refaktoryzacje** menu.

   - Kliknij prawym przyciskiem myszy i wybierz **szybkie akcje i Refaktoryzacje** menu.

   - Kliknij ikonę ![śrubokręt](../media/screwdriver-icon.png) ikona, która pojawia się na lewym marginesie.

   ![Generowanie zastąpienia (wersja zapoznawcza)](media/overrides-preview-cs.png)

1. Wybierz **Generuj element Equals(object)** lub **Generowanie Equals i GetHashCode** z menu rozwijanego.

1. W **Wybierz składowe** okno dialogowe, zaznacz elementy członkowskie, aby wygenerować metody:

    ![Generowanie zastąpienia okna dialogowego](media/overrides-dialog-cs.png)

    > [!TIP]
    > Możesz również generować operatory z tego okna dialogowego za pomocą pola wyboru w dolnej części okna dialogowego.

   `Equals` i `GetHashCode` metody są generowane przy użyciu domyślnej implementacji.

   ![Generowanie wyników — metoda](media/overrides-result-cs.png)

## <a name="see-also"></a>Zobacz także

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)