---
title: 'Instrukcje: programowe usuwanie wszystkich komentarzy z dokumentów'
description: Dowiedz się, jak za pomocą programu Visual Studio programowo usunąć wszystkie komentarze z dokumentu programu Microsoft Word.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cdb2d7b61efc1e40bf08b6b38ea6564892a04a33
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97526655"
---
# <a name="how-to-programmatically-remove-all-comments-from-documents"></a>Instrukcje: programowe usuwanie wszystkich komentarzy z dokumentów
  Użyj `DeleteAllComments` metody, aby usunąć wszystkie komentarze z dokumentu programu Microsoft Office Word.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-remove-all-comments-from-a-document-that-is-part-of-a-document-level-customization"></a>Aby usunąć wszystkie komentarze z dokumentu, który jest częścią dostosowania na poziomie dokumentu

1. Wywołaj <xref:Microsoft.Office.Tools.Word.Document.DeleteAllComments%2A> metodę `ThisDocument` klasy w projekcie. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisDocument` klasy.

     [!code-vb[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomation#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#119)]

## <a name="to-remove-all-comments-from-a-document-by-using-a-vsto-add-in"></a>Aby usunąć wszystkie komentarze z dokumentu przy użyciu dodatku VSTO

1. Wywołaj <xref:Microsoft.Office.Interop.Word._Document.DeleteAllComments%2A> metodę, <xref:Microsoft.Office.Interop.Word.Document> z której chcesz usunąć komentarze.

     Poniższy przykład kodu usuwa wszystkie komentarze z aktywnego dokumentu. Aby użyć tego przykładu kodu, należy uruchomić go z `ThisAddIn` klasy w projekcie.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#119)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#119](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#119)]

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Programowane dodawanie komentarzy do tekstu w dokumentach](../vsto/how-to-programmatically-add-comments-to-text-in-documents.md)
- [Element hosta dokumentu](../vsto/document-host-item.md)
