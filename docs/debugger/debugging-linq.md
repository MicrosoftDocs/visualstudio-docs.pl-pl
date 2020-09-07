---
title: Debugowanie LINQ | Microsoft Docs
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
ms.openlocfilehash: 146519b33be19da1103aed958e42ec5ffaee8bd0
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509773"
---
# <a name="debugging-linq"></a>Debugowanie LINQ
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] obsługuje debugowanie kodu programu Query Integrated Language (LINQ) z pewnymi ograniczeniami. Większość funkcji debugowania współpracuje z instrukcjami LINQ, w tym krokowe, ustawianie punktów przerwania i wyświetlanie wyników w oknach debugera. W tym temacie opisano główne ograniczenia debugowania LINQ.

## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> Wyświetlanie wyników LINQ
 Można wyświetlić wynik instrukcji LINQ przy użyciu etykietek danych, okno wyrażeń kontrolnych i okna dialogowego QuickWatch. W przypadku korzystania z okna źródłowego można wstrzymywać wskaźnik zapytania w oknie źródło i pojawić się etykietki danych. Można skopiować zmienną LINQ i wkleić ją do okna dialogowego okno wyrażeń kontrolnych lub QuickWatch.

 W LINQ, zapytanie nie jest oceniane podczas tworzenia lub deklarowania, ale tylko wtedy, gdy zapytanie jest używane. W związku z tym zapytanie nie ma wartości, dopóki nie zostanie obliczone. Pełny opis tworzenia i oceny zapytania można znaleźć w temacie [wprowadzenie do zapytań LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries) lub [pisanie pierwszej kwerendy LINQ](/dotnet/visual-basic/programming-guide/concepts/linq/writing-your-first-linq-query).

 Aby wyświetlić wynik zapytania, debuger musi ją oszacować. Ta niejawna Ocena, która występuje po wyświetleniu wyniku zapytania LINQ w debugerze, ma pewne skutki, które należy wziąć pod uwagę:

- Każda Ocena zapytania trwa. Rozszerzanie węzła wyników zajmuje trochę czasu. W przypadku niektórych zapytań powtarzające się oceny mogą spowodować zauważalną spadek wydajności.

- Obliczenie zapytania może skutkować efektami ubocznymi, które są zmianami wartości danych lub stanu programu. Nie wszystkie zapytania mają efekty uboczne. Aby określić, czy zapytanie może być bezpiecznie ocenione bez efektów ubocznych, należy zrozumieć kod implementujący zapytanie.

## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> Krokowe i LINQ
 Podczas debugowania kodu LINQ, krok po kroku ma pewne różnice behawioralne, o których należy wiedzieć.

### <a name="linq-to-sql"></a>LINQ do SQL
 W LINQ to SQL zapytaniach kod predykatu jest poza kontrolą debugera. W związku z tym nie można wkroczyć do kodu predykatu. Wszystkie zapytania, które kompilują do drzewa wyrażenia, tworzą kod, który jest poza kontrolą debugera.

### <a name="stepping-in-visual-basic"></a>Krokowe Visual Basic
 Gdy przechodzisz przez program Visual Basic i debuger napotka deklarację zapytania, nie wkracza do deklaracji, ale podświetli całą deklarację jako pojedynczą instrukcję. Takie zachowanie występuje, ponieważ zapytanie nie jest oceniane, dopóki nie zostanie wywołane. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq).

 Po przekroczeniu poniższego przykładowego kodu debuger podświetla deklarację zapytania lub utworzenie zapytania jako pojedynczej instrukcji.

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

 Po ponownym przekroczeniu kroku debuger zostanie wyróżniony `For Each cur In x` . W następnym kroku przeprowadzimy do funkcji `MyFunction` . Po przejściu przez `MyFunction` program przechodzi z powrotem do `Console.WriteLine(cur.ToSting())` . W żadnym momencie przekroczenie kodu predykatu w deklaracji zapytania, chociaż debuger szacuje ten kod.

### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Zamienianie predykatu na funkcję w celu włączenia taktowania (Visual Basic)
 Jeśli musisz przejść przez kod predykatu do celów debugowania, możesz zamienić predykat z wywołaniem funkcji, która zawiera oryginalny kod predykatu. Załóżmy na przykład, że masz ten kod:

```vb
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}

' Get the even numbers
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt

For each item in query
      Console.WriteLine(item)
Next
```

 Kod predykatu można przenieść do nowej funkcji o nazwie `IsEven` :

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

 Poprawione zapytanie wywołuje funkcję `IsEven` przy każdym przebiegu przez `items` . Możesz użyć okien debugera, aby sprawdzić, czy każdy element spełnia określony warunek, i możesz przejść przez kod w `IsEven` . Predykat w tym przykładzie jest dość prosty. Jednak jeśli istnieje trudniejszy predykat, który trzeba debugować, ta technika może być bardzo przydatna.

## <a name="edit-and-continue-not-supported-for-linq"></a><a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Edytowanie i kontynuowanie nie jest obsługiwane w przypadku LINQ
 Edytuj i Kontynuuj obsługuje zmiany zapytań LINQ z ograniczeniami. Aby uzyskać szczegółowe informacje, zobacz temat [obsługiwane zmiany](https://github.com/dotnet/roslyn/blob/master/docs/wiki/EnC-Supported-Edits.md) w programie Enc

## <a name="see-also"></a>Zobacz także

- [Debugowanie SQL](/previous-versions/visualstudio/visual-studio-2010/zefbf0t6\(v\=vs.100\))
- [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)
- [Wprowadzenie do kwerend LINQ (C#)](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq-queries)
- [Wprowadzenie do LINQ w Visual Basic](/dotnet/visual-basic/programming-guide/language-features/linq/introduction-to-linq)
