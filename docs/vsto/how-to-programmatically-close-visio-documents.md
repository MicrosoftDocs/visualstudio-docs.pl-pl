---
title: 'How to: Programmatically close Visio documents (2017: Programowe zamykanie dokumentów programu Visio)'
description: Dowiedz się, jak zamknąć aktywną Microsoft Office programu Visio przy użyciu Microsoft.Office.Interop.Visio.Document. Close, metoda.
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
ms.openlocfilehash: 8802cc34555fcb695c5554209255cb8fd9f154c2
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825306"
---
# <a name="how-to-programmatically-close-visio-documents"></a>How to: Programmatically close Visio documents (2017: Programowe zamykanie dokumentów programu Visio)
  Aktywny dokument programu Visio Microsoft Office zamknąć przy użyciu `Microsoft.Office.Interop.Visio.Document.Close` metody .

 Szczegółowe informacje na temat tej metody można znaleźć w dokumentacji referencyjnej dotyczącejMicrosoft.Office.Interop.Visio.Doc[ VBA. Close,](/office/vba/api/Visio.Document.Close) metoda.

## <a name="close-the-active-document"></a>Zamykanie aktywnego dokumentu

### <a name="to-close-the-active-document"></a>Aby zamknąć aktywny dokument

- Wywołaj `Microsoft.Office.Interop.Visio.Document.Close` metodę , aby zamknąć aktywny dokument.

     Aby użyć poniższego przykładu kodu, uruchom go w `ThisAddIn` klasie w projekcie dodatku narzędzi VSTO dla programu Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)
- [How to: Programmatically create new Visio documents (Tworzyć programowo nowe dokumenty programu Visio)](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [How to: Programmatically open Visio documents (2017: Programowe otwieranie dokumentów programu Visio)](../vsto/how-to-programmatically-open-visio-documents.md)
- [How to: Programmatically save Visio documents (2017: Programowe zapisywanie dokumentów programu Visio)](../vsto/how-to-programmatically-save-visio-documents.md)
- [How to: Programmatically print Visio documents (2017: Programowe drukowanie dokumentów programu Visio)](../vsto/how-to-programmatically-print-visio-documents.md)
