---
title: Testy jednostkowe metod ogólnych | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.assetid: ffc89814-a7df-44fc-aef5-dd3dfeb28a9b
caps.latest.revision: 49
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 1b419568490e41b135c2c7c801154f6550c546e9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771468"
---
# <a name="unit-tests-for-generic-methods"></a>Testy jednostkowe metod ogólnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Możesz wygenerować testy jednostkowe metod ogólnych dokładnie tak jak w przypadku innych metod, zgodnie z opisem w [jak: Tworzenie i uruchamianie testu jednostkowego](http://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48). Poniższe sekcje zawierają informacje i przykłady tworzenia testów jednostkowych dla metod ogólnych.  
  
## <a name="type-arguments-and-type-constraints"></a>Argumenty typu i ograniczenia typu  
 Gdy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje testu jednostkowego dla klasy ogólnej, takich jak `MyList<T>`, generuje on dwie metody: ogólny pomocnika i metody testowej. Jeśli `MyList<T>` ma co najmniej jedno ograniczenie typu, argument typu musi spełniać wszystkie ograniczenia typu. Aby upewnić się, że ogólny kodu w ramach testu działa zgodnie z oczekiwaniami wszystkie dozwolone danych wejściowych, testowana metoda wywołuje metodę pomocnika ogólnego z ograniczeniami, które mają zostać przetestowane.  
  
## <a name="examples"></a>Przykłady  
 Poniższe przykłady ilustrują, testy jednostkowe dla typów ogólnych:  
  
-   [Edytowanie wygenerowany kod testu](#EditingGeneratedTestCode). W tym przykładzie ma dwie sekcje wygenerowany kod testu i edytować kod testu. Widoczny jest sposób edytować kod testu raw, który jest generowany na podstawie metody ogólnej do metody testowej przydatne.  
  
-   [Za pomocą ograniczenia typu](#TypeConstraintNotSatisfied). Ten przykład przedstawia metody rodzajowej, który używa ograniczenia typu testu jednostkowego. W tym przykładzie ograniczenia typu nie został spełniony.  
  
###  <a name="EditingGeneratedTestCode"></a> Przykład 1: Edytowanie kodu wygenerowanego testu  
 Kod testu w tej sekcji testuje metodę kodu w ramach testu o nazwie `SizeOfLinkedList()`. Ta metoda zwraca całkowitą, która określa liczbę węzłów w połączonej listy.  
  
 Pierwszy przykład kodu w sekcji wygenerowanego kodu testu, zawiera kod testu bitu wygenerowane przez program Visual Studio Enterprise. Drugi przykład, w sekcji kodu testu edytowana, pokazuje, jak można wprowadzić testowania funkcjonowania metoda SizeOfLinkedList dla dwóch różnych typów danych, `int` i `char`.  
  
 Ten kod ilustruje dwóch metod:  
  
-   metodą pomocnika testu `SizeOfLinkedListTestHelper<T>()`. Domyślnie metody pomocnika testu ma "TestHelper" w nazwie.  
  
-   Metoda testowa, `SizeOfLinkedListTest()`. Każdej metody testowej jest oznaczona przez atrybut TestMethod.  
  
#### <a name="generated-test-code"></a>Kod wygenerowany Test  
 Poniższy kod testu został wygenerowany z `SizeOfLinkedList()` metody. Ponieważ jest to bitu wygenerowany test, muszą zostać zmodyfikowane, aby poprawnie metoda SizeOfLinkedList testu.  
  
```  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T); // TODO: Initialize to an appropriate value  
    MyLinkedList<T> target = new MyLinkedList<T>(val); // TODO: Initialize to an appropriate value  
    int expected = 0; // TODO: Initialize to an appropriate value  
    int actual;  
    actual = target.SizeOfLinkedList();  
    Assert.AreEqual(expected, actual);  
    Assert.Inconclusive("Verify the correctness of this test method.");  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()  
{  
   SizeOfLinkedListTestHelper<GenericParameterHelper>();  
}  
```  
  
 W poprzednim kodzie parametr typu ogólnego jest `GenericParameterHelper`. Należy go podać konkretnych typów danych, można edytować, jak pokazano w poniższym przykładzie, można uruchomić testu bez konieczności edytowania tej instrukcji.  
  
#### <a name="edited-test-code"></a>Edytować kod testu  
 W poniższym kodzie metody testowej, a także metoda pomocnika test był edytowany aby były one pomyślnie metody testowej kodu na obszarze badania `SizeOfLinkedList()`.  
  
##### <a name="test-helper-method"></a>Metoda pomocnika testu  
 Metoda pomocnika testu wykonuje następujące czynności, które odnoszą się do wierszy w kodzie etykietą kroki od 1 do 5.  
  
1.  Tworzenie połączonej listy ogólnej.  
  
2.  Dołącz czterech węzłów do połączonej listy. Typ danych w treści tych węzłów jest nieznany.  
  
3.  Przypisz oczekiwanego rozmiaru połączonej listy do zmiennej `expected`.  
  
4.  Obliczenia rzeczywisty rozmiar połączonej listy i przypisz ją do zmiennej `actual`.  
  
5.  Porównaj `actual` z `expected` w instrukcji asercji. Rzeczywiste nie jest równa oczekiwana, test kończy się niepowodzeniem.  
  
##### <a name="test-method"></a>Test — metoda  
 Metoda testowa jest kompilowane do kodu, która jest wywoływana po uruchomieniu testu o nazwie SizeOfLinkedListTest. Wykonuje następujące czynności, które odnoszą się do wierszy w kodzie etykietą kroki 6 i 7.  
  
1.  Określ `<int>` wywołanie metody pomocnika test, aby zweryfikować, że test działa w ramach `integer` zmiennych.  
  
2.  Określ `<char>` wywołanie metody pomocnika test, aby zweryfikować, że test działa w ramach `char` zmiennych.  
  
```  
  
public void SizeOfLinkedListTestHelper<T>()  
{  
    T val = default(T);   
    MyLinkedList<T> target = new MyLinkedList<T>(val); // step 1  
    for (int i = 0; i < 4; i++) // step 2  
    {  
        MyLinkedList<T> newNode = new MyLinkedList<T>(val);  
        target.Append(newNode);  
    }  
    int expected = 5; // step 3  
    int actual;  
    actual = target.SizeOfLinkedList(); // step 4  
    Assert.AreEqual(expected, actual); // step 5  
}  
  
[TestMethod()]  
public void SizeOfLinkedListTest()   
{  
    SizeOfLinkedListTestHelper<int>();  // step 6  
    SizeOfLinkedListTestHelper<char>(); // step 7  
}  
```  
  
> [!NOTE]
>  Przy każdym uruchomieniu testu SizeOfLinkedListTest jego TestHelper metoda jest wywoływana dwa razy. Instrukcję assert musi zwrócić wartość true, co czas test kończył się pomyślnie. Jeśli test zakończy się niepowodzeniem, może nie być jasne czy wywołania określona `<int>` lub wywołanie, które określono `<char>` spowodował, że jego nie powiedzie się. Aby znaleźć odpowiedzi, można analizować stos wywołań, lub można ustawić punkty przerwania w metodzie testowej, a następnie debugować podczas wykonywania testu. Aby uzyskać więcej informacji, zobacz [jak: Debugowanie podczas przeprowadzania testu w rozwiązaniu ASP.NET](http://msdn.microsoft.com/library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).  
  
###  <a name="TypeConstraintNotSatisfied"></a> Przykład 2: Za pomocą ograniczenia typu  
 Ten przykład przedstawia test jednostkowy metody rodzajowej, który używa ograniczenia typu, który nie jest spełniony. Pierwsza sekcja wyświetla kod z projektu kodu w ramach testu. Ograniczenie typu jest wyróżniona.  
  
 Druga sekcja wyświetla kod z projektu testów.  
  
#### <a name="code-under-test-project"></a>Code-Under-Test Project  
  
```  
using System;  
using System.Linq;  
using System.Collections.Generic;  
using System.Text;  
  
namespace ClassLibrary2  
{  
    public class Employee  
    {  
        public Employee(string s, int i)  
        {  
        }  
    }  
  
    public class GenericList<T> where T : Employee  
    {  
        private class Node  
        {  
            private T data;  
            public T Data  
            {  
                get { return data; }  
                set { data = value; }  
            }  
        }  
    }  
}  
```  
  
#### <a name="test-project"></a>Projekt testowy  
 Podobnie jak w przypadku wszystkich nowo wygenerowane testy jednostkowe, należy dodać-niejednoznaczny Assert-instrukcje do tego testu jednostkowego, aby zwrócić przydatnych wyników. Użytkownik nie należy dodawać ich metoda oznaczona przez atrybut TestMethod, ale metoda "TestHelper", który nosi nazwę dla tego testu `DataTestHelper<T>()`.  
  
 W tym przykładzie parametr typu ogólnego `T` ma ograniczenie `where T : Employee`. To ograniczenie nie został spełniony w metodzie testowej. W związku z tym `DataTest()` metoda zawiera instrukcję Assert, która ostrzega o konieczności podać ograniczenia typu, który został umieszczony na `T`. Komunikat ten instrukcję Assert odczytuje w następujący sposób: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`  
  
 Innymi słowy, gdy wywołujesz `DataTestHelper<T>()` metody z metody testowej `DataTest()`, należy przekazać do parametru typu `Employee` lub klasą pochodną `Employee`.  
  
 `using ClassLibrary2;`  
  
 `using Microsoft.VisualStudio.TestTools.UnitTesting;`  
  
 `namespace TestProject1`  
  
```  
{  
    [TestClass()]  
    public class GenericList_NodeTest  
    {  
  
        public void DataTestHelper<T>()  
            where T : Employee  
        {  
            GenericList_Shadow<T>.Node target = new GenericList_Shadow<T>.Node(); // TODO: Initialize to an appropriate value  
            T expected = default(T); // TODO: Initialize to an appropriate value  
            T actual;  
            target.Data = expected;  
            actual = target.Data;  
            Assert.AreEqual(expected, actual);  
            Assert.Inconclusive("Verify the correctness of this test method.");  
        }  
  
        [TestMethod()]  
        public void DataTest()  
        {  
            Assert.Inconclusive("No appropriate type parameter is found to satisfies the type constraint(s) of T. " +  
            "Please call DataTestHelper<T>() with appropriate type parameters.");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Anatomia testu jednostkowego](http://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144)   
 [Testowanie jednostek kodu](../test/unit-test-your-code.md)
