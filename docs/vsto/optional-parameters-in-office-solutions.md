---
title: Parametry opcjonalne w rozwiązaniach pakietu Office
description: Dowiedz się, jak nie musisz przekazywać wartości parametrów opcjonalnych, ponieważ wartości domyślne są automatycznie używane dla każdego brakującego parametru.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: d6824d53d552a27a68a49d63497156147283fd29
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99847703"
---
# <a name="optional-parameters-in-office-solutions"></a>Parametry opcjonalne w rozwiązaniach pakietu Office
  Wiele metod w modelach obiektów Microsoft Office aplikacji akceptuje parametry opcjonalne. Jeśli używasz Visual Basic do tworzenia rozwiązań pakietu Office w programie Visual Studio, nie musisz przekazać wartości parametrów opcjonalnych, ponieważ wartości domyślne są automatycznie używane dla każdego brakującego parametru. W większości przypadków można także pominąć parametry opcjonalne w projektach Visual C#. Nie można jednak pominąć opcjonalnych parametrów **ref** `ThisDocument` klasy w projektach programu Word na poziomie dokumentu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Aby uzyskać więcej informacji na temat pracy z opcjonalnymi parametrami w Visual C# i Visual Basic projektach, zobacz [argumenty nazwane i opcjonalne &#40;C&#35; Przewodnik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) i [Parametry opcjonalne &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;.

> [!NOTE]
> We wcześniejszych wersjach programu Visual Studio należy przekazać wartość dla każdego opcjonalnego parametru w projektach Visual C#. Dla wygody te projekty obejmują zmienną globalną o nazwie `missing` , którą można przekazać do opcjonalnego parametru, gdy chcesz użyć wartości domyślnej parametru. Projekty Visual C# dla pakietu Office w programie Visual Studio nadal zawierają `missing` zmienną, ale zazwyczaj nie trzeba jej używać podczas opracowywania rozwiązań pakietu Office w programie [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] , z wyjątkiem przypadków, gdy metoda wywołuje metody z opcjonalnymi parametrami **ref** w `ThisDocument` klasie w projektach na poziomie dokumentu dla programu Word.

## <a name="example-in-excel"></a>Przykład w programie Excel
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A>Metoda ma wiele opcjonalnych parametrów. Możesz określić wartości dla niektórych parametrów i zaakceptować wartość domyślną innych, jak pokazano w poniższym przykładzie kodu. Ten przykład wymaga projektu na poziomie dokumentu z klasą arkusza o nazwie `Sheet1` .

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Przykład w programie Word
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>Metoda ma wiele opcjonalnych parametrów. Możesz określić wartości dla niektórych parametrów i zaakceptować wartość domyślną innych, jak pokazano w poniższym przykładzie kodu.

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Użyj parametrów opcjonalnych metod w klasie ThisDocument w projektach na poziomie dokumentu w języku Visual C# dla programu Word
 Model obiektów programu Word zawiera wiele metod z opcjonalnymi parametrami **ref** , które akceptują <xref:System.Object> wartości. Nie można jednak pominąć opcjonalnych parametrów **ref** metod wygenerowanej `ThisDocument` klasy w projektach na poziomie dokumentu w języku Visual C# dla programu Word. Visual C# pozwala pominąć opcjonalne parametry **ref** tylko dla metod interfejsów, a nie klas. Na przykład poniższy przykład kodu nie kompiluje się, ponieważ nie można pominąć opcjonalnych parametrów **ref** <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody `ThisDocument` klasy.

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 Gdy wywołujesz metody `ThisDocument` klasy, postępuj zgodnie z następującymi wskazówkami:

- Aby zaakceptować wartość domyślną opcjonalnego parametru **ref** , Przekaż `missing` zmienną do parametru. `missing`Zmienna jest automatycznie definiowana w projektach pakietu Office w języku Visual C# i jest przypisywana do wartości <xref:System.Type.Missing> w wygenerowanym kodzie projektu.

- Aby określić własną wartość opcjonalnego parametru **ref** , zadeklaruj obiekt, który jest przypisany do wartości, którą chcesz określić, a następnie przekaż obiekt do parametru.

  Poniższy przykład kodu demonstruje sposób wywołania <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody przez określenie wartości parametru *ignoreUppercase* i zaakceptowanie wartości domyślnej dla innych parametrów.

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  Jeśli chcesz napisać kod, który pomija opcjonalne parametry **ref** metody w `ThisDocument` klasie, możesz alternatywnie wywołać tę samą metodę dla <xref:Microsoft.Office.Interop.Word.Document> obiektu zwróconego przez <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> Właściwość i pominąć parametry z tej metody. Można to zrobić, ponieważ <xref:Microsoft.Office.Interop.Word.Document> jest interfejsem, a nie klasą.

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  Aby uzyskać więcej informacji na temat parametrów typu wartości i odwołania, zobacz [przekazywanie argumentów według wartości i przez odwołanie &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (dla Visual Basic) i [parametrów Pass &#40;C&#35; Przewodnik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
