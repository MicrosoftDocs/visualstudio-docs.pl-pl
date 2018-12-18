---
title: Debugowanie LINQ | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 081c97bffc062bf2bbc9d24feed13e5e512b8c74
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51755611"
---
# <a name="debugging-linq"></a>Debugowanie LINQ
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Obsługa debugowania języka zintegrowanego zapytania kodu (LINQ), z pewnymi ograniczeniami. Najbardziej debugujące funkcje współpracują z instrukcjami LINQ, w tym przechodzenie krok po kroku, ustawiania punktów przerwania i wyświetlaniem wyników w oknach debugera. Ten temat opisuje główne ograniczenia debugowania LINQ.  
  
##  <a name="BKMK_ViewingLINQResults"></a> Wyświetlanie wyników programu LINQ  
 Można przeglądać rezultaty instrukcji LINQ, używając DataTips, okna czujki i okna dialogowego QuickWatch. Kiedy używasz okna źródła, możesz wstrzymać wskaźnik na zapytaniu w oknie źródła i wyświetli się datatip. Można kopiować zmienną LINQ i wklej go w oknie czujki lub okno dialogowe QuickWatch.  
  
 W programie LINQ kwerenda nie jest uwzględniana podczas tworzenia lub deklarowania, ale tylko wtedy, gdy kwerenda jest używana. W związku z tym zapytanie nie ma wartości dopóki jest ocenione. Aby uzyskać pełny opis tworzenia i oceny kwerend, zobacz [wprowadzenie do zapytań LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8) lub [Your pierwszego zapytania LINQ pisania](http://msdn.microsoft.com/library/4affb732-3e9b-4479-aa31-1f9bd8183cbe).  
  
 Aby wyświetlić wynik zapytania, debugger musi je ocenić. Bezwarunkowa ocena, która występuje podczas wyświetlania wyniku zapytania LINQ w debugerze, ma jakieś konsekwencje, które należy wziąć pod uwagę:  
  
-   Każdej oceny kwerendy jest czasochłonne. Rozwinięcie węzła wyników zajmuje trochę czasu. Dla niektórych zapytań powtarzające się oceny może prowadzić do kar zauważalna zmiana wydajności.  
  
-   Ocena zapytania może spowodować efekty uboczne, które są zmianami wartości danych lub stanu programu. Nie wszystkie kwerendy mają skutki uboczne. Aby ustalić, czy zapytanie może być bezpiecznie ocenione bez efektów ubocznych, musisz zrozumieć kod, który implementuje zapytanie.  
  
##  <a name="BKMK_SteppingAndLinq"></a> Przechodzenie krok po kroku i LINQ  
 Podczas debugowania kodu LINQ, krokowość posiada różnice w zachowaniu, które należy poznać.  
  
### <a name="linq-to-sql"></a>LINQ do SQL  
 W zapytaniach składnika LINQ to SQL kod predykatu jest poza kontrolą debugera. W związku z tym nie możesz wejść w kod predykatu. Wszystkie zapytania, który kompiluje do drzewa wyrażenie generuje kod, który jest poza kontrolą debugera.  
  
### <a name="stepping-in-visual-basic"></a>Przechodzenie krok po kroku w języku Visual Basic  
 Jeśli są krokowe program Visual Basic debugger napotka deklarację zapytania, nie wkracza w deklarację, ale wyróżnia całą deklarację jako pojedynczą instrukcję. Dzieje się tak, ponieważ zapytanie nie jest oceniany, dopóki nie jest wywoływana. Aby uzyskać więcej informacji, zobacz [wprowadzenie do LINQ w Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984).  
  
 Jeśli prześledzisz poniższy przykład kodu do usuwania błędów podkreśli deklarację kwerendy lub utworzenie kwerendy jako pojedynczej instrukcji.  
  
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
  
 Kiedy wkraczasz ponownie, debugger wyróżnia `For Each cur In x`. Na następnym etapie przechodzi do funkcji `MyFunction`. Po przejściu przez `MyFunction`, skacze z powrotem do `Console.WriteLine(cur.ToSting())`. W żadnym punkcie nie ona przejść przez kod predykatu w zgłoszeniu zapytania, chociaż debuger ocenia ten kodu.  
  
### <a name="replacing-a-predicate-with-a-function-to-enable-stepping-visual-basic"></a>Zastąpienie predykatu funkcją, aby włączyć przechodzenia krok po kroku (Visual Basic)  
 Jeśli masz można przejść przez kod predykatu do debugowania, możesz zastąpić predykat wywołaniem funkcji, która zawiera oryginalny kod predykatu. Na przykład załóżmy, że masz taki kod:  
  
```  
Dim items() as integer ={1, 2, 3, 4, 5, 6, 7, 8, 9, 10}  
  
' Get the even numbers  
Dim query = From nextInt in items Where nextInt Mod 2 = 0 Select nextInt  
  
For each item in query  
      Console.WriteLine(item)  
Next  
```  
  
 Można przemieścić kod orzeczenia do nowej funkcji o nazwie `IsEven`:  
  
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
  
 Zrewidowane zapytanie wywołuje funkcję `IsEven` przy każdym przejściu przez `items`. Można użyć okien debugera, aby zobaczyć, czy każdy element spełnia podany warunek i można przejść przez kod w `IsEven`. Predykat w tym przykładzie jest dość prosta. Jednak jeśli masz trudniejszy predykat, który musisz zdebugować, ta technika może być bardzo przydatne.  
  
##  <a name="BKMK_EditandContinueNotSupportedforLINQ"></a> Edytuj i Kontynuuj nie obsługiwanie dla programu LINQ  
 Edytuj i Kontynuuj nie obsługuje zmiany zapytań LINQ. Jeśli dodać, usunąć lub zmienisz instrukcję LINQ podczas sesji debugowania pojawia się okno dialogowe informujące, że zmiana nie jest obsługiwana przez Edytuj i Kontynuuj. W tym momencie można albo cofnąć zmiany lub zatrzymać sesję debugowania i ponownie uruchomić nową sesję edycji kodu.  
  
 Ponadto, Edytuj i Kontynuuj nie obsługuje zmiany typu lub wartości zmiennej, która jest używana w instrukcji LINQ. Ponownie można albo cofnąć zmiany lub zatrzymać i ponownie uruchomić sesję debugowania.  
  
 W języku C# nie możesz użyć Edytuj i Kontynuuj na dowolnym kodzie w metodzie, która zawiera kwerendę LINQ.  
  
 W języku Visual Basic umożliwia Edytuj i Kontynuuj na kodzie non-LINQ, nawet w metodzie, która zawiera kwerendę LINQ. Można dodać lub usunąć kod przez instrukcją LINQ, nawet jeśli zmiany mają wpływ na numer wiersza zapytania LINQ. Języka Visual Basic obsługi debugowania dla kodu-LINQ, pozostaje taki sam, jakim był, zanim wprowadzenie LINQ nie zmieniło. Nie można zmienić, Dodaj lub jednak usuwać w zapytaniu LINQ, chyba że chcesz zatrzymać debugowanie, aby zastosować zmiany.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie SQL](http://msdn.microsoft.com/en-us/f27c17e6-1d90-49f2-9fc0-d02e6a27f109)   
 [Efekty uboczne i wyrażenia](http://msdn.microsoft.com/library/e1f8a6ea-9e19-481d-b6bd-df120ad3bf4e)   
 [Zarządzanie wyjątkami za pomocą debugera](../debugger/managing-exceptions-with-the-debugger.md)   
 [Wprowadzenie do zapytań LINQ (C#)](http://msdn.microsoft.com/library/37895c02-268c-41d5-be39-f7d936fa88a8)   
 [Wprowadzenie do LINQ w Visual Basic](http://msdn.microsoft.com/library/3047d86e-0d49-40e2-928b-dc02e46c7984)



