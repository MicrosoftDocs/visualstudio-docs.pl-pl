---
title: 'Instrukcje: Tworzenie i modyfikowanie właściwości dokumentu niestandardowego'
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
ms.openlocfilehash: 6dd4f4ada36be4ef7b70f4f32d659abb10c8a62a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547215"
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

## <a name="see-also"></a>Zobacz też
- [Dodatki narzędzi VSTO programu](../vsto/programming-vsto-add-ins.md)
- [Dostosowywanie na poziomie dokumentu programu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: odczytywanie i zapisywanie właściwości dokumentu](../vsto/how-to-read-from-and-write-to-document-properties.md)
