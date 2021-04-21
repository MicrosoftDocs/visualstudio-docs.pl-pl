---
title: Zdarzenia w projektach pakietu Office
description: Dowiedz się, jak każdy szablon projektu pakietu Office generuje kilka programów obsługi zdarzeń i jak te programy obsługi zdarzeń różnią się nieco od obsługi zdarzeń dla dodatków VSTO.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Sheet1_Startup
- ThisDocument_Shutdown
- ThisDocument_Startup
- application-level add-ins [Office development in Visual Studio], events
- event handlers [Office development in Visual Studio]
- ThisWorkbook_Startup
- Sheet2_Startup
- ThisWorkbook_Shutdown
- document-level customizations [Office development in Visual Studio], events
- Sheet2_Shutdown
- Startup event
- Sheet3_Shutdown
- add-ins [Office development in Visual Studio], events
- Shutdown event
- ThisAddIn_Startup
- Sheet3_Startup
- Startup method [Office development in Visual Studio]
- Shutdown method [Office development in Visual Studio]
- Sheet1_Shutdown
- events [Office development in Visual Studio]
- ThisAddIn_Shutdown
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: be1625be3d8c3fce409562be948c83a34d40d7b1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825683"
---
# <a name="events-in-office-projects"></a>Zdarzenia w projektach pakietu Office
  Każdy szablon projektu pakietu Office automatycznie generuje kilka programów obsługi zdarzeń. Procedury obsługi zdarzeń dostosowań na poziomie dokumentu różnią się nieco od obsługi zdarzeń dla dodatków VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Projekty na poziomie dokumentu
 Visual Studio kod wygenerowany za nowymi lub istniejącymi dokumentami lub arkuszami w dostosowaniach na poziomie dokumentu. Ten kod zgłasza dwa różne zdarzenia: **uruchamianie i** **zamykanie**.

### <a name="startup-event"></a>Startup — Zdarzenie
 Zdarzenie **uruchamiania** jest wywoływane dla każdego z elementów hosta (dokumentu, skoroszytu lub arkusza) po uruchomieniu dokumentu i uruchomieniu całego kodu inicjalizacji w zestawie. Jest to ostatnia rzecz do uruchomienia w konstruktorze klasy, w których działa kod. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [Host items and host controls overview (Omówienie elementów hosta i kontrolek hosta).](../vsto/host-items-and-host-controls-overview.md)

 Podczas tworzenia projektu na poziomie dokumentu program Visual Studio procedury  obsługi zdarzeń dla zdarzenia uruchamiania w wygenerowanych plikach kodu:

- W Microsoft Office programu Word program obsługi zdarzeń ma nazwę `ThisDocument_Startup` .

- W Microsoft Office programu Excel procedury obsługi zdarzeń mają następujące nazwy:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown — Zdarzenie
 Zdarzenie **Zamknięcia** jest wywoływane dla każdego z elementów hosta (dokument lub arkusz), gdy domena aplikacji, w którym jest ładowany kod, zostanie zwolniona. Jest to ostatnia rzecz, która ma być wywoływana w klasie podczas zwalniania.

 Podczas tworzenia projektu na poziomie dokumentu program Visual Studio procedury obsługi  zdarzeń zamknięcia w wygenerowanych plikach kodu:

- W Microsoft Office programu Word program obsługi zdarzeń ma nazwę `ThisDocument_Shutdown` .

- W Microsoft Office programu Excel procedury obsługi zdarzeń mają następujące nazwy:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Nie należy programowo usuwać kontrolek podczas obsługi **zdarzeń** zamykania dokumentu. Elementy interfejsu użytkownika dokumentu nie są już dostępne po zdarzeniu **Zamknięcia.** Jeśli chcesz usunąć kontrolki przed zamknięciem aplikacji, dodaj kod do innej procedury obsługi zdarzeń, takiej jak **BeforeClose** lub **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Deklaracje metod procedury obsługi zdarzeń
 Każda deklaracja metody procedury obsługi zdarzeń ma przekazane te same argumenty: *nadawca* *i e*. W programie Excel *argument* nadawcy odwołuje się do arkusza, takiego jak lub ; w `Sheet1` `Sheet2` programie Word argument *nadawcy* odwołuje się do dokumentu. Argument *e* odwołuje się do standardowych argumentów zdarzenia, które nie są używane w tym przypadku.

 Poniższy przykład kodu przedstawia domyślne procedury obsługi zdarzeń w projektach na poziomie dokumentu dla programu Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet121":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet121":::

 Poniższy przykład kodu przedstawia domyślne procedury obsługi zdarzeń w projektach na poziomie dokumentu dla programu Excel.

> [!NOTE]
> Poniższy przykład kodu przedstawia procedury obsługi zdarzeń w `Sheet1` klasie . Nazwy programów obsługi zdarzeń w innych klasach elementów hosta odpowiadają nazwie klasy. Na przykład w klasie procedura obsługi zdarzeń `Sheet2` uruchamiania ma nazwę  `Sheet2_Startup` . W klasie `ThisWorkbook` procedura obsługi **zdarzeń** uruchamiania ma nazwę `ThisWorkbook_Startup` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet83":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet83":::

### <a name="order-of-events-in-document-level-excel-projects"></a>Kolejność zdarzeń w projektach programu Excel na poziomie dokumentu
 Procedury **obsługi zdarzeń** uruchamiania w projektach programu Excel są wywoływane w tej kolejności:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Inne arkusze w kolejności.

   Procedury **obsługi** zdarzeń zamknięcia w rozwiązaniu skoroszytu są wywoływane w tej kolejności:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Inne arkusze w kolejności.

    Kolejność jest określana podczas kompilowania projektu. Jeśli użytkownik zmienia kolejność arkuszy w czasie uruchamiania, nie zmienia kolejności wywoływania zdarzeń przy następnym otwarciu lub zamknięciu skoroszytu.

## <a name="vsto-add-in-projects"></a>Projekty dodatków VSTO
 Visual Studio kod wygenerowany w dodatki VSTO. Ten kod zgłasza dwa różne zdarzenia: <xref:Microsoft.Office.Tools.AddInBase.Startup> i <xref:Microsoft.Office.Tools.AddInBase.Shutdown> .

### <a name="startup-event"></a>Startup — Zdarzenie
 Zdarzenie jest wywoływane po załadowaniu dodatku VSTO i uruchomieniu całego <xref:Microsoft.Office.Tools.AddIn.Startup> kodu inicjowania w zestawie. To zdarzenie jest obsługiwane przez `ThisAddIn_Startup` metodę w wygenerowanym pliku kodu.

 Kod w programie obsługi zdarzeń jest pierwszym kodem użytkownika do uruchomienia, chyba że dodatek `ThisAddIn_Startup` VSTO zastępuje <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metodę . W tym przypadku program `ThisAddIn_Startup` obsługi zdarzeń jest wywoływany po <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> .

 Nie dodawaj kodu w programie obsługi zdarzeń, jeśli kod wymaga otwarcia `ThisAdd-In_Startup` dokumentu. Zamiast tego należy dodać ten kod do zdarzenia, które jest zgłaszane przez aplikację pakietu Office, gdy użytkownik utworzy lub otworzy dokument. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do dokumentu podczas uruchamiania aplikacji pakietu Office.](../vsto/programming-vsto-add-ins.md#AccessingDocuments)

 Aby uzyskać więcej informacji na temat sekwencji uruchamiania dodatków VSTO, zobacz [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)(Architektura dodatków VSTO).

### <a name="shutdown-event"></a>Shutdown — Zdarzenie
 Zdarzenie jest wywoływane, gdy domena aplikacji, w która jest ładowany <xref:Microsoft.Office.Tools.AddInBase.Shutdown> kod, zostanie zwolniona. To zdarzenie jest obsługiwane przez `ThisAddIn_Shutdown` metodę w wygenerowanym pliku kodu. Ta procedura obsługi zdarzeń jest ostatnim kodem użytkownika do uruchomienia po zwolniniu dodatku VSTO.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Zdarzenie zamknięcia w dodatekach VSTO programu Outlook
 Zdarzenie jest wywoływane tylko wtedy, gdy użytkownik wyłączy dodatek VSTO przy użyciu okna dialogowego Dodatki COM w <xref:Microsoft.Office.Tools.AddInBase.Shutdown> programie Outlook. Nie jest on wywoływany, gdy program Outlook kończy działanie. Jeśli masz kod, który musi zostać uruchomiony, gdy program Outlook zakończy działanie, obsłuż następujące zdarzenia:

- Zdarzenie <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> <xref:Microsoft.Office.Interop.Outlook.Application> obiektu.

- Zdarzenie <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektu.

> [!NOTE]
> Możesz wymusić, aby program Outlook zgłaszał zdarzenie podczas zamykania, <xref:Microsoft.Office.Tools.AddInBase.Shutdown> modyfikując rejestr. Jeśli jednak administrator przywróci to ustawienie, dowolny kod, który dodasz do metody, nie będzie już uruchamiany, gdy program `ThisAddIn_Shutdown` Outlook zakończy działanie. Aby uzyskać więcej informacji, zobacz Shutdown changes for Outlook 2010 (Zamykanie systemu zmian w [programie Outlook 2010).](/previous-versions/office/developer/office-2010/ee720183(v=office.14))

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [How to: Create Office projects in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Omówienie szablonów projektów pakietu Office](../vsto/office-project-templates-overview.md)
