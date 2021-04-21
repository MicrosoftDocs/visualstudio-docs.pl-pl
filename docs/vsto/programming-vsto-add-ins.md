---
title: Program VSTO Add-ins
description: Dowiedz się, jak za pomocą klasy ThisAddIn wykonywać zadania, takie jak uzyskiwanie dostępu do modelu obiektów Microsoft Office aplikacji hosta.
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
ms.openlocfilehash: 2ee62f35b0626139a8080649076d2ac941366a26
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828712"
---
# <a name="program-vsto-add-ins"></a>Program VSTO Add-ins
  Podczas rozszerzania aplikacji Microsoft Office przez utworzenie dodatku VSTO kod jest pisany bezpośrednio `ThisAddIn` względem klasy w projekcie. Za pomocą tej klasy można wykonywać zadania, takie jak uzyskiwanie dostępu do modelu obiektów aplikacji hosta programu Microsoft Office, dostosowywanie interfejsu użytkownika aplikacji i uwyłaczanie obiektów w dodatku VSTO innym rozwiązaniom pakietu Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Niektóre aspekty pisania kodu w projektach dodatków VSTO różnią się od innych typów projektów w Visual Studio. Wiele z tych różnic wynika ze sposobu, w jaki modele obiektów pakietu Office są widoczne dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [Pisanie kodu w rozwiązaniach pakietu Office.](../vsto/writing-code-in-office-solutions.md)

 Aby uzyskać ogólne informacje na temat dodatków narzędzi VSTO i innych typów rozwiązań, które można utworzyć przy użyciu narzędzi programistycznych pakietu Office w programie Visual Studio, zobacz Omówienie tworzenia rozwiązań pakietu Office &#40;[VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Używanie klasy ThisAddIn
 Możesz rozpocząć pisanie kodu dodatku VSTO w `ThisAddIn` klasie . Visual Studio automatycznie generuje tę klasę w pliku kodu *ThisAddIn.vb* (w pliku ) lub [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] *ThisAddIn.cs* (w języku C#) w projekcie dodatku VSTO. Klasa automatycznie tworzy wystąpienia tej klasy, gdy [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] aplikacja Microsoft Office ładuje dodatek VSTO.

 Klasa ma dwa domyślne programy obsługi `ThisAddIn` zdarzeń. Aby uruchomić kod po załadowaniu dodatku VSTO, dodaj kod do procedury `ThisAddIn_Startup` obsługi zdarzeń. Aby uruchomić kod tuż przed zwolnieniem dodatku VSTO, dodaj kod do procedury `ThisAddIn_Shutdown` obsługi zdarzeń. Aby uzyskać więcej informacji na temat tych programów obsługi zdarzeń, zobacz [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> W programie Outlook domyślnie program obsługi zdarzeń nie jest zawsze wywoływany, gdy dodatek `ThisAddIn_Shutdown` VSTO jest zwalniany. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)

### <a name="access-the-object-model-of-the-host-application"></a>Uzyskiwanie dostępu do modelu obiektów aplikacji hosta
 Aby uzyskać dostęp do modelu obiektów aplikacji hosta, użyj `Application` pola `ThisAddIn` klasy . To pole zwraca obiekt reprezentujący bieżące wystąpienie aplikacji hosta. W poniższej tabeli wymieniono typ zwracanej wartości pola `Application` w każdym projekcie dodatku VSTO.

|Aplikacja hosta|Typ wartości zwracanej|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Aplikacja](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Microsoft Office projektu|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Poniższy przykład kodu pokazuje, jak za pomocą pola utworzyć nowy skoroszyt w dodatku VSTO dla programu `Application` Excel Microsoft Office Excel. Ten przykład jest przeznaczony do uruchamiania z `ThisAddIn` klasy .

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Aby wykonać to samo spoza klasy , użyj obiektu , `ThisAddIn` aby uzyskać dostęp do `Globals` `ThisAddIn` klasy. Aby uzyskać więcej informacji na temat `Globals` obiektu , zobacz Globalny dostęp do obiektów w [projektach pakietu Office.](../vsto/global-access-to-objects-in-office-projects.md)

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Aby uzyskać więcej informacji na temat modeli obiektów określonych aplikacji Microsoft Office, zobacz następujące tematy:

- [Omówienie modelu obiektów programu Excel](../vsto/excel-object-model-overview.md)

- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)

- [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md)

- [Rozwiązania InfoPath](../vsto/infopath-solutions.md)

- [Rozwiązania programu PowerPoint](../vsto/powerpoint-solutions.md)

- [Rozwiązania projektu](../vsto/project-solutions.md)

- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a> Uzyskiwanie dostępu do dokumentu podczas uruchamiania aplikacji pakietu Office
 Nie wszystkie aplikacje automatycznie otwierają dokument po ich uruchomieniu i żadna z aplikacji nie otwiera [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] dokumentu po ich uruchomieniu. W związku z tym nie należy dodawać kodu do procedury `ThisAdd-In_Startup` obsługi zdarzeń, jeśli kod wymaga otwarcia dokumentu. Zamiast tego należy dodać ten kod do zdarzenia, które jest zgłaszane przez aplikację pakietu Office, gdy użytkownik utworzy lub otworzy dokument. Dzięki temu można zagwarantować, że dokument zostanie otwarty, zanim kod wykona na nim operacje.

 Poniższy przykład kodu działa z dokumentem w programie Word tylko wtedy, gdy użytkownik tworzy dokument lub otwiera istniejący dokument.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs" id="Snippet3":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb" id="Snippet3":::

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn elementów członkowskich do użycia w innych zadaniach
 W poniższej tabeli opisano inne typowe zadania i pokazano, których składowych klasy można używać `ThisAddIn` do wykonywania zadań.

|Zadanie|Członek do użycia|
|----------|-------------------|
|Uruchom kod, aby zainicjować dodatek VSTO po załadowaniu dodatku VSTO.|Dodaj kod do `ThisAddIn_Startup` metody . Jest to domyślna procedura obsługi <xref:Microsoft.Office.Tools.AddInBase.Startup> zdarzeń dla zdarzenia. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)|
|Uruchom kod, aby wyczyścić zasoby używane przez dodatek VSTO przed zwolnieniem dodatku VSTO.|Dodaj kod do `ThisAddIn_Shutdown` metody . Jest to domyślna procedura obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Shutdown> zdarzenia. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md) **Uwaga:**  W programie Outlook domyślnie program obsługi zdarzeń nie jest zawsze wywoływany, gdy dodatek `ThisAddIn_Shutdown` VSTO jest zwalniany. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office.](../vsto/events-in-office-projects.md)|
|Wyświetlanie niestandardowego okienka zadań.|Użyj `CustomTaskPanes` pola . Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań.](../vsto/custom-task-panes.md)|
|Uwidocznij obiekty w dodatku VSTO dla innych Microsoft Office rozwiązań.|Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę . Aby uzyskać więcej informacji, zobacz [Call code in VSTO Add-ins from other Office solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)(Wywołanie kodu w dodatki VSTO z innych rozwiązań pakietu Office).|
|Dostosowywanie funkcji w systemie Microsoft Office przez zaimplementowanie interfejsu rozszerzalności.|Zastąp metodę <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> , aby zwrócić wystąpienie klasy, która implementuje interfejs. Aby uzyskać więcej informacji, zobacz [Customize UI features by using extensibility interfaces (Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności).](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md) **Uwaga:**  Aby dostosować interfejs użytkownika wstążki, możesz również przesłonić <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> metodę .|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Opis projektu klasy ThisAddIn
 W projektach, które są docelowe [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] dla obiektu , jest <xref:Microsoft.Office.Tools.AddIn> interfejsem. Klasa `ThisAddIn` pochodzi od <xref:Microsoft.Office.Tools.AddInBase> klasy . Ta klasa bazowa przekierowuje wszystkie wywołania do jej składowych do wewnętrznej implementacji <xref:Microsoft.Office.Tools.AddIn> interfejsu w klasie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] .

 W projektach dodatku VSTO dla programu Outlook klasa pochodzi z klasy w projektach docelowych programu `ThisAddIn` `Microsoft.Office.Tools.Outlook.OutlookAddIn` .NET Framework 3.5, a w projektach docelowych <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Te klasy bazowe zapewniają pewne dodatkowe funkcje do obsługi regionów formularzy. Aby uzyskać więcej informacji na temat regionów formularzy, zobacz [Create Outlook form regions (Tworzenie regionów formularzy programu Outlook).](../vsto/creating-outlook-form-regions.md)

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika Microsoft Office aplikacji
 Możesz programowo dostosować interfejs użytkownika aplikacji Microsoft Office za pomocą dodatku VSTO. Możesz na przykład dostosować wstążkę, wyświetlić niestandardowe okienko zadań lub utworzyć niestandardowy region formularza w programie Outlook. Aby uzyskać więcej informacji, zobacz [Dostosowywanie interfejsu użytkownika pakietu Office.](../vsto/office-ui-customization.md)

 Visual Studio projektantom i klasom, których można używać do tworzenia niestandardowych okienek zadań, dostosowań wstążki i regionów formularzy programu Outlook. Te projektanci i klasy pomagają uprościć proces dostosowywania tych funkcji. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań,](../vsto/custom-task-panes.md) [Projektant wstążki](../vsto/ribbon-designer.md)i [Tworzenie regionów formularzy programu Outlook.](../vsto/creating-outlook-form-regions.md)

 Jeśli chcesz dostosować jedną z tych funkcji w sposób, który nie jest obsługiwany przez klasy i  projektantów, możesz również dostosować te funkcje, implementując interfejs rozszerzalności w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Customize UI features by using extensibility interfaces](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)(Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności).

 Ponadto można modyfikować interfejs użytkownika dokumentów programu Word i skoroszytów programu Excel, generując elementy hosta, które rozszerzają zachowanie dokumentów i skoroszytów. Umożliwia to dodawanie kontrolek zarządzanych do dokumentów i arkuszy. Aby uzyskać więcej informacji, zobacz [Extend Word documents and Excel workbooks in VSTO Add-ins at run time](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)(Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Wywołanie kodu w dodatki VSTO z innych rozwiązań
 Obiekty w dodatku VSTO można uwidocznić dla innych rozwiązań, w tym innych rozwiązań pakietu Office. Jest to przydatne, jeśli dodatek VSTO udostępnia usługę, której chcesz używać w innych rozwiązaniach. Jeśli na przykład masz dodatek VSTO dla programu Microsoft Office Excel, który wykonuje obliczenia na danych finansowych z usługi internetowej, inne rozwiązania mogą wykonać te obliczenia, wywołując dodatek VSTO programu Excel w czasie wykonywania.

 Aby uzyskać więcej informacji, zobacz [Call code in VSTO Add-ins from other Office solutions](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)(Wywołanie kodu w dodatki VSTO z innych rozwiązań pakietu Office).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatki VSTO w czasie uruchamiania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Wywołanie kodu w dodatki VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Przewodnik: wywołanie kodu w dodatku VSTO z VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
