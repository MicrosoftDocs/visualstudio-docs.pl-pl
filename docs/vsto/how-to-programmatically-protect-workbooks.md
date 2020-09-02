---
title: 'Instrukcje: programowane włączanie ochrony skoroszytów'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, passwords
- documents [Office development in Visual Studio], document protection
- workbooks, unprotecting
- document protection, removing from workbooks
- document protection, adding to workbooks
- workbooks, protecting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ee7444c63c2d774e9b22ea612049f09429729c79
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85537634"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Instrukcje: programowane włączanie ochrony skoroszytów
  Możesz chronić Microsoft Office skoroszyt programu Excel, aby użytkownicy nie mogli dodawać ani usuwać arkuszy, a także programowo wyłączyć ochronę skoroszytu. Opcjonalnie możesz określić hasło, wskazać, czy ma być chroniona struktura (w związku z czym użytkownicy nie mogą przenosić arkuszy) i wskazać, czy ma być chroniona w systemie Windows.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Ochrona skoroszytu nie uniemożliwia użytkownikom edytowania komórek. Aby chronić dane, należy chronić arkusze. Aby uzyskać więcej informacji, zobacz [jak: programowo chronić arkusze](../vsto/how-to-programmatically-protect-worksheets.md).

 Poniższy przykład kodu używa zmiennej, aby zawierała hasło uzyskane od użytkownika.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Ochrona skoroszytu, który jest częścią dostosowania na poziomie dokumentu

### <a name="to-protect-a-workbook"></a>Aby chronić skoroszyt

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodę skoroszytu i Dołącz hasło. Aby użyć następującego przykładu kodu, należy uruchomić go w `ThisWorkbook` klasie, a nie w klasie arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#10)]
     [!code-vb[Trin_VstcoreExcelAutomation#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#10)]

### <a name="to-unprotect-a-workbook"></a>Aby wyłączyć ochronę skoroszytu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> metodę, przekazując hasło, jeśli jest to wymagane. Aby użyć następującego przykładu kodu, należy uruchomić go w `ThisWorkbook` klasie, a nie w klasie arkusza.

     [!code-csharp[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs#11)]
     [!code-vb[Trin_VstcoreExcelAutomation#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb#11)]

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Ochrona skoroszytu przy użyciu dodatku na poziomie aplikacji

### <a name="to-protect-a-workbook"></a>Aby chronić skoroszyt

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> metodę skoroszytu i Dołącz hasło. Ten przykład kodu używa aktywnego skoroszytu. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#6)]

### <a name="to-unprotect-a-workbook"></a>Aby wyłączyć ochronę skoroszytu

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> metodę aktywnego skoroszytu, przekazując hasło, jeśli jest to wymagane. Aby użyć tego przykładu, należy uruchomić kod z `ThisAddIn` klasy w projekcie.

     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#7)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#7](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#7)]

## <a name="see-also"></a>Zobacz też
- [Pracuj ze skoroszytami](../vsto/working-with-workbooks.md)
- [Instrukcje: programowe Włączanie ochrony arkuszy](../vsto/how-to-programmatically-protect-worksheets.md)
- [Instrukcje: programowe ukrywanie arkuszy](../vsto/how-to-programmatically-hide-worksheets.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
