---
title: 'How to: Programowe zliczaj znaki w dokumentach'
description: Dowiedz się, jak określić liczbę znaków w dokumencie przy użyciu właściwości Count kolekcji Znaki.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 68ddc86183eacd7f76e39bb06e47968c0129849c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824009"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>How to: Programowe zliczaj znaki w dokumentach
  Pierwszy znak w dokumencie znajduje się na pozycji znaku 0, która reprezentuje punkt wstawiania. Ostatnia pozycja znaku jest równa całkowitej liczbie znaków w dokumencie. Liczbę znaków w dokumencie można określić przy użyciu <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> właściwości <xref:Microsoft.Office.Interop.Word.Characters> kolekcji .

 Wszystkie znaki w dokumencie są zliczane, w tym spacje, znaki akapitu i inne znaki, które są zwykle ukryte. Nawet nowy, pusty dokument zwraca liczbę jednego znaku, ponieważ zawiera znacznik akapitu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Aby wyświetlić liczbę znaków w dostosowywaniu na poziomie dokumentu

1. Zaznacz cały dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet98":::

2. Wyświetlanie liczby znaków w dokumencie w oknie komunikatu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet99":::

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Aby wyświetlić liczbę znaków w dodatku VSTO

1. Zaznacz cały dokument. Poniższy przykład wybiera aktywny dokument.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet98":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet98":::

2. Wyświetlanie liczby znaków w dokumencie w oknie komunikatu.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet99":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet99":::

## <a name="see-also"></a>Zobacz też
- [How to: Programowe pobieranie znaków początku i końca w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Jak programowo definiować i wybierać zakresy w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
