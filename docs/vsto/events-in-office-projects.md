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
ms.openlocfilehash: 0fdea53ec99c4f95fb4bb9526b3f154bea5b662b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441825"
---
# <a name="events-in-office-projects"></a>Zdarzenia w projektach pakietu Office
  Każdy szablon projektu pakietu Office automatycznie generuje kilka programów obsługi zdarzeń. Programy obsługi zdarzeń w przypadku dostosowań na poziomie dokumentu są nieco inne niż dodatków narzędzi VSTO dla programów obsługi zdarzeń.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="document-level-projects"></a>Projektów na poziomie dokumentu
 Program Visual Studio udostępnia wygenerowany kod związany z nowych lub istniejących dokumentów lub arkuszy w dostosowaniach na poziomie dokumentu. Ten kod wywołuje dwóch różnych zdarzeń: **Uruchamianie** i **zamknięcia**.

### <a name="startup-event"></a>Startup — Zdarzenie
 **Uruchamiania** zdarzenie jest wywoływane dla każdego z elementów hosta (dokumentu, skoroszytu lub arkusza) po dokumentu i całego kodu inicjowania w zestawie została uruchomiona. To ostatnia rzecz do uruchamiania w konstruktorze klasy, działający w kodzie. Aby uzyskać więcej informacji na temat elementów hosta, zobacz [elementów, a omówienie kontrolek](../vsto/host-items-and-host-controls-overview.md).

 Podczas tworzenia projektów dokumentów programu Visual Studio tworzy obsługę zdarzeń dla **uruchamiania** zdarzenia w plikach wygenerowanego kodu:

- Dla projektów programu Microsoft Office Word, program obsługi zdarzeń o nazwie `ThisDocument_Startup`.

- Dla projektów programu Microsoft Office Excel programy obsługi zdarzeń mają następujące nazwy:

    - `Sheet1_Startup`

    - `Sheet2_Startup`

    - `Sheet3_Startup`

    - `ThisWorkbook_Startup`

### <a name="shutdown-event"></a>Shutdown — Zdarzenie
 **Zamknięcia** zdarzenie jest wywoływane dla każdego z elementów hosta (dokument lub arkusz) po domenie aplikacji, które Twój kod jest ładowany w chcesz zwolnić. Jest ostatnim zadaniem, które ma zostać wywołana w klasie, ponieważ zwalnia.

 Podczas tworzenia projektów dokumentów programu Visual Studio tworzy obsługę zdarzeń dla **zamknięcia** zdarzenia w plikach wygenerowanego kodu:

- Dla projektów programu Microsoft Office Word, program obsługi zdarzeń o nazwie `ThisDocument_Shutdown`.

- Dla projektów programu Microsoft Office Excel programy obsługi zdarzeń mają następujące nazwy:

    - `Sheet1_Shutdown`

    - `Sheet2_Shutdown`

    - `Sheet3_Shutdown`

    - `ThisWorkbook_Shutdown`

> [!NOTE]
> Nie usuwaj programowo kontrole podczas **zamknięcia** program obsługi zdarzeń dokumentu. Elementy interfejsu użytkownika w pliku nie są już dostępne podczas **zamknięcia** wystąpi zdarzenie. Jeśli chcesz usunąć kontrolki przed zamknięciem aplikacji, Dodaj kod do innego programu obsługi zdarzeń, takich jak **BeforeClose** lub **BeforeSave**.

### <a name="event-handler-method-declarations"></a>Deklaracje metody obsługi zdarzeń
 Co deklaracja metody obsługi zdarzeń ma te same argumenty przekazywane do niej: *nadawcy* i *e*. W programie Excel *nadawcy* argument odwołuje się do arkusza, takich jak `Sheet1` lub `Sheet2`; w programie Word, *nadawcy* argument, który odwołuje się do dokumentu. *e* argument, który odwołuje się do standardowych argumenty dla zdarzenia, które nie są używane w tym przypadku.

 Poniższy przykład kodu pokazuje domyślne programy obsługi zdarzeń w projektach na poziomie dokumentu dla programu Word.

 [!code-vb[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#121)]
 [!code-csharp[Trin_VstcoreWordAutomation#121](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#121)]

 Poniższy przykład kodu pokazuje domyślne programy obsługi zdarzeń w projektach na poziomie dokumentu dla programu Excel.

> [!NOTE]
> Poniższy przykład kodu pokazuje obsługę zdarzeń w `Sheet1` klasy. Nazwy programów obsługi zdarzeń w innych klas elementów hosta odpowiadać Nazwa klasy. Na przykład w `Sheet2` klasy **uruchamiania** nosi nazwę programu obsługi zdarzeń `Sheet2_Startup`. W `ThisWorkbook` klasy **uruchamiania** nosi nazwę programu obsługi zdarzeń `ThisWorkbook_Startup`.

 [!code-csharp[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#83)]
 [!code-vb[Trin_VstcoreExcelAutomation#83](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#83)]

### <a name="order-of-events-in-document-level-excel-projects"></a>Kolejność zdarzeń w projektach programu Excel poziomie dokumentu
 **Uruchamiania** są wywoływane programy obsługi zdarzeń w projektach programu Excel, w następującej kolejności:

1. `ThisWorkbook_Startup`.

2. `Sheet1_Startup`.

3. `Sheet2_Startup`.

4. `Sheet3_Startup`.

5. Inne arkusze w kolejności.

   **Zamknięcia** procedury obsługi zdarzeń w rozwiązaniu skoroszytu są wywoływane w następującej kolejności:

6. `ThisWorkbook_Shutdown`.

7. `Sheet1_Shutdown`.

8. `Sheet2_Shutdown`.

9. `Sheet3_Shutdown`.

10. Inne arkusze w kolejności.

    Kolejność jest określana podczas kompilowania projektu. Jeśli użytkownik zmienia arkuszy w czasie wykonywania, nie powoduje zmiany kolejności, że zdarzenia są wywoływane przy następnym otwarcie lub zamknięcie skoroszytu.

## <a name="vsto-add-in-projects"></a>Projekty dodatków narzędzi VSTO
 Program Visual Studio udostępnia wygenerowanego kodu w dodatkach VSTO. Ten kod wywołuje dwóch różnych zdarzeń: <xref:Microsoft.Office.Tools.AddInBase.Startup> i <xref:Microsoft.Office.Tools.AddInBase.Shutdown>.

### <a name="startup-event"></a>Startup — Zdarzenie
 <xref:Microsoft.Office.Tools.AddIn.Startup> Zdarzenie jest wywoływane po dodatku narzędzi VSTO zostanie załadowany i całego kodu inicjowania w zestawie została uruchomiona. To zdarzenie jest obsługiwane przez `ThisAddIn_Startup` metody w pliku wygenerowanego kodu.

 Możesz pisać kod w `ThisAddIn_Startup` procedura obsługi zdarzeń jest pierwszy kod użytkownika do uruchomienia, chyba że dodatku narzędzi VSTO dla programów zastępuje <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> metody. W tym przypadku `ThisAddIn_Startup` programu obsługi zdarzeń jest wywoływana po <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A>.

 Nie należy dodawać kod w `ThisAdd-In_Startup` programu obsługi zdarzeń, jeśli kod wymaga dokument jest otwarty. Zamiast tego należy dodać kod do zdarzenia, które wywołuje aplikacji pakietu Office, gdy użytkownik tworzy lub otwiera dokument. Aby uzyskać więcej informacji, zobacz [dostęp do dokumentu, podczas uruchamiania aplikacji Office](../vsto/programming-vsto-add-ins.md#AccessingDocuments).

 Aby uzyskać więcej informacji na temat sekwencji uruchamiania dodatków narzędzi VSTO dla programów, zobacz [architektury VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="shutdown-event"></a>Shutdown — Zdarzenie
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Zdarzenie jest wywoływane, gdy domena aplikacji, który Twój kod jest ładowany w ma zostać zwolniony. To zdarzenie jest obsługiwane przez `ThisAddIn_Shutdown` metody w pliku wygenerowanego kodu. Ta procedura obsługi zdarzeń jest ostatni kod użytkownika do uruchomienia po dodatku narzędzi VSTO jest zwalniana.

#### <a name="shutdown-event-in-outlook-vsto-add-ins"></a>Zdarzenie zamknięcia w dodatkach VSTO programu Outlook
 <xref:Microsoft.Office.Tools.AddInBase.Shutdown> Zdarzenie jest zgłaszane tylko wtedy, gdy użytkownik wyłącza dodatku narzędzi VSTO za pomocą okna dialogowego Dodatki COM w programie Outlook. Nie jest zgłaszany, gdy kończy działanie programu Outlook. Jeśli masz kod, który należy uruchomić, gdy kończy działanie programu Outlook, obsługują jedną z następujących zdarzeń:

- <xref:Microsoft.Office.Interop.Outlook.ApplicationEvents_11_Event.Quit> Zdarzenia <xref:Microsoft.Office.Interop.Outlook.Application> obiektu.

- <xref:Microsoft.Office.Interop.Outlook.ExplorerEvents_10_Event.Close> Zdarzenia <xref:Microsoft.Office.Interop.Outlook.Explorer> obiektu.

> [!NOTE]
> Można wymusić programu Outlook w celu podniesienia <xref:Microsoft.Office.Tools.AddInBase.Shutdown> zdarzenie, kiedy wychodzi przez modyfikację rejestru. Jednak jeśli administrator przywraca ustawienie, dowolny kod dodasz do `ThisAddIn_Shutdown` metoda jest już uruchamiany, gdy kończy działanie programu Outlook. Aby uzyskać więcej informacji, zobacz [zamykania zmian dla programu Outlook 2010](http://go.microsoft.com/fwlink/?LinkID=184614).

## <a name="see-also"></a>Zobacz także
- [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Instrukcje: Tworzenie projektów Office w Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Omówienie szablonów projektu pakietu Office](../vsto/office-project-templates-overview.md)
