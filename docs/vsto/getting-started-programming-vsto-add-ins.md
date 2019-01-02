---
title: Wprowadzenie do programowania dodatków narzędzi VSTO
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: eef79de32a467bee1d96972da0ccdfd91eede350
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53853047"
---
# <a name="get-started-programming-vsto-add-ins"></a>Wprowadzenie do programowania dodatków narzędzi VSTO
  Za pomocą dodatków narzędzi VSTO automatyzację aplikacji Microsoft Office, Rozszerz funkcje aplikacji i dostosowywanie interfejsu użytkownika (UI) aplikacji. Aby uzyskać informacji na temat jak dodatków narzędzi VSTO wypadają w porównaniu do innych typów rozwiązań dla pakietu Office, można utworzyć przy użyciu programu Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]  
  
## <a name="create-vsto-add-in-projects"></a>Tworzenie projektów dodatku narzędzi VSTO  
 Tworzenie projektów w dodatku narzędzi VSTO za pomocą jednego z dodatku narzędzi VSTO szablonów projektów w **nowy projekt** okno dialogowe. Te szablony zawierają odwołania do zestawów wymagane, a pliki projektu. Visual Studio udostępnia dodatku narzędzi VSTO szablony projektów dla większości aplikacji pakietu Office.  
  
 Aby uzyskać więcej informacji o sposobie tworzenia projektu dodatku narzędzi VSTO dla programów, zobacz [jak: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektu, zobacz [Przegląd szablony projektu pakietu Office](../vsto/office-project-templates-overview.md).  
  
## <a name="develop-vsto-add-in-projects"></a>Tworzenie projektów dodatku narzędzi VSTO  
 Podczas tworzenia projektu dodatku narzędzi VSTO dla programu Visual Studio automatycznie tworzy *ThisAddIn.vb* (w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) lub *ThisAddIn.cs* plik kodu (w języku C#). Ten plik zawiera `ThisAddIn` klasy, która stanowi podstawę dla dodatku VSTO. Elementy członkowskie tej klasy można użyć do uruchomienia kodu po dodatku narzędzi VSTO jest załadowany lub zwolnione, dostępu do modelu obiektu aplikacji hosta, a także aby rozszerzyć funkcje aplikacji. Aby uzyskać więcej informacji, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
## <a name="automate-applications-by-using-the-object-models"></a>Automatyzacja aplikacji przy użyciu modeli obiektów  
 Modele obiektów w aplikacji pakietu Microsoft Office ujawnia wiele typów, których można programować względem w dodatku VSTO. Te typy można użyć do zautomatyzowania aplikacji. Na przykład można programowo tworzyć i wysyłać wiadomości e-mail w programie Outlook lub możesz otworzyć dokument i Dodaj zawartość w programie Word. Aby uzyskać więcej informacji na temat dostępu do modelu obiektu w kodzie aplikacji hosta, zobacz [dodatków narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md).  
  
 Aby uzyskać więcej informacji na temat modeli obiektów określonych aplikacji pakietu Microsoft Office zobacz następujące tematy:  
  
-   [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)  
  
-   [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)  
  
-   [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)  
  
-   [Rozwiązania InfoPath](../vsto/infopath-solutions.md)  
  
-   [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)  
  
-   [Rozwiązania projektu](../vsto/project-solutions.md)  
  
-   [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)  
  
## <a name="customize-the-user-interface-of-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji  
 Istnieje kilka różnych sposobów dostosowania interfejsu użytkownika aplikacji hosta przy użyciu dodatku VSTO:  
  
- Dla programów Excel i Word można dodać formanty zarządzanego do dokumentów. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
- Jeśli aplikacja obsługuje tę funkcję, możesz dostosować wstążki. Aby uzyskać więcej informacji, zobacz [Wstążka ― omówienie](../vsto/ribbon-overview.md).  
  
- Jeśli aplikacja obsługuje tę funkcję, możesz utworzyć niestandardowego okienka zadań. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).  
  
- Dla programu Outlook można utworzyć region formularza niestandardowego. Aby uzyskać więcej informacji, zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).  
  
- Dla wszystkich aplikacji programu Microsoft Office możesz wyświetlić Windows Forms w dodatku VSTO.  
  
  Aby uzyskać więcej informacji na temat sposobu dostosowywania aplikacji interfejsu użytkownika pakietu Microsoft Office, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).  
  
## <a name="next-steps"></a>Następne kroki  
 Aby dowiedzieć się, jak tworzenie dodatków narzędzi VSTO dla programów, zobacz następujące instruktaże:  
  
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)  
  
- [Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)  
  
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)  
  
- [Przewodnik: Tworzenie swojej pierwszej dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)  
  
- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)  
  
  Te wskazówki zawierają wprowadzenie do narzędzi programistycznych pakietu Office w Visual Studio i modelu programowania dla dodatków narzędzi VSTO.  
  
  Aby uzyskać listę tematów, które prowadzą użytkownika przez niektóre typowe zadania w projektach pakietu Office, zobacz [typowe zadania w programowaniu Office](../vsto/common-tasks-in-office-programming.md).  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Rozpoczynanie pracy &#40;programowanie Office w Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)   
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)  
