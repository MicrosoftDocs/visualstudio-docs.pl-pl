---
title: Parametry opcjonalne w rozwiązaniach pakietu Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d6baf0c32d087ea804bb8e221745337c73b64114
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56639271"
---
# <a name="optional-parameters-in-office-solutions"></a>Parametry opcjonalne w rozwiązaniach pakietu Office
  Wiele metod w modele obiektów w aplikacji pakietu Microsoft Office akceptuje następujące parametry opcjonalne. Jeśli używasz języka Visual Basic do opracowywania rozwiązań pakietu Office w programie Visual Studio, nie masz do przekazania wartości dla parametrów opcjonalnych, ponieważ wartości domyślne są automatycznie używane dla każdego brakującego parametru. W większości przypadków można również pominąć parametry opcjonalne w projektach Visual C#. Jednak nie można pominąć opcjonalne **ref** parametry `ThisDocument` klas w projektach programu Word w poziomie dokumentu.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Aby uzyskać więcej informacji na temat pracy z opcjonalnymi parametrami w projektach Visual C# i Visual Basic, zobacz [nazwane i opcjonalne argumenty &#40;C&#35; Podręcznik programowania&#41; ](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) i [ &#40;Języka Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters).

> [!NOTE]
>  We wcześniejszych wersjach programu Visual Studio należy przekazać wartość dla każdego opcjonalnego parametru, w projektach Visual C#. Dla wygody te projekty zawierają zmienna globalna o nazwie `missing` , można przekazać do parametru opcjonalnego użyć wartości domyślnej parametru. Projekty Visual C# dla pakietu Office w programie Visual Studio nadal zawierają `missing` zmienną, ale zwykle nie trzeba używać go podczas opracowywania rozwiązań pakietu Office w [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)], z wyjątkiem sytuacji, gdy wywołujesz metody z opcjonalnymi **ref** Parametry w `ThisDocument` klasy w projektów na poziomie dokumentu dla programu Word.

## <a name="example-in-excel"></a>Przykład w programie Excel
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> Metoda ma wiele parametrów opcjonalnych. Można określić wartości dla niektórych parametrów i zaakceptuj wartość domyślną innych, jak pokazano w poniższym przykładzie kodu. W tym przykładzie wymaga projektów dokumentów z arkusza klasę o nazwie `Sheet1`.

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Przykład w programie Word
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> Metoda ma wiele parametrów opcjonalnych. Można określić wartości dla niektórych parametrów i zaakceptuj wartość domyślną innych, jak pokazano w poniższym przykładzie kodu.

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Parametry opcjonalne użycie metod w klasie ThisDocument w Visual C# projektów na poziomie dokumentu dla programu Word
 Model obiektów programu Word zawiera wiele metod z opcjonalnymi **ref** parametry, które akceptują <xref:System.Object> wartości. Jednak nie można pominąć opcjonalne **ref** parametrów metod wygenerowany `ThisDocument` klasy w Visual C# projektów poziomie dokumentu dla programu Word. Visual C# umożliwia pominięcie opcjonalne **ref** parametry tylko dla metod interfejsów nie klasy. Na przykład, poniższy kod nie kompiluje się, ponieważ nie można pominąć opcjonalne **ref** parametry <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody `ThisDocument` klasy.

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 Podczas wywoływania metody `ThisDocument` klasy, należy przestrzegać następujących wytycznych:

- Aby zaakceptować wartość domyślną opcjonalny **ref** parametr, — dostęp próbny `missing` zmienną do parametru. `missing` Zmienna jest automatycznie definiowana w projektach Visual C# pakietu Office i ma przypisaną wartość <xref:System.Type.Missing> kodu wygenerowanego projektu.

- Aby określić wartość dla opcjonalny **ref** parametru zadeklarować obiekt, który jest przypisany do określonej wartości, aby określić, a następnie przekazać obiekt do parametru.

  Poniższy przykład kodu pokazuje sposób wywołania <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> metody, określając wartość dla *ignoreUppercase* parametru i akceptując wartości domyślne dla innych parametrów.

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  Jeśli chcesz napisać kod, który umożliwia pominięcie opcjonalne **ref** parametry metody w `ThisDocument` klasy, można też wywołać tej samej metody na <xref:Microsoft.Office.Interop.Word.Document> obiektu zwróconego przez <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> właściwości i pominąć Parametry z tej metody. Można to zrobić, ponieważ <xref:Microsoft.Office.Interop.Word.Document> jest interfejsem, a nie klasę.

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  Aby uzyskać więcej informacji na temat parametrów typu wartości i odwołań, zobacz [przekazywanie argumentów według wartości i według odwołania &#40;języka Visual Basic&#41; ](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (dla języka Visual Basic) i [parametry są przekazywane &#40;C&#35; Podręcznik programowania&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters).

## <a name="see-also"></a>Zobacz także
- [Opracowywania rozwiązań pakietu Office](../vsto/developing-office-solutions.md)
- [Pisanie kodu w rozwiązaniach pakietu Office](../vsto/writing-code-in-office-solutions.md)
