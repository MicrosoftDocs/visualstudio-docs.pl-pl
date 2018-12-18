---
title: Typ funkcji według aplikacji pakietu Office i projekt
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio]
- Office development in Visual Studio, features
- Ribbon [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], features available
- document-level customizations [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], features available
- add-ins [Office development in Visual Studio]
- form regions [Office development in Visual Studio], features available
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6fac14df471b0dfcda1d0bf4763158280211bc33
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50672469"
---
# <a name="features-available-by-office-application-and-project-type"></a>Typ funkcji według aplikacji pakietu Office i projekt
  Program Visual Studio zawiera kilka typów szablonów projektu obsługi różnych scenariuszy biznesowych aplikacji pakietu Microsoft Office, w tym następujących typów:  
  
- Dostosowania poziomu dokumentu.  
  
- Dodatków narzędzi VSTO.  
  
  Nie wszystkie aplikacje mogą używać każdego typu projektu. Na przykład projektów na poziomie dokumentu są dostępne tylko dla programu Microsoft Office Word i Microsoft Office Excel. Podobnie niektóre funkcje są dostępne tylko dla niektórych typów projektów lub aplikacji. Na przykład w okienku Akcje jest dostępna tylko w projektach na poziomie dokumentu i wstążki rozszerzenia są dostępne tylko dla niektórych aplikacji. Aby uzyskać więcej informacji o różnych typach projektów, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
> [!NOTE]  
>  Szablony projektów pakietu Office są dostępne tylko w niektórych wersjach [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]. Aby uzyskać więcej informacji, zobacz [Konfigurowanie komputera do opracowywania rozwiązań pakietu Office](../vsto/configuring-a-computer-to-develop-office-solutions.md).  
  
## <a name="project-types-available-for-different-microsoft-office-applications"></a>Typy projektów dostępnych w innej aplikacji pakietu Microsoft Office  
 W poniższej tabeli przedstawiono aplikacje korzystające z każdym typem projektu.  
  
|Typy projektów|Aplikacja Microsoft Office|  
|-------------------|----------------------------------|  
|Dostosowania na poziomie dokumentów|Excel<br /><br /> Word|  
|Dodatków narzędzi VSTO|Excel<br /><br /> InfoPath (InfoPath 2013 i InfoPath 2010)<br /><br /> Outlook<br /><br /> PowerPoint<br /><br /> Projekt<br /><br /> Visio<br /><br /> Word<br /><br /> Excel|  
  
## <a name="features-available-in-different-project-types"></a>Funkcje dostępne w różnych typach projektów  
 Poniższej tabeli przedstawiono, które typy projektów zapewniają każdej funkcji.  
  
|Funkcja|Typów projektów, które zapewnia tę funkcję|Dalsze informacje|  
|-------------|--------------------------------------------|---------------------|  
|W okienku Akcje.|Projektów na poziomie dokumentu.|[Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)|  
|Wdrożenie ClickOnce.|VS i projektów na poziomie dokumentu.|[Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)|  
|Niestandardowe okienka zadań.|Dodatek projektów VSTO dla następujących aplikacji:<br /><br /> — Excel<br />-Program InfoPath (InfoPath 2013 i InfoPath 2010)<br />-Programu outlook<br />— PowerPoint<br />-Programu Word|[Niestandardowe okienka zadań](../vsto/custom-task-panes.md)|  
|Niestandardowe elementy XML.|Projektów na poziomie dokumentu.<br /><br /> Poziomu projektów aplikacji dla następujących aplikacji:<br /><br /> — Excel<br />— PowerPoint<br />-Programu Word|[Niestandardowe części XML ― omówienie](../vsto/custom-xml-parts-overview.md)|  
|Pamięć podręczna danych.|Projektów na poziomie dokumentu.|[Dane w pamięci podręcznej dostosowywane na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)|  
|Udostępnianie obiektu w dodatku narzędzi VSTO dla programów do innych rozwiązań programu Microsoft Office.|Dodatek projekty VSTO.|[Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)|  
|Następujące kontrolki hosta:<br /><br /> -Wykresu<br />— ListObject<br />-NamedRange<br />-Zawartość kontrolki<br />-Zakładki|Projektów na poziomie dokumentu.<br /><br /> Dodatek projektów VSTO dla programów Word i Excel.|[Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)|  
|Następujące kontrolki hosta:<br /><br /> — XMLMappedRange<br />-XMLNode<br />-XMLNodes|Projektów na poziomie dokumentu.|[Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)|  
|Wdrażanie wielu projektów.|Projektów na poziomie dokumentu.<br /><br /> Dodatek projekty VSTO.|[Przewodnik: Wdrażanie wielu rozwiązań pakietu Office w jednym Instalatorze ClickOnce](https://msdn.microsoft.com/051223c0-4082-4799-b78b-a4763a9def55)|  
|Regionach formularzy programu Outlook.|Dodatek projektów VSTO dla programu Outlook.|[Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)|  
|Akcje po wdrożeniu.|Projektów na poziomie dokumentu.<br /><br /> Dodatek projekty VSTO.|[Wskazówki: Kopiowanie dokumentu do komputera użytkownika końcowego po zakończeniu instalacji ClickOnce](https://msdn.microsoft.com/100090f7-bc63-4152-b3e1-19b48bc27466)|  
|Dostosowywanie Wstążki.|Projektów na poziomie dokumentu.<br /><br /> Dodatek projektów VSTO dla następujących aplikacji:<br /><br /> — Excel<br />-Program InfoPath (InfoPath 2013 i InfoPath 2010)<br />-Programu outlook<br />— PowerPoint<br />-Projekt<br />-Programu Visio<br />-Programu Word|[Wstążka — omówienie](../vsto/ribbon-overview.md)|  
|Projektant wizualny dokumentu.|Projektów na poziomie dokumentu.|[Projekty pakietu Office w środowisku Visual Studio](../vsto/office-projects-in-the-visual-studio-environment.md)|  
  
## <a name="see-also"></a>Zobacz także  
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Okienko akcji ― omówienie](../vsto/actions-pane-overview.md)   
 [Wstążka — omówienie](../vsto/ribbon-overview.md)   
 [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Dane w pamięci podręcznej dostosowywane na poziomie dokumentu](../vsto/cached-data-in-document-level-customizations.md)   
 [Wdrażanie rozwiązania do pakietu Office](../vsto/deploying-an-office-solution.md)  
  
  