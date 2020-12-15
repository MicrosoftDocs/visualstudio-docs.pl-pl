---
title: Późne powiązania w rozwiązaniach pakietu Office
description: Dowiedz się, w jaki sposób niektóre typy w modelach obiektów w aplikacjach Microsoft Office udostępniają funkcje, które są dostępne za pomocą funkcji późnego wiązania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 201b850d8a577f8cc76aff97e2370998b6f885ed
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/15/2020
ms.locfileid: "97523571"
---
# <a name="late-binding-in-office-solutions"></a>Późne powiązania w rozwiązaniach pakietu Office
  Niektóre typy w modelach obiektów aplikacji pakietu Office udostępniają funkcje, które są dostępne za pomocą funkcji późnego wiązania. Na przykład niektóre metody i właściwości mogą zwracać różne typy obiektów w zależności od kontekstu aplikacji pakietu Office, a niektóre typy mogą uwidaczniać różne metody lub właściwości w różnych kontekstach.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic projekty, w których **opcja Strict** jest wyłączona i projekty języka Visual C#, które są przeznaczone dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] mogą współpracować bezpośrednio z typami, które korzystają z tych funkcji.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Niejawne i jawne rzutowanie wartości zwracanych obiektu
 Wiele metod i właściwości w Microsoft Office wartości zwracanych podstawowych zestawów międzyoperacyjnych (zestawów PIA) <xref:System.Object> , ponieważ mogą zwracać kilka różnych typów obiektów. Na przykład <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> Właściwość zwraca obiekt <xref:System.Object> , ponieważ jego wartość zwracana może być <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> obiektem lub, w zależności od tego, jaki jest aktywny arkusz.

 Gdy metoda lub właściwość zwraca <xref:System.Object> , należy jawnie skonwertować (w Visual Basic) obiekt na poprawny typ w projektach Visual Basic, w których **opcja Strict** jest włączona. Nie musisz jawnie rzutować <xref:System.Object> wartości zwracanych w projektach Visual Basic, w których **opcja Strict** jest wyłączona.

 W większości przypadków dokumentacja referencyjna zawiera listę możliwych typów wartości zwracanej dla elementu członkowskiego zwracającego element <xref:System.Object> . Konwertowanie lub rzutowanie obiektu włącza funkcję IntelliSense dla obiektu w edytorze kodu.

 Aby uzyskać informacje na temat konwersji w Visual Basic, zobacz [konwersje niejawne i jawne &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) i [funkcji CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).

### <a name="examples"></a>Przykłady
 Poniższy przykład kodu ilustruje sposób rzutowania obiektu do określonego typu w projekcie Visual Basic, w którym **opcja Strict** jest włączona. W tym typie projektu, musisz jawnie rzutować <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Właściwość na <xref:Microsoft.Office.Interop.Excel.Range> . Ten przykład wymaga projektu programu Excel na poziomie dokumentu z klasą arkusza o nazwie `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 Poniższy przykład kodu demonstruje sposób niejawnie rzutowania obiektu na określony typ w projekcie Visual Basic, gdzie **Option Strict** jest wyłączona lub w projekcie Visual C#, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . W tych typach projektów <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> Właściwość jest niejawnie rzutowana na <xref:Microsoft.Office.Interop.Excel.Range> . Ten przykład wymaga projektu programu Excel na poziomie dokumentu z klasą arkusza o nazwie `Sheet1` .

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>Dostęp do elementów członkowskich, które są dostępne tylko przez późne wiązanie
 Niektóre właściwości i metody w zestawów PIA pakietu Office są dostępne tylko za pomocą późnego wiązania. W Visual Basic projekty, w których **opcja Strict** jest wyłączona lub w projektach Visual C#, które są [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] przeznaczone dla lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] , można użyć funkcji późnego wiązania w tych językach, aby uzyskać dostęp do późnych elementów członkowskich. W Visual Basic projekty, w których **opcja Strict** jest włączona, należy użyć odbicia, aby uzyskać dostęp do tych elementów członkowskich.

### <a name="examples"></a>Przykłady
 Poniższy przykład kodu demonstruje, jak uzyskać dostęp do późnych elementów członkowskich w projekcie Visual Basic, gdzie **Option Strict** jest wyłączona lub w projekcie Visual C#, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . Ten przykład uzyskuje dostęp do właściwości **Nazwa** z późnym wiązaniem okna dialogowego **otwieranie pliku** w programie Word. Aby użyć tego przykładu, należy uruchomić go `ThisDocument` z `ThisAddIn` klasy lub w projekcie programu Word.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 Poniższy przykład kodu ilustruje sposób użycia odbicia w celu wykonania tego samego zadania w projekcie Visual Basic, w którym **opcja Strict** jest włączona.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>Zobacz też
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Użyj &#40;&#35; Przewodnik programowania w języku DHTML&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict — Instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
