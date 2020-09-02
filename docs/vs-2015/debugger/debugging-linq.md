---
title: Debugowanie LINQ | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, LINQ
- LINQ, viewing results in debugger
- LINQ, debugging
- LINQ, stepping
- LINQ, edit and continue
ms.assetid: dbae26cb-ac5f-4312-b474-b9f29714f4c6
caps.latest.revision: 28
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0292bf5b62bf150a598b4c750929ba6928216a50
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65691271"
---
# <a name="debugging-linq"></a>Debugowanie LINQ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obsługuje debugowanie kodu programu Query Integrated Language (LINQ) z pewnymi ograniczeniami. Większość funkcji debugowania współpracuje z instrukcjami LINQ, w tym krokowe, ustawianie punktów przerwania i wyświetlanie wyników w oknach debugera. W tym temacie opisano główne ograniczenia debugowania LINQ.  
  
## <a name="viewing-linq-results"></a><a name="BKMK_ViewingLINQResults"></a> Wyświetlanie wyników LINQ  
 Można wyświetlić wynik instrukcji LINQ przy użyciu etykietek danych, okno wyrażeń kontrolnych i okna dialogowego QuickWatch. W przypadku korzystania z okna źródłowego można wstrzymywać wskaźnik zapytania w oknie źródło i pojawić się etykietki danych. Można skopiować zmienną LINQ i wkleić ją do okna dialogowego okno wyrażeń kontrolnych lub QuickWatch.  
  
 W LINQ, zapytanie nie jest oceniane podczas tworzenia lub deklarowania, ale tylko wtedy, gdy zapytanie jest używane. W związku z tym zapytanie nie ma wartości, dopóki nie zostanie obliczone. Pełny opis tworzenia i oceny zapytania można znaleźć w temacie [wprowadzenie do zapytań LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8) lub [pisanie pierwszej kwerendy LINQ](https://msdn.microsoft.com/library/4affb732-3e9b-4479-aa31-1f9bd8183cbe).  
  
 Aby wyświetlić wynik zapytania, debuger musi ją oszacować. Ta niejawna Ocena, która występuje po wyświetleniu wyniku zapytania LINQ w debugerze, ma pewne skutki, które należy wziąć pod uwagę:  
  
- Każda Ocena zapytania trwa. Rozszerzanie węzła wyników zajmuje trochę czasu. W przypadku niektórych zapytań powtarzające się oceny mogą spowodować zauważalną spadek wydajności.  
  
- Obliczenie zapytania może skutkować efektami ubocznymi, które są zmianami wartości danych lub stanu programu. Nie wszystkie zapytania mają efekty uboczne. Aby określić, czy zapytanie może być bezpiecznie ocenione bez efektów ubocznych, należy zrozumieć kod implementujący zapytanie.  
  
## <a name="stepping-and-linq"></a><a name="BKMK_SteppingAndLinq"></a> Krokowe i LINQ  
 Podczas debugowania kodu LINQ, krok po kroku ma pewne różnice behawioralne, o których należy wiedzieć.  
  
### <a name="linq-to-sql"></a>LINQ to SQL  
 W LINQ to SQL zapytaniach kod predykatu jest poza kontrolą debugera. W związku z tym nie można wkroczyć do kodu predykatu. Wszystkie zapytania, które kompilują do drzewa wyrażenia, tworzą kod, który jest poza kontrolą debugera.  
  
### <a name="stepping-in-visual-basic"></a>Krokowe Visual Basic  
 Gdy przechodzisz przez program Visual Basic i debuger napotka deklarację zapytania, nie wkracza do deklaracji, ale podświetli całą deklarację jako pojedynczą instrukcję. Takie zachowanie występuje, ponieważ zapytanie nie jest oceniane, dopóki nie zostanie wywołane. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984).  
  
 Po przekroczeniu poniższego przykładowego kodu debuger podświetla deklarację zapytania lub utworzenie zapytania jako pojedynczej instrukcji.  
  
```  
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
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Kod predykatu można przenieść do nowej funkcji o nazwie `IsEven` :  
  
```  
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
 Edytuj i Kontynuuj nie obsługuje zmian w zapytaniach LINQ. W przypadku dodania, usunięcia lub zmiany instrukcji LINQ podczas sesji debugowania zostanie wyświetlone okno dialogowe z informacją, że zmiana nie jest obsługiwana przez polecenie Edytuj i Kontynuuj. W tym momencie można albo cofnąć zmiany lub zatrzymać sesję debugowania i ponownie uruchomić nową sesję z edytowanym kodem.  
  
 Ponadto polecenie Edytuj i Kontynuuj nie obsługuje zmiany typu ani wartości zmiennej, która jest używana w instrukcji LINQ. Ponownie można cofnąć zmiany lub zatrzymać i ponownie uruchomić sesję debugowania.  
  
 W języku C# nie można używać żadnych kodów w metodzie, która zawiera kwerendę LINQ.  
  
 W Visual Basic można użyć funkcji Edytuj i Kontynuuj w kodzie innym niż LINQ, nawet w metodzie zawierającej zapytanie LINQ. Możesz dodać lub usunąć kod przed instrukcją LINQ, nawet jeśli zmiany wpłyną na numer wiersza zapytania LINQ. Środowisko debugowania Visual Basic dla kodu nielinq pozostaje takie samo, jak przed wprowadzeniem LINQ. Nie można jednak zmienić, dodać ani usunąć zapytania LINQ, chyba że chcesz zatrzymać debugowanie, aby zastosować zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie SQL](https://msdn.microsoft.com/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Efekty uboczne i wyrażenia](https://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)   
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Wprowadzenie do zapytań LINQ (C#)](https://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)   
 [Wprowadzenie do LINQ w Visual Basic](https://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)
