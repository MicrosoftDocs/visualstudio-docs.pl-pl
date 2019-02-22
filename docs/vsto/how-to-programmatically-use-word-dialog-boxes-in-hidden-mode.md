---
title: 'Instrukcje: Programowe używanie okien dialogowych programu Word w trybie ukrytym'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- hidden dialog boxes
- Word [Office development in Visual Studio], dialog boxes
- dialog boxes, hidden mode in Word
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7a422e9548fabefa2066fb439c01e382586cd36
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56633681"
---
# <a name="how-to-programmatically-use-word-dialog-boxes-in-hidden-mode"></a>Instrukcje: Programowe używanie okien dialogowych programu Word w trybie ukrytym
  Złożonych operacji za pomocą jednego wywołania metody można wykonywać za pomocą wbudowanych okien dialogowych w programie Microsoft Office Word bez wyświetlania ich do użytkownika. Można to zrobić za pomocą <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> metody <xref:Microsoft.Office.Interop.Word.Dialog> obiektu bez wywoływania <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A> metody.

 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

## <a name="examples"></a>Przykłady
 Poniższe przykłady kodu przedstawiają sposoby użycia **ustawienia strony** okno dialogowe w trybie ukrytym, aby ustawić stronę wiele właściwości instalacji bez udziału użytkownika. W przykładach użyto <xref:Microsoft.Office.Interop.Word.Dialog> obiektu, aby skonfigurować niestandardowy rozmiar strony. Określone ustawienia strony, takie jak górny margines, dolny margines i tak dalej, są dostępne jako właściwości późnego wiązania <xref:Microsoft.Office.Interop.Word.Dialog> obiektu. Te właściwości są tworzone przez program Word dynamicznie w czasie wykonywania.

 Poniższy przykład przedstawia sposób wykonania tego zadania w projektach języka Visual Basic gdzie **Option Strict** jest wyłączona i w projektach Visual C#, których platformą docelową [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W tych projektach można użyć późne powiązania funkcji w Kompilatory języka Visual Basic i Visual C#. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#123)]
 [!code-csharp[Trin_VstcoreWordAutomation#123](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#123)]

 Poniższy przykład przedstawia sposób wykonania tego zadania w projektach języka Visual Basic gdzie **Option Strict** znajduje się na. W tych projektach należy użyć odbicia, uzyskiwania dostępu do właściwości późnego wiązania. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie.

 [!code-vb[Trin_VstcoreWordAutomation#104](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#104)]

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Programowe używanie wbudowanych okien dialogowych w programie Word](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)
- [Model obiektu Word — omówienie](../vsto/word-object-model-overview.md)
- [Późne powiązania w rozwiązaniach pakietu Office](../vsto/late-binding-in-office-solutions.md)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
