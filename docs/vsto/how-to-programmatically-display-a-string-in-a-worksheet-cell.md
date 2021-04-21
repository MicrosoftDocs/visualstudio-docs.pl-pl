---
title: 'How to: Programowe wyświetlanie ciągu w komórce arkusza'
description: Dowiedz się, jak programowo wyświetlać ciąg w komórce arkusza programu Microsoft Excel przy użyciu kontrolki NamedRange lub natywnego obiektu zakresu programu Excel.
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
ms.openlocfilehash: 8a7bc48df6e30381ff275b9f11dabe04a25d6dd7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825930"
---
# <a name="how-to-programmatically-display-a-string-in-a-worksheet-cell"></a>How to: Programowe wyświetlanie ciągu w komórce arkusza
  W tym przykładzie pokazano, jak programowo wyświetlać tekst w komórce. Aby wyświetlić tekst w komórce, użyj <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki lub natywnego obiektu zakresu programu Excel.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="use-a-namedrange-control"></a>Używanie kontrolki NamedRange
 W tym przykładzie użyto <xref:Microsoft.Office.Tools.Excel.NamedRange> kontrolki o nazwie `message` . Kontrolkę należy dodać do dostosowania na poziomie dokumentu w czasie projektowania. Poniższy kod należy umieścić w klasie arkusza, a nie w `ThisWorkbook` klasie .

### <a name="to-display-text-in-a-namedrange-control"></a>Aby wyświetlić tekst w kontrolce NamedRange

1. Ustaw wartość kontrolki <xref:Microsoft.Office.Tools.Excel.NamedRange> na **Hello world**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet68":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet68":::

## <a name="use-a-native-excel-range"></a>Używanie natywnego zakresu programu Excel
 Poniższy kod tworzy nowy zakres programowo, a następnie przypisuje do niego wartość.

### <a name="to-display-text-in-an-excel-range"></a>Aby wyświetlić tekst w zakresie programu Excel

1. Pobierz zakres w komórce **A1** i `Sheet1` ustaw wartość na **Hello world**.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet69":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet69":::

## <a name="see-also"></a>Zobacz też
- [Przewodnik: zbieranie danych przy użyciu formularza systemu Windows](../vsto/walkthrough-collecting-data-using-a-windows-form.md)
- [Rozwiązywanie problemów z rozwiązaniami pakietu Office](../vsto/troubleshooting-office-solutions.md)
- [NamedRange, kontrolka](../vsto/namedrange-control.md)
- [Globalny dostęp do obiektów w projektach pakietu Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
