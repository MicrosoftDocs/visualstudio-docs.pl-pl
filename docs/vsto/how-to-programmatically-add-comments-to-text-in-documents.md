---
title: 'How to: Programowe dodawanie komentarzy do tekstu w dokumentach'
description: Programowe dodawanie komentarzy do tekstu w dokumentach. Właściwość Comments klasy Document dodaje komentarz do zakresu tekstu w dokumencie programu Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- comments, adding to documents
- documents [Office development in Visual Studio], adding comments
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4e03f189f2236131308b8f9ea5d90c52ffa3147d
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825826"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>How to: Programowe dodawanie komentarzy do tekstu w dokumentach
  Właściwość Komentarze klasy Document dodaje komentarz do zakresu tekstu w dokumencie Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższy przykład dodaje komentarz do pierwszego akapitu w dokumencie.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Aby dodać nowy komentarz do tekstu w dostosowywaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodę właściwości i podać zakres oraz tekst <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> komentarza. Aby użyć poniższego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet118":::

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Aby dodać nowy komentarz do tekstu w dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodę właściwości i podać zakres oraz tekst <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> komentarza.

     Poniższy przykład kodu dodaje komentarz do aktywnego dokumentu. Aby użyć tego przykładu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet118":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet118":::

## <a name="robust-programming"></a>Niezawodne programowanie
 Aby zmienić inicjały użytkownika, które program Word dodaje do komentarzy, użyj <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> właściwości .

## <a name="see-also"></a>Zobacz też
- [How to: Programowe usuwanie wszystkich komentarzy z dokumentów](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
