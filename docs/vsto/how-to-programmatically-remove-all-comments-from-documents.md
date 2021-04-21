---
title: 'How to: Programowe usuwanie wszystkich komentarzy z dokumentów'
description: Dowiedz się, jak za pomocą Visual Studio programowo usunąć wszystkie komentarze z dokumentu programu Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], removing comments
- comments, removing from documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 5d51f44537c4e9564162d458c564dd428e57d154
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827048"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>How to: Programowe usuwanie wszystkich komentarzy z dokumentów
  Użyj metody `DeleteAllComments` , aby usunąć wszystkie komentarze z Microsoft Office programu Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Aby usunąć wszystkie komentarze z dokumentu, który jest częścią dostosowania na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> metodę klasy w `ThisDocument` projekcie. Aby użyć tego przykładu kodu, uruchom go z `ThisDocument` klasy .

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet119":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet119":::

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Aby usunąć wszystkie komentarze z dokumentu przy użyciu dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> metodę metody , z której chcesz usunąć <xref:Microsoft.Office.Interop.Word.Document> komentarze.

     Poniższy przykład kodu usuwa wszystkie komentarze z aktywnego dokumentu. Aby użyć tego przykładu kodu, uruchom go z `ThisAddIn` klasy w projekcie.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb" id="Snippet119":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs" id="Snippet119":::

## <a name="see-also"></a>Zobacz też
- [How to: Programowe dodawanie komentarzy do tekstu w dokumentach](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
