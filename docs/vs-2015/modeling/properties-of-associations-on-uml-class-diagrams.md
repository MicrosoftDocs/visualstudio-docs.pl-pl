---
title: Właściwości skojarzeń w UML, diagramy klas | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.common.association.properties
helpviewer_keywords:
- UML, element properties
ms.assetid: f82bcd34-7903-4c00-8da1-613efa07d223
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a322ea68053012a2e8f53993f06768b966cb61d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54774567"
---
# <a name="properties-of-associations-on-uml-class-diagrams"></a>Właściwości skojarzeń w diagramach klas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Na diagramie klas UML można narysować *skojarzenia* między jakiejkolwiek parze typów. Typ jest klasą, interfejsem lub wyliczenia.  

 Skojarzenie wskazuje na tym, że system, które tworzysz przechowuje łącza pewnego rodzaju między wystąpieniami skojarzone typy. Ogólnie rzecz biorąc go nie oznacza niczego więcej o implementacji łącza. Na przykład mogą być wskaźniki wierszy w tabeli, zaktualizowana w informacjach odsyłaczy nazwy w formacie XML i tak dalej.  

 Asocjacja jest diagramowy metody przedstawiania atrybutu lub para atrybutów. Na przykład jeśli zdefiniowano klasy restauracja ma atrybut typu Menu można stanu tej samej definicji za pomocą rysowania skojarzenia między restauracji i Menu.  

 Aby narysować asocjację, kliknij przycisk **skojarzenia** w przyborniku, kliknij pierwszy typ, a następnie drugiego. Możesz kliknąć ten sam typ dwa razy, aby pokazać, że wystąpienia mogą być połączone z innymi wystąpieniami tego samego typu.  

## <a name="properties"></a>Właściwości  
 Są to właściwości asocjacji na diagramie klas UML.  

 Aby wyświetlić właściwości asocjacji, kliknij prawym przyciskiem myszy skojarzenia, a następnie kliknij przycisk **właściwości**. Właściwości będą wyświetlane w oknie dialogowym właściwości.  

 Niektóre właściwości są widoczne na diagramie, jak pokazano na poniższej ilustracji.  

 ![Właściwości w skojarzeniach](../modeling/media/uml-classprop.png "UML_ClassProp")  

|**Property**|Opis|  
|------------------|-----------------|  
|**Nazwa (1)**|Określa skojarzenie. Również pojawia się na diagramie, w pobliżu środka skojarzenia.|  
|**Kwalifikowana nazwa**|Jednoznacznie identyfikuje skojarzenia. Prefiks kwalifikowana nazwa pakietu, który zawiera roli pierwszego skojarzenia.|  
|**Elementy robocze**|Liczba elementów roboczych połączonych z tego skojarzenia. Łączenie elementów roboczych, zobacz [łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md).|  
|**Kolor**|Kolor łącznika. W przeciwieństwie do innych właściwości jest to właściwość tego widoku skojarzenia, nie właściwością podstawowego relacji w modelu.|  
|**Pierwsza rola**<br /><br /> **Druga rola**|Każdy koniec asocjacji nosi nazwę roli. Każda rola opisuje właściwości atrybutu równoważne na klasę na przeciwległym końcu asocjacji.<br /><br /> Na diagramie przykład skojarzenie elementu Menu i Menu ma role o nazwie Menu i zawartość.<br /><br /> Zawartość jest nazwa atrybutu dla klasy Menu.|  

### <a name="properties-of-each-role"></a>Właściwości każdej roli  
 Aby wyświetlić właściwości każdej roli, należy rozwinąć **pierwsza rola** lub **druga rola** właściwości.  


|     **Property**     |          **Default**          |                                                                                                                                                                                                                                                                                                                                        Opis                                                                                                                                                                                                                                                                                                                                         |
|----------------------|-------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|  **Nazwa roli (2)**   | Nazwa typu w tej roli |                                                                                                                                                                                                                                                                                                       Nazwa roli. Pojawi się w pobliżu końca asocjacji na diagramie.                                                                                                                                                                                                                                                                                                        |
|   **Agregacja**    |             Brak              |                                                                        **Brak** (4) — przedstawia ogólne relacja między wystąpieniami klas.<br /><br /> **Złożone** (5) — obiekt w tej roli zawiera obiekt pod rolę odwrotną. Możesz użyć **złożonego** narzędzie, aby utworzyć skojarzenie z złożonych agregacji.<br /><br /> **Udostępnione** [6] - obiektu w tej roli zawiera odwołania do obiektu w innej roli. Możesz użyć **agregacji** narzędzie, aby utworzyć skojarzenie z agregacją Shared.<br /><br /> Dokładne interpretacji jest otwarty do Konwencji lokalnego.                                                                         |
|    **Jest tworzony**    |             False             |                                                                                                                                                                                                                          W przypadku opcji true obiektu na końcu tego łącza jest obliczany od innych atrybuty i asocjacje. Na przykład MyWorkPlace obliczonym na podstawie MyEmployer.WorkPlace. Szczegółowe informacje, należy wpisać w opisie lub dołączonego komentarza.                                                                                                                                                                                                                           |
| **Jest pochodzących z Unii** |             False             |                                                                                                                                                                                                                                                                                                             W przypadku opcji true rola jest złożenie zestawu ról w typach pochodnych.                                                                                                                                                                                                                                                                                                             |
|   **Można nawigować**   |             Prawda              |                                                 Skojarzenie mogą być odczytywane w tym kierunku. Biorąc pod uwagę wystąpienie rolę odwrotną, oprogramowanie, które są opisujące efektywnie można określić skojarzonego wystąpienia w tej roli.<br /><br /> Jeśli jedna rola jest Navigable, a druga nie jest, strzałka pojawia się (7) na skojarzenie w kierunku można nawigować.<br /><br /> Domyślnie narzędzie skojarzenia tworzy skojarzenia, które można nawigować w jednym kierunku. Aby przekonwertować go na skojarzenie dwukierunkowy, można wybrać skojarzenie, kliknij tag akcji, który pojawia się, a następnie kliknij przycisk **wprowadzić dwukierunkowe**.                                                 |
|   **Jest tylko do odczytu**   |             False             |                                                                                                                                                                                                                                                                                   W przypadku opcji true wystąpienia skojarzenia nie można zmienić po jego utworzeniu. Łącze jest zawsze do tego samego obiektu.                                                                                                                                                                                                                                                                                    |
| **Element multiplicity (3)** |               1               | **1** — tym końcu asocjacji zawsze łączy się z jednego obiektu. Na rysunku każdy element Menu ma jedno Menu.<br /><br /> **od 0 do 1** — jedno to końcu asocjacji, który stanowi łącze do jednego obiektu lub nie ma żadnego połączenia.<br /><br /> **\\**\* — Każdy obiekt na drugim końcu skojarzenia jest połączony z kolekcji obiektów, w tym celu, a kolekcja może być pusta.<br /><br /> **1..\\**  \* — każdy obiekt na drugim końcu skojarzenia jest połączony z co najmniej jednego obiektu, w tym celu. Na rysunku każdego Menu ma co najmniej jeden element Menu.<br /><br /> *n* **...** *m* — każdy obiekt na drugim końcu ma kolekcję między *n* i *m* łączy do obiektów w tym celu. |
|    **Jest uporządkowany**    |             False             |                                                                                                                                                                                                                                                                                                  W przypadku opcji true zwrócona kolekcja formularzy uporządkowanej listy. Aby uzyskać liczebność jest większa niż 1.                                                                                                                                                                                                                                                                                                   |
|    **Jest unikatowa**     |             False             |                                                                                                                                                                                                                                                                                              W przypadku opcji true istnieją zduplikowane wartości w kolekcji zwrócone. Aby uzyskać liczebność jest większa niż 1.                                                                                                                                                                                                                                                                                              |
|    **Widoczność**    |            Public             |                                                                                                                                                                                                                                 Publiczny — widoczne globalnie<br /><br /> Prywatny — nie są widoczne poza typu, będącego właścicielem<br /><br /> Chronione - widoczna dla typów pochodnych typu właściciela<br /><br /> Pakiet — widoczne dla innych typów, w tym samym pakiecie.                                                                                                                                                                                                                                  |

## <a name="see-also"></a>Zobacz też  
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Właściwości typów w diagramach przypadków UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Właściwości atrybutów w diagramach przypadków UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Właściwości operacji w diagramach przypadków UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Diagramy klas UML: Wytyczne dotyczące](../modeling/uml-class-diagrams-guidelines.md)
