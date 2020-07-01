---
title: 'Instrukcje: Programowane otwieranie dokumentów Visio'
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: eb21d201c282461cbe82005f56bed023bb022209
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85519993"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Instrukcje: Programowane otwieranie dokumentów Visio
  Istnieją dwie metody otwierania istniejących Microsoft Office dokumentów programu Visio: otwarte i OpenEx. Metoda OpenEx jest taka sama jak Metoda Open, z tą różnicą, że zawiera argumenty, w których obiekt wywołujący może określić sposób otwierania dokumentu.

 Aby uzyskać szczegółowe informacje na temat modelu obiektów, zobacz dokumentację referencyjną języka VBA dla [Microsoft.Office.Interop.Visio.Documents. Otwórz](/office/vba/api/Visio.Documents.Open) metodę i [Microsoft.Office.Interop.Visio.Documents. OpenEx](/office/vba/api/Visio.Documents.OpenEx) .

## <a name="open-a-visio-document"></a>Otwieranie dokumentu programu Visio

### <a name="to-open-a-visio-document"></a>Aby otworzyć dokument programu Visio

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.Open` metodę i podaj w pełni kwalifikowaną ścieżkę dokumentu programu Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#5)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#5](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#5)]

## <a name="open-a-visio-document-with-specified-arguments"></a>Otwieranie dokumentu programu Visio z określonymi argumentami

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Aby otworzyć dokument programu Visio jako tylko do odczytu i zadokowany

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.OpenEx` metodę, podaj w pełni kwalifikowaną ścieżkę dokumentu programu Visio i Uwzględnij argumenty, których chcesz użyć — w tym przypadku zadokowanych i tylko do odczytu.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#6)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#6](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#6)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład kodu wymaga następujących czynności:

- Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w folderze *Moje dokumenty* (dla systemu Windows XP i starszych) lub folderu *dokumenty* (dla systemu Windows Vista).

## <a name="see-also"></a>Zobacz także
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Instrukcje: Programowane tworzenie nowych dokumentów programu Visio](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Instrukcje: Programowane Zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Instrukcje: programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Instrukcje: Programowane drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)
