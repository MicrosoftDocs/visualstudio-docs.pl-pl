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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 39cf3e8d59a2ced26f878da979fa87fc663b5bab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "71253591"
---
# <a name="get-started-programming-vsto-add-ins"></a>Wprowadzenie do programowania dodatków narzędzi VSTO
  Dodatków VSTO można używać do automatyzowania Microsoft Office aplikacji, rozszerzenia funkcji aplikacji i dostosowywania interfejsu użytkownika aplikacji. Aby uzyskać informacje na temat sposobu, w jaki Dodatki VSTO są porównywane z innymi typami rozwiązań pakietu Office, które można utworzyć przy użyciu programu Visual Studio, zobacz [Omówienie rozwiązań programistycznych dla pakietu office &#40;narzędzi VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Tworzenie projektów dodatków VSTO
 Utwórz projekty dodatków VSTO przy użyciu jednego z szablonów projektów dodatku VSTO w oknie dialogowym **Nowy projekt** . Szablony te zawierają wymagane odwołania do zestawów i pliki projektu. Program Visual Studio zawiera szablony projektów dodatku VSTO dla większości aplikacji w pakiecie Office.

 Aby uzyskać więcej informacji na temat sposobu tworzenia projektu dodatku VSTO, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji o szablonach projektów, zobacz [Office Project Templates Overview](../vsto/office-project-templates-overview.md).

## <a name="develop-vsto-add-in-projects"></a>Opracowywanie projektów dodatków VSTO
 Podczas tworzenia projektu dodatku programu VSTO program Visual Studio automatycznie tworzy plik kodu *ThisAddIn. vb* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) lub *ThisAddIn.cs* (w języku C#). Ten plik zawiera `ThisAddIn` klasę, która stanowi podstawę dla dodatku VSTO. Elementy członkowskie tej klasy mogą być używane do uruchamiania kodu podczas ładowania lub zwalniania dodatku VSTO, uzyskiwania dostępu do modelu obiektów aplikacji hosta oraz do rozszerzeń funkcji aplikacji. Aby uzyskać więcej informacji, zobacz [dodatki narzędzi VSTO dla programu](../vsto/programming-vsto-add-ins.md).

## <a name="automate-applications-by-using-the-object-models"></a>Automatyzowanie aplikacji przy użyciu modeli obiektów
 Modele obiektów Microsoft Office aplikacji uwidaczniają wiele typów, które można programować w ramach dodatku VSTO. Można używać tych typów do automatyzowania aplikacji. Na przykład możesz programowo utworzyć i wysłać wiadomość e-mail w programie Outlook lub otworzyć dokument i dodać zawartość w programie Word. Aby uzyskać więcej informacji na temat uzyskiwania dostępu do modelu obiektów aplikacji hosta w kodzie, zobacz [dodatki narzędzi VSTO](../vsto/programming-vsto-add-ins.md).

 Aby uzyskać więcej informacji na temat modeli obiektów określonych Microsoft Office aplikacji, zobacz następujące tematy:

- [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md)

- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)

- [Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)

- [Rozwiązania programu InfoPath](../vsto/infopath-solutions.md)

- [Rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md)

- [Rozwiązania projektu](../vsto/project-solutions.md)

- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji
 Istnieje kilka różnych sposobów dostosowywania interfejsu użytkownika aplikacji hosta przy użyciu dodatku VSTO:

- Dla programów Excel i Word można dodawać zarządzane formanty do dokumentów. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

- Możesz dostosować Wstążkę, jeśli aplikacja ją obsługuje. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki](../vsto/ribbon-overview.md).

- Można utworzyć niestandardowe okienko zadań, jeśli jest ono obsługiwane przez aplikację. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).

- W przypadku programu Outlook można utworzyć niestandardowy region formularza. Aby uzyskać więcej informacji, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

- W przypadku wszystkich aplikacji Microsoft Office można wyświetlić Windows Forms w dodatku VSTO.

  Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika aplikacji Microsoft Office, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

## <a name="next-steps"></a>Następne kroki
 Aby dowiedzieć się, jak utworzyć Dodatki VSTO, zobacz następujące przewodniki:

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Przewodnik: Tworzenie pierwszego dodatku narzędzi VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Te instruktaże zawierają wprowadzenie do narzędzi programistycznych pakietu Office w programie Visual Studio i modelu programowania dla dodatków narzędzi VSTO.

  Aby zapoznać się z listą tematów, które przeprowadzą Cię przez niektóre typowe zadania w projektach pakietu Office, zobacz [typowe zadania w programowaniu pakietu Office](../vsto/common-tasks-in-office-programming.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Wprowadzenie &#40;Programowanie Office w programie Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
