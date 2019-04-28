---
title: 'Instrukcje: Programowe kopiowanie i wklejanie kształtów w dokumencie programu Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- shapes [Office development in Visual Studio], copying and pasting Visio shapes
- Visio [Office development in Visual Studio], copying and pasting Visio shapes
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 81941d131b51135771333aeab966716f4126a58b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62575211"
---
# <a name="how-to-programmatically-copy-and-paste-shapes-in-a-visio-document"></a>Instrukcje: Programowe kopiowanie i wklejanie kształtów w dokumencie programu Visio
  Możesz programowo skopiuj kształtów na jednej stronie dokumentu i wklej je do nowej strony w tym samym dokumencie. Można wkleić je do lokalizacji domyślnej (Centrum aktywne okno) lub te same lokalizacje współrzędnych ponieważ na stronie oryginalnej.

## <a name="copy-and-paste-shapes"></a>Kopiowanie i wklejanie kształtów
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [ Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy), i [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) metod i [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNormal](/office/vba/api/Visio.viscutcopypastecodes) flagi.

### <a name="to-copy-shapes-to-the-center-of-another-page"></a>Aby skopiować kształty do środka innej strony

- Poniższy przykład pokazuje, jak skopiować kształty od pierwszej strony i wklej je do Centrum drugiej strony.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#14)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#14](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#14)]

## <a name="copy-and-paste-shapes-with-the-same-positions"></a>Kopiowanie i wklejanie kształtów do tej samej pozycji
 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Shape.DrawRectangle](/office/vba/api/Visio.Shape.DrawRectangle), [Microsoft.Office.Interop.Visio.Shape.DrawOval](/office/vba/api/Visio.Shape.DrawOval), [ Microsoft.Office.Interop.Visio.Shape.Copy](/office/vba/api/Visio.Shape.Copy), i [Microsoft.Office.Interop.Visio.Shape.Paste](/office/vba/api/Visio.Shape.Paste) metod i [ Microsoft.Office.Interop.Visio.VisCutCopyPasteCodes.visCopyPasteNoTranslate](/office/vba/api/Visio.viscutcopypastecodes) flagi.

 Jeśli zachodzi potrzeba kontrolować format information wklejany i (opcjonalnie) ustanowić łącze do pliku źródłowego (na przykład dokument programu Microsoft Office Word), należy użyć metody PasteSpecial.

### <a name="to-copy-shapes-and-shape-locations-to-another-page"></a>Aby skopiować kształty i lokalizacje kształtów do innej strony

- Poniższy przykład pokazuje, jak skopiować kształty od pierwszej strony i wklej je do drugiej strony, przy użyciu oryginalnych lokalizacji współrzędnych.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#15)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#15](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#15)]

## <a name="see-also"></a>Zobacz także
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)
- [Praca z dokumentami Visio shapes](../vsto/working-with-visio-shapes.md)
- [Instrukcje: Programowe Dodawanie kształtów do dokumentu programu Visio](../vsto/how-to-programmatically-add-shapes-to-a-visio-document.md)
