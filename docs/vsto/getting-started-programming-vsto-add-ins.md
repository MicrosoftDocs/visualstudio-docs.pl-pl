---
title: Wprowadzenie do programowania dodatków VSTO
description: Dowiedz się, jak za pomocą dodatków VSTO można automatyzować aplikacje Microsoft Office, rozszerzać funkcje aplikacji i dostosowywać interfejs użytkownika aplikacji.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848295"
---
# <a name="get-started-programming-vsto-add-ins"></a>Wprowadzenie do programowania dodatków VSTO
> [!IMPORTANT]
> VSTO opiera się na [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview). Dodatki COM można również zapisywać za pomocą .NET Framework. Dodatków pakietu Office nie można tworzyć za pomocą [programu .NET Core i .NET 5+](https://docs.microsoft.com/dotnet/core/dotnet-five), najnowszych wersji programu .NET. Jest to spowodowane tym, że program .NET Core/.NET 5+ nie może współpracować z programem .NET Framework w tym samym procesie i może prowadzić do błędów ładowania dodatków. Możesz nadal używać usługi .NET Framework do pisania dodatków VSTO i COM dla pakietu Office. Firma Microsoft nie będzie aktualizować usługi VSTO ani platformy dodatku COM w celu używania platformy .NET Core lub .NET 5+. Możesz skorzystać z programu .NET Core i .NET 5+, w tym programu ASP.NET Core, aby utworzyć stronę serwera dodatków internetowych [pakietu Office.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  Za pomocą dodatków VSTO można automatyzować aplikacje Microsoft Office, rozszerzać funkcje aplikacji i dostosowywać interfejs użytkownika aplikacji. Aby uzyskać informacje o porównaniu dodatków VSTO z innymi typami rozwiązań pakietu Office, które można utworzyć przy użyciu programu Visual Studio, zobacz Omówienie tworzenia rozwiązań pakietu Office &#40;[VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>Tworzenie projektów dodatków VSTO
 Tworzenie projektów dodatków VSTO przy użyciu jednego z szablonów projektów dodatku VSTO w **oknie dialogowym Nowy** projekt. Te szablony zawierają wymagane odwołania do zestawu i pliki projektu. Visual Studio udostępnia szablony projektów dodatków VSTO dla większości aplikacji w psłudze Office.

 Aby uzyskać więcej informacji na temat tworzenia projektu dodatku VSTO, zobacz [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md). Aby uzyskać więcej informacji na temat szablonów projektów, zobacz [Office project templates overview (Omówienie szablonów projektów pakietu Office).](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>Opracowywanie projektów dodatków VSTO
 Podczas tworzenia projektu dodatku VSTO program Visual Studio automatycznie tworzy plik kodu *ThisAddIn.vb* (w pliku ) lub [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (w języku C#). Ten plik zawiera `ThisAddIn` klasę , która stanowi podstawę dla dodatku VSTO. Składowych tej klasy można używać do uruchamiania kodu podczas ładowania lub zwalniania dodatku VSTO, uzyskiwania dostępu do modelu obiektów aplikacji hosta i rozszerzania funkcji aplikacji. Aby uzyskać więcej informacji, zobacz [Program VSTO Add-Ins (Program VSTO Add-Ins).](../vsto/programming-vsto-add-ins.md)

## <a name="automate-applications-by-using-the-object-models"></a>Automatyzowanie aplikacji przy użyciu modeli obiektów
 Modele obiektów aplikacji Microsoft Office uwidoczniają wiele typów, względem których można programować w dodatku VSTO. Za pomocą tych typów można zautomatyzować aplikację. Można na przykład programowo utworzyć i wysłać wiadomość e-mail w programie Outlook lub otworzyć dokument i dodać zawartość w programie Word. Aby uzyskać więcej informacji na temat sposobu uzyskiwania dostępu do modelu obiektów aplikacji hosta w kodzie, zobacz [Program VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)(Dodatki programu VSTO).

 Aby uzyskać więcej informacji na temat modeli obiektów określonych aplikacji Microsoft Office, zobacz następujące tematy:

- [Omówienie modelu obiektu programu Excel](../vsto/excel-object-model-overview.md)

- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)

- [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md)

- [Rozwiązania InfoPath](../vsto/infopath-solutions.md)

- [Rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md)

- [Rozwiązania projektu](../vsto/project-solutions.md)

- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji
 Istnieje kilka różnych sposobów dostosowywania interfejsu użytkownika aplikacji hosta za pomocą dodatku VSTO:

- W przypadku programów Excel i Word można dodawać zarządzane kontrolki do dokumentów. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

- Możesz dostosować wstążkę, jeśli aplikacja ją obsługuje. Aby uzyskać więcej informacji, zobacz [Omówienie wstążki.](../vsto/ribbon-overview.md)

- Jeśli aplikacja je obsługuje, możesz utworzyć niestandardowe okienko zadań. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)

- W przypadku programu Outlook możesz utworzyć niestandardowy region formularza. Aby uzyskać więcej informacji, zobacz [Create Outlook form regions (Tworzenie regionów formularzy programu Outlook).](../vsto/creating-outlook-form-regions.md)

- W przypadku Microsoft Office aplikacji można wyświetlać Windows Forms w dodatku VSTO.

  Aby uzyskać więcej informacji na temat dostosowywania interfejsu użytkownika aplikacji Microsoft Office, zobacz [Dostosowywanie interfejsu użytkownika pakietu Office.](../vsto/office-ui-customization.md)

## <a name="next-steps"></a>Następne kroki
 Aby dowiedzieć się, jak tworzyć dodatki VSTO, zobacz następujące wskazówki:

- [Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [Przewodnik: tworzenie pierwszego pliku VSTO Add-In dla programu Outlook](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [Przewodnik: tworzenie pierwszego dodatku VSTO dla programu PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [Przewodnik: tworzenie pierwszego dodatku VSTO dla projektu](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [Przewodnik: tworzenie pierwszego dodatku VSTO dla programu Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  Te wskazówki wprowadzają narzędzia programistyczne pakietu Office w usłudze Visual Studio oraz model programowania dla dodatków narzędzi VSTO.

  Aby uzyskać listę tematów, które zawierają informacje na temat niektórych typowych zadań w projektach pakietu Office, zobacz [Typowe zadania w programowaniu pakietu Office.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>Zobacz też
- [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Wprowadzenie do tworzenia &#40;Office w usłudze Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
