---
title: Tworzenie modeli dla aplikacji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da86a6cf2e561fdc7e642a76b84b4e604bec12d6
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651241"
---
# <a name="create-models-for-your-app"></a>Tworzenie modeli aplikacji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagramy modelowania ułatwiają zrozumienie, wyjaśnienie i komunikowanie pomysłów dotyczących kodu oraz wymagań użytkownika, które musi obsługiwać system oprogramowania. Na przykład aby opisać i przekazać wymagania dotyczące użytkowników, można użyć UML (UML) diagramów przypadków użycia, działań, klas i sekwencji. Do opisywania i przekazywania funkcjonalności systemu można użyć diagramów składnika UML, klasy, działania i sekwencji.

 Zobacz [wideo Channel 9: ulepszanie architektury za pośrednictwem modelowania](http://go.microsoft.com/fwlink/?LinkID=252078).

 W tej wersji można utworzyć następujące diagramy UML:

|**4b**|**Pokazując**|
|-----------------|---------------|
|[Diagramy aktywności UML: informacje](../modeling/uml-activity-diagrams-reference.md)|Przepływ pracy między działaniami i uczestnikami w procesie biznesowym|
|[Diagramy składników UML: informacje](../modeling/uml-component-diagrams-reference.md)|Składniki systemu, ich interfejsy, porty i relacje|
|[Diagramy klas UML: informacje](../modeling/uml-class-diagrams-reference.md)|Typy, które są używane do przechowywania i wymiany danych w systemie i ich relacji|
|[Diagramy sekwencji UML: informacje](../modeling/uml-sequence-diagrams-reference.md)|Sekwencje interakcji między obiektami, składnikami, systemami lub aktorami|
|[Diagramy przypadków użycia UML: informacje](../modeling/uml-use-case-diagrams-reference.md)|Cele użytkownika i zadania obsługiwane przez system|

 Aby sprawdzić, które wersje programu Visual Studio obsługują poszczególne typy diagramów, zobacz temat [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Aby wizualizować architekturę systemu lub istniejącego kodu, Utwórz następujące diagramy:

|**4b**|**Pokazując**|
|-----------------|---------------|
|[Diagramy warstw: wskazówki](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Diagramy warstw: informacje](../modeling/layer-diagrams-reference.md)|Architektura wysokiego poziomu systemu|
|Mapy kodu<br /><br /> [Zależności mapy w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)|Zależności i inne relacje w istniejącym kodzie|
|Diagramy klas generowane przez kod<br /><br /> [Praca z diagramami klas (Projektant klas)](../ide/working-with-class-diagrams-class-designer.md)|Typy i ich relacje w kodzie .NET|

## <a name="common-tasks"></a>Typowe zadania

|**Rozdziału**|**Zadaniem**|
|---------------|--------------|
|[Tworzenie projektów i diagramów modelowania UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Tworzenie modeli** i Dodawanie diagramów.|
|[Edytowanie modeli i diagramów UML](../modeling/edit-uml-models-and-diagrams.md)|**Rysuj diagramy** , aby edytować model.|
|[Definiowanie pakietów i przestrzeni nazw](../modeling/define-packages-and-namespaces.md)|**Utwórz pakiety** , aby podzielić model na jednostki, na których mogą korzystać różne członków zespołu.|
|[Generowanie kodu na podstawie diagramów klas UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Generowanie C# kodu na podstawie diagramów klas** w celu uruchomienia implementacji.|
|[Dostosowywanie modelu za pomocą profili i stereotypów](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Dostosuj elementy modelu** przy użyciu stereotypów, aby zwiększyć standardowe elementy modelu UML do określonych celów.|
|[Łączenie elementów modeli i elementów roboczych](../modeling/link-model-elements-and-work-items.md)|**Utwórz linki między elementami modelu i elementami roboczymi** , aby ułatwić śledzenie zadań, przypadków testowych, usterek, wymagań, problemów lub innych rodzajów pracy, które są skojarzone z określonymi częściami modelu.|
|[Eksportowanie diagramów jako obrazów](../modeling/export-diagrams-as-images.md)|**Zapisz model i diagramy** , aby umożliwić udostępnianie ich innym użytkownikom, w tym tym, którzy nie używają [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].|

## <a name="related-tasks"></a>Powiązane zadania

|**Rozdziału**|**Zadaniem**|
|---------------|--------------|
|[Tworzenie wizualizacji kodu](../modeling/visualize-code.md)|Tworzenie map kodu i diagramów warstwowych w celu lepszego zrozumienia nieznanego kodu.|
|[Wymagania modelu użytkownika](../modeling/model-user-requirements.md)|Używaj modeli, aby wyjaśnić potrzeby użytkowników.|
|[Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|Używaj modeli, aby opisać ogólną strukturę i zachowanie systemu oraz upewnić się, że spełnia on potrzeby użytkowników.|
|[Weryfikacja systemu w czasie opracowywania](../modeling/validate-your-system-during-development.md)|Upewnij się, że oprogramowanie pozostaje spójne z potrzebami użytkowników i ogólną architekturą systemu.|
|[Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)<br /><br /> [Używanie modeli w programowaniu Agile](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Używaj modeli, aby pomóc w zrozumieniu i zmianie systemu podczas jego tworzenia.|
|[Tworzenie struktury rozwiązania modelowania](../modeling/structure-your-modeling-solution.md)|Organizuj modele w dużym lub średnim projekcie.|

## <a name="external-resources"></a>Zasoby zewnętrzne

|**Kategorii**|**Linki**|
|------------------|---------------|
|**Dotyczące**|-   [Wizualizacja programu Visual Studio & narzędzia do modelowania](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [wizualizacji programu Visual Studio & Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|
