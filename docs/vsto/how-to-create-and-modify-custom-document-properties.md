---
title: 'Instrukcje: Tworzenie i modyfikowanie właściwości dokumentu niestandardowego'
description: Dowiedz się, jak tworzyć i modyfikować właściwości dokumentu niestandardowego, jeśli są dostępne dodatkowe informacje, które mają być przechowywane w dokumencie.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4897008f102600bd222a21761237acc4bcb62a30
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96844299"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Instrukcje: Tworzenie i modyfikowanie właściwości dokumentu niestandardowego
  Aplikacje Microsoft Office wymienione powyżej zapewniają wbudowane właściwości, które są przechowywane w dokumentach. Ponadto można tworzyć i modyfikować właściwości dokumentu niestandardowego, jeśli istnieją dodatkowe informacje, które mają być przechowywane w dokumencie.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Użyj właściwości CustomDocumentProperties dokumentu do pracy z właściwościami niestandardowymi. Na przykład w projekcie na poziomie dokumentu dla Microsoft Office Excel, użyj <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> właściwości `ThisWorkbook` klasy. W projekcie dodatku VSTO dla programu Excel Użyj <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> właściwości <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiekt, który jest kolekcją <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Możesz użyć `Item` właściwości kolekcji, aby pobrać określoną właściwość według nazwy lub indeksu w kolekcji.

 Poniższy przykład pokazuje, jak dodać właściwość niestandardową do dostosowania na poziomie dokumentu dla programu Excel i przypisać ją do wartości.

## <a name="example"></a>Przykład
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Niezawodne programowanie
 Próba uzyskania dostępu do `Value` Właściwości niezdefiniowanych właściwości wywołuje wyjątek.

## <a name="see-also"></a>Zobacz także
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: odczytywanie i zapisywanie właściwości dokumentu](../vsto/how-to-read-from-and-write-to-document-properties.md)
