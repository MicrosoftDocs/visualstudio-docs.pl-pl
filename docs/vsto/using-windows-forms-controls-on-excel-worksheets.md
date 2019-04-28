---
title: Użyj kontrolek Windows Forms w arkuszach Excel
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Windows Forms controls [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], Windows Forms controls
- controls [Office development in Visual Studio], Window Forms controls
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 032ee551ff04590ccdb8744c1274b137dec0b756
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62982318"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Użyj kontrolek Windows Forms w arkuszach Excel
  Możesz dodać kontrolek formularzy Windows Forms do skoroszyty programu Microsoft Office Excel w taki sam sposób, dodawanie formantów do formularzy Windows Forms. Aby uzyskać ogólne informacje na temat pracy z formanty w dokumentach, zobacz [kontrolek formularzy Windows w przegląd dokumentów pakietu Office](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Informacje dotyczące sterowania programu Excel
 Istnieje kilka istotnych kwestii, które są specyficzne dla programu Excel.

### <a name="match-control-size-to-cell-size"></a>Rozmiar kontrolki dopasowania do rozmiaru komórek
 Możesz ustawić kontroli rozmiaru automatycznie po zmianie rozmiaru komórki nadrzędnej. Aby uzyskać więcej informacji, zobacz [jak: Zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Dodawanie składników, które są współużytkowane przez wszystkie arkusze
 Możesz dodać składniki, które chcesz udostępnić wśród wszystkich arkuszy, takich jak <xref:System.Data.DataSet>, aby Projektant skoroszytów zamiast do arkuszy. Składnik pojawi się w zasobniku składnika.

### <a name="formula-for-embedding-controls"></a>Formuła dla osadzania formantów
 Po wybraniu kontrolki w programie Excel, zobaczysz **=EMBED("WinForms.Control.Host","")** w **pasek formuły**. Ten tekst jest wymagane i nie powinny być usuwane.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Zmiana rozmiaru formantów w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Instrukcje: Ukrywanie formantów w arkuszu podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Przewodnik: Zmiana formatowania arkusza za pomocą formantów CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Przewodnik: Wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Przewodnik: Aktualizacja wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
