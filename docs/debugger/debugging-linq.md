---
title: Debugowanie LINQ | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a21fb412b5b207dca78c70561b8b25199ae3ac96
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54976397"
---
# <a name="debugging-linq"></a>Debugowanie LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Obsługa debugowania języka zintegrowanego zapytania kodu (LINQ), z pewnymi ograniczeniami. Najbardziej debugujące funkcje współpracują z instrukcjami LINQ, w tym przechodzenie krok po kroku, ustawiania punktów przerwania i wyświetlaniem wyników w oknach debugera. Ten temat opisuje główne ograniczenia debugowania LINQ.  
  
##  <a name="BKMK_ViewingLINQResults"></a> Wyświetlanie wyników programu LINQ  
 Można przeglądać rezultaty instrukcji LINQ, używając DataTips, okna czujki i okna dialogowego QuickWatch. Kiedy używasz okna źródła, możesz wstrzymać wskaźnik na zapytaniu w oknie źródła i wyświetli się datatip. Można kopiować zmienną LINQ i wklej go w oknie czujki lub okno dialogowe QuickWatch.  
  
 W programie LINQ kwerenda nie jest uwzględniana podczas tworzenia lub deklarowania, ale tylko wtedy, gdy kwerenda jest używana. W związku z tym zapytanie nie ma wartości dopóki jest ocenione. Aby uzyskać pełny opis tworzenia i oceny kwerend, zobacz [wprowadzenie do zapytań LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) lub [Your pierwszego zapytania LINQ pisania](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).  
  
 Aby wyświetlić wynik zapytania, debugger musi je ocenić. Bezwarunkowa ocena, która występuje podczas wyświetlania wyniku zapytania LINQ w debugerze, ma jakieś konsekwencje, które należy wziąć pod uwagę:  
  
-   Każdej oceny kwerendy jest czasochłonne. Rozwinięcie węzła wyników zajmuje trochę czasu. Dla niektórych zapytań powtarzające się oceny może prowadzić do kar zauważalna zmiana wydajności.  
  
-   Ocena zapytania może spowodować efekty uboczne, które są zmianami wartości danych lub stanu programu. Nie wszystkie kwerendy mają skutki uboczne. Aby ustalić, czy zapytanie może być bezpiecznie ocenione bez efektów ubocznych, musisz zrozumieć kod, który implementuje zapytanie.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Przechodzenie krok po kroku i LINQ  
 Podczas debugowania kodu LINQ, krokowość posiada różnice w zachowaniu, które należy poznać.  
  
### <a name="linq-to-sql"></a>LINQ do SQL  
 W zapytaniach składnika LINQ to SQL kod predykatu jest poza kontrolą debugera. W związku z tym nie możesz wejść w kod predykatu. Wszystkie zapytania, który kompiluje do drzewa wyrażenie generuje kod, który jest poza kontrolą debugera.  
  
### <a name="stepping-in-visual-basic"></a>Przechodzenie krok po kroku w języku Visual Basic  
 Jeśli są krokowe program Visual Basic debugger napotka deklarację zapytania, nie wkracza w deklarację, ale wyróżnia całą deklarację jako pojedynczą instrukcję. Dzieje się tak, ponieważ zapytanie nie jest oceniany, dopóki nie jest wywoływana. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).  
  
 Jeśli prześledzisz poniższy przykład kodu do usuwania błędów podkreśli deklarację kwerendy lub utworzenie kwerendy jako pojedynczej instrukcji.  
  
```vb
Function MyFunction(ByVal x As Char)  
    Return True  
End Function  
  
Sub Main()  
    'Query creation  
    Dim x = From it In "faoaoeua" _  
            Where MyFunction(it) _  
            Select New With {.a = it}  
  
    ' Query execution  
    For Each cur In x  
        Console.WriteLine(cur.ToString())  
    Next  
End Sub  
```  
  
 Kiedy wkraczasz ponownie, debugger wyróżnia `For Each cur In x`. Na następnym etapie przechodzi do funkcji `MyFunction`. Po przejściu przez `MyFunction`, skacze z powrotem do `Console.WriteLine(cur.ToSting())`. W żadnym punkcie nie ona przejść przez kod predykatu w zgłoszeniu zapytania, chociaż debuger ocenia ten kodu.  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Zastąpienie predykatu funkcją, aby włączyć przechodzenia krok po kroku (Visual Basic)  
 Jeśli masz można przejść przez kod predykatu do debugowania, możesz zastąpić predykat wywołaniem funkcji, która zawiera oryginalny kod predykatu. Na przykład załóżmy, że masz taki kod:  
  
```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Można przemieścić kod orzeczenia do nowej funkcji o nazwie `IsEven`:  
  
```vb
Dim items () as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where IsEven(nextInt) Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
...   
Function IsEven(item As =Integer) as Boolean  
      Return item Mod 2 = 0  
End Function  
```  
  
 Zrewidowane zapytanie wywołuje funkcję `IsEven` przy każdym przejściu przez `items`. Można użyć okien debugera, aby zobaczyć, czy każdy element spełnia podany warunek i można przejść przez kod w `IsEven`. Predykat w tym przykładzie jest dość prosta. Jednak jeśli masz trudniejszy predykat, który musisz zdebugować, ta technika może być bardzo przydatne.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Edytuj i Kontynuuj nie obsługiwanie dla programu LINQ  
 Edytuj i Kontynuuj obsługuje zmiany zapytań LINQ z ograniczeniami. Aby uzyskać więcej informacji, zobacz [EnC obsługiwane zmiany](https://github.com/dotnet/roslyn/wiki/EnC-Supported-Edits))
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)
- [Wprowadzenie do zapytań LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
