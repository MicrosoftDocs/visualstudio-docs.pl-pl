---
title: 'Instrukcje: Programowe otwieranie dokumentów programu Visio'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening Visio documents
- Visio [Office development in Visual Studio], opening Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b863040bcceb4e86aae7ed4efd83c2466eec12c6
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60037858"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Instrukcje: Programowe otwieranie dokumentów programu Visio
  Istnieją dwie metody otwieranie istniejących dokumentów programu Microsoft Office Visio: Otwórz i OpenEx. Metoda OpenEx jest taka sama jak metody Open, z tą różnicą, że zawiera argumenty, w których obiekt wywołujący można określić sposób otwierania dokumentu.

 Aby uzyskać szczegółowe informacje o modelu obiektów, zobacz dokumentację referencyjną VBA [Microsoft.Office.Interop.Visio.Documents.Open](/office/vba/api/Visio.Documents.Open) metody i [Microsoft.Office.Interop.Visio.Documents.OpenEx](/office/vba/api/Visio.Documents.OpenEx) Metoda.

## <a name="open-a-visio-document"></a>Otwórz dokument programu Visio

### <a name="to-open-a-visio-document"></a>Aby otworzyć dokument programu Visio

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.Open` metody i dostarczyć w pełni kwalifikowaną ścieżkę dokumentu programu Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Otwórz dokument programu Visio z określonymi argumentami

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Aby otworzyć dokument programu Visio jako tylko do odczytu i jest zadokowany

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.OpenEx` metody, podaj w pełni kwalifikowaną ścieżkę dokumentu programu Visio i zawierać argumenty, którego chcesz użyć — w tym przypadku zadokowany i tylko do odczytu.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Skompilować kod
 Ten przykład kodu wymaga następujących elementów:

- Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w *Moje dokumenty* folder (Windows XP i starszych) lub *dokumenty* folder (Windows Vista).

## <a name="see-also"></a>Zobacz także
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektu Visio ― omówienie](../vsto/visio-object-model-overview.md)
- [Instrukcje: Programowe tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Instrukcje: Programowe zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Instrukcje: Programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Instrukcje: Programowe drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)
