---
title: 'Instrukcje: Programowane wyświetlanie ciągu w komórce arkusza'
description: Dowiedz się, jak programowo wyświetlić ciąg w komórce arkusza programu Microsoft Excel przy użyciu kontrolki NamedRange lub natywnego obiektu programu Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5a89716797ec460b461f79c94df8cea475532a8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99885563"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Instrukcje: Programowane wyświetlanie ciągu w komórce arkusza
  W tym przykładzie pokazano, jak w programie programowo wyświetlać tekst w komórce. Aby wyświetlić tekst w komórce, użyj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki lub natywnego obiektu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Korzystanie z kontrolki NamedRange
 W tym przykładzie używa <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `message` . Kontrolka musi zostać dodana do dostosowania na poziomie dokumentu w czasie projektowania. Poniższy kod musi być umieszczony w klasie arkusza, a nie w `ThisWorkbook` klasie.

### <a name="to-display-text-in-a-namedrange-control"></a>Aby wyświetlić tekst w kontrolce NamedRange

1. Ustaw wartość <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu na **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Użyj natywnego zakresu programu Excel
 Poniższy kod tworzy nowy zakres programowo, a następnie przypisuje do niego wartość.

### <a name="to-display-text-in-an-excel-range"></a>Aby wyświetlić tekst w zakresie programu Excel

1. Pobierz zakres w komórce **a1** na `Sheet1` i ustaw wartość na **Hello World**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Zobacz też
- [Przewodnik: zbieranie danych przy użyciu formularza systemu Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Rozwiązywanie problemów z rozwiązaniami pakietu Office](../vsto/troubleshooting-office-solutions.md)
- [NamedRange — formant](../vsto/namedrange-control.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
