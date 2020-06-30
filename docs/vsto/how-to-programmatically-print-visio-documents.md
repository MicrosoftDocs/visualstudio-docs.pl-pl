---
title: 'Instrukcje: Programowane drukowanie dokumentów programu Visio'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], printing Visio documents
- documents [Office development in Visual Studio], printing Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0e31a55e49d42311b5ec5fff82769584cc55ce09
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537803"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Instrukcje: Programowane drukowanie dokumentów programu Visio
  Można wydrukować kompletny dokument programu Microsoft Office Visio lub tylko określoną stronę.

 Aby uzyskać szczegółowe informacje o metodach drukowania, zobacz dokumentację referencyjną języka VBA dla [Microsoft.Office.Interop.Visio.Document. Metoda Print](/office/vba/api/Visio.Document.Print) oraz Metoda [Microsoft. Office. Interop. Visio. Page. Print](/office/vba/api/Visio.Page.Print) .

## <a name="print-a-visio-document"></a>Drukowanie dokumentu programu Visio

### <a name="to-print-a-complete-document"></a>Aby wydrukować kompletny dokument

- Wywołaj `Microsoft.Office.Interop.Visio.Document.Print` metodę `Microsoft.Office.Interop.Visio.Document` obiektu, który chcesz wydrukować.

     Poniższy przykład kodu Drukuje aktywny dokument. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#8)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#8](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#8)]

## <a name="print-a-page-of-a-visio-document"></a>Drukowanie strony dokumentu programu Visio

### <a name="to-print-a-page-of-a-document"></a>Aby wydrukować stronę dokumentu

- Wywołaj `Microsoft.Office.Interop.Visio.Pages.Print` metodę `Microsoft.Office.Interop.Visio.Pages` obiektu, który chcesz wydrukować.

     Poniższy przykład kodu drukuje pierwszą stronę aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#9)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#9](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#9)]

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Instrukcje: Programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Instrukcje: Programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Instrukcje: Programowane Zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Instrukcje: programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)
