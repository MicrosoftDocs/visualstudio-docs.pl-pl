---
title: Późne powiązania w rozwiązaniach pakietu Office
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
ms.openlocfilehash: 520ad17bf96f4a6c657a8bd48ac0fdd29b52e1b1
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54873174"
---
# <a name="late-binding-in-office-solutions"></a>Późne powiązania w rozwiązaniach pakietu Office
  Niektóre typy modeli obiektów w aplikacji pakietu Office udostępniają funkcje, które są dostępne za pośrednictwem funkcji późnego wiązania. Na przykład niektóre metody i właściwości może zwracać różne typy obiektów, w zależności od kontekstu aplikacji pakietu Office, a w niektórych typów może narazić różne metody lub właściwości w różnych kontekstach.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Projektów języka Visual Basic, gdzie **Option Strict** jest wyłączone i wizualna C# projekty [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] może współpracować bezpośrednio z typami, korzystających z tych funkcji późne powiązania.  
  
## <a name="implicit-and-explicit-casting-of-object-return-values"></a>Wartości zwracane jawne i niejawne rzutowanie obiektu  
 Wielu metod i właściwości w programie Microsoft Office, podstawowe zestawy międzyoperacyjne (PIA) zwracają <xref:System.Object> wartości, ponieważ zwracają kilka różnych typów obiektów. Na przykład <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> właściwość zwraca <xref:System.Object> jego zwracanej wartości mogą być <xref:Microsoft.Office.Interop.Excel.Worksheet> lub <xref:Microsoft.Office.Interop.Excel.Chart> obiektu, w zależności od aktywnego arkusza.  
  
 Gdy metoda lub właściwość zwraca <xref:System.Object>, jawnie przekonwertuj (w języku Visual Basic) obiektu do poprawnego typu w projektach języka Visual Basic gdzie **Option Strict** znajduje się na. Nie trzeba jawnie rzutowane <xref:System.Object> wartości zwracane w projektach języka Visual Basic gdzie **Option Strict** jest wyłączona.  
  
 W większości przypadków dokumentację referencyjną zawiera listę możliwych typów wartość zwracaną dla elementu członkowskiego, która zwraca <xref:System.Object>. Konwertowanie lub Rzutowanie obiektu temu IntelliSense dla obiektów w edytorze kodu.  
  
 Aby uzyskać informacje o konwersji w języku Visual Basic, zobacz [Konwersje jawne i niejawne &#40;języka Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) i [funkcja CType &#40;języka Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje, jak można rzutować obiektu określonego typu w projekcie Visual Basic gdzie **Option Strict** znajduje się na. W tym typie projektu, musisz jawnie rzutowane <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> właściwość <xref:Microsoft.Office.Interop.Excel.Range>. W tym przykładzie wymaga dokumentu projektów programu Excel z arkusza klasę o nazwie `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]  
  
 Poniższy przykład kodu pokazuje, jak niejawnie rzutowany obiektu określonego typu w projekcie Visual Basic gdzie **Option Strict** jest wyłączony lub element wizualny C# projektu, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. W przypadku tych typów projektów <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> właściwość jest niejawnie rzutowany na <xref:Microsoft.Office.Interop.Excel.Range>. W tym przykładzie wymaga dokumentu projektów programu Excel z arkusza klasę o nazwie `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]  
  
## <a name="access-members-that-are-available-only-through-late-binding"></a>Elementy członkowskie dostępu, które są dostępne wyłącznie za pośrednictwem późne wiązanie  
 Niektóre właściwości i metody w zestawy PIA pakietu Office są dostępne wyłącznie za pośrednictwem późnego wiązania. W języku Visual Basic projektów, gdzie **Option Strict** jest wyłączone lub w elemencie wizualnym C# projektów, których celem [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] lub [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], można użyć funkcji późne powiązania w tych językach na dostęp do elementów członkowskich z późnym wiązaniem. W języku Visual Basic projektów, gdzie **Option Strict** jest włączona, należy używać odbicia do dostęp do tych elementów członkowskich.  
  
### <a name="examples"></a>Przykłady  
 Poniższy przykład kodu pokazuje, jak uzyskać dostęp z późnym wiązaniem członków w projektach Visual Basic gdzie **Option Strict** jest wyłączony lub element wizualny C# projektu, który jest przeznaczony dla [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]. Ten przykład uzyskuje dostęp z późnym wiązaniem **nazwa** właściwość **Otwórz plik** okno dialogowe w programie Word. Aby użyć tego przykładu, należy uruchomić go z `ThisDocument` lub `ThisAddIn` klasy w projekcie programu Word.  
  
 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]  
  
 Poniższy przykład kodu pokazuje, jak używać odbicia w celu wykonania tego samego zadania w projekcie Visual Basic gdzie **Option Strict** znajduje się na.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]  
  
## <a name="see-also"></a>Zobacz także  
 [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)   
 [Parametry opcjonalne w rozwiązaniach pakietu Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Użyj typu dynamicznego &#40;C&#35; Podręcznik programowania&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict — instrukcja](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Odbicie (C#)](/dotnet/csharp/programming-guide/concepts/reflection)  
 [Odbicie (Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)  
 [Projektowanie i tworzenie rozwiązań pakietu Office](../vsto/designing-and-creating-office-solutions.md)  
