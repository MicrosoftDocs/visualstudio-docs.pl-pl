---
title: Jak programowo chronić skoroszyty
description: Dowiedz się, jak chronić skoroszyt programu Microsoft Excel, aby użytkownicy nie mogą dodawać ani usuwać arkuszy, a także wyłączyć ochronę skoroszytu programowo.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9f0b479c56be6da7b14f87263c8c01d66910ac20
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827113"
---
# <a name="how-to-programmatically-protect-workbooks"></a>Jak programowo chronić skoroszyty
  Możesz chronić skoroszyt programu Microsoft Office Excel, aby użytkownicy nie mogą dodawać ani usuwać arkuszy, a także wyłączyć ochronę skoroszytu programowo. Opcjonalnie możesz określić hasło, wskazać, czy chcesz chronić strukturę (aby użytkownicy nie mogą przenosić arkuszy) i wskazać, czy chcesz chronić okna skoroszytu.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 Ochrona skoroszytu nie zatrzymuje użytkownikom możliwości edytowania komórek. Aby chronić dane, należy chronić arkusze. Aby uzyskać więcej informacji, [zobacz How to: Programmatically protect arkusze](../vsto/how-to-programmatically-protect-worksheets.md).

 W poniższych przykładach kodu zmienna zawiera hasło uzyskane od użytkownika.

## <a name="protect-a-workbook-that-is-part-of-a-document-level-customization"></a>Ochrona skoroszytu, który jest częścią dostosowania na poziomie dokumentu

### <a name="to-protect-a-workbook"></a>Aby chronić skoroszyt

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A> metodę skoroszytu i dołącz hasło. Aby użyć poniższego przykładu kodu, uruchom go w `ThisWorkbook` klasie , a nie w klasie arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet10":::

### <a name="to-unprotect-a-workbook"></a>Aby wyłączyć ochronę skoroszytu

1. Wywołaj <xref:Microsoft.Office.Tools.Excel.Workbook.Unprotect%2A> metodę , przekazując hasło, jeśli jest to wymagane. Aby użyć poniższego przykładu kodu, uruchom go w `ThisWorkbook` klasie , a nie w klasie arkusza.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/ThisWorkbook.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/ThisWorkbook.vb" id="Snippet11":::

## <a name="protect-a-workbook-by-using-an-application-level-add-in"></a>Ochrona skoroszytu przy użyciu dodatku na poziomie aplikacji

### <a name="to-protect-a-workbook"></a>Aby chronić skoroszyt

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Protect%2A> metodę skoroszytu i dołącz hasło. W tym przykładzie kodu jest używany aktywny skoroszyt. Aby użyć tego przykładu, uruchom kod z `ThisAddIn` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet6":::

### <a name="to-unprotect-a-workbook"></a>Aby wyłączyć ochronę skoroszytu

1. Wywołaj <xref:Microsoft.Office.Interop.Excel._Workbook.Unprotect%2A> metodę aktywnego skoroszytu, przekazując hasło, jeśli jest to wymagane. Aby użyć tego przykładu, uruchom kod z `ThisAddIn` klasy w projekcie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet7":::

## <a name="see-also"></a>Zobacz też
- [Praca ze skoroszytami](../vsto/working-with-workbooks.md)
- [Jak programowo chronić arkusze](../vsto/how-to-programmatically-protect-worksheets.md)
- [How to: Programmatically hide arkusze](../vsto/how-to-programmatically-hide-worksheets.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
