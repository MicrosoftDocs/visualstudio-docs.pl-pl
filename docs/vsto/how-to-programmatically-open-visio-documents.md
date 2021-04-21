---
title: Jak programowo otwierać dokumenty programu Visio
description: Dowiedz się, jak za pomocą Visual Studio programowo otworzyć dokument programu Visio przy użyciu metod Open lub OpenEx.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5f96efd41eb91551fe3cf7c03b55a44b7a9e1bf1
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824747"
---
# <a name="how-to-programmatically-open-visio-documents"></a>Jak programowo otwierać dokumenty programu Visio
  Istnieją dwie metody otwierania istniejących dokumentów Microsoft Office Visio: Otwórz i OpenEx. Metoda OpenEx jest taka sama jak metoda Open, z tą różnicą, że udostępnia argumenty, w których wywołujący może określić sposób otwierania dokumentu.

 Aby uzyskać szczegółowe informacje na temat modelu obiektów, zobacz dokumentację referencyjną VBAMicrosoft.Office.Interop.Visio.Doc[ dokumentacji. Otwórz](/office/vba/api/Visio.Documents.Open) metodę [ iMicrosoft.Office.Interop.Visio.Documents. OpenEx,](/office/vba/api/Visio.Documents.OpenEx) metoda.

## <a name="open-a-visio-document"></a>Otwieranie dokumentu programu Visio

### <a name="to-open-a-visio-document"></a>Aby otworzyć dokument programu Visio

- Wywołaj `Microsoft.Office.Interop.Visio.Documents.Open` metodę i podać w pełni kwalifikowaną ścieżkę dokumentu programu Visio.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet5":::

## <a name="open-a-visio-document-with-specified-arguments"></a>Otwieranie dokumentu programu Visio z określonymi argumentami

### <a name="to-open-a-visio-document-as-read-only-and-docked"></a>Aby otworzyć dokument programu Visio jako tylko do odczytu i zadokowany

- Wywołaj metodę , podać w pełni kwalifikowaną ścieżkę dokumentu programu Visio i dołączyć argumenty, których chcesz użyć — w tym przypadku zadokowane i tylko `Microsoft.Office.Interop.Visio.Documents.OpenEx` do odczytu.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb" id="Snippet6":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład kodu wymaga następujących czynności:

- Dokument programu Visio o nazwie musi znajdować się w katalogu o nazwie w folderze Moje dokumenty (dla systemu Windows XP i starszych) lub `myDrawing.vsd` `Test` w folderze *Dokumenty* (dla systemu Windows Vista). 

## <a name="see-also"></a>Zobacz też
- [Rozwiązania programu Visio](../vsto/visio-solutions.md)
- [Omówienie modelu obiektów programu Visio](../vsto/visio-object-model-overview.md)
- [How to: Programmatically create new Visio documents (Tworzyć programowo nowe dokumenty programu Visio)](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [Pisano: Programowe zamykanie dokumentów programu Visio](../vsto/how-to-programmatically-close-visio-documents.md)
- [Jak programowo zapisywać dokumenty programu Visio](../vsto/how-to-programmatically-save-visio-documents.md)
- [How to: Programmatically print Visio documents (2017: Programowe drukowanie dokumentów programu Visio)](../vsto/how-to-programmatically-print-visio-documents.md)
