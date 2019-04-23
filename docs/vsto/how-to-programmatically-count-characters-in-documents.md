---
title: 'Instrukcje: Programowe zliczanie znaków w dokumentach'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- characters, counting in documents
- counting characters in documents
- documents [Office development in Visual Studio], counting characters
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb4bbb124575346c930fa5539801deb3c9981cac
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60102175"
---
# <a name="how-to-programmatically-count-characters-in-documents"></a>Instrukcje: Programowe zliczanie znaków w dokumentach
  Pierwszy znak w dokumencie jest od pozycji znaku 0, który reprezentuje punkt wstawiania. Ostatnia pozycja znaku jest równa całkowita liczba znaków w dokumencie. Można określić liczbę znaków w dokumencie za pomocą <xref:Microsoft.Office.Interop.Word.Characters.Count%2A> właściwość <xref:Microsoft.Office.Interop.Word.Characters> kolekcji.

 Zliczane są wszystkie znaki w dokumencie, łącznie ze spacjami, znaczniki akapitu i innych znaków, które zwykle są ukryte. Nawet nowy pusty dokument zwraca liczbę o jeden znak, ponieważ zawiera ona akapitu.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="to-display-the-number-of-characters-in-a-document-level-customization"></a>Aby wyświetlić liczbę znaków w dostosowaniu na poziomie dokumentu

1. Wybierz cały dokument.

     [!code-vb[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomation#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#98)]

2. Wyświetl liczbę znaków w dokumencie, w oknie komunikatu.

     [!code-vb[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomation#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#99)]

## <a name="to-display-the-number-of-characters-in-a-vsto-add-in"></a>Aby wyświetlić liczbę znaków w dodatku narzędzi VSTO

1. Wybierz cały dokument. Poniższy przykład wybiera aktywnego dokumentu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#98)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#98](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#98)]

2. Wyświetl liczbę znaków w dokumencie, w oknie komunikatu.

     [!code-vb[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationAddIn/ThisAddIn.vb#99)]
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#99](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationAddIn/ThisAddIn.cs#99)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe pobieranie znaków początkowych i końcowych w zakresach](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)
- [Instrukcje: Programowe definiowanie i zaznaczanie zakresów w dokumentach](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)
