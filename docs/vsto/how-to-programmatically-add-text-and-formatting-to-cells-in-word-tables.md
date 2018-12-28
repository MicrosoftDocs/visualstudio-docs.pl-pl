---
title: 'Instrukcje: Programowe Dodawanie tekstu i formatowania do komórek w tabelach programu Word'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- cells, adding text and formatting
- text [Office development in Visual Studio], adding to Word tables
- formatting [Office development in Visual Studio]
- tables [Office development in Visual Studio], adding text and formatting
author: John-Hart
ms.author: johnhart
manager: douge
ms.workload:
- office
ms.openlocfilehash: 44f80b6eb2144b5cf831566c47d77aa1c3bc0c7b
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802307"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Instrukcje: Programowe Dodawanie tekstu i formatowania do komórek w tabelach programu Word
  Każda tabela składa się z kolekcji komórek. Poszczególnym <xref:Microsoft.Office.Interop.Word.Cell> obiekt reprezentuje jedną komórkę w tabeli. To odwołanie do każdej komórki według lokalizacji w tabeli. Ten przykład dotyczy komórek znajduje się w pierwszym wierszu i pierwszą kolumnę tabeli; dodaje tekst do komórki; i stosuje formatowanie.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## <a name="to-add-text-and-formatting-to-cells"></a>Dodawanie tekstu i formatowania do komórek  
  
1.  Odwołanie do komórki według lokalizacji w tabeli, Dodaj tekst do komórki i zastosować formatowanie.  
  
     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]  
  
     Poniższy przykład kodu może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu. Aby korzystać z przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.  
  
     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]  
  
## <a name="see-also"></a>Zobacz także  
 [Instrukcje: Programowe tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md)   
 [Instrukcje: Programowe Dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Instrukcje: Programowe Wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  