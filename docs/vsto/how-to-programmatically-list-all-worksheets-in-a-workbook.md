---
title: Jak programowo wyświetlić listę wszystkich arkuszy w skoroszycie
description: Dowiedz się, jak programowo wyświetlić listę wszystkich arkuszy w skoroszycie programu Microsoft Excel przy użyciu Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, listing worksheets
- worksheets, listing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: c0cdd57c801617d8b3c37df28b91faae378bc4cc
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824903"
---
# <a name="how-to-programmatically-list-all-worksheets-in-a-workbook"></a>Jak programowo wyświetlić listę wszystkich arkuszy w skoroszycie
  Klasa <xref:Microsoft.Office.Interop.Excel.Workbook> udostępnia <xref:Microsoft.Office.Interop.Excel.Worksheets> obiekt . Ten obiekt zawiera kolekcję wszystkich <xref:Microsoft.Office.Interop.Excel.Worksheet> obiektów w skoroszycie.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-document-level-customization"></a>Aby wyświetlić listę wszystkich istniejących arkuszy w skoroszycie w dostosowywaniu na poziomie dokumentu

1. Iteruj po kolekcji i wysyłaj nazwy poszczególnych arkuszy do <xref:Microsoft.Office.Interop.Excel.Worksheets> przesunięcia komórki z <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet21":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet21":::

## <a name="to-list-all-existing-worksheets-in-a-workbook-in-a-vsto-add-in"></a>Aby wyświetlić listę wszystkich istniejących arkuszy w skoroszycie w dodatku VSTO

1. Iteruj po kolekcji i wysyłaj nazwy poszczególnych arkuszy do <xref:Microsoft.Office.Interop.Excel.Worksheets> przesunięcia komórki z <xref:Microsoft.Office.Interop.Excel.Range> obiektu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet13":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet13":::

## <a name="see-also"></a>Zobacz też
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [How to: Programowe dodawanie nowych arkuszy do skoroszytów](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [How to: Programowe przenoszenie arkuszy w obrębie skoroszytów](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
