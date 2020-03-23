---
title: Dodatki programu VSTO
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
ms.openlocfilehash: 93470ebcea306d3cea762d60e061994b2bf27cc8
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/13/2020
ms.locfileid: "79301707"
---
# <a name="program-vsto-add-ins"></a>Dodatki programu VSTO
  Po rozszerzeniu aplikacji pakietu Microsoft Office przez utworzenie dodatku VSTO, należy napisać kod bezpośrednio względem `ThisAddIn` klasy w projekcie. Tej klasy można używać do wykonywania zadań, takich jak uzyskiwanie dostępu do modelu obiektowego aplikacji hosta pakietu Microsoft Office, dostosowywanie interfejsu użytkownika (UI) aplikacji i udostępnianie obiektów w dodatku VSTO do innych rozwiązań pakietu Office.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 Niektóre aspekty pisania kodu w projektach dodatku VSTO różnią się od innych typów projektów w programie Visual Studio. Wiele z tych różnic są spowodowane przez sposób modeli obiektów pakietu Office są narażone na kod zarządzany. Aby uzyskać więcej informacji, zobacz [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md).

 Aby uzyskać ogólne informacje na temat dodatków VSTO i innych typów rozwiązań, które można utworzyć za pomocą narzędzi deweloperskich pakietu Office w programie Visual Studio, zobacz [omówienie tworzenia rozwiązań pakietu Office &#40;&#41;VSTO ](../vsto/office-solutions-development-overview-vsto.md).

## <a name="use-the-thisaddin-class"></a>Użyj klasy ThisAddIn
 Możesz rozpocząć pisanie kodu dodatku `ThisAddIn` VSTO w klasie. Visual Studio automatycznie generuje tę klasę w pliku kodu *ThisAddIn.vb* (w) [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]lub *ThisAddIn.cs* (w języku C#) w projekcie dodatku VSTO. Automatycznie [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] wystąpienia tej klasy dla Ciebie, gdy aplikacja pakietu Microsoft Office ładuje dodatek VSTO.

 Istnieją dwa domyślne programy `ThisAddIn` obsługi zdarzeń w klasie. Aby uruchomić kod po załadowaniu dodatku VSTO, `ThisAddIn_Startup` dodaj kod do programu obsługi zdarzeń. Aby uruchomić kod tuż przed wyładowaniem dodatku VSTO, dodaj kod do programu obsługi `ThisAddIn_Shutdown` zdarzeń. Aby uzyskać więcej informacji na temat tych programów obsługi zdarzeń, zobacz [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

> [!NOTE]
> W programie Outlook `ThisAddIn_Shutdown` domyślnie program obsługi zdarzeń nie zawsze jest wywoływany, gdy dodatek VSTO jest zwalniany. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).

### <a name="access-the-object-model-of-the-host-application"></a>Dostęp do modelu obiektowego aplikacji hosta
 Aby uzyskać dostęp do modelu obiektu `Application` aplikacji hosta, należy użyć pola `ThisAddIn` klasy. To pole zwraca obiekt reprezentujący bieżące wystąpienie aplikacji hosta. W poniższej tabeli wymieniono typ `Application` wartości zwracanej pola w każdym projekcie dodatku VSTO.

|Aplikacja hosta|Typ wartości zwracanej|
|----------------------|-----------------------|
|Microsoft Office Excel|<xref:Microsoft.Office.Interop.Excel.Application>|
|Microsoft Office InfoPath|<xref:Microsoft.Office.Interop.InfoPath.Application>|
|Microsoft Office Outlook|<xref:Microsoft.Office.Interop.Outlook.Application>|
|Microsoft Office PowerPoint|[Aplikacja](/previous-versions/office/developer/office-2010/ff764034(v=office.14))|
|Projekt pakietu Microsoft Office|Microsoft.Office.Interop.MSProject.Application|
|Microsoft Office Visio|Aplikacja microsoft.office.interop.visio.|
|Microsoft Office Word|<xref:Microsoft.Office.Interop.Word.Application>|

 W poniższym przykładzie kodu `Application` pokazano, jak użyć tego pola do utworzenia nowego skoroszytu w dodatku VSTO dla programu Microsoft Office Excel. W tym przykładzie jest `ThisAddIn` przeznaczony do uruchomienia z klasy.

```vb
Dim newWorkbook As Excel.Workbook = Me.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = this.Application.Workbooks.Add(System.Type.Missing);
```

 Aby zrobić to samo `ThisAddIn` spoza klasy, `Globals` użyj obiektu, aby uzyskać dostęp do `ThisAddIn` klasy. Aby uzyskać więcej `Globals` informacji o obiekcie, zobacz [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md).

```vb
Dim newWorkbook As Excel.Workbook = Globals.ThisAddIn.Application.Workbooks.Add()
```

```csharp
Excel.Workbook newWorkbook = Globals.ThisAddIn.Application.Workbooks.Add(System.Type.Missing);
```

 Aby uzyskać więcej informacji na temat modeli obiektów określonych aplikacji pakietu Microsoft Office, zobacz następujące tematy:

- [Omówienie modelu obiektów programu Excel](../vsto/excel-object-model-overview.md)

- [Omówienie modelu obiektów programu Word](../vsto/word-object-model-overview.md)

- [Omówienie modelu obiektów programu Outlook](../vsto/outlook-object-model-overview.md)

- [Rozwiązania programu InfoPath](../vsto/infopath-solutions.md)

- [Rozwiązania powerpoint](../vsto/powerpoint-solutions.md)

- [Rozwiązania projektowe](../vsto/project-solutions.md)

- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)

### <a name="access-a-document-when-the-office-application-starts"></a><a name="AccessingDocuments"></a>Uzyskiwanie dostępu do dokumentu po uruchomieniu aplikacji pakietu Office
 Nie [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] wszystkie aplikacje automatycznie otwierają dokument po uruchomieniu, [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] a żadna z aplikacji nie otwiera dokumentu po uruchomieniu. W związku z tym nie `ThisAdd-In_Startup` należy dodawać kodu w programie obsługi zdarzeń, jeśli kod wymaga dokumentu, aby być otwarte. Zamiast tego dodaj ten kod do zdarzenia, które aplikacja pakietu Office wywołuje, gdy użytkownik tworzy lub otwiera dokument. W ten sposób można zagwarantować, że dokument jest otwarty, zanim kod wykonuje operacje na nim.

 Poniższy przykład kodu działa z dokumentem w programie Word tylko wtedy, gdy użytkownik utworzy dokument lub otworzy istniejący dokument.

 [!code-csharp[Trin_WordAddIn_Menus#3](../vsto/codesnippet/CSharp/trin_wordaddin_menus.cs/thisaddin.cs#3)]
 [!code-vb[Trin_WordAddIn_Menus#3](../vsto/codesnippet/VisualBasic/trin_wordaddin_menus.vb/thisaddin.vb#3)]

### <a name="thisaddin-members-to-use-for-other-tasks"></a>ThisAddIn członków do użycia w innych zadaniach
 W poniższej tabeli opisano inne typowe `ThisAddIn` zadania i pokazano, których członków klasy można używać do wykonywania zadań.

|Zadanie|Członek do użycia|
|----------|-------------------|
|Uruchom kod, aby zainicjować dodatek VSTO po załadowaniu dodatku VSTO.|Dodaj kod `ThisAddIn_Startup` do metody. Jest to domyślny program <xref:Microsoft.Office.Tools.AddInBase.Startup> obsługi zdarzeń dla zdarzenia. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|
|Uruchom kod, aby oczyścić zasoby używane przez dodatek VSTO przed wyładowaniem dodatku VSTO.|Dodaj kod `ThisAddIn_Shutdown` do metody. Jest to domyślny program <xref:Microsoft.Office.Tools.AddInBase.Shutdown> obsługi zdarzeń dla zdarzenia. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md). **Uwaga:**  W programie Outlook `ThisAddIn_Startup` domyślnie program obsługi zdarzeń nie zawsze jest wywoływany, gdy dodatek VSTO jest zwalniany. Aby uzyskać więcej informacji, zobacz [Zdarzenia w projektach pakietu Office](../vsto/events-in-office-projects.md).|
|Wyświetlanie niestandardowego okienka zadań.|Użyj `CustomTaskPanes` tego pola. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań](../vsto/custom-task-panes.md).|
|Uwidacznianie obiektów w dodatku VSTO do innych rozwiązań pakietu Microsoft Office.|Zastąd <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> w tej metodzie. Aby uzyskać więcej informacji, zobacz [Kod wywołania w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).|
|Dostosuj funkcję w systemie Microsoft Office, implementując interfejs rozszerzalności.|Zastądeń <xref:Microsoft.Office.Tools.AddInBase.RequestService%2A> metodę zwracania wystąpienia klasy, która implementuje interfejs. Aby uzyskać więcej informacji, zobacz [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md). **Uwaga:**  Aby dostosować interfejs użytkownika wstążki, można również <xref:Microsoft.Office.Tools.AddInBase.CreateRibbonExtensibilityObject%2A> zastąpić metodę.|

### <a name="understand-the-design-of-the-thisaddin-class"></a>Opis projektu thisaddin klasy
 W projektach, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] <xref:Microsoft.Office.Tools.AddIn> które są przeznaczone na , jest interfejsem. Klasa `ThisAddIn` pochodzi od <xref:Microsoft.Office.Tools.AddInBase> klasy. Ta klasa podstawowa przekierowuje wszystkie wywołania <xref:Microsoft.Office.Tools.AddIn> do [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]swoich członków do wewnętrznej implementacji interfejsu w .

 W projektach dodatku VSTO `ThisAddIn` dla programu Outlook `Microsoft.Office.Tools.Outlook.OutlookAddIn` klasa pochodzi od klasy w projektach przeznaczonych <xref:Microsoft.Office.Tools.Outlook.OutlookAddInBase> dla programu .NET Framework 3.5 oraz z projektów przeznaczonych dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]programu . Te klasy podstawowe zapewniają pewne dodatkowe funkcje do obsługi regionów formularza. Aby uzyskać więcej informacji o regionach formularza, zobacz [Tworzenie regionów formularzy programu Outlook](../vsto/creating-outlook-form-regions.md).

## <a name="customize-the-user-interface-of-microsoft-office-applications"></a>Dostosowywanie interfejsu użytkownika aplikacji pakietu Microsoft Office
 Można programowo dostosować interfejs użytkownika aplikacji pakietu Microsoft Office przy użyciu dodatku VSTO. Można na przykład dostosować wstążkę, wyświetlić niestandardowe okienko zadań lub utworzyć niestandardowy obszar formularza w programie Outlook. Aby uzyskać więcej informacji, zobacz [Dostosowywanie interfejsu użytkownika pakietu Office](../vsto/office-ui-customization.md).

 Program Visual Studio udostępnia projektantów i klasy, których można używać do tworzenia niestandardowych okienek zadań, dostosowań wstążki i regionów formularzy programu Outlook. Te projektanci i klasy pomagają uprościć proces dostosowywania tych funkcji. Aby uzyskać więcej informacji, zobacz [Niestandardowe okienka zadań,](../vsto/custom-task-panes.md) [Projektant wstążki](../vsto/ribbon-designer.md)i [Tworzenie regionów formularza programu Outlook](../vsto/creating-outlook-form-regions.md).

 Jeśli chcesz dostosować jedną z tych funkcji w sposób, który nie jest obsługiwany przez klasy i projektantów, można również dostosować te funkcje, implementując *interfejs rozszerzalności* w dodatku VSTO. Aby uzyskać więcej informacji, zobacz [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md).

 Ponadto można zmodyfikować interfejs użytkownika dokumentów programu Word i skoroszytów programu Excel, generując elementy hosta rozszerzające zachowanie dokumentów i skoroszytów. Umożliwia to dodawanie formantów zarządzanych do dokumentów i arkuszy. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="call-code-in-vsto-add-ins-from-other-solutions"></a>Kod wywoławów w dodatkach VSTO z innych rozwiązań
 Obiekty w dodatku VSTO można udostępnić na inne rozwiązania, w tym inne rozwiązania pakietu Office. Jest to przydatne, jeśli dodatek VSTO zapewnia usługę, której chcesz włączyć inne rozwiązania do użycia. Jeśli na przykład masz dodatek VSTO dla programu Microsoft Office Excel, który wykonuje obliczenia danych finansowych z usługi sieci web, inne rozwiązania mogą wykonywać te obliczenia, wywołując dodatek VSTO programu Excel w czasie wykonywania.

 Aby uzyskać więcej informacji, zobacz [Kod wywołania w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach vsto w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)
- [Kod wywołania w dodatkach VSTO z innych rozwiązań pakietu Office](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)
- [Instruktaż: Wywołanie kodu w dodatku VSTO z VBA](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Dostosowywanie funkcji interfejsu użytkownika przy użyciu interfejsów rozszerzalności](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
- [Jak: Tworzenie projektów pakietu Office w programie Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
