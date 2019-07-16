---
title: Właściwości atrybutów w UML, diagramy klas | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 24575f125c07a016bef4742e010cbdd51f6c75e9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68154863"
---
# <a name="properties-of-attributes-on-uml-class-diagrams"></a>Właściwości atrybutów w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie klas UML, można dodać *atrybuty* do klasy i interfejsy. Atrybut definiuje wartości, które mogą być dołączane do wystąpienia klasy lub interfejsu.  

 Aby dodać atrybut, kliknij prawym przyciskiem myszy klasę lub interfejs, wskaż opcję **Dodaj**, a następnie kliknij przycisk **atrybutu**.  

 Jeśli atrybuty klasy na diagramie nie są widoczne, kliknij strzałkę w górnej części klasy lub interfejsu, aby ją rozwinąć. Jeśli widzisz **atrybuty** nagłówka, kliknij przycisk **[+]** aby rozwinąć sekcję atrybutów.  

## <a name="signature-of-an-attribute"></a>Podpis atrybutu  
 Podpis atrybutu jest wiersz, który reprezentuje go w klasę lub interfejs na diagramie klas UML. Ma postać:  

```  
+ AttributeName : TypeName [*]  
```  

 \+ Wskazuje, że publiczne widoczności. Dozwolone wartości to - (prywatny), # (chroniony) ~ (pakiet).  

 `AttributeName` jest podkreślone, jeśli ten atrybut jest statyczna.  

 `: TypeName` zostanie pominięty, jeśli ten atrybut nie ma typu.  

 `[*]` Wskazuje, że liczebności. Zostanie pominięta, jeśli liczebność jest 1.  

## <a name="properties"></a>Właściwości  
 W poniższej tabeli opisano właściwości atrybut w klasie lub interfejsie na diagramie klas UML.  

 Aby wyświetlić właściwości atrybutu, kliknij prawym przyciskiem myszy ten atrybut w klasie lub interfejsie na diagramie, a następnie kliknij przycisk **właściwości**. Właściwości są wyświetlane w oknie dialogowym właściwości.  

 Aby wyświetlić właściwości atrybutu, kliknij go prawym przyciskiem myszy, a następnie kliknij przycisk **właściwości**.  

|   **Property**    | **Default**  |                                                                                                                                                                                                         Opis                                                                                                                                                                                                          |
|-------------------|--------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Wartość domyślna** |   (pusty)    |                                                                                                                                                                               Wartość atrybutu podczas tworzenia wystąpienia klasyfikatora.                                                                                                                                                                                |
| **Jest tylko do odczytu**  |    False     |                                                                                                                                                                                    W przypadku opcji true, wartość atrybutu nie można zmienić.                                                                                                                                                                                    |
|   **Jest statyczny**   |    False     |                                                                                                                    W przypadku opcji true pojedynczą wartość dla tego atrybutu jest współużytkowana przez wszystkie wystąpienia tego typu.<br /><br /> W przypadku opcji true nazwa atrybutu jest podkreślone, gdzie się pojawia się na diagramie.                                                                                                                    |
|     **Nazwa**      | (Nowa nazwa) |                                                                                                                                                                                        Powinny być unikatowe w obrębie klasyfikatora będącej właścicielem.                                                                                                                                                                                        |
|     **Typ**      |    (Brak)    |                                                Typ pierwotny, takie jak **całkowitą**, lub typu, który jest zdefiniowany w modelu. Nie można użyć niepodstawowe typy, takie jak **dziesiętna** ponieważ wartości muszą być kodowane w metadanych. Jeśli wprowadzasz nazwę dla nowego typu w tej właściwości, typ zostanie dodany do **nieokreślonym** części Eksploratora modelu UML.                                                 |
|  **Widoczność**   |    Public    |                                     Dozwolone wartości i znaki, które są wyświetlane w podpisie są następujące:<br /><br /> **+ Publicznych** — jest to widoczne globalnie<br /><br /> **— Prywatny** — nie są widoczne poza typu, będącego właścicielem<br /><br /> **# Chronione** — widoczny dla typów pochodnych typu właściciela<br /><br /> **~ Pakietu** — są one widoczne dla innych typów, w tym samym pakiecie.                                      |
|  **Elementy robocze**   | skojarzone 0 |                                                                                                                          Liczba skojarzonych elementów roboczych. Tylko do odczytu.<br /><br /> Aby uzyskać więcej informacji, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).                                                                                                                           |
|    **Jest typu liść**    |    False     |                                                                                                                                                                    W przypadku opcji true go nie ma umożliwić ponowna definicja tego atrybutu w typach pochodnych.                                                                                                                                                                     |
|  **Jest tworzony**   |    False     |                                                                                                              W przypadku opcji true ten atrybut jest obliczany od innych atrybutów. Na przykład po przekątnej, obliczana na podstawie szerokości i wysokości. Szczegółowe informacje, należy napisać w **opis** lub dołączonego komentarza.                                                                                                              |
|  **Opis**  |   (pusty)    |                                                                                                                                                                        Aby uzyskać ogólne informacje o lub do definiowania ograniczeń na podstawie wartości w atrybucie.                                                                                                                                                                        |
| **Liczebność**  |      1       | **1** — ten atrybut ma pojedynczą wartość dla określonego typu.<br /><br /> **od 0 do 1** — ten atrybut może mieć wartość `null`.<br /><br /> **\\** \* -wartość tego atrybutu to zbiór wartości.<br /><br /> **1..\\**  \* — wartość tego atrybutu jest kolekcja, która zawiera co najmniej jedną wartość.<br /><br /> *n* **...** *m* — wartość tego atrybutu jest kolekcja, która zawiera między *n* i *m* wartości. |
|  **Jest uporządkowany**   |    False     |                                                                                                                                                                    W przypadku opcji true kolekcji formularzy uporządkowanej listy. Aby uzyskać **liczebność** więcej niż 1.                                                                                                                                                                     |
|   **Jest unikatowa**   |    False     |                                                                                                                                                                W przypadku opcji true istnieją zduplikowane wartości w kolekcji. Aby uzyskać **liczebność** więcej niż 1.                                                                                                                                                                |

## <a name="see-also"></a>Zobacz też  
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Właściwości typów w diagramach przypadków UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Właściwości operacji w diagramach przypadków UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)   
 [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)
