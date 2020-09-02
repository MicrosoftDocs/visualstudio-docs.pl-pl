---
title: Właściwości atrybutów w diagramach klas UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.logicalclassdiagram.attribute.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: ba01e064-7424-4e72-98fa-42fa1c30e153
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: de32eba5fc6e4afc21d62f4432d9317d85408ffd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652069"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Właściwości atrybutów w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie klas UML można dodawać *atrybuty* do klas i interfejsów. Atrybut definiuje wartości, które mogą być dołączane do wystąpień klasy lub interfejsu.

 Aby dodać atrybut, kliknij prawym przyciskiem myszy klasę lub interfejs, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **atrybut**.

 Jeśli atrybuty klasy na diagramie nie są widoczne, kliknij cudzysłów ostrokątny w górnej części klasy lub interfejsu, aby go rozwinąć. Jeśli widzisz nagłówek **atrybutów** , kliknij przycisk **[+]** , aby rozwinąć sekcję atrybuty.

## <a name="signature-of-an-attribute"></a>Podpis atrybutu
 Podpis atrybutu to linia, która reprezentuje ją w klasie lub interfejsie na diagramie klas UML. Ma to formę:

```
+ AttributeName : TypeName [*]
```

 \+ wskazuje publiczną widoczność. Inne dozwolone wartości to-(Private), # (Protected), ~ (Package).

 `AttributeName` jest podkreślony, jeśli atrybut jest statyczny.

 `: TypeName` jest pomijane, jeśli atrybut nie ma typu.

 `[*]` wskazuje liczebność. Zostanie pominięty, Jeśli liczebność wynosi 1.

## <a name="properties"></a>Właściwości
 W poniższej tabeli opisano właściwości atrybutu w klasie lub interfejsie na diagramie klas UML.

 Aby wyświetlić właściwości atrybutu, kliknij prawym przyciskiem myszy atrybut w klasie lub interfejsie na diagramie, a następnie kliknij przycisk **Właściwości**. Właściwości są wyświetlane w okno Właściwości.

 Aby wyświetlić właściwości atrybutu, kliknij go prawym przyciskiem myszy, a następnie kliknij polecenie **Właściwości**.

|   **Właściwość**    | **Wartooć**  |                                                                                                                                                                                                         Opis                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Wartość domyślna** |   ciągiem    |                                                                                                                                                                               Wartość atrybutu, gdy zostanie utworzone wystąpienie klasyfikatora.                                                                                                                                                                                |
| **Jest tylko do odczytu**  |    Fałsz     |                                                                                                                                                                                    W przypadku wartości true wartość atrybutu nie może być zmieniona.                                                                                                                                                                                    |
|   **Jest statyczny**   |    Fałsz     |                                                                                                                    W przypadku wartości true pojedyncza wartość tego atrybutu jest współdzielona między wszystkimi wystąpieniami tego typu.<br /><br /> Jeśli wartość jest równa true, nazwa atrybutu jest podkreślona, gdzie pojawia się na diagramie.                                                                                                                    |
|     **Nazwa**      | (Nowa nazwa) |                                                                                                                                                                                        Powinna być unikatowa w obrębie klasyfikatora będącego właścicielem.                                                                                                                                                                                        |
|     **Typ**      |    (brak)    |                                                Typ pierwotny, taki jak **Integer**lub typ, który jest zdefiniowany w modelu. Nie można użyć typów niepierwotnych, takich jak **Decimal** , ponieważ wartość musi być zakodowana w metadanych. W przypadku wprowadzenia nazwy nowego typu w tej właściwości, typ zostanie dodany do sekcji **nieokreślone typy** w EKSPLORATORZE modelu UML.                                                 |
|  **Widoczność**   |    Publiczne    |                                     Dozwolone wartości i znaki, które pojawiają się w podpisie, są następujące:<br /><br /> **I publicznie** widoczne globalnie<br /><br /> **-Private** -niewidoczny poza typem będącym właścicielem<br /><br /> **# Protected** -Visible do typów pochodzących od właściciela<br /><br /> **~ Pakiet** jest widoczny dla innych typów w tym samym pakiecie.                                      |
|  **Elementy robocze**   | 0 skojarzone |                                                                                                                          Liczba skojarzonych elementów roboczych. Tylko do odczytu.<br /><br /> Aby uzyskać więcej informacji, zobacz [łączenie elementów modelu i elementów roboczych](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Jest liściem**    |    Fałsz     |                                                                                                                                                                    Jeśli wartość jest równa true, nie ma zezwolenia na ponowną definicję tego atrybutu w typach pochodnych.                                                                                                                                                                     |
|  **Jest pochodny**   |    Fałsz     |                                                                                                              W przypadku wartości true ten atrybut jest obliczany na podstawie innych atrybutów. Na przykład ukośny, obliczony na podstawie szerokości i wysokości. Szczegóły powinny być zapisywane w **opisie** lub dołączonym komentarzu.                                                                                                              |
|  **Opis**  |   ciągiem    |                                                                                                                                                                        W przypadku notatek ogólnych lub do definiowania ograniczeń dotyczących wartości w atrybucie.                                                                                                                                                                        |
| **Kardynalność**  |      1       | **1** — ten atrybut ma pojedynczą wartość określonego typu.<br /><br /> **0.. 1** — ten atrybut może mieć wartość `null` .<br /><br /> **\\**\* -wartość tego atrybutu jest kolekcją wartości.<br /><br /> **1.. \\ ** \* — wartość tego atrybutu jest kolekcją zawierającą co najmniej jedną wartość.<br /><br /> *n* **..** *m* — wartość tego atrybutu jest kolekcją zawierającą między *n* i *m* wartościami. |
|  **Jest uporządkowany**   |    Fałsz     |                                                                                                                                                                    W przypadku wartości true kolekcja tworzy listę sekwencyjną. **Liczebność** większa niż 1.                                                                                                                                                                     |
|   **Jest unikatowy**   |    Fałsz     |                                                                                                                                                                W przypadku opcji true w kolekcji nie ma zduplikowanych wartości. **Liczebność** większa niż 1.                                                                                                                                                                |

## <a name="see-also"></a>Zobacz też
 [Diagramy klas UML: właściwości referencyjne](../modeling/uml-class-diagrams-reference.md) [typów na diagramach klas UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [właściwości operacji na](../modeling/properties-of-operations-on-uml-class-diagrams.md) diagramach klas UML diagramy [: wytyczne](../modeling/uml-class-diagrams-guidelines.md) [diagramy klas UML: wytyczne](../modeling/uml-class-diagrams-guidelines.md)
