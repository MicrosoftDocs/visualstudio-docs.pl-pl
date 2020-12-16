---
title: 'Instrukcje: Programowane tworzenie nowych dokumentów'
description: Dowiedz się, jak można programowo tworzyć nowe dokumenty w programie Microsoft Word przy użyciu programu Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- templates [Office development in Visual Studio], custom document
- Word [Office development in Visual Studio], creating documents
- documents [Office development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a7168c6b80657fe0e5ba7c8ae8511c1e000db4cb
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525882"
---
# <a name="how-to-programmatically-create-new-documents"></a>Instrukcje: Programowane tworzenie nowych dokumentów
  Gdy tworzysz dokument programowo, nowy dokument jest <xref:Microsoft.Office.Interop.Word.Document> obiektem macierzystym. Ten obiekt nie ma dodatkowych zdarzeń i możliwości powiązania danych <xref:Microsoft.Office.Tools.Word.Document> elementu hosta. Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Podczas opracowywania projektu na poziomie dokumentu nie można programowo dodawać <xref:Microsoft.Office.Tools.Word.Document> elementów hosta do projektu. W projekcie dodatku VSTO można przekonwertować dowolny <xref:Microsoft.Office.Interop.Word.Document> obiekt na <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Aby utworzyć nowy dokument w oparciu o normalny szablon

- Użyj <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcji, aby utworzyć nowy dokument w oparciu o normalny szablon. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]

## <a name="use-custom-templates"></a>Korzystanie z szablonów niestandardowych
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A>Metoda ma opcjonalny argument *szablonu* do tworzenia nowego dokumentu na podstawie szablonu innego niż normalny szablon. Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę szablonu.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Aby utworzyć nowy dokument na podstawie szablonu niestandardowego

- Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metodę <xref:Microsoft.Office.Interop.Word.Documents> kolekcji i określ ścieżkę do szablonu. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
