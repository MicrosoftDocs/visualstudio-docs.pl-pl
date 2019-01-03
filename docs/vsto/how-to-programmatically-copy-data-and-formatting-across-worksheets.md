---
title: 'Instrukcje: Programowe kopiowanie danych i formatowanie między arkuszami'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, copying data
- formatting [Office development in Visual Studio]
- data [Office development in Visual Studio], copying across worksheets
- copying data, Office development in Visual Studio
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9995b347fdfcb60acf72c79b0e1bddc20bab717b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924868"
---
# <a name="how-to-programmatically-copy-data-and-formatting-across-worksheets"></a>Instrukcje: Programowe kopiowanie danych i formatowanie między arkuszami
  Możesz skopiować dane z zakresu na jeden arkusz do innych arkuszy w skoroszycie za pomocą <xref:Microsoft.Office.Interop.Excel.Worksheets.FillAcrossSheets%2A> metody. Określ zakres, oraz czy mają zostać skopiowane dane, formatowanie lub obu.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## <a name="example"></a>Przykład  
 [!code-csharp[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#44)]
 [!code-vb[Trin_VstcoreExcelAutomation#44](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#44)]  
  
## <a name="compile-the-code"></a>Skompilować kod  
 W tym przykładzie wymaga danych o nazwie `rangeData` w arkuszu.  
  
## <a name="see-also"></a>Zobacz także  
 [Praca z arkuszami](../vsto/working-with-worksheets.md)   
 [Instrukcje: Programowe Dodawanie nowych arkuszy do skoroszytu](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Instrukcje: Programowe zmienianie formatowania w wierszach arkusza zawierających zaznaczone komórki](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)  
