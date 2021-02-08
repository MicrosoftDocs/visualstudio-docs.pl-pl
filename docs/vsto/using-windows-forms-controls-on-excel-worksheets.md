---
title: Używanie formantów Windows Forms w arkuszach programu Excel
description: Dowiedz się, jak dodać kontrolki Windows Forms do skoroszytów programu Microsoft Excel w taki sam sposób, jak w przypadku dodawania formantów do Windows Forms.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f8c79e487e116741c393cef5a6f65b30cc4a8cfb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99838220"
---
# <a name="use-windows-forms-controls-on-excel-worksheets"></a>Używanie formantów Windows Forms w arkuszach programu Excel
  Możesz dodać kontrolki Windows Forms do Microsoft Office skoroszytów programu Excel w taki sam sposób, jak w przypadku dodawania formantów do Windows Forms. Aby uzyskać ogólne informacje na temat pracy z kontrolkami w dokumentach, zobacz [Windows Forms Controls on Documents Overview](../vsto/windows-forms-controls-on-office-documents-overview.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

## <a name="control-considerations-for-excel"></a>Zagadnienia dotyczące kontroli dla programu Excel
 Istnieje kilka kwestii, które są specyficzne dla programu Excel.

### <a name="match-control-size-to-cell-size"></a>Dopasuj rozmiar kontrolki do rozmiaru komórki
 Można ustawić zmianę rozmiaru kontrolki automatycznie, gdy zmieni się rozmiar komórki nadrzędnej. Aby uzyskać więcej informacji, zobacz [How to: zmiana rozmiaru kontrolek w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md).

### <a name="add-components-that-are-shared-by-all-worksheets"></a>Dodaj składniki, które są współużytkowane przez wszystkie arkusze
 Możesz dodać składniki, które mają być udostępniane między wszystkimi arkuszami, takimi jak <xref:System.Data.DataSet> , do projektanta skoroszytów, a nie arkuszami. Składnik będzie widoczny na pasku składnika.

### <a name="formula-for-embedding-controls"></a>Formuła osadzania formantów
 Po wybraniu kontrolki w programie Excel zobaczysz wartość " **Osadź" (WinForms. Control. host "," ")** na **pasku formuły**. Ten tekst jest wymagany i nie należy go usuwać.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: zmiana rozmiaru kontrolek w komórkach arkusza](../vsto/how-to-resize-controls-within-worksheet-cells.md)
- [Instrukcje: ukrywanie kontrolek w arkuszach podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Przewodnik: zmiana formatowania arkusza za pomocą kontrolek CheckBox](../vsto/walkthrough-changing-worksheet-formatting-using-checkbox-controls.md)
- [Przewodnik: wyświetlanie tekstu w polu tekstowym w arkuszu za pomocą przycisku](../vsto/walkthrough-displaying-text-in-a-text-box-in-a-worksheet-using-a-button.md)
- [Przewodnik: aktualizowanie wykresu w arkuszu za pomocą przycisków radiowych](../vsto/walkthrough-updating-a-chart-in-a-worksheet-using-radio-buttons.md)
