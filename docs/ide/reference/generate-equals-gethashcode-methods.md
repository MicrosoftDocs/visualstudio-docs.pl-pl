---
title: Generuj zastąpienia metody Equals i GetHashCode języka C#
description: Dowiedz się, jak generować metody Equals i GetHashCode przy użyciu menu szybkie akcje i refaktoryzacje.
ms.custom: SEO-VS-2020
ms.date: 03/08/2021
ms.topic: reference
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 597d17b69aa3f0feca520e6100439d934e5d9211
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607355"
---
# <a name="generate-equals-and-gethashcode-method-overrides-in-visual-studio"></a>Generuj zastąpienia metody Equals i GetHashCode w programie Visual Studio

Ta generacja kodu ma zastosowanie do:

- C#

**Co:** Umożliwia generowanie metod **Equals** i **GetHashCode** .

**Kiedy:** Generuj te zastąpienia, gdy masz typ, który powinien być porównywany przez co najmniej jedno pole, a nie lokalizację obiektu w pamięci.

**Zalet**

- W przypadku implementowania typu wartości należy rozważyć Zastępowanie metody **Equals** . Gdy to zrobisz, można uzyskać większą wydajność w porównaniu z domyślną implementacją metody Equals dla elementu ValueType.

- Jeśli wdrażasz typ referencyjny, należy rozważyć Zastępowanie metody **Equals** , jeśli typ wygląda jak typ podstawowy, taki jak Point, String, BigNumber itd.

- Zastąp metodę **GetHashCode** , aby umożliwić prawidłowe działanie typu w tabeli skrótów. Przeczytaj więcej wskazówek na temat [operatorów równości](/dotnet/standard/design-guidelines/equality-operators).

## <a name="how-to"></a>Porady

1. Umieść kursor w dowolnym miejscu w wierszu deklaracji typu.

    ```csharp
    public class ImaginaryNumber
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }
    }
    ```

   Kod powinien wyglądać podobnie do poniższego zrzutu ekranu:

   ![Zrzut ekranu przedstawiający wyróżniony kod, na którym należy zastosować wygenerowaną metodę](media/overrides-highlight-cs.png)

   > [!TIP]
   > Nie klikaj dwukrotnie opcji zaznacz nazwę typu lub opcja menu nie będzie dostępna. Umieść kursor w dowolnym miejscu w wierszu.

1. Następnie wybierz jedną z następujących akcji:

   - Naciśnij klawisz **Ctrl** + **.** Aby wyzwolić menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij prawym przyciskiem myszy i wybierz menu **szybkie akcje i operacje refaktoryzacji** .

   - Kliknij pozycję ![Zrzut ekranu przedstawiający ikonę śrubokrętu Quick Actions w programie Visual Studio](../media/screwdriver-icon.png) ikona wyświetlana na lewym marginesie.

1. W menu rozwijanym wybierz pozycję **Generuj wartość Equals (Object)** lub **Generuj wartość Equals i GetHashCode**.

   ![Zrzut ekranu przedstawiający menu rozwijane Generuj zastąpienia](media/overrides-preview-cs.png)

1. W oknie dialogowym **Wybierz członków** wybierz członków, dla których chcesz wygenerować metody:

    ![Generowanie okna dialogowego zastąpień](media/overrides-dialog-cs.png)

    > [!TIP]
    > Możesz również generować operatory z tego okna dialogowego przy użyciu pola wyboru w dolnej części okna dialogowego.

   `Equals`Metody i `GetHashCode` są generowane z domyślnymi implementacjami, jak pokazano w poniższym kodzie:

    ```csharp
   public class ImaginaryNumber : IEquatable<ImaginaryNumber>
    {
        public double RealNumber { get; set; }
        public double ImaginaryUnit { get; set; }

        public override bool Equals(object obj)
        {
            return Equals(obj as ImaginaryNumber);
        }

        public bool Equals(ImaginaryNumber other)
        {
            return other != null &&
                   RealNumber == other.RealNumber &&
                   ImaginaryUnit == other.ImaginaryUnit;
        }

        public override int GetHashCode()
        {
            return HashCode.Combine(RealNumber, ImaginaryUnit);
        }
    }
    ```

   Kod powinien wyglądać podobnie do poniższego zrzutu ekranu:

   ![Zrzut ekranu przedstawiający wynik wygenerowanej metody](media/overrides-result-cs.png)

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu](../code-generation-in-visual-studio.md)
- [Podgląd zmian](../../ide/preview-changes.md)
