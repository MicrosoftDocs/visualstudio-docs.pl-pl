---
title: 'Instrukcje: Programowe otwieranie skoroszytów'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, opening
- Excel [Office development in Visual Studio], opening workbooks
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: facf3cbeb6635324e74244983fcb33138ad64cfe
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812388"
---
# <a name="how-to-programmatically-open-workbooks"></a>Instrukcje: Programowe otwieranie skoroszytów
  <xref:Microsoft.Office.Interop.Excel.Workbooks> Kolekcji w programie Microsoft Office Excel sprawia, że jest to możliwe do pracy ze skoroszytami wszystkie otwarte i otwieranie skoroszytów.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-open-an-existing-workbook"></a>Aby otworzyć istniejący skoroszyt

1. Użyj <xref:Microsoft.Office.Interop.Excel.Workbooks.Open%2A> metody <xref:Microsoft.Office.Interop.Excel.Workbooks> kolekcji, przekazując ścieżkę do skoroszytu.

     [!code-csharp[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#2)]
     [!code-vb[Trin_VstcoreExcelAutomation#2](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#2)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład kodu wymaga następujących elementów:

- Jest skoroszyt o nazwie `YourWorkbook.xls` muszą istnieć w katalogu o nazwie `Test` na dysku C.

## <a name="see-also"></a>Zobacz także
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [Instrukcje: Programowe otwieranie plików tekstowych jako skoroszytu](../vsto/how-to-programmatically-open-text-files-as-workbooks.md)
- [Instrukcje: Programowe tworzenie nowych skoroszytów](../vsto/how-to-programmatically-create-new-workbooks.md)
- [Instrukcje: Programowe zapisywanie skoroszytów](../vsto/how-to-programmatically-save-workbooks.md)
- [Instrukcje: Programowe zamykanie skoroszytów](../vsto/how-to-programmatically-close-workbooks.md)
- [Ograniczenia programowe elementów hosta i kontrolek hosta](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Host formantów Przegląd obiektów hosta i](../vsto/host-items-and-host-controls-overview.md)
