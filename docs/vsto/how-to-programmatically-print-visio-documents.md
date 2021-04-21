---
title: Jak programowo drukować dokumenty programu Visio
description: Dowiedz się, jak wydrukować pełny dokument programu Microsoft Visio lub wydrukować tylko określoną stronę w tym dokumencie.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 13e18b1d1e20c836be740a6b44a591be6df6e926
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827191"
---
# <a name="how-to-programmatically-print-visio-documents"></a>Jak programowo drukować dokumenty programu Visio
  Możesz wydrukować pełny dokument Microsoft Office Visio lub tylko określoną stronę.

 Szczegółowe informacje na temat metod drukowania można znaleźć w dokumentacji referencyjnej dotyczącejMicrosoft.Office.Interop.Visio.Doc[VBA. Metoda](/office/vba/api/Visio.Document.Print) Print i [metoda Microsoft.Office.Interop.Visio.Page.Print.](/office/vba/api/Visio.Page.Print)

## <a name="print-a-visio-document"></a>Drukowanie dokumentu programu Visio

### <a name="to-print-a-complete-document"></a>Aby wydrukować pełny dokument

- Wywołaj `Microsoft.Office.Interop.Visio.Document.Print` metodę `Microsoft.Office.Interop.Visio.Document` obiektu, który chcesz wydrukować.

     Poniższy przykładowy kod drukuje aktywny dokument. Aby użyć tego przykładu, uruchom kod z `ThisAddIn` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet8":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet8":::

## <a name="print-a-page-of-a-visio-document"></a>Drukowanie strony dokumentu programu Visio

### <a name="to-print-a-page-of-a-document"></a>Aby wydrukować stronę dokumentu

- Wywołaj `Microsoft.Office.Interop.Visio.Pages.Print` metodę `Microsoft.Office.Interop.Visio.Pages` obiektu, który chcesz wydrukować.

     Poniższy przykład kodu drukuje pierwszą stronę aktywnego dokumentu. Aby użyć tego przykładu, uruchom kod z `ThisAddIn` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet9":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet9":::

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)
- [How to: Programmatically create new Visio documents (Tworzyć programowo nowe dokumenty programu Visio)](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Jak programowo otwierać dokumenty programu Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Pisano: Programowe zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [How to: Programmatically save Visio documents (2017: Programowe zapisywanie dokumentów programu Visio)](../vsto/how-to-programmatically-save-visio-documents.md)
