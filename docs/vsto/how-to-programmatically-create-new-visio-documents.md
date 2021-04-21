---
title: 'How to: Programmatically create new Visio documents (Tworzyć programowo nowe dokumenty programu Visio)'
description: Dowiedz się, jak programowo utworzyć nowy dokument rysunkowy programu Microsoft Visio i dodać go do kolekcji Dokumenty otwartych dokumentów programu Visio.
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
ms.openlocfilehash: 4b12b7e94109391928ad7c83387917e5934ae1c7
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825319"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>How to: Programmatically create new Visio documents (Tworzyć programowo nowe dokumenty programu Visio)
  Podczas tworzenia nowego dokumentu Microsoft Office visio należy dodać go do kolekcji `Microsoft.Office.Interop.Visio.Documents` otwartych dokumentów programu Visio. W związku z tym `Microsoft.Office.Interop.Visio.Documents.Add` metoda tworzy nowy dokument rysunek programu Visio. Aby uzyskać więcej informacji, zobacz dokumentację referencyjną dotyczącąMicrosoft.Office.Interop.Visio.Doc[ VBA. Dodaj](/office/vba/api/Visio.Documents.Add) metodę .

## <a name="create-new-blank-documents"></a>Tworzenie nowych pustych dokumentów

### <a name="to-create-a-new-document"></a>Aby utworzyć nowy dokument

- Użyj metody `Microsoft.Office.Interop.Visio.Documents.Add` , aby utworzyć nowy pusty dokument, który nie jest oparty na szablonie.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet1":::

## <a name="create-documents-copied-from-existing-documents"></a>Tworzenie dokumentów skopiowanych z istniejących dokumentów
 Metoda `Microsoft.Office.Interop.Visio.Documents.Add` może utworzyć nowy dokument, który jest kopią istniejącego dokumentu programu Visio. Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę diagramu.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>Aby utworzyć nowy dokument skopiowany z istniejącego dokumentu

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.Add` metodę i określ ścieżkę diagramu programu Visio.

:::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet2":::
:::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet2":::

## <a name="create-stencils-copied-from-existing-stencils"></a>Tworzenie wzorników skopiowanych z istniejących wzorników
 Ten [Microsoft.Office.Interop.Visio.Documents. Metoda](/office/vba/api/Visio.Documents.Add) Add umożliwia utworzenie nowego wzornika, który jest kopią istniejącego wzornika programu Visio. Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę wzornika.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>Aby utworzyć nowy wzornik skopiowany z istniejącego wzornika

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.Add` metodę i określ ścieżkę wzornika.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet3":::

## <a name="create-documents-based-on-existing-templates"></a>Tworzenie dokumentów na podstawie istniejących szablonów
 Metoda `Microsoft.Office.Interop.Visio.Documents.Add` może utworzyć nowy dokument *(plik vsd)* oparty na istniejącym szablonie programu Visio *(pliku vst).* Ta metoda kopiuje wzorniki, style i ustawienia, które są częścią obszaru roboczego szablonu. Należy podać nazwę pliku i w pełni kwalifikowaną ścieżkę szablonu.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>Aby utworzyć nowy dokument oparty na istniejącym szablonie

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.Add` metodę i określ ścieżkę szablonu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet4":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład kodu wymaga następujących czynności:

- Dokument programu Visio o nazwie musi znajdować się w katalogu o nazwie w folderze Moje dokumenty (dla systemu Windows XP i starszych wersji) lub `myDrawing.vsd` `Test` w folderze *Dokumenty* (system Windows Vista). 

- Dokument programu Visio o nazwie musi znajdować się w katalogu o nazwie w folderze Moje dokumenty (dla systemu Windows XP i starszych wersji) lub `myStencil.vss` `Test` w folderze *Dokumenty* (system Windows Vista). 

- Dokument programu Visio o nazwie musi znajdować się w katalogu o nazwie w folderze Moje dokumenty (dla systemu Windows XP i starszych wersji) lub `myTemplate.vst` `Test` w folderze *Dokumenty* (system Windows Vista). 

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)
- [How to: Programmatically open Visio documents (2017: Programowe otwieranie dokumentów programu Visio)](../vsto/how-to-programmatically-open-visio-documents.md)
- [How to: Programmatically close Visio documents (2017: Programowe zamykanie dokumentów programu Visio)](../vsto/how-to-programmatically-close-visio-documents.md)
- [How to: Programmatically save Visio documents (2017: Programowe zapisywanie dokumentów programu Visio)](../vsto/how-to-programmatically-save-visio-documents.md)
- [How to: Programmatically print Visio documents (2017: Programowe drukowanie dokumentów programu Visio)](../vsto/how-to-programmatically-print-visio-documents.md)
