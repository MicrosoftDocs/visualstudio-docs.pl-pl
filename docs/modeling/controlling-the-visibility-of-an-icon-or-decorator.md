---
title: Kontrolowanie widoczności ikony lub elementu Decorator
description: Dowiedz się, jak kontrolować widoczność ikony lub dekoratora w zależności od stanu właściwości w modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c60d66188364ddd18be1d60a92b51ee5d7a9fc8
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389621"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub elementu Decorator
Dekorator *to* ikona lub wiersz tekstu, który pojawia się na kształcie w języku specyficznym dla domeny (DSL). Dekorator można wyświetlać i znikać w zależności od stanu właściwości w modelu. Na przykład na kształcie reprezentującym osobę możesz mieć różne ikony, które są wyświetlane w zależności od płci, liczby dzieci i tak dalej.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub dekoratora
 W poniższej procedurze przyjęto założenie, że zdefiniowano już kształt i jego mapowanie na klasę domeny. Aby uzyskać więcej informacji, [zobacz How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Aby kontrolować widoczność ikony lub dekoratora tekstu

1. Na diagramie definicji DSL dodaj do klasy kształtu ikony lub dekoratory tekstu, które mają być wyświetlane.

   1. Kliknij prawym przyciskiem myszy klasę kształtu, wskaż **polecenie Dodaj**, a następnie kliknij wymagany typ dekoratora.

   2. Ustaw właściwość Position **dekoratora.** Więcej niż jeden dekorator może mieć tę samą pozycję. Możesz na przykład mieć ikony dla mężczyzn i kobiet, które mają tę samą pozycję.

   3. Ustaw właściwość **Ikona domyślna** dekoratora ikon.

2. Wybierz mapę elementu diagramu, która jest szarą linią między klasą kształtu i klasą domeny na diagramie definicji DSL.

3. W oknie Szczegóły DSL na karcie **Decorator Maps (Mapy dekoratora)** wybierz dekorator. Na przykład MaleDecorator.

4. Zaznacz pole **Filtr widoczności.**

5. Jeśli właściwość domeny, która powinna kontrolować widoczność, znajduje się w bezpośredniej klasie domeny, pozostaw pole **Ścieżka do właściwości filtru** puste.

    W przeciwnym razie kliknij menu rozwijane i przejdź do relacji lub klasy, w której znajduje się właściwość.

   - Aby uniknąć raportu o błędach, nie należy nawigować po relacji oznaczonej znakiem "*" w narzędziu nawigacyjnym.

6. Ustaw właściwość **Filter na** właściwość domeny. Na przykład Płeć.

7. Na liście **Wpisy widoczności** dodaj wartości tej właściwości domeny, dla której dekorator powinien być widoczny. Na przykład Mężczyzna.

8. Powtórz kroki dla każdej ikony.

9. **Przekształć wszystkie** szablony, skompilować i uruchomić oraz otworzyć diagram testowy.

10. Po zmianie wartości właściwości kontrolującej dekoratory powinny pojawić się i zniknąć.

    Często chcesz, aby widoczność podlegała bardziej złożonej formule niż prosty zestaw wartości. Na przykład aby mieć ikonę, zależy od liczby linków określonego typu lub od tego, czy liczba znajduje się w określonym zakresie. W takim przypadku należy użyć poniższej procedury.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Aby kontrolować widoczność dekoratora na podstawie formuły

1. Dodaj właściwość domeny obliczeniowej do klasy domeny. W **oknie** Właściwości ustaw następujące wartości:

     **IsBrowsable =** `False` **— ukrywa właściwość przed użytkownikiem**    

     **Rodzaj =** `Calculated` **— oznacza to, że należy podać kod, który oblicza jego wartość**    

     **Nazwa** przykładu **DecoratorControl**

     **Typu** = `Boolean`

     Aby uzyskać więcej informacji, zobacz [Właściwości magazynu obliczeniowego i niestandardowego.](../modeling/calculated-and-custom-storage-properties.md)

2. Spraw, aby nowa właściwość kontrolowała widoczność dekoratora.

    1. Wybierz mapę elementu diagramu, która jest szarym wierszem z klasy domeny do kształtu. W **oknie Szczegóły DSL** otwórz **kartę DecoratorMap.**

    2. Zaznacz pole **Filtr widoczności.**

    3. W **właściwości filter** wybierz właściwość kontrolki **DecoratorControl**.

    4. W **obszarze Wpisy widoczności** wprowadź wartość `True` .

3. Kliknij **pozycję Przekształć wszystkie** szablony na **Eksplorator rozwiązań** narzędzi.

4. Kliknij **pozycję Build Solution (Skompilowanie** rozwiązania) w menu Build **(Kompilacja).**

5. Kliknij dwukrotnie raport o błędach, który się pojawił: "*YourClass* does not contain a definition for GetDecoratorControlValue ...".

     Zostanie otwarty edytor tekstów w pliku Dsl\GeneratedCode\DomainClasses.cs. Powyżej wyróżniony błąd znajduje się komentarz, który prosi o dodanie metody.

6. Zwróć uwagę na brakujące przestrzenie nazw, klasę i metodę.  Na przykład Company.FamilyTree.Person.GetDecoratorControlValue().

7. W oddzielnym pliku kodu napisz definicję klasy częściowej, która zawiera brakującą metodę. Na przykład:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Aby uzyskać więcej informacji na temat dostosowywania modelu za pomocą kodu programu, zobacz [Navigating and Updating a Model in Program Code](../modeling/navigating-and-updating-a-model-in-program-code.md)(Nawigowanie i aktualizowanie modelu w kodzie programu).

8. Ponownie skompilować i uruchomić rozwiązanie.

## <a name="see-also"></a>Zobacz też

- [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md)
- [Ustawienie obrazu tła w diagramie](../modeling/setting-a-background-image-on-a-diagram.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)