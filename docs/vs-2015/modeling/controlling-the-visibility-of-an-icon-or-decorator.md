---
title: Kontrolowanie widoczności ikony lub Dekoratora | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2697fd5d-b936-4b6b-b87b-be64825dc7a4
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 49cecff999e0155209ba58c20c0d623b15d63698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667827"
---
# <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub elementu Decorator
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Dekoratora* jest ikoną lub wierszem tekstu, który pojawia się na kształcie w języku specyficznym dla domeny (DSL). Można sprawić, aby dekoratora pojawiał się i znikał w zależności od stanu właściwości w modelu. Na przykład na kształcie reprezentującym osobę można mieć różne ikony, które są wyświetlane w zależności od płci osoby, liczby elementów podrzędnych itd.

## <a name="controlling-the-visibility-of-an-icon-or-decorator"></a>Kontrolowanie widoczności ikony lub Dekoratora
 W poniższej procedurze przyjęto założenie, że zdefiniowano już kształt i jego mapowanie na klasę domeny. Aby uzyskać więcej informacji, zobacz [jak zdefiniować język specyficzny dla domeny](../modeling/how-to-define-a-domain-specific-language.md).

#### <a name="to-control-the-visibility-of-an-icon-or-text-decorator"></a>Aby kontrolować widoczność ikony lub tekstu Dekoratora

1. Na diagramie definicji DSL Dodaj do klasy Shape ikon lub dekoratory tekstu, które mają być wyświetlane.

   1. Kliknij prawym przyciskiem myszy klasę Shape, wskaż polecenie **Dodaj**, a następnie kliknij wymagany typ dekoratora.

   2. Ustaw właściwość **Position** dekoratora. Więcej niż jeden dekoratora może mieć taką samą pozycję. Na przykład można mieć ikony dla wtyków i samic, które udostępniają te same pozycje.

   3. Ustaw **domyślną właściwość ikony** ikony dekoratora.

2. Wybierz mapę elementu diagramu, która jest szarą linią między klasą Shape i klasą domeny na diagramie definicji DSL.

3. W oknie Szczegóły DSL na karcie **mapy dekoratora** wybierz dekoratora. Na przykład MaleDecorator.

4. Zaznacz pole wyboru **Filtr widoczności** .

5. Jeśli właściwość domeny, która ma kontrolować widoczność, znajduje się w klasie bezpośredniej domeny, pozostaw pustą **ścieżkę do właściwości Filter** .

    W przeciwnym razie kliknij menu rozwijane i przejdź do relacji lub klasy, w której znajduje się właściwość.

   - Aby uniknąć raportu o błędach, nie należy nawigować przez relację oznaczoną przy użyciu znaku "*" w narzędziu do nawigacji.

6. Ustaw **Właściwość Filter** na właściwość domeny. Na przykład płci.

7. Na liście **wpisy widoczności** Dodaj wartości tej właściwości domeny, dla której dekoratora powinna być widoczna. Na przykład samce.

8. Powtórz kroki dla każdej ikony.

9. **Przekształć wszystkie szablony**, Kompiluj i Uruchom, a następnie Otwórz diagram testowy.

10. Gdy zmieniasz wartość właściwości kontrolki, dekoratory powinien pojawić się i znika.

    Często widoczność ma być kontrolowana przez bardziej złożoną formułę niż prosty zestaw wartości. Na przykład, aby ikona była zależna od liczby linków określonego typu lub zależała od tego, czy liczba znajduje się w określonym zakresie. W takim przypadku należy wykonać poniższą procedurę.

#### <a name="to-control-the-visibility-of-a-decorator-based-on-a-formula"></a>Aby kontrolować widoczność dekoratora na podstawie formuły

1. Dodaj właściwość domeny obliczeniowej do klasy domeny. W oknie **Właściwości** ustaw następujące wartości:

     **Jest przeglądalna =** `False` **— spowoduje to ukrycie właściwości użytkownika**    

     **Rodzaj =** `Calculated` **-oznacza to, że będzie można dostarczyć kod, który oblicza jego wartość**    

     **Nazwa** na przykład **DecoratorControl**

     **Wprowadź** = `Boolean`

     Aby uzyskać więcej informacji, zobacz [właściwości magazynu obliczeniowego i niestandardowego](../modeling/calculated-and-custom-storage-properties.md).

2. Ustaw nową właściwość na dekoratora widoczność.

    1. Wybierz mapę elementu diagramu, która jest szarym wierszem z klasy domeny do kształtu. W oknie **Szczegóły DSL** Otwórz kartę **Mapa DecoratorMap** .

    2. Zaznacz pole wyboru **Filtr widoczności** .

    3. W **Właściwości filtru**zaznacz właściwość **DecoratorControl**.

    4. W obszarze **wpisy widoczności**wprowadź `True` .

3. Kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.

4. Kliknij pozycję **Kompiluj rozwiązanie** w menu **kompilacja** .

5. Kliknij dwukrotnie raport o błędach, który pojawił się: "*YourClass* nie zawiera definicji dla GetDecoratorControlValue...".

     Edytor tekstu zostanie otwarty w Dsl\GeneratedCode\DomainClasses.cs. Nad wyróżnionym błędem jest komentarz, który żąda dodania metody.

6. Zanotuj brakującą przestrzeń nazw, klasę i metodę.  Na przykład firma. FamilyTree. Person. GetDecoratorControlValue ().

7. W osobnym pliku kodu Napisz częściową definicję klasy, która zawiera brakującą metodę. Na przykład:

    ```
    namespace Company.FamilyTree
    { partial class Person
      { bool GetDecoratorControlValue()
        {
          return this.Children.Count > 0;
    } } }
    ```

     Aby uzyskać więcej informacji na temat dostosowywania modelu przy użyciu kodu programu, zobacz [nawigowanie i aktualizowanie modelu w kodzie programu](../modeling/navigating-and-updating-a-model-in-program-code.md).

8. Skompiluj ponownie i uruchom rozwiązanie.

## <a name="see-also"></a>Zobacz też
 [Definiowanie kształtów i łączników](../modeling/defining-shapes-and-connectors.md) [Ustawianie obrazu tła na diagramie](../modeling/setting-a-background-image-on-a-diagram.md) [nawigowanie i aktualizowanie modelu w kodzie programowym](../modeling/navigating-and-updating-a-model-in-program-code.md) [pisanie kodu w celu dostosowywania języka specyficznego dla domeny](../modeling/writing-code-to-customise-a-domain-specific-language.md)
