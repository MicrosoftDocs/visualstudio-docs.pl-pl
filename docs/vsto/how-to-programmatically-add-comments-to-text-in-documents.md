---
title: 'Instrukcje: Programowane dodawanie komentarzy do tekstu w dokumentach'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 04d4ffdc747823a3df9a884b054b39ad484e09a4
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/30/2020
ms.locfileid: "91583791"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Instrukcje: Programowane dodawanie komentarzy do tekstu w dokumentach
  Właściwość Comment klasy Document dodaje komentarz do zakresu tekstu w dokumencie programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższy przykład dodaje komentarz do pierwszego akapitu w dokumencie.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Aby dodać nowy komentarz do tekstu w dostosowaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodę <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> właściwości i podaj zakres oraz tekst komentarza. Aby użyć następującego przykładu kodu, uruchom go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Aby dodać nowy komentarz do tekstu w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metodę <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> właściwości i podaj zakres oraz tekst komentarza.

     Poniższy przykład kodu dodaje komentarz do aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>Niezawodne programowanie
 Aby zmienić inicjały użytkownika, które program Word dodaje do komentarzy, użyj <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> właściwości.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: programowe usuwanie wszystkich komentarzy z dokumentów](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
