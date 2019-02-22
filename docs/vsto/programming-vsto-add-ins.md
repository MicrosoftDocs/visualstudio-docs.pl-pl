---
title: Program dodatków narzędzi VSTO
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 304b61a7e0e11cf3b714fcc6f43855f5ded35713
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56641419"
---
# <a name="program-vsto-add-ins"></a>Program dodatków narzędzi VSTO
  Podczas rozszerzania aplikacji pakietu Microsoft Office, tworzenia dodatku narzędzi VSTO dla programów, piszesz kod bezpośrednio przed `ThisAddIn` klasy w projekcie. Ta klasa służy do wykonywania zadań, takich jak uzyskiwanie dostępu do modelu obiektów programu Microsoft Office aplikacji hosta, dostosowywanie interfejsu użytkownika (UI), aplikacji i udostępnianie obiektów w dodatku narzędzi VSTO dla programów do innych rozwiązań pakietu Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Niektóre aspekty pisanie kodu w projektach dodatku narzędzi VSTO różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic jest spowodowana przez sposób Office modele obiektów są widoczne dla kodu zarządzanego. Aby uzyskać więcej informacji, zobacz [pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

 Aby uzyskać ogólne informacje dotyczące dodatków narzędzi VSTO dla programów i innych typów rozwiązań, można utworzyć za pomocą narzędzi programistycznych pakietu Office w programie Visual Studio, zobacz [rozwój rozwiązań Office ― omówienie &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Użyj thisaddin — klasa
 Możesz rozpocząć pisanie kodu dodatku narzędzi VSTO dla programów w `ThisAddIn` klasy. Program Visual Studio automatycznie generuje tej klasy w *ThisAddIn.vb* (w [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]) lub *ThisAddIn.cs* (w języku C#) plik w projekcie dodatku narzędzi VSTO kodu. [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Automatycznie tworzy tę klasę, podczas ładowania aplikacji Microsoft Office dodatku narzędzi VSTO dla programów.

 Istnieją dwie domyślne obsługi zdarzeń w `ThisAddIn` klasy. Aby uruchomić kod, gdy jest ładowany dodatku narzędzi VSTO dla programów, Dodaj kod, aby `ThisAddIn_Startup` programu obsługi zdarzeń. Aby uruchomić kod przed dodatku narzędzi VSTO zwolniony, Dodaj kod, aby `ThisAddIn_Shutdown` programu obsługi zdarzeń. Aby uzyskać więcej informacji na temat tych programów obsługi zdarzeń, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

> [!NOTE]
>  W programie Outlook, domyślnie `ThisAddIn_Shutdown` program obsługi zdarzeń nie zawsze jest wywoływany podczas dodatku narzędzi VSTO jest zwalniana. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Dostęp do modelu obiektów w aplikacji hosta
 Aby uzyskać dostęp do modelu obiektów w aplikacji hosta, należy użyć `Application` pole `ThisAddIn` klasy. To pole zwraca obiekt reprezentujący bieżące wystąpienie aplikacji hosta. W poniższej tabeli przedstawiono typ wartości zwracanej przez `Application` pola w każdym projekcie dodatku narzędzi VSTO.

|Aplikacja hosta|Zwracany typ wartości|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|<xref:Microsoft.Office.Interop.PowerPoint.Application>|
|Microsoft Office Project|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Microsoft.Office.Interop.Visio.Application|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 Poniższy przykład kodu pokazuje sposób użycia `Application` pola, aby utworzyć nowy skoroszyt w dodatku narzędzi VSTO dla programu Microsoft Office Excel. W tym przykładzie jest przeznaczona do uruchamiania z `ThisAddIn` klasy.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Aby zrobić to samo z poza `ThisAddIn` klasy, należy użyć `Globals` do dostępu do obiektu `ThisAddIn` klasy. Aby uzyskać więcej informacji na temat `Globals` obiektu, zobacz [globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Aby uzyskać więcej informacji na temat modeli obiektów określonych aplikacji pakietu Microsoft Office zobacz następujące tematy:

-   [Model obiektu Excel ― omówienie](../vsto/excel-object-model-overview.md)

-   [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)

-   [Model obiektu Outlook ― omówienie](../vsto/outlook-object-model-overview.md)

-   [Rozwiązania InfoPath](../vsto/infopath-solutions.md)

-   [PowerPoint — rozwiązania](../vsto/powerpoint-solutions.md)

-   [Rozwiązania projektu](../vsto/project-solutions.md)

-   [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)

###  <a name="AccessingDocuments"></a> Dostęp do dokumentu, podczas uruchamiania aplikacji pakietu Office
 Nie wszystkie [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] aplikacje automatycznie otworzyć dokument po uruchomieniu je i żaden [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] aplikacje otworzyć dokument po ich uruchomieniu. W związku z tym, nie dodawaj kodu w `ThisAdd-In_Startup` programu obsługi zdarzeń, jeśli kod wymaga dokument jest otwarty. Zamiast tego należy dodać kod do zdarzenia, które wywołuje aplikacji pakietu Office, gdy użytkownik tworzy lub otwiera dokument. W ten sposób można gwarantuje, że dokument jest otwarty, zanim kod wykonuje operacje na nim.

 Poniższy przykład kodu współpracuje z dokumentu programu Word, tylko wtedy, gdy użytkownik tworzy dokument lub otwiera istniejący dokument.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn członków do użycia w celu wykonania innych zadań
 Poniższa tabela opisuje innych typowych zadań i pokazuje, którzy członkowie `ThisAddIn` klasy, można użyć do wykonywania zadań.

|Zadanie|Element członkowski do użycia|
|----------|-------------------|
|Uruchom kod, aby zainicjować dodatku narzędzi VSTO dla programów, gdy jest ładowany dodatku narzędzi VSTO.|Dodaj kod, aby `ThisAddIn_Startup` metody. Jest to domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Startup> zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|
|Uruchom kod, aby wyczyścić zasoby używane przez dodatek narzędzi VSTO dla programów przed dodatku narzędzi VSTO jest zwalniana.|Dodaj kod, aby `ThisAddIn_Shutdown` metody. Jest to domyślny program obsługi zdarzeń dla <xref:Microsoft.Office.Tools.AddInBase.Shutdown> zdarzeń. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md). **Uwaga:**  W programie Outlook, domyślnie `ThisAddIn_Startup` program obsługi zdarzeń nie zawsze jest wywoływany podczas dodatku narzędzi VSTO jest zwalniana. Aby uzyskać więcej informacji, zobacz [zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|
|Wyświetlanie niestandardowego okienka zadań.|Użyj `CustomTaskPanes` pola. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md).|
|Udostępnianie obiektów w dodatku narzędzi VSTO dla programów do innych rozwiązań programu Microsoft Office.|Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Dostosowywanie funkcji w systemie Microsoft Office, implementując interfejs rozszerzalności.|Zastąp <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodę, aby zwrócić wystąpienia klasy, która implementuje interfejs. Aby uzyskać więcej informacji, zobacz [dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Uwaga:**  Aby dostosować interfejs użytkownika wstążki, możesz również zastąpić <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> metody.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Omówienie konstrukcji thisaddin — klasa
 W przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], <xref:Microsoft.Office.Tools.AddIn> jest interfejsem. `ThisAddIn` Klasa pochodzi od <xref:Microsoft.Office.Tools.AddInBase> klasy. Ta klasa bazowa przekierowuje wszystkie wywołania do swoich elementów członkowskich do wewnętrzną implementację <xref:Microsoft.Office.Tools.AddIn> interfejsu w [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)].

 W projektach dodatku narzędzi VSTO dla programu Outlook `ThisAddIn` klasa pochodzi od `Microsoft.Office.Tools.Outlook.OutlookAddIn` klas w projektach przeznaczonych dla programu .NET Framework 3.5, a także z <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> w przypadku projektów, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Tych klas bazowych zapewniają nowe funkcje do obsługi regionów formularza. Aby uzyskać więcej informacji na temat regionów formularzy zobacz [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji pakietu Microsoft Office
 Aplikacje interfejsu użytkownika pakietu Microsoft Office można dostosować programowo przy użyciu dodatku narzędzi VSTO. Można na przykład dostosowania wstążki, wyświetlić niestandardowego okienka zadań lub Utwórz region formularza niestandardowego w programie Outlook. Aby uzyskać więcej informacji, zobacz [dostosowywania interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

 Program Visual Studio udostępnia projektantów i klas, które służą do tworzenia niestandardowych okienek zadań, dostosowań Wstążki i regionach formularzy programu Outlook. Te klasy i projektanci pomoc, aby uprościć proces dostosowywania tych funkcji. Aby uzyskać więcej informacji, zobacz [niestandardowych okienek zadań](../vsto/custom-task-panes.md), [projektanta wstążki](../vsto/ribbon-designer.md), i [regionach formularzy programu Outlook z tworzenia](../vsto/creating-outlook-form-regions.md).

 Jeśli chcesz dostosować jeden z tych funkcji w taki sposób, że nie jest obsługiwana przez klasy i projektantów, można również dostosować te funkcje, implementując *interfejsu rozszerzalności* w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Ponadto można zmodyfikować dokumentów interfejsu użytkownika programu Word i skoroszytów programu Excel, generowania elementów hosta, które rozszerzają zachowanie dokumenty i skoroszyty. Pozwala na dodawanie formantów zarządzanego do dokumentów i arkuszy. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Wywoływanie kodu w dodatkach VSTO z innych rozwiązań
 Obiekty można ujawnić w dodatku narzędzi VSTO dla programów do innych rozwiązań, w tym innych rozwiązań pakietu Office. Jest to przydatne, jeśli dodatku narzędzi VSTO dla programów udostępnia usługę, aby włączyć innych rozwiązań do użycia. Na przykład jeśli masz dodatku narzędzi VSTO dla programu Microsoft Office Excel wykonuje obliczenia na dane finansowe z usługi sieci web, innych rozwiązań może wykonywania tych obliczeń przez wywołanie dodatku narzędzi VSTO programu Excel w czasie wykonywania.

 Aby uzyskać więcej informacji, zobacz [wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Zobacz także
- [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Wywoływanie kodu w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Przewodnik: Wywoływanie kodu w dodatku VSTO z kodu VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Dostosowywanie funkcji interfejsu użytkownika, korzystając z rozszerzalności interfejsów](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
