---
title: 'Diagramy klas UML: Odwołanie | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4f3a4fe9949236045238688a9edcd5eef911efb8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51741066"
---
# <a name="uml-class-diagrams-reference"></a>Diagramy klas UML: Odwołanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagram klas UML w tym artykule opisano obiektu i informacje struktury używane przez aplikację, zarówno wewnętrznie, jak i komunikuje się z jej użytkowników. Opisano w nim informacji bez odwołania do konkretnej implementacji. Jego klas i relacji można zaimplementować na wiele sposobów, np. tabele bazy danych, węzłów XML lub kompozycje obiektów oprogramowania.  
  
> [!NOTE]
>  Ten temat dotyczy diagramów klas UML. Istnieje inny rodzaj diagramów klas, diagram klas platformy .NET, który jest używany w celu wizualizacji kodu programu. Aby uzyskać więcej informacji, zobacz [projektowanie i wyświetlanie klas i typów](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
 Aby utworzyć diagram klasy UML na **architektury** menu, wybierz **nowe UML lub diagramu warstwowego**. Aby uzyskać więcej informacji o tym, jak Rysowanie diagramów klas UML, zobacz [UML Class Diagrams: wskazówki dotyczące](../modeling/uml-class-diagrams-guidelines.md). Aby uzyskać więcej informacji o sposobie tworzenia i narysować diagramy modelowania, zobacz [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-class-diagrams"></a>Odczytywanie diagramów klas  
 W tabeli w tej sekcji opisano elementy, które są widoczne na diagramie klas UML. Aby uzyskać informacji na temat właściwości tych elementów zobacz następujące tematy:  
  
- [Właściwości typów w diagramach klas UML](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
- [Właściwości atrybutów w diagramach klas UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
- [Właściwości operacji w diagramach klas UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
- [Właściwości skojarzeń w diagramach klas UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
  ![Trzy klasy, właściwości i relacje przedstawiający](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
| **Kształt** |       **Element**        |                                                                                                                                                             **Opis**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Class**         |                                                           Definicja obiektów mających daną strukturalnych szczególnymi cechami strukturalnymi i. Aby uzyskać więcej informacji, zobacz [właściwości typów w UML, diagramy klas](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Klasyfikator        |                                                                                                             Nazwa głównej klasą, interfejsem lub wyliczenia. Aktorzy są także klasyfikatorów oraz składników, przypadków użycia.                                                                                                             |
|     2     | Zwiń / Rozwiń kontrolki |                                                                                         Jeśli nie można wyświetlić szczegóły klasyfikatora, kliknij przycisk ekspandera w lewym górnym rogu klasyfikatora. Może być również konieczne kliknij [+] w każdym segmencie.                                                                                         |
|     3     |      **Atrybut**       |   Wpisane wartości, dołączonych do każdego wystąpienia klasyfikatora.<br /><br /> Aby dodać atrybut, kliknij przycisk **atrybuty** sekcji, a następnie naciśnij klawisz **ENTER**. Typ podpisu atrybutu. Aby uzyskać więcej informacji, zobacz [właściwości atrybutów w UML, diagramy klas](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operacja**       | Metoda lub funkcja, która może zostać wykonana przez wystąpienia klasyfikatora. Aby dodać operację, kliknij przycisk **operacji** sekcji, a następnie naciśnij klawisz **ENTER**. Wpisz podpis wykonać operację. Aby uzyskać więcej informacji, zobacz [właściwości operacji w UML, diagramy klas](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Skojarzenie**      |                                                                  Relacja między członkami dwoma klasyfikatorami. Aby uzyskać więcej informacji, zobacz [właściwości skojarzeń w UML, diagramy klas](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Agregacja**      |                                                                                                    Skojarzenie reprezentująca relację wspólną własność. **Agregacji** roli właściciel jest właściwością **Shared**.                                                                                                     |
|    5b     |     **Kompozycja**      |                                                                                                      Skojarzenie ukazujące relacje reprezentujący. **Agregacji** roli właściciel jest właściwością **złożonego**.                                                                                                      |
|     6     |   **Nazwa skojarzenia**   |                                                                                                                                         Nazwa skojarzenia. Nazwa może być puste.                                                                                                                                          |
|     7     |      **Nazwa roli**       |                       Nazwa roli, oznacza to, co end elementu association. Może służyć do odwoływania się do skojarzonego obiektu. Na poprzedniej ilustracji dowolnej kolejności `O`, `O.ChosenMenu` jest jego skojarzonego Menu.<br /><br /> Każda rola ma własne właściwości wyświetlane w obszarze właściwości skojarzenia.                       |
|     8     |     **Liczebność**     |                                         Wskazuje liczbę obiektów w tym zakończenie może zostać powiązany z każdego obiektu na drugim. W przykładzie każde zamówienie muszą zostać połączone z dokładnie jedno Menu.<br /><br /> **\\**\* oznacza, że nie ma żadnego górnego limitu liczby łączy, które mogą być wykonane.                                         |
|     9     |    **Generalizacja**    |  *Określonych* Klasyfikator dziedziczy część jego definicji z *ogólne* klasyfikatora. Klasyfikatora ogólnego znajduje się na końcu strzałkę łącznika. Atrybuty, powiązania i operacje są dziedziczone przez dany klasyfikator.<br /><br /> Użyj **dziedziczenia** narzędzia do tworzenia generalizacji między dwoma klasyfikatorami.   |
  
 ![Pakiet zawierający wersję interfejsu i wyliczenie](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|Kształt|Element|Opis|  
|-----------|-------------|-----------------|  
|10|**Interface**|Definicja część widocznych zewnętrznych zachowań obiektu. Aby uzyskać więcej informacji, zobacz [właściwości typów w UML, diagramy klas](../modeling/properties-of-types-on-uml-class-diagrams.md).|  
|11|**Wyliczenie**|Klasyfikator, który zawiera zestaw wartości literałów.|  
|12|**Pakiet**|Grupa klasyfikatorów, skojarzeń, działania, linii życia, składników i pakietów. Diagram logiczny klasy pokazuje klasyfikatorów elementu członkowskiego i pakiety są zawarte w pakiecie.<br /><br /> Nazwy są ograniczone w ramach pakietów, aby **klasa1** w ramach **pakiet1** różni się od **klasa1** poza tym pakietem. Nazwa pakietu jest wyświetlany jako część **kwalifikowana nazwa** właściwości jego zawartość.<br /><br /> Możesz ustawić **połączone pakietu** właściwości dowolnego diagramu UML do odwoływania się do pakietu. Wszystkie elementy, które tworzysz na tym diagramie stanie się częścią pakietu. Pojawią się one w ramach pakietu w **Eksploratora modelu UML**.|  
|13|**Importujuj**|Relacja między pakietami, wskazujący, że jeden pakiet zawiera wszystkie definicje innego.|  
|14|**Zależności**|Definicja lub implementacji zależne klasyfikatora, mogą ulec zmianie po zmianie klasyfikatora na końcu grot strzałki.|  
  
 ![Realizacja pokazana z łącznikiem i lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|Kształt|**Element**|Opis|  
|-----------|-----------------|-----------------|  
|15|**Realizacja**|Klasa implementuje operacje i atrybuty zdefiniowane przez interfejs.<br /><br /> Użyj **dziedziczenia** narzędzia do tworzenia realizacja między klasą a interfejsem.|  
|16|**Realizacja**|Alternatywny sposób prezentacji tej samej relacji. Etykieta na symbol interfejsu typu lizak identyfikuje interfejs.<br /><br /> Aby utworzyć w tej prezentacji, wybierz istniejącą relację, która realizacji. Tag akcji pojawia się obok skojarzenia. Kliknij tag akcji, a następnie kliknij przycisk **Pokaż jako lizak**.|  
  
## <a name="see-also"></a>Zobacz też  
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy klas UML: wskazówki](../modeling/uml-class-diagrams-guidelines.md)   
 [Właściwości typów w diagramach przypadków UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Właściwości atrybutów w diagramach przypadków UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Właściwości operacji w diagramach przypadków UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Właściwości skojarzeń w diagramach klas UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)



