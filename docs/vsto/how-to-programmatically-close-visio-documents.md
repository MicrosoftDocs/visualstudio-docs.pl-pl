---
title: 'Porady: programowane zamykanie dokumentów programu Visio'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d800fbe0a6dda6fc7c5160d607d393afcb920cd9
ms.sourcegitcommit: be938c7ecd756a11c9de3e6019a490d0e52b4190
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50671576"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Porady: programowane zamykanie dokumentów programu Visio
  Możesz zamknąć aktywny dokument programu Microsoft Visio pakietu Office przy użyciu `Microsoft.Office.Interop.Visio.Document.Close` metody.  
  
 Aby uzyskać szczegółowe informacje o tej metodzie, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) metody.  
  
## <a name="close-the-active-document"></a>Zamyka aktywny dokument.  
  
### <a name="to-close-the-active-document"></a>Aby zamknąć aktywny dokument  
  
-   Wywołaj `Microsoft.Office.Interop.Visio.Document.Close` metodę, aby zamknąć aktywny dokument.  
  
     Aby użyć w poniższym przykładzie kodu, należy uruchomić go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]  
  
## <a name="see-also"></a>Zobacz także  
 [Rozwiązania programu Visio](../vsto/visio-solutions.md)   
 [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)   
 [Porady: programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Porady: programowane otwieranie dokumentów programu Visio](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Porady: programowane zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)   
 [Porady: programowane drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  