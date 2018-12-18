---
title: 'Porady: programowane drukowanie dokumentów programu Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6beed729ed670d5f34c645575795b625e03e9583
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671225"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Porady: programowane drukowanie dokumentów programu Visio
  Można wydrukować pełną dokumentu Microsoft Visio pakietu Office lub określonej strony.  
  
 Aby uzyskać szczegółowe informacje o metodach wydruku, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Document.Print](/office/vba/api/Visio.Document.Print) metody i [Microsoft.Office.Interop.Visio.Page.Print](/office/vba/api/Visio.Page.Print) — metoda .  
  
## <a name="print-a-visio-document"></a>Drukuj dokument programu Visio  
  
### <a name="to-print-a-complete-document"></a>Aby wydrukować pełnego dokumentu  
  
-   Wywołaj `Microsoft.Office.Interop.Visio.Document.Print` metody `Microsoft.Office.Interop.Visio.Document` obiekt, który chcesz wydrukować.  
  
     Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]  
  
## <a name="print-a-page-of-a-visio-document"></a>Wydrukować strony z dokumentu programu Visio  
  
### <a name="to-print-a-page-of-a-document"></a>Aby wydrukować stronę dokumentu  
  
-   Wywołaj `Microsoft.Office.Interop.Visio.Pages.Print` metody `Microsoft.Office.Interop.Visio.Pages` obiekt, który chcesz wydrukować.  
  
     Poniższy przykład kodu Drukuje aktywny dokument pierwszej strony. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane otwieranie dokumentów programu Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)  
  
  