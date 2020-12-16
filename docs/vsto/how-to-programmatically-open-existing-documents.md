---
title: 'Instrukcje: programowe otwieranie istniejących dokumentów'
description: Dowiedz się, jak otworzyć istniejący dokument programu Microsoft Word określony przez w pełni kwalifikowaną ścieżkę i nazwę pliku przy użyciu metody Open.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 994afc6f0d8d9bb76aff56097d0a18b8c3f940d9
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97525553"
---
# <a name="how-to-programmatically-open-existing-documents"></a>Instrukcje: programowe otwieranie istniejących dokumentów
  <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>Metoda otwiera istniejący dokument programu Microsoft Office Word określony przez w pełni kwalifikowaną ścieżkę i nazwę pliku. Ta metoda zwraca <xref:Microsoft.Office.Interop.Word.Document> , który reprezentuje otwarty dokument.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-open-a-document"></a>Aby otworzyć dokument

- Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodę <xref:Microsoft.Office.Interop.Word.Documents> kolekcji i podaj ścieżkę do dokumentu.

     [!code-vb[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#5)]
     [!code-csharp[Trin_VstcoreWordAutomation#5](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#5)]

## <a name="to-open-a-document-as-read-only"></a>Aby otworzyć dokument jako tylko do odczytu

- Wywołaj <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> metodę, podaj ścieżkę do dokumentu i ustaw dla argumentu *ReadOnly* **wartość true** w wywołaniu metody.

     [!code-vb[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#6)]
     [!code-csharp[Trin_VstcoreWordAutomation#6](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#6)]

## <a name="compile-the-code"></a>Kompiluj kod
 Ten przykład kodu wymaga następujących czynności:

- Dokument o nazwie *NewDocument.doc* musi znajdować się w katalogu o nazwie *test* na dysku C.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane tworzenie nowych dokumentów](../vsto/how-to-programmatically-create-new-documents.md)
- [Instrukcje: programowe Zamykanie dokumentów](../vsto/how-to-programmatically-close-documents.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
