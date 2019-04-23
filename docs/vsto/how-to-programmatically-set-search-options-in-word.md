---
title: 'Instrukcje: Programowe Ustawianie opcji wyszukiwania w programie Word'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- settings, Word search options
- documents [Office development in Visual Studio], search options
- Word, searching options
- searching, Word options
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 6e3b66bfd7f3f5d0ef0f4893efeb81c80df5d4ae
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60093517"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>Instrukcje: Programowe Ustawianie opcji wyszukiwania w programie Word
  Istnieją dwa sposoby, aby ustawić opcje wyszukiwania dla zaznaczenia w dokumentach programu Microsoft Office Word:

- Ustaw właściwości poszczególnych <xref:Microsoft.Office.Interop.Word.Find> obiektu.

- Używać argumentów <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiektu.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Użyj właściwości w obiekcie Find
 Poniższy kod ustawia właściwości <xref:Microsoft.Office.Interop.Word.Find> obiektu, aby wyszukać tekst w zaznaczeniu. Zauważ, że kryteria wyszukiwania, takie jak wyszukiwanie do przodu, zawijania i tekst do wyszukania, są właściwości <xref:Microsoft.Office.Interop.Word.Find> obiektu.

 Ustawienie każdej z właściwości <xref:Microsoft.Office.Interop.Word.Find> obiekt nie jest przydatne podczas pisania kodu w języku C#, ponieważ należy określić te same właściwości jako parametry w <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody. W związku z tym ten przykład zawiera tylko kod języka Visual Basic.

### <a name="to-set-search-options-using-a-find-object"></a>Aby ustawić opcje wyszukiwania przy użyciu obiektu wyszukiwania

1. Ustawianie właściwości <xref:Microsoft.Office.Interop.Word.Find> obiekt, aby wyszukiwać zaznaczenia tekstu w kierunku do przodu **mnie znaleźć**.

     [!code-vb[Trin_VstcoreWordAutomation#76](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#76)]

## <a name="use-execute-method-arguments"></a>Użyj argumentów metody Execute
 Poniższy kod używa <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiektu, aby wyszukać tekst w zaznaczeniu. Należy zauważyć, że kryteria wyszukiwania, takie jak wyszukiwanie do przodu, zawijania i tekst do wyszukania, są przekazywane jako parametry <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody.

### <a name="to-set-search-options-using-execute-method-arguments"></a>Aby ustawić opcje wyszukiwania przy użyciu argumentów metody Execute

1. Przekaż kryteria wyszukiwania jako parametry <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodę, aby wyszukiwać zaznaczenia tekstu w kierunku do przodu **mnie znaleźć**.

     [!code-vb[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#77)]
     [!code-csharp[Trin_VstcoreWordAutomation#77](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#77)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [Instrukcje: Programowe przechodzenie w pętli poprzez znalezione elementy w dokumentach](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [Instrukcje: Programowe Przywracanie zaznaczenia po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
