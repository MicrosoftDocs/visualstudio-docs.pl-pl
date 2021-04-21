---
title: 'Pisano: Programowe otwieranie istniejących dokumentów'
description: Dowiedz się, jak za pomocą metody Open otworzyć istniejący dokument programu Microsoft Word określony przez w pełni kwalifikowaną ścieżkę i nazwę pliku.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], opening
- Word [Office development in Visual Studio], opening documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 0153413a357a122b4bb5a1f1cbfb44079f78e128
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827308"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Pisano: Programowe otwieranie istniejących dokumentów
  Metoda otwiera istniejący dokument programu Word Microsoft Office określony przez w pełni kwalifikowaną <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> ścieżkę i nazwę pliku. Ta metoda zwraca wartość <xref:Microsoft.Office.Interop.Word.Document> reprezentującą otwarty dokument.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Aby otworzyć dokument

- Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodę <xref:Microsoft.Office.Interop.Word.Documents> kolekcji i podać ścieżkę do dokumentu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet5":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet5":::

## <a name="to-open-a-document-as-read-only"></a>Aby otworzyć dokument jako tylko do odczytu

- Wywołaj metodę , podać ścieżkę do dokumentu i ustawić <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> argument *ReadOnly* na wartość **True** w wywołaniu metody.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet6":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet6":::

## <a name="compile-the-code"></a>Kompilowanie kodu
 Ten przykład kodu wymaga następujących czynności:

- Dokument o nazwie *NewDocument.doc* musi istnieć w katalogu o nazwie *Test* na dysku C.

## <a name="see-also"></a>Zobacz też
- [Jak programowo tworzyć nowe dokumenty](../vsto/how-to-programmatically-create-new-documents.md)
- [Pisano: Programowe zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
