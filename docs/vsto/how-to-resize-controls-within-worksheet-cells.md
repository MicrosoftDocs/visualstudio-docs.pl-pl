---
title: Jak zmienić rozmiar kontrolek w komórkach arkusza
description: Dowiedz się, jak za pomocą Visual Studio zmienić rozmiar kontrolek w komórkach arkusza programu Microsoft Excel zarówno w czasie projektowania, jak i w czasie uruchamiania.
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
ms.openlocfilehash: 7b42c10fd82ec077b295a8bc683fa138c2eb095b
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825748"
---
# <a name="how-to-resize-controls-within-worksheet-cells"></a>Jak zmienić rozmiar kontrolek w komórkach arkusza
  Podczas zmieniania rozmiaru kolumn lub wierszy w arkuszu wszelkie kontrolki hosta w komórkach automatycznie do rozmiaru lub szerokości komórki, do których rozmiar został zmieniony. Windows Forms kontrolki domyślnie nie mają automatycznego rozmiaru.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 W przypadku dodawania kontrolek w czasie projektowania należy ustawić opcje pozycjonowania dla każdej kontrolki.

 Jeśli dodasz kontrolkę Windows Forms programowo i podasz argument zakresu, rozmiar kontrolki zostanie automatycznie zmieniony po zmianie rozmiaru komórki w zakresie. Aby uzyskać więcej informacji, zobacz [Dodawanie kontrolek do dokumentów pakietu Office w czasie rzeczywistym.](../vsto/adding-controls-to-office-documents-at-run-time.md)

## <a name="resize-controls-at-design-time"></a>Zmiana rozmiaru kontrolek w czasie projektowania

### <a name="to-make-controls-resize-with-cells-at-design-time"></a>Aby zmienić rozmiar kontrolek za pomocą komórek w czasie projektowania

1. Z **przybornika przeciągnij** kontrolkę Windows Forms do arkusza.

2. Kliknij prawym przyciskiem myszy kontrolkę, a następnie kliknij **pozycję Formatuj kontrolkę**.

3. W **oknie dialogowym Kontrolka** formatowania kliknij **kartę** Właściwości.

4. W **obszarze Pozycjonowanie** obiektu wybierz **opcję Przenieś i rozmiar z komórkami,** a następnie kliknij przycisk **OK**.

     Gdy zmieniasz rozmiar komórki zawierającej kontrolkę, zmienia ona rozmiar tak, aby pasowała do komórki.

## <a name="resize-controls-at-run-time"></a>Zmienianie rozmiaru kontrolek w czasie uruchamiania
 Jeśli dodasz kontrolkę Windows Forms czasie uruchamiania i przekażemy ją jako lokalizację kontrolki, rozmiar kontrolki zostanie automatycznie zmieniony po zmianie rozmiaru komórki arkusza zawierającej <xref:Microsoft.Office.Interop.Excel.Range> zakres.

### <a name="to-make-controls-resize-with-cells-at-run-time"></a>Aby zmienić rozmiar kontrolek za pomocą komórek w czasie uruchamiania

1. Dodaj kontrolkę do zakresu A1.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet5":::

     Gdy zmieniasz rozmiar komórki zawierającej kontrolkę, zmienia ona rozmiar tak, aby pasowała do komórki.

## <a name="reset-control-placement"></a>Resetowanie położenia kontrolki
 Położenie i zmiana rozmiaru kontrolki można zresetować, ustawiając właściwość na jedną `Placement` z następujących <xref:Microsoft.Office.Interop.Excel.XlPlacement> wartości:

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMove>

- <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlMoveAndSize>

### <a name="to-change-the-behavior-of-a-control-so-that-it-does-not-resize-or-move-with-the-cell"></a>Aby zmienić zachowanie kontrolki tak, aby nie zmieniała rozmiaru ani nie była przenosłana z komórką

1. Wywołaj właściwość placement kontrolki i ustaw wartość na <xref:Microsoft.Office.Interop.Excel.XlPlacement.xlFreeFloating> .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/my excel chart/Sheet1.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingControlsExcelCS/Sheet1.cs" id="Snippet6":::

## <a name="see-also"></a>Zobacz też
- [Kontrolki w dokumentach pakietu Office](../vsto/controls-on-office-documents.md)
- [Jak dodać kontrolki Windows Forms do dokumentów pakietu Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)
- [Dzieje się tak: ukrywanie kontrolek w arkuszach podczas drukowania](../vsto/how-to-hide-controls-on-worksheets-when-printing.md)
- [Dodawanie kontrolek do dokumentów pakietu Office w czasie uruchamiania](../vsto/adding-controls-to-office-documents-at-run-time.md)
- [Ograniczenia kontrolek Windows Forms dokumentów pakietu Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)
