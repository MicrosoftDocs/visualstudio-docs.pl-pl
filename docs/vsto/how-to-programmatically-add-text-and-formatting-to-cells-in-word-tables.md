---
title: Programowe dodawanie & tekstu do komórek tabeli programu Word
description: Dowiedz się, jak programowo dodawać tekst i formatowanie do komórek w Microsoft Office programu Word.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 58c9e7f7d5537e4b052a732a85ad9d1c7298afa0
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107828400"
---
# <a name="how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables"></a>Jak programowo dodać tekst i formatowanie do komórek w tabelach programu Word
  Każda tabela składa się z kolekcji komórek. Każdy pojedynczy <xref:Microsoft.Office.Interop.Word.Cell> obiekt reprezentuje jedną komórkę w tabeli. Każdą komórkę należy odwoływać się według jej lokalizacji w tabeli. Ten przykład odwołuje się do komórki znajdującej się w pierwszym wierszu i pierwszej kolumnie tabeli; dodaje tekst do komórki; i stosuje formatowanie.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-add-text-and-formatting-to-cells"></a>Aby dodać tekst i formatowanie do komórek

1. Odwołaj się do komórki według jej lokalizacji w tabeli, dodaj tekst do komórki i zastosuj formatowanie.

     Poniższy przykład kodu może służyć do dostosowywania na poziomie dokumentu. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet97":::

     Poniższy przykład kodu może być używany w dodatku VSTO. W tym przykładzie jest używany aktywny dokument. Aby użyć przykładu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet97":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet97":::

## <a name="see-also"></a>Zobacz też
- [How to: Programmatically create Word tables (Tworzyć programowo tabele programu Word)](../vsto/how-to-programmatically-create-word-tables.md)
- [How to: Programowe dodawanie wierszy i kolumn do tabel programu Word](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)
- [How to: Programowe wypełnianie tabel programu Word właściwościami dokumentu](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)
