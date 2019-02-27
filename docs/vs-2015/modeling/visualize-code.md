---
title: Wizualizacja kodu | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- code, understanding
- code, visualizing
- code, exploring
ms.assetid: 0dd7d438-393a-4cd3-b417-9bf37379e1b0
caps.latest.revision: 49
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 2d5803544e4e7279179929c7c04a3792e4dd9318
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841672"
---
# <a name="visualize-code"></a>Tworzenie wizualizacji kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby pomóc Ci zrozumieć istniejący kod i opisać swoją aplikację, można użyć wizualizacji i modelowania narzędzi w programie Visual Studio. Dzięki temu możesz wzrokowo sprawdzić, jak Twoje zmiany mogą wpłynąć na kod i ocenić nakład pracy oraz zagrożenia związane z tymi zmianami. Na przykład:  
  
- Aby zrozumieć relacje w kodzie, mapować te relacje wizualnie.  
  
- Do opisywania architektury Twojego systemu i zachować zgodność kodu z projektem, tworzyć diagramy warstwowe, a następnie walidować kod dla tych diagramów.  
  
- Do opisania klasy, struktury, tworzenie diagramów klasy.  
  
- Aby modelować i komunikują się różnymi aspektami systemu, narysować diagramy modelowania UML (Unified Language). Można na przykład model, składników, typów, interakcji i procesów systemu.  
  
  Te narzędzia ułatwiają także łatwiejszą komunikację z osobami, które są związane z projektem. Na przykład służy diagramów klas UML do utworzenia wspólny słownik dyskusyjnym systemu z zainteresowanymi stronami projektu, użytkowników i członków zespołu.  
  
  Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdej funkcji, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
## <a name="what-do-you-want-to-do"></a>Co chcesz zrobić?  
  
|||  
|-|-|  
|**Poznaj kodu i jej relacje:**<br /><br /> Mapowanie relacji między określonych fragmentów kodu.<br /><br /> Zobacz Omówienie relacji w kodzie dla całego rozwiązania.<br /><br /> **Uwaga**: W tej wersji programu Visual Studio termin *mapy kodu* jest używana zamiast *wykres zależności*.|-   [Mapowanie zależności w ramach rozwiązań](../modeling/map-dependencies-across-your-solutions.md)<br />-   [Używanie map kodu do debugowania aplikacji](../modeling/use-code-maps-to-debug-your-applications.md)<br />-   [Wyszukiwanie potencjalnych problemów za pomocą analizatorów mapy kodu](../modeling/find-potential-problems-using-code-map-analyzers.md)<br />-   [Metody mapowania dla stosu wywołań podczas debugowania](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)|  
|**Zrozumienie struktury klasy:**<br /><br /> Umożliwia wizualizację struktury klas w projekcie, tworząc diagramów klas z kodu.|[Instrukcje: Dodawanie diagramów klas do projektu (Projektant klas)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md)|  
|**Opisz projektowania wysokiego poziomu systemu, a następnie walidować kod dla tego projektu:**<br /><br /> Opisz projektowania wysokiego poziomu systemu i jego zależności zamierzone, tworząc diagramów warstwowych. Walidować kod dla tego projektu, aby upewnić się, że zależności w kodzie zachować spójność z projektem.|-   [Tworzenie diagramów warstwy na podstawie kodu](../modeling/create-layer-diagrams-from-your-code.md)<br />-   [Diagramy warstw: Odwołanie](../modeling/layer-diagrams-reference.md)<br />-   [Diagramy warstw: Wytyczne dotyczące](../modeling/layer-diagrams-guidelines.md)<br />-   [Weryfikacja kodu przy użyciu diagramów warstw](../modeling/validate-code-with-layer-diagrams.md)|  
|**Komunikują się wymagania użytkownika i architektury:**<br /><br /> Modelowanie wymagań użytkowników i architektura systemu oprogramowania za pomocą rysowania na poniższych diagramach UML: działanie, składnika, klasy, sekwencja i przypadek użycia.|-   [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)<br />-   [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)<br />-   [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)|  
  
## <a name="external-resources"></a>Zasoby zewnętrzne  
  
|**Kategoria**|**Łącza**|  
|------------------|---------------|  
|**Fora**|-   [Program Visual Studio visualization and Modeling Tools](http://go.microsoft.com/fwlink/?LinkId=184720)<br />-   [Program Visual Studio visualization and Modeling SDK (narzędzia DSL)](http://go.microsoft.com/fwlink/?LinkId=184721)|  
|**Blogi**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|  
|**Artykuły techniczne i dzienniki**|[Forum MSDN poświęcone systemowi architektury](http://go.microsoft.com/fwlink/?LinkId=201343)|  
  
## <a name="see-also"></a>Zobacz też  
 [Scenariusz: Zmiana projektu z wykorzystaniem wizualizacji i modelowania](../modeling/scenario-change-your-design-using-visualization-and-modeling.md)   
 [Analizowanie i modelowanie architektury](../modeling/analyze-and-model-your-architecture.md)   
 [Tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md)   
 [Wymagania modelu użytkownika](../modeling/model-user-requirements.md)   
 [Modelowanie architektury aplikacji](../modeling/model-your-app-s-architecture.md)   
 [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
