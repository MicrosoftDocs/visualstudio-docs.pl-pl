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
manager: douge
ms.workload:
- office
ms.openlocfilehash: 882183d1e23168e1a3a833cd7cc723f28ce1a139
ms.sourcegitcommit: 73861cd0ea92e50a3be1ad2a0ff0a7b07b057a1c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2019
ms.locfileid: "54154125"
---
# <a name="how-to-programmatically-create-new-documents"></a>Instrukcje: Programowe tworzenie nowych dokumentów
  Po utworzeniu dokumentu programowo nowy dokument jest natywny <xref:Microsoft.Office.Interop.Word.Document> obiektu. Ten obiekt nie ma dodatkowych zdarzeń i możliwości wiązania danych <xref:Microsoft.Office.Tools.Word.Document> element hosta. Aby uzyskać więcej informacji, zobacz [ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 Podczas tworzenia projektów dokumentów nie można programowo dodać <xref:Microsoft.Office.Tools.Word.Document> hosta elementy do projektu. W projekcie dodatku narzędzi VSTO dla programów, należy przekonwertować którekolwiek <xref:Microsoft.Office.Interop.Word.Document> obiekt <xref:Microsoft.Office.Tools.Word.Document> element hosta w czasie wykonywania. Aby uzyskać więcej informacji, zobacz [Rozszerzanie dokumentów programu Word i skoroszytów programu Excel w dodatkach VSTO w czasie wykonywania](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md).  
  
## <a name="to-create-a-new-document-based-on-the-normal-template"></a>Aby utworzyć nowy dokument oparty na szablonie normalnego  
  
-   Użyj <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcję, aby utworzyć nowy dokument oparty na szablonie normalny. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#1)]
     [!code-csharp[Trin_VstcoreWordAutomation#1](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#1)]  
  
## <a name="use-custom-templates"></a>Użyj szablonów niestandardowych  
 <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> Metoda ma opcjonalny *szablonu* argumentu, aby utworzyć nowy dokument oparty na szablonie inne niż szablonu normalnej. Musisz podać nazwę pliku i w pełni kwalifikowana ścieżka szablonu.  
  
### <a name="to-create-a-new-document-based-on-a-custom-template"></a>Aby utworzyć nowy dokument oparty na szablonie niestandardowym  
  
-   Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Add%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> kolekcji i określ ścieżkę do szablonu. Aby wykorzystać ten przykład kodu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#2)]
     [!code-csharp[Trin_VstcoreWordAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#2)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe otwieranie istniejących dokumentów](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)   
 [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
