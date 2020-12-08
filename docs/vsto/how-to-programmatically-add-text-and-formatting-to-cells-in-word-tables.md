---
title: Programowo Dodaj formatowanie tekstu & do komórek tabeli programu Word
description: Dowiedz się, w jaki sposób można programowo dodawać tekst i formatowanie do komórek w Microsoft Office tabelach programu Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: f10684fa3e9309611ebf3b04d3cea77ee822f49e
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2020
ms.locfileid: "96848017"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Instrukcje: Programowane dodawanie tekstu i formatowania do komórek w tabelach programu Word
  Każda tabela składa się z kolekcji komórek. Każdy pojedynczy <xref:Microsoft.Office.Interop.Word.Cell> obiekt reprezentuje jedną komórkę w tabeli. Odwołujesz się do każdej komórki według jej lokalizacji w tabeli. Ten przykład odnosi się do komórki znajdującej się w pierwszym wierszu i pierwszej kolumnie tabeli; dodaje tekst do komórki; i stosuje formatowanie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Aby dodać tekst i formatowanie do komórek

1. Zapoznaj się z komórką według jej lokalizacji w tabeli, Dodaj tekst do komórki i Zastosuj formatowanie.

     Poniższy przykład kodu może być używany w dostosowaniu na poziomie dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomation#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#97)]

     Poniższy przykład kodu może być używany w dodatku VSTO. Ten przykład używa aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#97)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#97](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#97)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowane tworzenie tabel programu Word](../vsto/how-to-programmatically-create-word-tables.md)
- [Instrukcje: programowe Dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [Instrukcje: Programowane Wypełnianie tabel programu Word przy użyciu właściwości dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
