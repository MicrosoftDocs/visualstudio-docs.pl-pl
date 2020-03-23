---
title: Testy jednostkowe metod ogólnych
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2158c889aefc85c908aa9ee42d45858fd11d557e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75590816"
---
# <a name="unit-tests-for-generic-methods"></a>Testy jednostkowe metod ogólnych

Można wygenerować testy jednostkowe dla metod ogólnych dokładnie tak, jak w przypadku innych metod. Poniższe sekcje zawierają informacje i przykłady tworzenia testów jednostkowych dla metod ogólnych.

## <a name="type-arguments-and-type-constraints"></a>Typ argumenty i ograniczenia typu

Gdy visual studio generuje test jednostkowy dla `MyList<T>`klasy ogólnej, takich jak , generuje dwie metody: pomocnika ogólnego i metody testowej. Jeśli `MyList<T>` ma jeden lub więcej ograniczeń typu, argument typu musi spełniać wszystkie ograniczenia typu. Aby upewnić się, że kod ogólny w ramach testu działa zgodnie z oczekiwaniami dla wszystkich dopuszczalnych danych wejściowych, metoda testowa wywołuje metodę pomocnika ogólnego ze wszystkimi ograniczeniami, które chcesz przetestować.

## <a name="examples"></a>Przykłady
Poniższe przykłady ilustrują testy jednostkowe dla leków generycznych:

- [Edytuj wygenerowany kod testowy](#EditingGeneratedTestCode). W tym przykładzie ma dwie sekcje, wygenerowany kod testowy i edytowany kod testu. Pokazuje, jak edytować nieprzetworzony kod testowy, który jest generowany z metody ogólnej do użytecznej metody testowej.

- [Użyj ograniczenia typu](#TypeConstraintNotSatisfied). W tym przykładzie pokazano test jednostkowy dla metody ogólnej, która używa ograniczenia typu. W tym przykładzie ograniczenie typu nie jest spełnione.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a>Przykład 1: Edytowanie wygenerowanego kodu testowego
Kod testowy w tej sekcji testuje metodę `SizeOfLinkedList()`kodu pod testem o nazwie . Ta metoda zwraca liczbę całkowitą, która określa liczbę węzłów na połączonej liście.

Pierwszy przykład kodu w sekcji Wygenerowany kod testowy pokazuje nieedytowany kod testowy, który został wygenerowany przez program Visual Studio Enterprise. Drugi przykład, w sekcji Edytowany kod testowy, pokazuje, jak można go przetestować działanie SizeOfLinkedList metody dla dwóch różnych typów danych `int` i `char`.

Ten kod ilustruje dwie metody:

- metodę pomocnika testu, `SizeOfLinkedListTestHelper<T>()`. Domyślnie metoda pomocnika testu ma "TestHelper" w nazwie.

- metodę badawczą, `SizeOfLinkedListTest()`. Każda metoda testowa jest oznaczona atrybutem TestMethod.

#### <a name="generated-test-code"></a>Wygenerowany kod testowy
Poniższy kod testu został `SizeOfLinkedList()` wygenerowany z metody. Ponieważ jest to test wygenerowany bez daty, musi zostać zmodyfikowany, aby poprawnie przetestować Metodę SizeOfLinkedList.

```csharp
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

W poprzednim kodzie parametr typu `GenericParameterHelper`ogólnego to . Podczas gdy można edytować go do dostarczania określonych typów danych, jak pokazano w poniższym przykładzie, można uruchomić test bez edycji tej instrukcji.

#### <a name="edited-test-code"></a>Edytowany kod testowy
W poniższym kodzie metoda testowa i metoda pomocnika testu zostały edytowane, aby pomyślnie `SizeOfLinkedList()`przetestować metodę kodu pod testem.

##### <a name="test-helper-method"></a>Metoda pomocnika testu
Metoda pomocnika testu wykonuje następujące kroki, które odpowiadają wierszom w kodzie oznaczonym krok od 1 do kroku 5.

1. Utwórz ogólną listę połączony.

2. Dołącz cztery węzły do połączonej listy. Typ danych zawartości tych węzłów jest nieznany.

3. Przypisz oczekiwany rozmiar połączonej `expected`listy do zmiennej .

4. Oblicz rzeczywisty rozmiar połączonej listy i przypisz ją do zmiennej `actual`.

5. `actual` Porównaj `expected` z w Assert instrukcji. Jeśli rzeczywista nie jest równa oczekiwanej, test zakończy się niepowodzeniem.

##### <a name="test-method"></a>Metoda testowa
Metoda testowa jest kompilowana do kodu, który jest wywoływany po uruchomieniu testu o nazwie SizeOfLinkedListTest. Wykonuje następujące kroki, które odpowiadają wierszom w kodzie oznaczonym krokiem 6 i 7.

1. Określ, `<int>` kiedy wywołasz metodę pomocnika testu, aby `integer` sprawdzić, czy test działa dla zmiennych.

2. Określ, `<char>` kiedy wywołasz metodę pomocnika testu, aby `char` sprawdzić, czy test działa dla zmiennych.

```csharp
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
> Za każdym razem, gdy test SizeOfLinkedListTest jest uruchamiany, jego TestHelper metoda jest wywoływana dwa razy. Instrukcja assert musi ocenić true za każdym razem, aby test przeszedł. Jeśli test zakończy się niepowodzeniem, może nie `<int>` być jasne, `<char>` czy wywołanie, które określone lub wywołanie, które określiło spowodowało jego niepowodzenie. Aby znaleźć odpowiedź, można sprawdzić stos wywołań lub można ustawić punkty przerwania w metodzie testowej, a następnie debugowania podczas uruchamiania testu. Aby uzyskać więcej informacji, zobacz [Jak: Debugowanie podczas uruchamiania testu w ASP.NET rozwiązanie](https://msdn.microsoft.com/Library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a>Przykład 2: Używanie ograniczenia typu
W tym przykładzie pokazano test jednostkowy dla metody rodzajowej, która używa ograniczenia typu, który nie jest spełniony. Pierwsza sekcja zawiera kod z projektu testowego kodu. Ograniczenie typu jest wyróżnione.

Druga sekcja zawiera kod z projektu testowego.

#### <a name="code-under-test-project"></a>Projekt podtestowany

```csharp
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

Podobnie jak w przypadku wszystkich nowo wygenerowanych testów jednostkowych, należy dodać nierozłączne Assert instrukcji do tego testu jednostkowego, aby zwrócić przydatne wyniki. Nie dodajesz ich do metody oznaczonej atrybutem TestMethod, ale do metody "TestHelper", która dla tego testu nosi nazwę `DataTestHelper<T>()`.

W tym przykładzie parametr `T` typu `where T : Employee`ogólnego ma ograniczenie . To ograniczenie nie jest spełnione w metodzie testowej. W związku `DataTest()` z tym metoda zawiera Assert instrukcji, która ostrzega do wymagań, `T`aby podać ograniczenie typu, który został umieszczony na . Komunikat tego Assert instrukcji brzmi następująco:`("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

Innymi słowy, po `DataTestHelper<T>()` wywołaniu metody z `DataTest()`metody testowej, należy `Employee` zdać parametr typu `Employee`lub klasę pochodną .

```csharp
using ClassLibrary2;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestProject1
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

- [Jednostka przetestować swój kod](../test/unit-test-your-code.md)
