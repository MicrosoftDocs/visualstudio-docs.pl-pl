---
title: 'Instrukcje: Programowane tworzenie nowych dokumentów programu Visio'
description: Dowiedz się, jak można programowo utworzyć nowy dokument rysowania programu Microsoft Visio i dodać go do kolekcji dokumenty otwartych dokumentów programu Visio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: a5aeddeecf7fb76000817f2c57b90e30465fa4ed
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99964033"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>Instrukcje: Programowane tworzenie nowych dokumentów programu Visio
  Podczas tworzenia nowego dokumentu rysowania programu Microsoft Office Visio należy dodać go do `Microsoft.Office.Interop.Visio.Documents` kolekcji otwartych dokumentów programu Visio. W związku z tym `Microsoft.Office.Interop.Visio.Documents.Add` Metoda tworzy nowy dokument rysowania programu Visio. Aby uzyskać więcej informacji, zobacz dokumentację referencyjną języka VBA dla [Microsoft.Office.Interop.Visio.Documents. Dodaj](/office/vba/api/Visio.Documents.Add) metodę.

## <a name="create-new-blank-documents"></a>Utwórz nowe puste dokumenty

### <a name="to-create-a-new-document"></a>Aby utworzyć nowy dokument

- Użyj `Microsoft.Office.Interop.Visio.Documents.Add` metody, aby utworzyć nowy pusty dokument, który nie jest oparty na szablonie.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>Utwórz dokumenty skopiowane z istniejących dokumentów
 `Microsoft.Office.Interop.Visio.Documents.Add`Metoda może utworzyć nowy dokument, który jest kopią istniejącego dokumentu programu Visio. Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę diagramu.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Aby utworzyć nowy dokument, który jest kopiowany z istniejącego dokumentu

- Wywoływanie `Microsoft.Office.Interop.Visio.Documents.Add` metody i Określanie ścieżki diagramu programu Visio.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>Twórz wzorniki skopiowane z istniejących wzorników
 [Microsoft.Office.Interop.Visio.Documents. Metoda Add](/office/vba/api/Visio.Documents.Add) umożliwia utworzenie nowego wzornika, który jest kopią istniejącego wzornika programu Visio. Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę wzornika.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Aby utworzyć nowy wzornik skopiowany z istniejącego wzornika

- Wywoływanie `Microsoft.Office.Interop.Visio.Documents.Add` metody i Określanie ścieżki wzornika.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>Tworzenie dokumentów na podstawie istniejących szablonów
 `Microsoft.Office.Interop.Visio.Documents.Add`Metoda może utworzyć nowy dokument (plik *. vsd* ), który jest oparty na istniejącym szablonie programu Visio (plik *. VST* ). Ta metoda kopiuje wzorniki, style i ustawienia, które są częścią obszaru roboczego szablonu. Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę szablonu.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Aby utworzyć nowy dokument oparty na istniejącym szablonie

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.Add` metodę i określ ścieżkę szablonu.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład kodu wymaga następujących czynności:

- Dokument programu Visio o nazwie `myDrawing.vsd` musi znajdować się w katalogu o nazwie `Test` w folderze *Moje dokumenty* (dla systemu Windows XP i starszych) lub folderu *dokumenty* (dla systemu Windows Vista).

- Dokument programu Visio o nazwie `myStencil.vss` musi znajdować się w katalogu o nazwie `Test` w folderze *Moje dokumenty* (dla systemu Windows XP i starszych) lub folderu *dokumenty* (dla systemu Windows Vista).

- Dokument programu Visio o nazwie `myTemplate.vst` musi znajdować się w katalogu o nazwie `Test` w folderze *Moje dokumenty* (dla systemu Windows XP i starszych) lub folderu *dokumenty* (dla systemu Windows Vista).

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Model obiektów programu Visio — Omówienie](../vsto/visio-object-model-overview.md)
- [Instrukcje: Programowane otwieranie dokumentów Visio](../vsto/how-to-programmatically-open-visio-documents.md)
- [Instrukcje: Programowane Zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Instrukcje: programowe zapisywanie dokumentów programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [Instrukcje: Programowane drukowanie dokumentów programu Visio](../vsto/how-to-programmatically-print-visio-documents.md)
