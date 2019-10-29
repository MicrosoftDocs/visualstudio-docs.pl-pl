---
title: Zdarzenia w projektach pakietu Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c8e8aca881ba25df134c675ac504ea0794c4b051
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986117"
---
# <a name="events-in-office-projects"></a>Zdarzenia w projektach pakietu Office
  Każdy szablon projektu pakietu Office automatycznie generuje kilka programów obsługi zdarzeń. Programy obsługi zdarzeń dla dostosowań na poziomie dokumentu różnią się nieco od programów obsługi zdarzeń dla dodatków narzędzi VSTO.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Projekty na poziomie dokumentu
 Program Visual Studio udostępnia wygenerowany kod za nowym lub istniejącymi dokumentami lub arkuszami w obszarze dostosowania na poziomie dokumentu. Ten kod wywołuje dwa różne zdarzenia: **Uruchamianie** i **wyłączanie**.

### <a name="startup-event"></a>Startup — Zdarzenie
 Zdarzenie **uruchamiania** jest wywoływane dla każdego elementu hosta (dokumentu, skoroszytu lub arkusza) po uruchomieniu dokumentu i został uruchomiony cały kod inicjalizacji w zestawie. Ostatnim krokiem jest uruchomienie w konstruktorze klasy, w której uruchomiono kod. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [Omówienie elementów hosta i formantów hosta](../vsto/host-items-and-host-controls-overview.md).

 Podczas tworzenia projektu na poziomie dokumentu program Visual Studio tworzy programy obsługi zdarzeń dla zdarzenia **uruchamiania** w wygenerowanych plikach kodu:

- W przypadku projektów programu Microsoft Office Word program obsługi zdarzeń ma nazwę `ThisDocument_Startup`.

- W przypadku Microsoft Office projektów programu Excel programy obsługi zdarzeń mają następujące nazwy:

  - `Sheet1_Startup`

  - `Sheet2_Startup`

  - `Sheet3_Startup`

  - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown — Zdarzenie
 Zdarzenie **zamknięcia** jest wywoływane dla każdego elementu hosta (dokumentu lub arkusza), gdy domena aplikacji, w której jest ładowany kod, zostanie zwolniona. Jest to ostatni element, który ma zostać wywołany w klasie podczas jej ładowania.

 Podczas tworzenia projektu na poziomie dokumentu program Visual Studio tworzy programy obsługi zdarzeń dla zdarzenia **zamknięcia** w wygenerowanych plikach kodu:

- W przypadku projektów programu Microsoft Office Word program obsługi zdarzeń ma nazwę `ThisDocument_Shutdown`.

- W przypadku Microsoft Office projektów programu Excel programy obsługi zdarzeń mają następujące nazwy:

  - `Sheet1_Shutdown`

  - `Sheet2_Shutdown`

  - `Sheet3_Shutdown`

  - `ThisWorkbook_Shutdown`

> [!NOTE]
> Nie należy programistycznie usuwać formantów podczas procedury obsługi zdarzeń **zamykania** dokumentu. Elementy interfejsu użytkownika dokumentu nie są już dostępne w przypadku wystąpienia zdarzenia **zamknięcia** . Jeśli chcesz usunąć formanty przed zamknięciem aplikacji, Dodaj kod do innego programu obsługi zdarzeń, takiego jak **BeforeClose** lub **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Deklaracje metody obsługi zdarzeń
 Każda deklaracja metody obsługi zdarzeń ma przekazane te same argumenty: *Sender* i *e*. W programie Excel argument *nadawcy* odwołuje się do arkusza, takiego jak `Sheet1` lub `Sheet2`; w programie Word argument *nadawcy* odwołuje się do dokumentu. Argument *e* odwołuje się do standardowych argumentów dla zdarzenia, które nie są używane w tym przypadku.

 Poniższy przykład kodu pokazuje domyślne programy obsługi zdarzeń w projektach na poziomie dokumentu dla programu Word.

 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]

 Poniższy przykład kodu pokazuje domyślne programy obsługi zdarzeń w projektach na poziomie dokumentu dla programu Excel.

> [!NOTE]
> Poniższy przykład kodu pokazuje procedury obsługi zdarzeń w klasie `Sheet1`. Nazwy programów obsługi zdarzeń w innych klasach elementów hosta odpowiadają nazwie klasy. Na przykład w klasie `Sheet2` program obsługi zdarzeń **uruchamiania** ma nazwę `Sheet2_Startup`. W klasie `ThisWorkbook` program obsługi zdarzeń **uruchamiania** ma nazwę `ThisWorkbook_Startup`.

 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]

### <a name="order-of-events-in-document-level-excel-projects"></a>Kolejność zdarzeń w projektach programu Excel na poziomie dokumentu
 Procedury obsługi zdarzeń **uruchamiania** w projektach programu Excel są wywoływane w następującej kolejności:

1. `ThisWorkbook_Startup`.,

2. `Sheet1_Startup`.,

3. `Sheet2_Startup`.,

4. `Sheet3_Startup`.,

5. Inne arkusze w kolejności.

   Programy obsługi zdarzeń **zamknięcia** w rozwiązaniu skoroszytu są wywoływane w następującej kolejności:

6. `ThisWorkbook_Shutdown`.,

7. `Sheet1_Shutdown`.,

8. `Sheet2_Shutdown`.,

9. `Sheet3_Shutdown`.,

10. Inne arkusze w kolejności.

    Kolejność jest określana podczas kompilowania projektu. Jeśli użytkownik zmieni rozmieszczenie arkuszy w czasie wykonywania, nie zmienia kolejności, w której zdarzenia są zgłaszane przy następnym otwarciu lub zamknięciu skoroszytu.

## <a name="vsto-add-in-projects"></a>Projekty dodatków VSTO
 Program Visual Studio udostępnia wygenerowany kod w dodatkach narzędzi VSTO. Ten kod wywołuje dwa różne zdarzenia: <xref:Microsoft.Office.Tools.AddInBase.Startup> i <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.

### <a name="startup-event"></a>Startup — Zdarzenie
 Zdarzenie <xref:Microsoft.Office.Tools.AddIn.Startup> jest wywoływane po załadowaniu dodatku VSTO i uruchomieniu wszystkich kodów inicjalizacji w zestawie. To zdarzenie jest obsługiwane przez metodę `ThisAddIn_Startup` w pliku wygenerowanego kodu.

 Kod w programie obsługi zdarzeń `ThisAddIn_Startup` to pierwszy kod użytkownika do uruchomienia, chyba że dodatek VSTO zastępuje metodę <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>. W takim przypadku program obsługi zdarzeń `ThisAddIn_Startup` jest wywoływany po <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.

 Nie dodawaj kodu w programie obsługi zdarzeń `ThisAdd-In_Startup`, jeśli kod wymaga otwarcia dokumentu. Zamiast tego należy dodać ten kod do zdarzenia, które aplikacja pakietu Office zgłasza, gdy użytkownik tworzy lub otwiera dokument. Aby uzyskać więcej informacji, zobacz [dostęp do dokumentu podczas uruchamiania aplikacji pakietu Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Aby uzyskać więcej informacji na temat sekwencji uruchamiania dodatków narzędzi VSTO, zobacz [Architektura dodatków narzędzi VSTO](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown — Zdarzenie
 Zdarzenie <xref:Microsoft.Office.Tools.AddInBase.Shutdown> jest zgłaszane, gdy domena aplikacji, w której jest ładowany kod, zostanie zwolniona. To zdarzenie jest obsługiwane przez metodę `ThisAddIn_Shutdown` w pliku wygenerowanego kodu. Ten program obsługi zdarzeń jest ostatnim kodem użytkownika do uruchomienia, gdy dodatek narzędzi VSTO zostanie zwolniony.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Zdarzenie zamknięcia w dodatkach narzędzia VSTO programu Outlook
 Zdarzenie <xref:Microsoft.Office.Tools.AddInBase.Shutdown> jest zgłaszane tylko wtedy, gdy użytkownik wyłączy dodatek VSTO przy użyciu okna dialogowego Dodatki COM w programie Outlook. Nie jest zgłaszane, gdy program Outlook zostanie zakończony. Jeśli masz kod, który musi być uruchamiany podczas zamykania programu Outlook, dojście jednego z następujących zdarzeń:

- Zdarzenie <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> obiektu <xref:Microsoft.Office.Interop.Outlook.Application>.

- Zdarzenie <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> obiektu <xref:Microsoft.Office.Interop.Outlook.Explorer>.

> [!NOTE]
> Można wymusić, aby program Outlook zgłaszał zdarzenie <xref:Microsoft.Office.Tools.AddInBase.Shutdown>, gdy zostanie on zakończony przez zmodyfikowanie rejestru. Jeśli jednak administrator powróci to ustawienie, dowolny kod, który zostanie dodany do metody `ThisAddIn_Shutdown`, nie będzie już uruchamiany po zamknięciu programu Outlook. Aby uzyskać więcej informacji, zobacz temat [zmiany w zamknięciu programu Outlook 2010](/previous-versions/office/developer/office-2010/ee720183(v=office.14)).

## <a name="see-also"></a>Zobacz także
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Szablony projektów pakietu Office — omówienie](../vsto/office-project-templates-overview.md)
