---
title: 'Instrukcje: Programowe przenoszenie arkuszy w obrębie skoroszytu'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, moving
- workbooks, moving worksheets in
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7e62e397bd9f8c2a0e8e8c8b7ed6581e289a9efc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62812741"
---
# <a name="how-to-programmatically-move-worksheets-within-workbooks"></a>Instrukcje: Programowe przenoszenie arkuszy w obrębie skoroszytu
  Można programowo zmienić położenie arkuszy względem innych arkuszy w skoroszycie. Jeśli nie określisz lokalizacji przenoszony arkusz Excel utworzy nowy skoroszyt zawiera go.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="to-move-a-worksheet-in-a-document-level-customization"></a>Aby przenieść arkusza w dostosowaniu na poziomie dokumentu

1. Przypisz całkowita liczba arkuszy w skoroszycie do zmiennej, a następnie przenieś pierwszego arkusza, tak, aby stał się ostatni z nich.

     [!code-csharp[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#24)]
     [!code-vb[Trin_VstcoreExcelAutomation#24](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#24)]

## <a name="to-move-a-worksheet-in-a-vsto-add-in"></a>Aby przenieść arkusza w dodatku narzędzi VSTO

1. Przypisz całkowita liczba arkuszy w skoroszycie do zmiennej, a następnie przenieś pierwszego arkusza, tak, aby stał się ostatni z nich.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#16)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#16](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#16)]

## <a name="see-also"></a>Zobacz także
- [Praca z arkuszami](../vsto/working-with-worksheets.md)
- [Instrukcje: Programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Instrukcje: Programowe usuwanie arkuszy ze skoroszytu](../vsto/how-to-programmatically-delete-worksheets-from-workbooks.md)
- [Instrukcje: Programowe Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
