---
title: 'Instrukcje: Programowe Dodawanie tekstu i formatowania do komórek w tabelach programu Word'
ms.date: 02/02/2017
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a415e55c263534ee4b29e5b45e24ad471d68fe0e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063871"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Instrukcje: Programowe Dodawanie tekstu i formatowania do komórek w tabelach programu Word
  Każda tabela składa się z kolekcji komórek. Poszczególnym <xref:Microsoft.Office.Interop.Word.Cell> obiekt reprezentuje jedną komórkę w tabeli. To odwołanie do każdej komórki według lokalizacji w tabeli. Ten przykład dotyczy komórek znajduje się w pierwszym wierszu i pierwszą kolumnę tabeli; dodaje tekst do komórki; i stosuje formatowanie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Dodawanie tekstu i formatowania do komórek

1. Odwołanie do komórki według lokalizacji w tabeli, Dodaj tekst do komórki i zastosować formatowanie.

     Poniższy przykład kodu może służyć w dostosowaniu na poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     Poniższy przykład kodu może służyć w dodatku VSTO. W tym przykładzie użyto aktywnego dokumentu. Aby korzystać z przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md)
- [Instrukcje: Programowe Dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Instrukcje: Programowe Wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
