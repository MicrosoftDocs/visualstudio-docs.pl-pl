---
title: Jak programowo używać wbudowanych okien dialogowych w programie Word
description: Dowiedz się, jak za pomocą Visual Studio programowo używać wbudowanych okien dialogowych w programie Microsoft Word.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, Word
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 6038000dec20f9183f974ad8d187230e634d5eed
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107826216"
---
# <a name="how-to-programmatically-use-built-in-dialog-boxes-in-word"></a>Jak programowo używać wbudowanych okien dialogowych w programie Word
  Podczas pracy z Microsoft Office Word czasami trzeba wyświetlić okna dialogowe dla danych wejściowych użytkownika. Mimo że możesz utworzyć własny, możesz również użyć wbudowanych okien dialogowych w programie Word, które są widoczne w <xref:Microsoft.Office.Interop.Word.Dialogs> kolekcji <xref:Microsoft.Office.Interop.Word.Application> obiektu . Dzięki temu można uzyskać dostęp do ponad 200 wbudowanych okien dialogowych, które są reprezentowane jako wyliczenia.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="display-dialog-boxes"></a>Wyświetlanie okien dialogowych
 Aby wyświetlić okno dialogowe, użyj jednej z wartości wyliczenia, aby utworzyć obiekt reprezentujący okno dialogowe, <xref:Microsoft.Office.Interop.Word.WdWordDialog> <xref:Microsoft.Office.Interop.Word.Dialog> które chcesz wyświetlić. Następnie wywołaj <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> metodę <xref:Microsoft.Office.Interop.Word.Dialog> obiektu .

 Poniższy przykład kodu przedstawia sposób wyświetlania **okna dialogowego Otwieranie** pliku. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet100":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet100":::

### <a name="access-dialog-box-members-that-are-available-through-late-binding"></a>Dostęp do elementów członkowskich okna dialogowego, które są dostępne za pośrednictwem późnego powiązania
 Niektóre właściwości i metody okien dialogowych w programie Word są dostępne tylko za pośrednictwem późnego powiązania. W Visual Basic, w których **opcja Strict** jest wł., należy użyć odbicia, aby uzyskać dostęp do tych elementów członkowskich. Aby uzyskać więcej informacji, zobacz [Późne powiązanie w rozwiązaniach pakietu Office.](../vsto/late-binding-in-office-solutions.md)

 W poniższym przykładzie kodu pokazano, jak  używać właściwości **Name** okna dialogowego Otwieranie pliku w projektach programu Visual Basic, w których opcja **Option Strict** jest wyłączona lub w projektach Visual C# dla obiektu docelowego lub [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] . Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 Poniższy przykład kodu pokazuje, jak używać odbicia w  celu uzyskania dostępu do właściwości **Name** okna dialogowego Otwieranie pliku w Visual Basic, w których jest wł. **opcja** Strict. Aby użyć tego przykładu, uruchom go z `ThisDocument` klasy lub `ThisAddIn` w projekcie.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Zobacz też
- [Jak programowo używać okien dialogowych programu Word w trybie ukrytym](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)
- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Option strict, instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
