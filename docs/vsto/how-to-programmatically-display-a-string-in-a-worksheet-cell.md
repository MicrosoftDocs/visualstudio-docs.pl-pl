---
title: 'Instrukcje: Programowe wyświetlanie ciągu w komórce arkusza'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- text [Office development in Visual Studio], adding to worksheets
- worksheets, displaying text in cells
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a9760d019fa80d4ecae63633c38ac9df60932202
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60101200"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>Instrukcje: Programowe wyświetlanie ciągu w komórce arkusza
  W tym przykładzie przedstawiono sposób wyświetlania tekstu w komórce programowo. Aby wyświetlić tekst w komórce, należy użyć <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Używanie formantu NamedRange
 W tym przykładzie użyto <xref:Microsoft.Office.Tools.Excel.NamedRange> formantu o nazwie `message`. Kontrolka musi zostać dodana do dostosowywania poziomie dokumentu, w czasie projektowania. Poniższy kod muszą być umieszczone w klasie arkusza, nie w `ThisWorkbook` klasy.

### <a name="to-display-text-in-a-namedrange-control"></a>Do wyświetlania tekstu w kontrolce NamedRange

1. Ustaw wartość <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolę **Witaj, świecie**.

     [!code-csharp[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#68)]

## <a name="use-a-native-excel-range"></a>Użyj natywnego zakresu programu Excel
 Poniższy kod tworzy nowy zakres programowo, a następnie przypisuje wartość do niego.

### <a name="to-display-text-in-an-excel-range"></a>Do wyświetlania tekstu w zakresie programu Excel

1. Pobieranie zakresu komórek **A1** na `Sheet1` i ustaw wartość **Witaj, świecie**.

     [!code-csharp[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#69)]

## <a name="see-also"></a>Zobacz także
- [Przewodnik: Zbieranie danych za pomocą formularza Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Rozwiązywanie problemów z rozwiązań pakietu Office](../vsto/troubleshooting-office-solutions.md)
- [Namedrange — formant](../vsto/namedrange-control.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
