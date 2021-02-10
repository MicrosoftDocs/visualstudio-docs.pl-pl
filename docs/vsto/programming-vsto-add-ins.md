---
title: Dodatki narzędzi VSTO programu
description: Dowiedz się, w jaki sposób można użyć klasy ThisAddIn do wykonywania zadań, takich jak uzyskiwanie dostępu do modelu obiektów aplikacji hosta Microsoft Office.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Addin
- VST.ProjectItem.AddinProject
- thisAddIn
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- ICustomTaskPaneConsumer interface
- add-ins [Office development in Visual Studio], programming
- IRibbonExtensibility interface
- UI customizing [Office development in Visual Studio]
- Office applications [Office development in Visual Studio], application-level add-ins
- programming [Office development in Visual Studio], application-level add-ins
- ThisAddIn class
- user interfaces [Office development in Visual Studio], customizing
- writing code for Office solutions
- host items [Office development in Visual Studio], AddIn
- application development [Office development in Visual Studio], application-level add-ins
- add-ins [Office development in Visual Studio], ThisAddIn class
- application-level add-ins [Office development in Visual Studio], ThisAddIn class
- FormRegionStartup interface
- ThisAddIn_Startup
- application-level add-ins [Office development in Visual Studio], programming
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 83fdc3b6a60c5f8972ff5d955c56476fb13315d9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99971833"
---
# <a name="program-vsto-add-ins"></a>Dodatki narzędzi VSTO programu
  Po rozbudowaniu aplikacji Microsoft Office przez utworzenie dodatku VSTO należy napisać kod bezpośrednio względem `ThisAddIn` klasy w projekcie. Ta klasa służy do wykonywania zadań, takich jak uzyskiwanie dostępu do modelu obiektów aplikacji hosta Microsoft Office, Dostosowywanie interfejsu użytkownika i udostępnianie obiektów w dodatku VSTO do innych rozwiązań pakietu Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Niektóre aspekty pisania kodu w projektach dodatku narzędzi VSTO różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic jest spowodowanych sposobem, w jaki modele obiektów pakietu Office są uwidocznione w kodzie zarządzanym. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

 Aby uzyskać ogólne informacje na temat dodatków VSTO i innych typów rozwiązań, które można utworzyć przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, zobacz [Omówienie rozwiązania do tworzenia rozwiązań pakietu office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Korzystanie z klasy ThisAddIn
 Możesz rozpocząć pisanie kodu dodatku VSTO w `ThisAddIn` klasie. Program Visual Studio automatycznie generuje tę klasę w pliku kodu *ThisAddIn. vb* (in [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) lub *ThisAddIn.cs* (w języku C#) w projekcie dodatku VSTO. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]Automatycznie tworzy wystąpienie tej klasy, gdy aplikacja Microsoft Office ładuje dodatek narzędzi VSTO.

 W klasie istnieją dwa domyślne programy obsługi zdarzeń `ThisAddIn` . Aby uruchomić kod podczas ładowania dodatku VSTO, Dodaj kod do `ThisAddIn_Startup` programu obsługi zdarzeń. Aby uruchomić kod tuż przed wyładowaniem dodatku VSTO, Dodaj kod do `ThisAddIn_Shutdown` programu obsługi zdarzeń. Aby uzyskać więcej informacji na temat obsługi zdarzeń, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> W programie Outlook domyślnie `ThisAddIn_Shutdown` program obsługi zdarzeń nie zawsze jest wywoływany, gdy dodatek narzędzi VSTO zostanie zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Dostęp do modelu obiektów aplikacji hosta
 Aby uzyskać dostęp do modelu obiektów aplikacji hosta, użyj `Application` pola `ThisAddIn` klasy. To pole zwraca obiekt, który reprezentuje bieżące wystąpienie aplikacji hosta. W poniższej tabeli przedstawiono typ wartości zwracanej dla `Application` pola w każdym projekcie dodatku VSTO.

|Aplikacja hosta|Typ wartości zwracanej|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Aplikacja](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Projekt Microsoft Office|Microsoft. Office. Interop. MSProject. Application|
|Microsoft Office Visio|Microsoft. Office. Interop. Visio. Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Poniższy przykład kodu pokazuje, jak za pomocą `Application` pola utworzyć nowy skoroszyt w dodatku narzędzi VSTO dla programu Microsoft Office Excel. Ten przykład jest przeznaczony do uruchamiania z `ThisAddIn` klasy.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Aby zrobić to samo z zewnątrz `ThisAddIn` klasy, użyj `Globals` obiektu, aby uzyskać dostęp do `ThisAddIn` klasy. Aby uzyskać więcej informacji na temat `Globals` obiektu, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Aby uzyskać więcej informacji na temat modeli obiektów określonych Microsoft Office aplikacji, zobacz następujące tematy:

- [Model obiektów programu Excel — Omówienie](../vsto/excel-object-model-overview.md)

- [Model obiektów programu Word — omówienie](../vsto/word-object-model-overview.md)

- [Model obiektów programu Outlook — Omówienie](../vsto/outlook-object-model-overview.md)

- [Rozwiązania programu InfoPath](../vsto/infopath-solutions.md)

- [Rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md)

- [Rozwiązania projektu](../vsto/project-solutions.md)

- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a> Uzyskaj dostęp do dokumentu podczas uruchamiania aplikacji pakietu Office
 Nie wszystkie [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikacje automatycznie otwierają dokument po ich uruchomieniu i żadna z [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikacji nie otwiera dokumentu po jego uruchomieniu. W związku z tym nie należy dodawać kodu w programie `ThisAdd-In_Startup` obsługi zdarzeń, jeśli kod wymaga otwarcia dokumentu. Zamiast tego należy dodać ten kod do zdarzenia, które aplikacja pakietu Office zgłasza, gdy użytkownik tworzy lub otwiera dokument. Dzięki temu można zagwarantować, że dokument jest otwarty przed wykonaniem przez kod operacji na nim.

 Poniższy przykład kodu działa z dokumentem w programie Word tylko wtedy, gdy użytkownik tworzy dokument lub otwiera istniejący dokument.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn członków do użycia z innymi zadaniami
 W poniższej tabeli opisano inne typowe zadania i przedstawiono elementy członkowskie `ThisAddIn` klasy, których można użyć do wykonania zadań.

|Zadanie|Członek do użycia|
|----------|-------------------|
|Uruchom kod, aby zainicjować dodatek VSTO po załadowaniu dodatku VSTO.|Dodaj kod do `ThisAddIn_Startup` metody. Jest to domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Startup> zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|
|Uruchom kod, aby wyczyścić zasoby używane przez dodatek VSTO przed wyładowaniem dodatku VSTO.|Dodaj kod do `ThisAddIn_Shutdown` metody. Jest to domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Shutdown> zdarzenia. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md). **Uwaga:**  W programie Outlook domyślnie `ThisAddIn_Shutdown` program obsługi zdarzeń nie zawsze jest wywoływany, gdy dodatek narzędzi VSTO zostanie zwolniony. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|
|Wyświetlanie niestandardowego okienka zadań.|Użyj `CustomTaskPanes` pola. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md).|
|Uwidacznianie obiektów w dodatku VSTO do innych rozwiązań Microsoft Office.|Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę. Aby uzyskać więcej informacji, zobacz [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Dostosuj funkcję w systemie Microsoft Office, implementując interfejs rozszerzalności.|Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodę, aby zwrócić wystąpienie klasy, która implementuje interfejs. Aby uzyskać więcej informacji, zobacz [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Uwaga:**  Aby dostosować interfejs użytkownika wstążki, można również zastąpić <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> metodę.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Zrozumienie projektu klasy ThisAddIn
 W projektach przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] , <xref:Microsoft.Office.Tools.AddIn> jest interfejsem. `ThisAddIn`Klasa pochodzi od <xref:Microsoft.Office.Tools.AddInBase> klasy. Ta klasa bazowa przekierowuje wszystkie wywołania do swoich elementów członkowskich do wewnętrznej implementacji <xref:Microsoft.Office.Tools.AddIn> interfejsu w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 W projektach dodatku narzędzi VSTO dla programu Outlook `ThisAddIn` Klasa pochodzi od `Microsoft.Office.Tools.Outlook.OutlookAddIn` klasy w projektach, która jest przeznaczona dla .NET Framework 3,5 i z <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> w projektach, które są przeznaczone dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Te klasy bazowe zapewniają dodatkową funkcjonalność do obsługi regionów formularzy. Aby uzyskać więcej informacji na temat regionów formularzy, zobacz [Tworzenie regionów formularzy w programie Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji Microsoft Office
 Można programowo dostosować interfejs użytkownika aplikacji Microsoft Office przy użyciu dodatku VSTO. Na przykład można dostosować Wstążkę, wyświetlić niestandardowe okienko zadań lub utworzyć niestandardowy region formularza w programie Outlook. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

 Program Visual Studio udostępnia projektantom i klasom, których można użyć do tworzenia niestandardowych okienek zadań, dostosowań Wstążki i regionów formularzy programu Outlook. Te projektanci i klasy pomagają uprościć proces dostosowywania tych funkcji. Aby uzyskać więcej informacji, zobacz [niestandardowe okienka zadań](../vsto/custom-task-panes.md), [Projektant wstążki](../vsto/ribbon-designer.md)i [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).

 Jeśli chcesz dostosować jedną z tych funkcji w sposób, który nie jest obsługiwany przez klasy i projektantów, możesz również dostosować te funkcje, implementując *interfejs rozszerzalności* w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Ponadto można modyfikować interfejs użytkownika dokumentów programu Word i skoroszytów programu Excel, generując elementy hosta, które poszerzają zachowanie dokumentów i skoroszytów. Pozwala to na dodawanie formantów zarządzanych do dokumentów i arkuszy. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Wywoływanie kodu w dodatkach VSTO z innych rozwiązań
 Można uwidocznić obiekty w dodatku narzędzi VSTO dla innych rozwiązań, w tym innych rozwiązań pakietu Office. Jest to przydatne, jeśli dodatek narzędzi VSTO udostępnia usługę, która umożliwia korzystanie z innych rozwiązań. Na przykład jeśli masz dodatek narzędzi VSTO dla programu Microsoft Office Excel, który wykonuje obliczenia dotyczące danych finansowych z usługi sieci Web, inne rozwiązania mogą wykonywać te obliczenia przez wywołanie dodatku VSTO programu Excel w czasie wykonywania.

 Aby uzyskać więcej informacji, zobacz [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Rozwiń dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Przewodnik: wywoływanie kodu w dodatku VSTO z języka VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
