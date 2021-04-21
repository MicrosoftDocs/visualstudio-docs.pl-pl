---
title: Parametry opcjonalne w rozwiązaniach pakietu Office
description: Dowiedz się, jak nie trzeba przekazywać wartości parametrów opcjonalnych, ponieważ wartości domyślne są automatycznie używane dla każdego brakującego parametru.
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
ms.openlocfilehash: 9c95842ac2c6d77a2312ac5c4c197ba22ed2020e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825423"
---
# <a name="optional-parameters-in-office-solutions"></a>Parametry opcjonalne w rozwiązaniach pakietu Office
  Wiele metod w modelach obiektów aplikacji Microsoft Office akceptuje parametry opcjonalne. Jeśli używasz Visual Basic pakietu Office w usłudze Visual Studio, nie musisz przekazywać wartości parametrów opcjonalnych, ponieważ wartości domyślne są automatycznie używane dla każdego brakującego parametru. W większości przypadków można również pominąć parametry opcjonalne w projektach Visual C#. Nie można jednak pominąć opcjonalnych **parametrów ref** klasy `ThisDocument` w projektach programu Word na poziomie dokumentu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Aby uzyskać więcej informacji na temat pracy z parametrami opcjonalnymi w projektach Visual C# i Visual Basic, zobacz Named and optional arguments &#40;C&#35; programming guide&#41;and Optional parameters &#40;Visual Basic&#41;(Nazwane i opcjonalne argumenty &#40;Przewodnik programowania w języku [C&#35;) ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) i [Optional parameters &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)(

> [!NOTE]
> We wcześniejszych wersjach Visual Studio należy przekazać wartość dla każdego opcjonalnego parametru w projektach Visual C#. Dla wygody te projekty zawierają zmienną globalną o nazwie , którą można przekazać do opcjonalnego parametru, gdy chcesz użyć wartości `missing` domyślnej parametru. Projekty Visual C# dla pakietu Office w programie Visual Studio nadal zawierają zmienną , ale zazwyczaj nie trzeba jej używać podczas opracowywania rozwiązań pakietu Office w programie , z wyjątkiem sytuacji, w których metody są wywołania z opcjonalnymi parametrami ref w klasie w projektach na poziomie dokumentu dla programu `missing` [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)]  `ThisDocument` Word.

## <a name="example-in-excel"></a>Przykład w programie Excel
 Metoda <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> ma wiele parametrów opcjonalnych. Możesz określić wartości dla niektórych parametrów i zaakceptować wartość domyślną innych, jak pokazano w poniższym przykładzie kodu. Ten przykład wymaga projektu na poziomie dokumentu z klasą arkusza o nazwie `Sheet1` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs" id="Snippet1":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb" id="Snippet1":::

## <a name="example-in-word"></a>Przykład w programie Word
 Metoda <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> ma wiele parametrów opcjonalnych. Możesz określić wartości dla niektórych parametrów i zaakceptować wartość domyślną innych, jak pokazano w poniższym przykładzie kodu.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet1":::

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Używanie opcjonalnych parametrów metod w klasie ThisDocument w projektach na poziomie dokumentu Visual C# dla programu Word
 Model obiektów programu Word zawiera wiele metod z opcjonalnymi **parametrami ref,** które akceptują <xref:System.Object> wartości. Nie można jednak pominąć opcjonalnych **parametrów ref** metod wygenerowanej klasy w projektach na poziomie dokumentu języka `ThisDocument` Visual C# dla programu Word. Język Visual C# umożliwia pominięcie opcjonalnych **parametrów ref** tylko dla metod interfejsów, a nie klas. Na przykład poniższy przykład kodu nie kompiluje się, ponieważ nie można pominąć opcjonalnych parametrów **ref** <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody klasy `ThisDocument` .

 :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet3":::

 Podczas wywołania metod klasy postępuj zgodnie `ThisDocument` z tymi wytycznymi:

- Aby zaakceptować wartość domyślną opcjonalnego **parametru ref,** przekaż `missing` zmienną do parametru . Zmienna jest automatycznie definiowana w projektach pakietu Office w języku Visual C# i jest przypisywana do wartości `missing` <xref:System.Type.Missing> w wygenerowanym kodzie projektu.

- Aby określić własną wartość opcjonalnego parametru **ref,** zadeklaruj obiekt przypisany do wartości, którą chcesz określić, a następnie przekaż obiekt do parametru .

  W poniższym przykładzie kodu pokazano, jak wywołać metodę , określając wartość parametru <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> *ignoreUppercase* i akceptując wartość domyślną dla innych parametrów.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet4":::

  Jeśli chcesz napisać kod, który  pomija opcjonalne parametry ref metody w klasie , możesz też wywołać tę samą metodę dla obiektu zwróconego przez właściwość i pominąć parametry z tej `ThisDocument` <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> metody. Można to zrobić, ponieważ <xref:Microsoft.Office.Interop.Word.Document> jest interfejsem, a nie klasą.

  :::code language="csharp" source="../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs" id="Snippet5":::

  Aby uzyskać więcej informacji na temat wartości i parametrów typu odwołania, zobacz Pass arguments by value and by reference &#40;Visual Basic&#41;(for Visual Basic) (Przekaż parametry i parametry odwołania do parametrów), zobacz Pass [arguments by value and ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) by reference &#40;Visual Basic&#41;(Przekaż parametry dla Visual Basic) i Pass parameters &#40;C&#35; programming guide (Przewodnik programowania dla języka C [&#35;)&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).

## <a name="see-also"></a>Zobacz też
- [Opracowywanie rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
