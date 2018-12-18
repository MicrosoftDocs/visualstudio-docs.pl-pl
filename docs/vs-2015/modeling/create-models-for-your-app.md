---
title: Tworzenie modeli aplikacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-techdebt
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 9e3aa389441914121493148ecb8fa45b9f86beed
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51745126"
---
# <a name="create-models-for-your-app"></a>Tworzenie modeli aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagramy modelowania pomagają zrozumieć, objaśnić i przedstawić istotę kodu oraz wymagania użytkowników, które Twój system oprogramowania musi obsługiwać. Na przykład do opisywania i przedstawiania wymagań użytkownika, można użyć przypadek użycia języka UML (Unified Modeling), działanie, klas i diagramów sekwencji. Do opisywania i przedstawiania funkcji Twojego systemu, można użyć składnika, klasa, działanie i diagramy sekwencji UML.  
  
 Zobacz [wideo Channel 9: poprawa architektury poprzez modelowanie](http://go.microsoft.com/fwlink/?LinkID=252078).  
  
 Można utworzyć następujące diagramy UML w tej wersji:  
  
|**Diagram**|**Pokazuje**|  
|-----------------|---------------|  
|[Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)|Przepływ pracy między działaniami i uczestników procesu biznesowego|  
|[Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)|Składniki systemu, ich interfejsy, portów i relacji|  
|[Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)|Typy, które są używane do przechowywania i wymiany danych w systemie oraz ich wzajemne relacje|  
|[Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)|Sekwencje interakcje między obiektów, składniki, systemów i aktorów|  
|[Diagramy przypadków użycia UML: informacje](../modeling/uml-use-case-diagrams-reference.md)|Cele użytkowników i zadań, które obsługuje system|  
  
 Aby zobaczyć, które wersje programu Visual Studio obsługi każdego typu diagramu, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Aby zwizualizować architektury systemu lub istniejącego kodu, należy utworzyć następujące diagramy:  
  
|**Diagram**|**Pokazuje**|  
|-----------------|---------------|  
|[Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)|Architektura wysokiego poziomu systemu|  
|Mapy kodu<br /><br /> [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)|Zależności i inne relacje w istniejącym kodzie|  
|Diagramy klas wygenerowany kod<br /><br /> [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md)|Typy i ich relacje w kodzie .NET|  
  
## <a name="common-tasks"></a>Typowe zadania  
  
|**Temat**|**Zadanie**|  
|---------------|--------------|  
|[Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Tworzenie modeli** i dodawanie diagramów.|  
|[Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)|**Rysowanie diagramów** edytowanie modelu.|  
|[Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md)|**Tworzenie pakietów** zostać podzielona modelu jednostek, które różni członkowie zespołu mogą pracować na.|  
|[Generowanie kodu na podstawie diagramów klas UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Generowanie kodu w języku C# na podstawie diagramów klas** można uruchomić implementacji.|  
|[Dostosowywanie modelu za pomocą profili i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Dostosowywanie elementów modelu** przy użyciu stereotypów, aby rozszerzyć standardowych elementów modelu UML do określonych celów.|  
|[Łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md)|**Tworzenie łączy między elementami modelu i elementami roboczymi** ułatwiające śledzenie zadań, przypadków testowych, usterek, wymagań, problemów lub innych rodzajów pracy, które są skojarzone z określonymi częściami modelu.|  
|[Eksportowanie diagramów jako obrazów](../modeling/export-diagrams-as-images.md)|**Zapisz swoją modeli i diagramów** tak, aby można je udostępnić innym użytkownikom, włącznie z tymi, którzy nie korzystają z [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|  
  
## <a name="related-tasks"></a>Informacje o zadaniach pokrewnych  
  
|**Temat**|**Zadanie**|  
|---------------|--------------|  
|[Tworzenie wizualizacji kodu](../modeling/visualize-code.md)|Tworzenie map kodu i diagramy warstwowe, aby lepiej zrozumieć nieznanego kodu.|  
|[Wymagania modelu użytkownika](../modeling/model-user-requirements.md)|Używanie modeli uściślenia i komunikują się potrzeby użytkowników.|  
|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|Używanie modeli do opisania ogólną strukturę i zachowanie systemu i upewnij się, że spełnia potrzeby użytkowników.|  
|[Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)|Upewnij się, że oprogramowanie pozostaje zgodny z potrzebami użytkowników i ogólną architekturę systemu.|  
|[Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)<br /><br /> [Używaj modeli w Agile development](http://msdn.microsoft.com/en-us/592ac27c-3d3e-454a-9c38-b76658ed137f)|Używanie modeli, aby pomóc Ci zrozumieć i zmienić systemu podczas jego tworzenia.|  
|[Tworzenie struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)|Organizowania modeli w dużych i średnich projektu.|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
|**Kategoria**|**Łącza**|  
|------------------|---------------|  
|**Fora**|-   [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|



