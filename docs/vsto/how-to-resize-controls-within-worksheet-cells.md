---
title: 'Instrukcje: zmiana rozmiaru kontrolek w komórkach arkusza'
description: Dowiedz się, jak można użyć programu Visual Studio do zmiany rozmiaru formantów w komórkach arkusza programu Microsoft Excel zarówno w czasie projektowania, jak i w czasie wykonywania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- controls [Office development in Visual Studio], resizing
- managed controls, resizing
- worksheets, resizing
- Windows Forms controls [Office development in Visual Studio], resizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7b62d3fed62b4d17b9f1918b76760593b38d83a9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99927824"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Instrukcje: zmiana rozmiaru kontrolek w komórkach arkusza
  W przypadku zmiany rozmiaru kolumn lub wierszy w arkuszu wszystkie kontrolki hosta w komórkach są automatycznie zmieniane na wysokość lub szerokość komórki, której rozmiar został zmieniony. Kontrolki Windows Forms domyślnie nie są zmieniane automatycznie.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Jeśli dodasz kontrolki w czasie projektowania, musisz ustawić opcje pozycjonowania dla każdej kontrolki.

 Jeśli dodasz kontrolkę Windows Forms programowo i podasz argument zakresu, formant automatycznie zmienia rozmiar, gdy zmieniany jest rozmiar komórki w zakresie. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md).

## <a name="resize-controls-at-design-time"></a>Zmień rozmiar kontrolek w czasie projektowania

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Aby zmienić rozmiar formantów w komórkach w czasie projektowania

1. Z **przybornika** przeciągnij formant Windows Forms do arkusza.

2. Kliknij prawym przyciskiem myszy kontrolkę, a następnie kliknij polecenie **Formatuj kontrolkę**.

3. W **kontrolce formatowanie** okna dialogowego kliknij kartę **Właściwości** .

4. W obszarze **pozycjonowanie obiektów** wybierz opcję **Przenieś i Skaluj z komórkami** , a następnie kliknij przycisk **OK**.

     Gdy zmieniasz rozmiar komórki, która zawiera kontrolkę, zmienia rozmiar kontrolki, aby dopasować ją do komórki.

## <a name="resize-controls-at-run-time"></a>Zmień rozmiar kontrolek w czasie wykonywania
 Jeśli dodasz kontrolkę Windows Forms w czasie wykonywania i przekażesz ją <xref:Microsoft.Office.Interop.Excel.Range> jako lokalizację kontrolki, zostanie ona automatycznie zmieniona, gdy zmienia się rozmiar komórki arkusza zawierającej zakres.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Aby zmienić rozmiar kontrolek w komórkach w czasie wykonywania

1. Dodaj kontrolkę do zakresu a1.

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#5)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#5](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#5)]

     Gdy zmieniasz rozmiar komórki, która zawiera kontrolkę, zmienia rozmiar kontrolki, aby dopasować ją do komórki.

## <a name="reset-control-placement"></a>Resetuj położenie kontrolki
 Możesz zresetować położenie i zmienić rozmiar kontrolki, ustawiając `Placement` Właściwość na jedną z następujących <xref:Microsoft.Office.Interop.Excel.XlPlacement> wartości:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Aby zmienić zachowanie kontrolki w taki sposób, aby nie zmieniała rozmiaru ani nie przenoszona z komórką

1. Wywołaj Właściwość umieszczania kontrolki i ustaw wartość na <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     [!code-vb[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb#6)]
     [!code-csharp[Trin_VstcoreProgrammingControlsExcel#6](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs#6)]

## <a name="see-also"></a>Zobacz też
- [Formanty w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Instrukcje: Dodawanie formantów Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Instrukcje: ukrywanie kontrolek w arkuszach podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie wykonywania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ograniczenia Windows Forms formantów w dokumentach pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
