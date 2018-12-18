---
title: Właściwości operacji w UML, diagramy klas | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.logicalclassdiagram.operation.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: 4128f3e2-3a51-4edf-b3e4-b7f170a32f6b
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 7a5a2e18c41f99462231da2a11dc80a0ae01e99e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51804480"
---
# <a name="properties-of-operations-on-uml-class-diagrams"></a>Właściwości operacji w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie klas UML, można dodać *operacji* do klasy i interfejsy. Operacja jest metodą albo funkcją, które mogą być wykonywane przez wystąpienie klasy lub interfejsu.  

 Aby dodać operację, kliknij prawym przyciskiem myszy klasę lub interfejs, wskaż opcję **Dodaj**, a następnie kliknij przycisk **operacji**.  

 Jeśli operacje w klasie na diagramie nie są widoczne, kliknij cudzysłów ostrokątny rozwijania u góry klasy lub interfejsu. Jeśli widzisz **operacji** nagłówka, kliknij przycisk **[+]** aby rozwinąć sekcję operacji.  

## <a name="signature-of-an-operation"></a>Podpis operacji  
 Podpis operacji jest wiersza tekstu, który reprezentuje go w klasę lub interfejs na diagramie klas UML. Ma następującą postać:  

 \+ OperationName (parameter1: Type1 [*],...): ReturnType [\*]  

 \+ Wskazuje, że publiczne widoczności. Dozwolone wartości to - (prywatny), # (chroniony) ~ (pakiet).  

 `OperationName` jest podkreślone, jeśli **Is Static** właściwość ma wartość true i jest pochylony Jeśli **jest abstrakcyjny** właściwość ma wartość true.  

 `: ReturnType` zostanie pominięty, jeśli nie zdefiniowano bez zwrotu typu.  

 `[*]` Wskazuje, że liczebność parametr lub zwracany typ. Zostanie pominięta, jeśli liczebność jest 1.  

 Zobacz następną sekcję, aby uzyskać pełny opis tych właściwości.  

## <a name="properties"></a>Właściwości  
 Są to właściwości operacji w klasie lub interfejsie na diagramie klas UML.  

 Aby wyświetlić właściwości operacji, kliknij prawym przyciskiem myszy działanie w klasie lub interfejsie na diagramie, a następnie kliknij przycisk **właściwości**. Właściwości są wyświetlane w **właściwości** okna.  


|      Właściwość       |   Domyślny    |                                                                                                                                                                                 Opis                                                                                                                                                                                 |
|---------------------|--------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      **Nazwa**       | (Nowa nazwa) |                                                                                                                                                                Powinny być unikatowe w obrębie typu zawierającego.                                                                                                                                                                 |
|   **Parametry**    |    (Brak)    |      Listę, która ma postać <em>nazwa</em>**:**<em>typu</em>**,** <em>nazwa</em>**:**  <em>Typ</em>**,...** Kliknij przycisk **[...]**  edytowanie listy.<br /><br /> Typy mogą być typy pierwotne oraz typy, które są zdefiniowane w modelu. Jeśli wprowadzasz nazwę dla nowego typu w tej właściwości, typ zostanie dodany do **nieokreślonym** części Eksploratora modelu UML.      |
|   **Zwracany typ**   |    (Brak)    |                                                                               **(Brak)** , lub typem pierwotnym lub typem, który jest zdefiniowany w modelu. Jeśli wprowadzasz nazwę dla nowego typu w tej właściwości, typ zostanie dodany do **nieokreślonym** części Eksploratora modelu UML.                                                                                |
| **Warunków końcowych**  |    (Brak)    |                                                                                                                         Opcjonalny warunek określający relację między stan systemu przed i po wykonaniu operacji.                                                                                                                         |
|  **Warunki wstępne**  |    (Brak)    |                                                                                                                            Opcjonalny warunek określający założeń dotyczących stanu systemu przed rozpoczęciem operacji rozpoczyna wykonywanie.                                                                                                                            |
| **Treść warunków** |    (Brak)    |                                                                                                                                                       Opcjonalne ograniczenia na podstawie wartości zwracanej przez operację.                                                                                                                                                       |
|   **Widoczność**    |    Public    |                  Dozwolone wartości i znaki, które są wyświetlane w podpisie są:<br /><br /> **+ Publicznych** — jest to widoczne globalnie<br /><br /> **— Prywatny** — nie są widoczne poza typu, będącego właścicielem<br /><br /> **# Chronione** — widoczny dla typów pochodnych typu właściciela<br /><br /> **~ Pakietu** — są one widoczne dla innych typów, w tym samym pakiecie.                   |
|    **Podpis**    |  +*Nazwa*)   |                                                                                      Zawiera podsumowanie widoczność, nazwę, parametry i typ zwracany tej operacji. Te właściwości można zmienić, edytując podpisu na diagramie, lub też edytując poszczególnych właściwości.                                                                                      |
|   **Elementy robocze**    | skojarzone 0 |                                                                                                  Liczba skojarzonych elementów roboczych. Tylko do odczytu.<br /><br /> Aby uzyskać więcej informacji, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).                                                                                                  |
|   **Współbieżność**   |  Sekwencyjne  | **Sekwencyjne** -operacji jest lub zostanie zaprojektowany bez kontroli współbieżności. Jednocześnie wywołaniem tej operacji może spowodować błędy.<br /><br /> **Chroniony** — operacja będzie automatycznie blokować ukończenie ma inne wystąpienia.<br /><br /> **Współbieżne** — operacja zaprojektowano tak, aby jednocześnie wykonać wiele wywołań do niego. |
|    **Jest statyczny**    |    False     |                                                                                                  W przypadku opcji true ta operacja jest współużytkowana przez wszystkie wystąpienia tego typu.<br /><br /> W przypadku opcji true Nazwa operacji zostanie podkreślone, gdzie się pojawia się na diagramie.                                                                                                   |
|   **Jest abstrakcyjna**   |    False     |                                                                                                                                        W przypadku opcji true nie jest skojarzona z tą operacją żaden kod. W związku z tym klasa będąca właścicielem jest abstrakcyjna.                                                                                                                                         |
|     **Jest typu liść**     |    False     |                                                                                                                                              Projektant zamierza się, że ta operacja nie może być zastąpiona w klasach pochodnych.                                                                                                                                              |
|    **Zapytanie**     |    False     |                                                                                                 W przypadku opcji true żadnych znaczących zmian stanu systemu są wprowadzone przez tę operację. Dlatego może służyć, na przykład w teście, aby sprawdzić stan systemu.                                                                                                  |
|  **Liczebność**   |      1       |                                 **1** -pojedynczą wartość dla określonego typu.<br /><br /> **od 0 do 1** — może być `null`.<br /><br /> \* -zbiór wartości dla określonego typu.<br /><br /> **1..\\**  \* — kolekcja zawierająca co najmniej jedną wartość.<br /><br /> *n* `..` *m* — zbierania, składającą się z `n` i `m` wartości.                                  |
|   **Jest uporządkowany**    |    False     |                                                                                                                                             W przypadku opcji true kolekcji formularzy uporządkowanej listy. Aby uzyskać **liczebność** więcej niż 1.                                                                                                                                              |
|    **Jest unikatowa**    |    False     |                                                                                                                                         W przypadku opcji true istnieją zduplikowane wartości w kolekcji. Aby uzyskać **liczebność** więcej niż 1.                                                                                                                                         |

## <a name="see-also"></a>Zobacz też  
 [Diagramy klas UML: odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Właściwości typów w diagramach przypadków UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Właściwości atrybutów w diagramach przypadków UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Właściwości skojarzeń w diagramach przypadków UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)   
 [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)



