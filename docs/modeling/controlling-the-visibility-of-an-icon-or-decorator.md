---
title: Kontrolowanie widoczności ikony lub elementu Decorator
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 731ca1a7091af81abb5b9ed2521cc41f575747cb
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54933753"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub elementu Decorator
A *dekoratora* jest ikona albo wiersz tekstu, który pojawia się na kształcie języka specyficznego dla domeny (DSL). Można wprowadzić dekoratora pojawiają się i znikają w zależności od stanu właściwości w modelu. Na przykład na kształcie reprezentująca osobę, może mieć różne ikony, które pojawiają się w zależności od danej osoby, płeć, liczba elementów podrzędnych i tak dalej.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub dekoratora
 W poniższej procedurze przyjęto, że został już zdefiniowany kształt i ich mapowanie do klasy domeny. Aby uzyskać więcej informacji, zobacz [sposób definiowania języka specyficznego dla domeny](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Aby kontrolowanie widoczności ikony lub tekstu elementu decorator

1. W definicji DSL diagramu Dodaj do klasy kształt ikony lub dekoratorów tekstu, które mają być wyświetlane.

   1.  Kliknij prawym przyciskiem myszy kształt klasy, wskaż opcję **Dodaj**, a następnie kliknij przycisk wymagany typ dekoratora.

   2.  Ustaw dekoratora **pozycji** właściwości. Więcej niż jeden dekorator może mieć taką samą pozycję. Na przykład można mieć ikony dla mężczyzn, a udostępnianie tej samej pozycji kobiet.

   3.  Ustaw **domyślna ikona** właściwość dekoratora ikony.

2. Wybierz mapowanie elementu diagramu, który jest szara linia między klasą kształt i klasy domeny na diagramem definicji DSL.

3. W oknie Szczegóły języka DSL w **mapy Dekoratora** , a następnie wybierz dekoratora. Na przykład MaleDecorator.

4. Sprawdź **filtr widoczności** pole.

5. Jeśli właściwość domeny, który należy kontrolować widoczność znajduje się w klasie natychmiastowego domeny, należy pozostawić **ścieżka do właściwości filtru** puste.

    W przeciwnym razie kliknij menu rozwijane i przejście do relacji lub klasy, w którym znajduje się właściwość.

   -   Aby uniknąć raport o błędzie, należy nie rozejrzysz się po relacji oznaczone "*" w narzędziu nawigacji.

6. Ustaw **właściwość filtra** z właściwością domeny. Na przykład płeć.

7. W **wpisy dotyczące widoczności** liście, Dodaj wartości tej właściwości domeny, dla którego powinny być widoczne dekoratora. Na przykład mężczyzn.

8. Powtórz kroki dla każdej ikony.

9. **Transformuj wszystkie szablony**, tworzenie i uruchamianie i Otwórz diagram testu.

10. Po zmianie wartości właściwości kontroli dekoratory powinien pojawiają się i znikają.

    Często mają widoczność kontrolowany przez formułę bardziej skomplikowane niż prosty zestaw wartości. Na przykład zawiera ikony są zależne od liczby łączy określonego typu lub ułatwiają są zależne od tego, i czy liczba jest w określonym zakresie. W takim przypadku należy użyć następującej procedury.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Można kontrolować widoczność dekoratora na podstawie formuły

1.  Dodaj właściwość domeny obliczeniowej do klasy domeny. W **właściwości** okna, ustaw następujące wartości:

     **IsBrowsable =**`False`**— spowoduje to ukrycie właściwości użytkownika**

     **Rodzaj =**`Calculated`**— oznacza to, że zapewni kod, który oblicza swoją wartość**

     **Nazwa** na przykład **DecoratorControl**

     **Typ** = `Boolean`

     Aby uzyskać więcej informacji, zobacz [obliczeniowe i niestandardowe właściwości przechowywania](../modeling/calculated-and-custom-storage-properties.md).

2.  Wprowadź nową właściwość kontrolować widoczność dekoratora.

    1.  Wybierz mapowanie elementu diagramu, czyli szara linia z klasy domeny, do kształtu. W **szczegóły języka DSL** otwarte okno **Mapa DecoratorMap** kartę.

    2.  Sprawdź **filtr widoczności** pole.

    3.  W **właściwość filtra**, wybierz właściwości kontrolki **DecoratorControl**.

    4.  W obszarze **wpisy dotyczące widoczności**, wprowadź `True`.

3.  Kliknij przycisk **Przekształć wszystkie szablony** w **Eksploratora rozwiązań** paska narzędzi.

4.  Kliknij przycisk **Kompiluj rozwiązanie** na **kompilacji** menu.

5.  Kliknij dwukrotnie raport o błędach, które pojawiły: "*YourClass* nie zawiera definicji GetDecoratorControlValue...".

     Zostanie otwarty Edytor tekstu Dsl\GeneratedCode\DomainClasses.cs. Powyższego błędu wyróżnionego jest komentarz, który użytkownik zostanie poproszony o dodanie metody.

6.  Należy pamiętać, przestrzeń nazw, klasy i metody, które są nieobecne.  For example, Company.FamilyTree.Person.GetDecoratorControlValue().

7.  W osobnym pliku kodu Napisz zawierającego metodę brakuje definicji klasy częściowej. Na przykład:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Aby uzyskać więcej informacji na temat Dostosowywanie modelu za pomocą kodu programu zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

8.  Ponownie skompiluj i uruchom rozwiązanie.

## <a name="see-also"></a>Zobacz też

- [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md)
- [Ustawienie obrazu tła w diagramie](../modeling/setting-a-background-image-on-a-diagram.md)
- [Nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Pisanie kodu pod kątem dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)