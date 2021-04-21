---
title: 'How to: Programowe ustawianie opcji wyszukiwania w programie Word'
description: Dowiedz się, jak za pomocą Visual Studio programowo ustawić opcje wyszukiwania dla wyborów w programie Microsoft Word.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 605f782bf6dc3bb56b52bdcd896d1c6419cf5f51
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825033"
---
# <a name="how-to-programmatically-set-search-options-in-word"></a>How to: Programowe ustawianie opcji wyszukiwania w programie Word
  Istnieją dwa sposoby ustawienia opcji wyszukiwania dla wyborów w dokumentach Microsoft Office Word:

- Ustaw poszczególne właściwości <xref:Microsoft.Office.Interop.Word.Find> obiektu.

- Użyj argumentów <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Find> obiektu .

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="use-properties-of-a-find-object"></a>Używanie właściwości obiektu Find
 Poniższy kod ustawia właściwości obiektu <xref:Microsoft.Office.Interop.Word.Find> w celu wyszukiwania tekstu w ramach bieżącego zaznaczenia. Zwróć uwagę, że kryteria wyszukiwania, takie jak wyszukiwanie do przodu, zawijanie i tekst do wyszukania, są właściwościami <xref:Microsoft.Office.Interop.Word.Find> obiektu.

 Ustawienie każdej właściwości obiektu nie jest przydatne podczas pisania kodu C#, ponieważ należy określić te same właściwości co <xref:Microsoft.Office.Interop.Word.Find> parametry w <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metodzie . W związku z tym ten przykład zawiera Visual Basic kodu.

### <a name="to-set-search-options-using-a-find-object"></a>Aby ustawić opcje wyszukiwania przy użyciu obiektu Znajdź

1. Ustaw właściwości obiektu, aby wyszukiwać dalej <xref:Microsoft.Office.Interop.Word.Find> po zaznaczeniu tekstu znajdź **mnie**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet76":::

## <a name="use-execute-method-arguments"></a>Używanie argumentów metody Execute
 Poniższy kod używa <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody obiektu do wyszukiwania tekstu w ramach <xref:Microsoft.Office.Interop.Word.Find> bieżącego zaznaczenia. Zwróć uwagę, że kryteria wyszukiwania, takie jak wyszukiwanie do przodu, zawijanie i tekst do wyszukania, są przekazywane jako parametry <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> metody .

### <a name="to-set-search-options-using-execute-method-arguments"></a>Aby ustawić opcje wyszukiwania przy użyciu argumentów metody Execute

1. Przekaż kryteria wyszukiwania jako parametry metody , aby wyszukać dalej zaznaczenie tekstu <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> **znajdź mnie**.

     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet77":::
     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet77":::

## <a name="see-also"></a>Zobacz też
- [How to: Programowe wyszukiwanie i zastępowanie tekstu w dokumentach](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)
- [How to: Programmatically loop through found items in documents ( Jak programowo przechodzić w pętli przez znalezione elementy w dokumentach)](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)
- [How to: Programowe przywracanie wyborów po wyszukiwaniu](../vsto/how-to-programmatically-restore-selections-after-searches.md)
