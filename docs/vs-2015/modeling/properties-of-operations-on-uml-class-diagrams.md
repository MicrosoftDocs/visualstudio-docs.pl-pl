---
title: Właściwości operacji w diagramach klas UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d752fa802deef5dcc40fdfa4d762dc6edb1d0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671349"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Właściwości operacji w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie klas UML można dodać *operacje* do klas i interfejsów. Operacja to metoda lub funkcja, która może być wykonywana przez wystąpienie klasy lub interfejsu.

 Aby dodać operację, kliknij prawym przyciskiem myszy klasę lub interfejs, wskaż polecenie **Dodaj**, a następnie kliknij przycisk **operacji**.

 Jeśli operacje klasy na diagramie nie są widoczne, kliknij przycisk Rozwiń podwójną w górnej części klasy lub interfejsu. Jeśli widzisz nagłówek **operacji** , kliknij przycisk **[+]** , aby rozwinąć sekcję operacje.

## <a name="signature-of-an-operation"></a>Podpis operacji
 Podpis operacji jest wierszem tekstu, który reprezentuje go w klasie lub interfejsie na diagramie klas UML. Ma następującą postać:

 \+ OperationName (parametr1: Type1 [*],...): ReturnType [ \* ]

 \+ wskazuje publiczną widoczność. Inne dozwolone wartości to-(Private), # (Protected), ~ (Package).

 `OperationName` jest podkreślony, jeśli właściwość **is static** ma wartość true, a kursywa, jeśli właściwość **jest abstrakcyjna** ma wartość true.

 `: ReturnType` jest pomijany, jeśli nie zdefiniowano typu zwracanego.

 `[*]` wskazuje liczebność parametru lub zwracanego typu. Zostanie pominięty, Jeśli liczebność wynosi 1.

 Zobacz następną sekcję, aby zapoznać się z pełnymi opisami tych właściwości.

## <a name="properties"></a>Właściwości
 Są to właściwości operacji w klasie lub interfejsie na diagramie klas UML.

 Aby wyświetlić właściwości operacji, kliknij prawym przyciskiem myszy operację w klasie lub interfejsie na diagramie, a następnie kliknij polecenie **Właściwości**. Właściwości są wyświetlane w oknie **Właściwości** .

|      Właściwość       |   Domyślne    |                                                                                                                                                                                 Opis                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Nazwa**       | (Nowa nazwa) |                                                                                                                                                                Musi być unikatowa w obrębie typu zawierającego.                                                                                                                                                                 |
|   **Parametry**    |    (brak)    |      Lista o <em>nazwie</em>**formularza:**<em>wpisz</em>**,** <em>name</em>**:**<em>Type</em>**,....** Kliknij przycisk **[...]** , aby edytować listę.<br /><br /> Typy mogą być typami pierwotnymi lub typami, które są zdefiniowane w modelu. W przypadku wprowadzenia nazwy nowego typu w tej właściwości, typ zostanie dodany do sekcji **nieokreślone typy** w EKSPLORATORZE modelu UML.      |
|   **Typ zwracany**   |    (brak)    |                                                                               **(brak)** lub typ pierwotny lub typ, który jest zdefiniowany w modelu. W przypadku wprowadzenia nazwy nowego typu w tej właściwości, typ zostanie dodany do sekcji **nieokreślone typy** w EKSPLORATORZE modelu UML.                                                                                |
| **Warunki końcowe**  |    (brak)    |                                                                                                                         Opcjonalny warunek określający relację między stanem systemu przed i po wykonaniu operacji.                                                                                                                         |
|  **Warunki wstępne**  |    (brak)    |                                                                                                                            Opcjonalny warunek określający założenia stanu systemu przed rozpoczęciem wykonywania operacji.                                                                                                                            |
| **Warunki treści** |    (brak)    |                                                                                                                                                       Opcjonalne ograniczenie wartości zwracanych przez operację.                                                                                                                                                       |
|   **Widoczność**    |    Publiczne    |                  Dozwolone wartości i znaki, które pojawiają się w podpisie:<br /><br /> **I publicznie** widoczne globalnie<br /><br /> **-Private** -niewidoczny poza typem będącym właścicielem<br /><br /> **# Protected** -Visible do typów pochodzących od właściciela<br /><br /> **~ Pakiet** jest widoczny dla innych typów w tym samym pakiecie.                   |
|    **Podpis**    |  +*Nazwa*()   |                                                                                      Podsumowuje widoczność, nazwę, parametry i zwracany typ tej operacji. Te właściwości można zmienić, edytując podpis na diagramie lub edytując poszczególne właściwości.                                                                                      |
|   **Elementy robocze**    | 0 skojarzone |                                                                                                  Liczba skojarzonych elementów roboczych. Tylko do odczytu.<br /><br /> Aby uzyskać więcej informacji, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Współbieżność**   |  Sekwencyjny  | **Sekwencyjnie** — operacja jest lub zostanie zaprojektowana bez kontroli współbieżności. Wywołanie tej operacji współbieżnie może spowodować błędy.<br /><br /> **Chroniona** — operacja zostanie automatycznie zablokowana do momentu ukończenia innych wystąpień.<br /><br /> **Współbieżne** — operacja jest zaprojektowana tak, aby wiele wywołań było wykonywanych jednocześnie. |
|    **Jest statyczny**    |    Fałsz     |                                                                                                  W przypadku wartości true ta operacja jest udostępniana między wszystkimi wystąpieniami tego typu.<br /><br /> Jeśli wartość jest równa true, nazwa operacji zostanie podkreślona, gdzie pojawia się na diagramie.                                                                                                   |
|   **Jest abstrakcyjny**   |    Fałsz     |                                                                                                                                        Jeśli wartość jest równa true, żaden kod nie jest skojarzony z tą operacją. W związku z tym Klasa będąca właścicielem jest abstrakcyjna.                                                                                                                                         |
|     **Jest liściem**     |    Fałsz     |                                                                                                                                              Projektant zaplanuje, że tej operacji nie można zastąpić w klasach pochodnych.                                                                                                                                              |
|    **Jest kwerendą**     |    Fałsz     |                                                                                                 W przypadku wartości true ta operacja nie powoduje wprowadzenia znaczących zmian stanu systemu. W związku z tym można go użyć na przykład w teście w celu sprawdzenia stanu systemu.                                                                                                  |
|  **Kardynalność**   |      1       |                                 **1** — pojedyncza wartość określonego typu.<br /><br /> **0.. 1** — może być `null` .<br /><br /> \* -Kolekcja wartości określonego typu.<br /><br /> **1.. \\ ** \* -Kolekcja zawierająca co najmniej jedną wartość.<br /><br /> *n* `..` *m* -Kolekcja zawierająca między `n` i `m` wartościami.                                  |
|   **Jest uporządkowany**    |    Fałsz     |                                                                                                                                             W przypadku wartości true kolekcja tworzy listę sekwencyjną. **Liczebność** jest większa niż 1.                                                                                                                                              |
|    **Jest unikatowy**    |    Fałsz     |                                                                                                                                         W przypadku opcji true w kolekcji nie ma zduplikowanych wartości. **Liczebność** jest większa niż 1.                                                                                                                                         |

## <a name="see-also"></a>Zobacz też
 [Diagramy klas UML: właściwości odwołania](../modeling/uml-class-diagrams-reference.md) [typów na diagramach klas](../modeling/properties-of-types-on-uml-class-diagrams.md) UML [właściwości atrybutów w](../modeling/properties-of-attributes-on-uml-class-diagrams.md) diagramach klas UML [właściwości skojarzenia na diagramach](../modeling/properties-of-associations-on-uml-class-diagrams.md) klas UML [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md)
