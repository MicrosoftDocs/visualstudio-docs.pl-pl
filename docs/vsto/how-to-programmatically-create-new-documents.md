---
title: 'Instrukcje: Programowe tworzenie nowych dokumentów'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 71610d0bd2e957d932e31d83d06aca914bf8b585
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71251953"
---
# <a name="how-to-programmatically-create-new-documents"></a>Instrukcje: Programowe tworzenie nowych dokumentów
  Gdy tworzysz dokument programowo, nowy dokument jest obiektem macierzystym <xref:Microsoft.Office.Interop.Word.Document> . Ten obiekt nie ma dodatkowych zdarzeń i możliwości <xref:Microsoft.Office.Tools.Word.Document> powiązania danych elementu hosta. Aby uzyskać więcej informacji, zobacz Ograniczenia programowe [elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Podczas opracowywania projektu na poziomie dokumentu nie można programowo dodawać <xref:Microsoft.Office.Tools.Word.Document> elementów hosta do projektu. W projekcie dodatku VSTO można przekonwertować dowolny <xref:Microsoft.Office.Interop.Word.Document> obiekt <xref:Microsoft.Office.Tools.Word.Document> na element hosta w czasie wykonywania. Aby uzyskać więcej informacji, zobacz sekcję [rozszerzając dokumenty programu Word i skoroszyty programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).

## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Aby utworzyć nowy dokument w oparciu o normalny szablon

- <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Użyj metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcji, aby utworzyć nowy dokument w oparciu o normalny szablon. Aby użyć tego przykładu kodu, należy uruchomić go `ThisDocument` z `ThisAddIn` lub klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]

## <a name="use-custom-templates"></a>Korzystanie z szablonów niestandardowych
 Metoda ma opcjonalny argument szablonu do tworzenia nowego dokumentu na podstawie szablonu innego niż normalny szablon. <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę szablonu.

### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Aby utworzyć nowy dokument na podstawie szablonu niestandardowego

- Wywołaj <xref:Microsoft.Office.Interop.Word.Documents> metodę kolekcji i określ ścieżkę do szablonu. <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Aby użyć tego przykładu kodu, należy uruchomić go `ThisDocument` z `ThisAddIn` lub klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)
- [Elementy hosta i formanty hosta — Omówienie](../vsto/host-items-and-host-controls-overview.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
