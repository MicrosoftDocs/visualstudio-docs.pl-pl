---
title: 'How to: Create and modify custom document properties (Tworzyć i modyfikować niestandardowe właściwości dokumentu)'
description: Dowiedz się, jak tworzyć i modyfikować niestandardowe właściwości dokumentu, jeśli istnieją dodatkowe informacje, które chcesz przechowywać w dokumencie.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom document properties
- documents [Office development in Visual Studio], properties
- document properties [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cd89cb1e2991f48fefd9984eaa6d5894d9b506c1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826580"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>How to: Create and modify custom document properties (Tworzyć i modyfikować niestandardowe właściwości dokumentu)
  Aplikacje Microsoft Office wymienione powyżej zapewniają wbudowane właściwości, które są przechowywane z dokumentami. Ponadto można tworzyć i modyfikować niestandardowe właściwości dokumentu, jeśli istnieją dodatkowe informacje, które mają być przechowywane razem z dokumentem.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Użyj właściwości CustomDocumentProperties dokumentu, aby pracować z właściwościami niestandardowymi. Na przykład w projekcie na poziomie dokumentu dla Microsoft Office Excel użyj <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> właściwości `ThisWorkbook` klasy . W projekcie dodatku VSTO dla programu Excel użyj <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> właściwości <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu . Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiekt , który jest kolekcją <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Właściwość kolekcji umożliwia pobranie określonej właściwości według nazwy lub `Item` indeksu w kolekcji.

 W poniższym przykładzie pokazano, jak dodać właściwość niestandardową w dostosowywaniu na poziomie dokumentu dla programu Excel i przypisać do niego wartość.

## <a name="example"></a>Przykład
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb" id="Snippet6":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs" id="Snippet6":::

## <a name="robust-programming"></a>Niezawodne programowanie
 Próba uzyskania dostępu do `Value` właściwości dla niezdefiniowanych właściwości zgłasza wyjątek.

## <a name="see-also"></a>Zobacz też
- [Program VSTO Add-ins](../vsto/programming-vsto-add-ins.md)
- [Zaprogramowanie dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [How to: Read from and write to document properties ( Jak odczytywać właściwości dokumentu i zapisywać je w dokumencie)](../vsto/how-to-read-from-and-write-to-document-properties.md)
