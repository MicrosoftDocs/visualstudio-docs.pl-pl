---
title: Późne powiązanie w rozwiązaniach pakietu Office
description: Dowiedz się, jak niektóre typy w modelach obiektów Microsoft Office aplikacji zapewniają funkcje, które są dostępne za pośrednictwem funkcji późnego wiązania.
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e618dcd0cc699b4626f825890cf0fc8bd7ddd853
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107823889"
---
# <a name="late-binding-in-office-solutions"></a>Późne powiązanie w rozwiązaniach pakietu Office
  Niektóre typy w modelach obiektów aplikacji pakietu Office zapewniają funkcje, które są dostępne za pośrednictwem funkcji późnego wiązania. Na przykład niektóre metody i właściwości mogą zwracać różne typy obiektów w zależności od kontekstu aplikacji pakietu Office, a niektóre typy mogą uwidaczniać różne metody lub właściwości w różnych kontekstach.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual Basic, w których opcja **Option Strict** jest wyłączona, a projekty Visual C# dla obiektu lub mogą pracować bezpośrednio z typami, które wykorzystują te [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] funkcje [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] późnego wiązania.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Niejawne i jawne rzutowanie wartości zwracanych obiektu
 Wiele metod i właściwości w Microsoft Office podstawowych zestawów międzyoptykowych (PIA) zwraca wartości, ponieważ mogą zwracać <xref:System.Object> kilka różnych typów obiektów. Na przykład właściwość zwraca wartość , ponieważ jej wartość zwracana może być obiektem lub , w zależności <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> <xref:System.Object> od <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> tego, co to jest aktywny arkusz.

 Gdy metoda lub właściwość zwraca wartość , należy jawnie przekonwertować (w Visual Basic) obiekt na poprawny typ w projektach Visual Basic, w których opcja <xref:System.Object> **Strict** jest wł. Nie trzeba jawnie rzutować wartości <xref:System.Object> zwracanych w projektach Visual Basic, w których **opcja Option Strict** jest wyłączona.

 W większości przypadków w dokumentacji referencyjnej wymieniono możliwe typy wartości zwracanej przez element członkowski, który zwraca element <xref:System.Object> . Konwertowanie lub rzutowanie obiektu włącza intellisense dla obiektu w edytorze kodu.

 Aby uzyskać informacje o konwersji w Visual Basic, zobacz Niejawne i jawne konwersje [&#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) i [CType ](/dotnet/visual-basic/language-reference/functions/ctype-function)&#40;Visual Basic&#41;.

### <a name="examples"></a>Przykłady
 W poniższym przykładzie kodu pokazano, jak rzutować obiekt na określony typ w Visual Basic, w którym jest wł. **opcja** Strict. W tym typie projektu należy jawnie rzutować <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> właściwość na <xref:Microsoft.Office.Interop.Excel.Range> obiekt . Ten przykład wymaga projektu programu Excel na poziomie dokumentu z klasą arkusza o nazwie `Sheet1` .

  :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet9":::

 W poniższym przykładzie kodu pokazano, jak niejawnie rzutować obiekt na określony typ w projekcie programu Visual Basic, w którym opcja **Strict** jest wyłączona lub w projekcie Visual C# przeznaczonym dla obiektu [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . W tego typu projektach właściwość <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> jest niejawnie rzutowania na <xref:Microsoft.Office.Interop.Excel.Range> obiekt . Ten przykład wymaga projektu programu Excel na poziomie dokumentu z klasą arkusza o nazwie `Sheet1` .

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb" id="Snippet10":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs" id="Snippet10":::

## <a name="access-members-that-are-available-only-through-late-binding"></a>Dostęp do elementów członkowskich, które są dostępne tylko za pośrednictwem późnego powiązania
 Niektóre właściwości i metody w usłudze Office PIA są dostępne tylko za pośrednictwem późnego powiązania. W Visual Basic, w których opcja **Strict** jest wyłączona, lub w projektach Visual C#, które są ukierunkowane na element lub , można użyć funkcji późnego powiązania w tych językach, aby uzyskać dostęp do elementów członkowskich z późnym [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] wiązaniem. W Visual Basic, w których **opcja Ściśle jest** wł., należy użyć odbicia, aby uzyskać dostęp do tych elementów członkowskich.

### <a name="examples"></a>Przykłady
 W poniższym przykładzie kodu pokazano, jak uzyskać dostęp do elementów członkowskich z późnym wiązaniem w projekcie Visual Basic, w którym opcja **Strict** jest wyłączona lub w projekcie Visual C# przeznaczonym [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] dla . W tym przykładzie uzyskujesz dostęp do właściwości **Name późnej granicy** okna **dialogowego Otwieranie** pliku w programie Word. Aby użyć tego przykładu, uruchom go z klasy `ThisDocument` lub `ThisAddIn` w projekcie programu Word.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet122":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs" id="Snippet122":::

 W poniższym przykładzie kodu pokazano, jak używać odbicia w celu wykonania tego samego zadania w Visual Basic projektu, w którym jest wł. **opcja Strict.**

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb" id="Snippet102":::

## <a name="see-also"></a>Zobacz też
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
- [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)
- [Użyj przewodnika programowania &#40;języka C&#35; typu&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict, instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)
