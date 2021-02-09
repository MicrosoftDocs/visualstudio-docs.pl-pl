---
title: 'Instrukcje: Programowane Zamykanie dokumentów programu Visio'
description: Dowiedz się, jak zamknąć dokument aktywnego programu Microsoft Office Visio przy użyciu Microsoft.Office.Interop.Visio.Document. Zamknij metodę.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], closing Visio documents
- Visio [Office development in Visual Studio], closing Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c1592bd500103a2db42934ab8f81392a5f1fa0d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99903684"
---
# <a name="how-to-programmatically-close-visio-documents"></a>Instrukcje: Programowane Zamykanie dokumentów programu Visio
  Możesz zamknąć dokument programu Active Microsoft Office Visio przy użyciu `Microsoft.Office.Interop.Visio.Document.Close` metody.

 Aby uzyskać szczegółowe informacje na temat tej metody, zobacz dokumentację referencyjną języka VBA dla [Microsoft.Office.Interop.Visio.Document. Zamknij](/office/vba/api/Visio.Document.Close) metodę.

## <a name="close-the-active-document"></a>Zamknij aktywny dokument

### <a name="to-close-the-active-document"></a>Aby zamknąć aktywny dokument

- Wywołaj `Microsoft.Office.Interop.Visio.Document.Close` metodę, aby zamknąć aktywny dokument.

     Aby użyć następującego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku VSTO dla programu Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Instrukcje: Programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Instrukcje: Programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Instrukcje: programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Instrukcje: Programowane drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)
