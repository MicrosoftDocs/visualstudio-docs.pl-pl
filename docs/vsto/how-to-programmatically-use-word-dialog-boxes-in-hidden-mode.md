---
title: 'How to: Programmatically use Word dialog boxes in hidden mode (Jak programowo używać okien dialogowych programu Word w trybie ukrytym)'
description: Dowiedz się, jak używać Visual Studio do programowego korzystania z okien dialogowych programu Microsoft Word w trybie ukrytym.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 39a81ccec284541d93d3a5901211d8a46ea6b61a
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826190"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>How to: Programmatically use Word dialog boxes in hidden mode (Jak programowo używać okien dialogowych programu Word w trybie ukrytym)
  Złożone operacje można wykonywać za pomocą jednego wywołania metody, wywołując wbudowane okna dialogowe w programie Microsoft Office Word bez wyświetlania ich użytkownikowi. Można to zrobić przy użyciu <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody obiektu <xref:Microsoft.Office.Interop.Word.Dialog> bez wywoływania <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody .

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Przykłady
 W poniższych przykładach kodu pokazano, jak za pomocą okna dialogowego **Ustawienia** strony w trybie ukrytym ustawić wiele właściwości konfiguracji strony bez wprowadzania danych przez użytkownika. W przykładach do <xref:Microsoft.Office.Interop.Word.Dialog> skonfigurowania niestandardowego rozmiaru strony jest obiekt . Określone ustawienia konfiguracji strony, takie jak górny margines, dolny margines itp., są dostępne jako właściwości obiektu z późnym <xref:Microsoft.Office.Interop.Word.Dialog> wiązaniem. Te właściwości są dynamicznie tworzone przez program Word w czasie działania.

 W poniższym przykładzie pokazano, jak wykonać to zadanie w projektach Visual Basic, w których opcja **Option Strict** jest wyłączona, i w projektach Visual C# dla obiektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] docelowego . W tych projektach można używać funkcji późnego wiązania w kompilatorach języka Visual Basic i Visual C#. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet123":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet123":::

 W poniższym przykładzie pokazano, jak wykonać to zadanie w Visual Basic projektach, w których **jest wł. opcja** Strict. W tych projektach należy użyć odbicia, aby uzyskać dostęp do właściwości z późnym wiązaniem. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet104":::

## <a name="see-also"></a>Zobacz też
- [How to: Programmatically use built-in dialog boxes in Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)
- [Późne powiązanie w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
