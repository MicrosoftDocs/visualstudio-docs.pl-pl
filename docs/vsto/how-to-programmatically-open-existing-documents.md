---
title: 'Instrukcje: Programowe otwieranie istniejących dokumentów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 670c4855806dcc5d781da8479963f6705ba99fd3
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54869151"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Instrukcje: Programowe otwieranie istniejących dokumentów
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> Metoda otwiera określone przez w pełni kwalifikowaną ścieżkę i nazwę istniejącego dokumentu Microsoft Office Word. Ta metoda zwraca <xref:Microsoft.Office.Interop.Word.Document> reprezentujący otwarty dokument.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-open-a-document"></a>Aby otworzyć dokument  
  
-   Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metody <xref:Microsoft.Office.Interop.Word.Documents> zbierania i podaj ścieżkę do dokumentu.  
  
     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]  
  
## <a name="to-open-a-document-as-read-only"></a>Aby otworzyć dokument jako tylko do odczytu  
  
-   Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metody, podaj ścieżkę do dokumentu, a następnie ustaw *tylko do odczytu* argument **True** w wywołaniu metody.  
  
     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 Ten przykład kodu wymaga następujących elementów:  
  
-   Dokument o nazwie *NewDocument.doc* muszą istnieć w katalogu o nazwie *testu* na dysku C.  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)   
 [Instrukcje: Programowe zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
