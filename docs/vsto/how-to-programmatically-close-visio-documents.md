---
title: 'Instrukcje: Programowe zamykanie dokumentów programu Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 9059e0f066cbd1dc6ced5f11f1139d7687afacf3
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56597210"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Instrukcje: Programowe zamykanie dokumentów programu Visio
  Możesz zamknąć aktywny dokument programu Microsoft Visio pakietu Office przy użyciu `Microsoft.Office.Interop.Visio.Document.Close` metody.

 Aby uzyskać szczegółowe informacje o tej metodzie, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Document.Close](/office/vba/api/Visio.Document.Close) metody.

## <a name="close-the-active-document"></a>Zamyka aktywny dokument.

### <a name="to-close-the-active-document"></a>Aby zamknąć aktywny dokument

-   Wywołaj `Microsoft.Office.Interop.Visio.Document.Close` metodę, aby zamknąć aktywny dokument.

     Aby użyć w poniższym przykładzie kodu, należy uruchomić go `ThisAddIn` klasy w projekcie dodatku narzędzi VSTO dla programu Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Zobacz także
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)
- [Instrukcje: Programowe tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Instrukcje: Programowe otwieranie dokumentów programu Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Instrukcje: Programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Instrukcje: Programowe drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)
