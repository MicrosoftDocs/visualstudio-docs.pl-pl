---
title: 'Diagramy przypadków użycia UML: Dokumentacja | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.usecasediagram.toolbox
- vs.teamarch.usecasediagram.diagram
- vs.teamarch.UMLModelExplorer.usecasediagram
helpviewer_keywords:
- diagrams - modeling, use case
- UML, use case diagrams
- diagrams - modeling, UML use case
- use case diagrams
- UML diagrams, use case
ms.assetid: aa15772b-eb67-4366-b145-b559112817df
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 256489e41c769452f9505f95ec64ec9aee853c67
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54777454"
---
# <a name="uml-use-case-diagrams-reference"></a>Diagramy przypadków użycia UML: Tematy pomocy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio *diagram przypadków użycia* znajduje się podsumowanie kto korzysta z aplikacji lub systemu i jak mogą one korzystają z nich. Aby utworzyć diagram przypadków użycia UML, na **architektury** menu, kliknij przycisk **nowe UML lub diagramu warstwowego**.  
  
 Diagram przypadków użycia działa jako fokus do opisu wymagań użytkownika. Przedstawia ona relacje między wymaganiami, użytkowników i główne składniki. Nie opisano wymagania, które szczegółowo; mogą one opisane w oddzielnym diagramie lub w dokumentach, które mogą być połączone z poszczególnymi przypadkami użycia. Aby dowiedzieć się, jak jak diagramy przypadków użycia może pomóc zrozumieć, omawianiu i komunikowaniu potrzeb użytkowników, zobacz [modelowanie wymagań użytkowników](../modeling/model-user-requirements.md).  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługuje tę funkcję, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
> [!NOTE]
>  W tym temacie opisano elementy, które są dostępne w diagramy przypadków użycia. Aby uzyskać więcej informacji na temat narysować diagramy przypadków użycia, zobacz [diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md). Aby uzyskać więcej informacji o sposobie tworzenia i narysować diagramy modelowania, zobacz [modeli i diagramów UML Edytuj](../modeling/edit-uml-models-and-diagrams.md).  
  
## <a name="reading-use-case-diagrams"></a>Diagramy przypadków użycia odczytu  
 W tabelach w poniższych sekcjach opisano elementy, które są dostępne na diagramie przypadku użycia wraz z ich właściwości głównego. Aby uzyskać pełną listę właściwości, zobacz [właściwości elementów na UML, diagramy przypadków użycia](../modeling/properties-of-elements-on-uml-use-case-diagrams.md).  
  
### <a name="actors-use-cases-and-subsystems"></a>Aktorów, przypadki użycia i podsystemów  
 ![Elementy na diagramie przypadku użycia](../modeling/media/uml-ucovactor.png "UML_UCOvActor")  
  
|**Kształt**|**Element**|**Opis i właściwości głównego**|  
|---------------|-----------------|-----------------------------------------|  
|1|**aktora**|Reprezentuje użytkownika, organizacji lub systemu zewnętrznego, który współdziała z aplikacji lub systemu. Aktor to rodzaj typu.<br /><br /> -   **Ścieżka obrazu** — ścieżka pliku obrazu, które mają być używane zamiast domyślnej ikony aktora. Ikona powinna być plik zasobów w ramach projektu programu Visual Studio.|  
|2|**Przypadek użycia**|Reprezentuje akcje wykonywane przez jeden lub więcej podmiotów zgodnie z określonym celem. Przypadek użycia to rodzaj typu.<br /><br /> -   **Przedmioty** -podsystemu, w której znajduje się w przypadku użycia.|  
|3|**Skojarzenie**|Wskazuje, że aktor bierze udział w przypadku użycia.|  
|4|**Podsystem lub składnika**|System lub aplikację, która pracujesz nad lub jej część. Może to być dowolna z dużych sieci do jednej klasy w aplikacji.<br /><br /> Przypadki użycia, obsługiwanych przez system lub składnika pojawiają się wewnątrz jego prostokąta. Może być przydatne pokazać, że niektóre przypadki użycia poza prostokąt, wyjaśnienie zakresu systemu.<br /><br /> Podsystem na diagramie przypadków użycia ma zasadniczo taki sam typ co składnik na diagramie składników.<br /><br /> -   **To wystąpienie utworzono pośrednio** — Jeśli "false", wykonywanie system ma jedną lub więcej obiektów, który bezpośrednio odpowiadają do ten podsystem. W przypadku opcji true podsystemu jest konstrukcja w projekcie, który pojawia się w systemie wykonywanie tylko za pośrednictwem wystąpienia jego elementów składowych.|  
  
### <a name="structuring-use-cases"></a>Tworzenie struktury przypadki użycia  
 ![Przypadki użycia z include, rozszerzania i generalizacji](../modeling/media/uml-ucovstructure.png "UML_UCOvStructure")  
  
|Kształt|**Element**|Opis|  
|-----------|-----------------|-----------------|  
|5|**Obejmują**|Tym przypadek użycia wywołuje lub wywołuje jeden dołączony. Włączenie służy do pokazywania, jak przypadek użycia dzieli się na mniejsze kroki. Przypadek użycia uwzględniona znajduje się na końcu grot strzałki.<br /><br /> Zwróć uwagę, diagram nie wyświetla kolejność kroków. Diagram aktywności, diagram sekwencji lub innego dokumentu służy do opisywania te szczegóły.|  
|6|**Rozszerzanie**|Rozszerzanie przypadek użycia dodaje cele i kroki do przypadku rozszerzonego użycia. Rozszerzenia działają tylko w określonych warunkach. Przypadek użycia rozszerzonych znajduje się na końcu grot strzałki.<br /><br /> Należy zauważyć, że diagram nie są wyświetlane dokładne okoliczności, w których jest stosowana przez rozszerzenie: można zarejestrować je w komentarz lub innego dokumentu.|  
|7|**Dziedziczenie**|Odnosi się wyspecjalizowanych i uogólnionego elementu. Element uogólnionego znajduje się na końcu grot strzałki.<br /><br /> Przypadek użycia wyspecjalizowane dziedziczy cele i aktorami jego Generalizacja i może dodać dokładniejszą cele i kroki do osiągnięcia je.<br /><br /> Wyspecjalizowane aktora dziedziczy przypadki użycia, atrybuty i powiązania jej generalizacji i dodać więcej.|  
|8|**Zależności**|Wskazuje, że projekt źródłowy zależy od projektu docelowego.|  
|9|**Komentarz**|Służy do dodawania notatek do diagramu.|  
|10|**Artefakt**|Artefakt zawiera również link do innego diagramu lub dokumentu. Można go utworzyć, przeciągając plik z Eksploratora rozwiązań. Może być połączony z zależnością do innego elementu na diagramie. Artefakt jest zazwyczaj używany do Łączenie przypadków użycia do diagramu sekwencji, strony programu OneNote, dokument programu Word lub prezentacji programu PowerPoint, który ją opisuje szczegółowo. Dokumentu mogą być element [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania lub dokument w lokalizacji udostępnionej, takich jak witryny programu SharePoint.<br /><br /> -   **Hiperłącze**. Ścieżka adresu URL lub pliku diagramu lub dokumentu.<br /><br /> Kliknij dwukrotnie artefaktu do otwarcia pliku lub strony sieci web, która łączy.|  
|11 (niewyświetlany)|**Pakiety**|Przypadki użycia, aktorów i podsystemów mogą być zawarte w ramach pakietów. Kształty pakietu nie są wyświetlane na diagramie, ale możesz ustawić **LinkedPackage** właściwości diagramu. Elementy, które utworzysz w diagramie są umieszczane w pakiecie. Aby uzyskać więcej informacji, zobacz [Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md).|  
  
## <a name="see-also"></a>Zobacz też  
 [Diagramy przypadków użycia UML: Wytyczne dotyczące](../modeling/uml-use-case-diagrams-guidelines.md)   
 [Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagramy sekwencji UML: Odwołanie](../modeling/uml-sequence-diagrams-reference.md)   
 [Diagramy klas UML: Odwołanie](../modeling/uml-class-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)   
 [Diagramy składników UML: Odwołanie](../modeling/uml-component-diagrams-reference.md)
