---
title: 'Instrukcje: Tworzenie i modyfikowanie właściwości niestandardowego dokumentu'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 7d6ef8332a5adc21e25f2a414c5b359e48cf1ba7
ms.sourcegitcommit: 4d9c54f689416bf1dc4ace058919592482d02e36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/19/2019
ms.locfileid: "58194593"
---
# <a name="how-to-create-and-modify-custom-document-properties"></a>Instrukcje: Tworzenie i modyfikowanie właściwości niestandardowego dokumentu
  Aplikacje Microsoft Office, w wymienionych powyżej oferują wbudowanej właściwości, które są przechowywane z dokumentami. Ponadto możesz utworzyć i modyfikowanie właściwości niestandardowego dokumentu, jeśli ma dodatkowych informacji, które mają być przechowywane w dokumencie.

 [!INCLUDE[appliesto_docprops](../vsto/includes/appliesto-docprops-md.md)]

 Aby pracować z właściwości niestandardowe, należy użyć właściwości CustomDocumentProperties dokumentu. Na przykład w projekcie na poziomie dokumentu dla programu Microsoft Office Excel, należy użyć <xref:Microsoft.Office.Tools.Excel.Workbook.CustomDocumentProperties%2A> właściwość `ThisWorkbook` klasy. W projekcie dodatku narzędzi VSTO dla programu Excel, należy użyć <xref:Microsoft.Office.Interop.Excel._Workbook.CustomDocumentProperties%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Workbook> obiektu. Te właściwości zwracają <xref:Microsoft.Office.Core.DocumentProperties> obiektu, który jest kolekcją z <xref:Microsoft.Office.Core.DocumentProperty> obiektów. Możesz użyć `Item` właściwość kolekcji można pobrać określonej właściwości według nazwy lub indeksu w tej kolekcji.

 Poniższy przykład pokazuje, jak dodać właściwość niestandardową w dostosowaniu na poziomie dokumentu dla programu Excel i przypisać jej wartości.

## <a name="example"></a>Przykład
 [!code-vb[Trin_VstcoreProgramming#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/ThisWorkbook.vb#6)]
 [!code-csharp[Trin_VstcoreProgramming#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/ThisWorkbook.cs#6)]

## <a name="robust-programming"></a>Skuteczne programowanie
 Podjęto próbę dostępu `Value` właściwość niezdefiniowanymi właściwościami zgłasza wyjątek.

## <a name="see-also"></a>Zobacz także
- [Program dodatków narzędzi VSTO](../vsto/programming-vsto-add-ins.md)
- [Program dostosowań na poziomie dokumentu](../vsto/programming-document-level-customizations.md)
- [Instrukcje: Odczytywanie i zapisywanie właściwości dokumentów](../vsto/how-to-read-from-and-write-to-document-properties.md)
