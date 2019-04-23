---
title: 'Instrukcje: Programowe Dodawanie komentarzy do tekstu w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
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
ms.openlocfilehash: 5aba4c6446b2dbcfcb31c423a28eedd552799b4e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60118139"
---
# <a name="how-to-programmatically-add-comments-to-text-in-documents"></a>Instrukcje: Programowe Dodawanie komentarzy do tekstu w dokumentach
  Właściwość komentarze klasy dokumentu dodaje komentarz do zakresu w dokumencie programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

 Poniższy przykład dodaje komentarz do pierwszego akapitu w dokumencie.

## <a name="to-add-a-new-comment-to-text-in-a-document-level-customization"></a>Aby dodać nowy komentarz do tekstu w dostosowaniu na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metody <xref:Microsoft.Office.Tools.Word.Document.Comments%2A> właściwości i podaj zakres i tekst komentarza. Aby użyć w poniższym przykładzie kodu, należy uruchomić go z `ThisDocument` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomation#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#118)]

## <a name="to-add-a-new-comment-to-text-in-a-vsto-add-in"></a>Aby dodać nowy komentarz do tekstu w dodatku narzędzi VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Word.Comments.Add%2A> metody <xref:Microsoft.Office.Interop.Word._Document.Comments%2A> właściwości i podaj zakres i tekst komentarza.

     Poniższy przykład kodu dodaje komentarz do aktywnego dokumentu. Aby użyć tego przykładu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#118)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#118](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#118)]

## <a name="robust-programming"></a>Skuteczne programowanie
 Aby zmienić inicjały użytkownika, które program Word dodaje do komentarzy, użyj <xref:Microsoft.Office.Interop.Word._Application.UserInitials%2A> właściwości.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe usuwanie wszystkich komentarzy z dokumentów](../vsto/how-to-programmatically-remove-all-comments-from-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
