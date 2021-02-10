---
title: Testy jednostkowe metod ogólnych
description: Dowiedz się, jak generować testy jednostkowe dla metod ogólnych przy użyciu tych informacji i przykładów tworzenia testów jednostkowych dla metod ogólnych.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 16d1348d74bb459a73dd4a5a4f8de21e367865c1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962499"
---
# <a name="unit-tests-for-generic-methods"></a>Testy jednostkowe metod ogólnych

Można generować testy jednostkowe dla metod ogólnych dokładnie tak samo jak w przypadku innych metod. Poniższe sekcje zawierają informacje o i przykłady tworzenia testów jednostkowych dla metod ogólnych.

## <a name="type-arguments-and-type-constraints"></a>Argumenty typu i ograniczenia typu

Gdy program Visual Studio generuje test jednostkowy dla klasy generycznej, na przykład `MyList<T>` generuje dwie metody: pomocnik generyczny i metodę testową. Jeśli `MyList<T>` ma co najmniej jedno ograniczenie typu, argument typu musi spełniać wszystkie ograniczenia typu. Aby upewnić się, że kod generyczny w teście działa zgodnie z oczekiwaniami dla wszystkich dopuszczalnych danych wejściowych, metoda testowa wywołuje ogólną metodę pomocnika ze wszystkimi ograniczeniami, które mają zostać przetestowane.

## <a name="examples"></a>Przykłady
Poniższe przykłady ilustrują testy jednostkowe dla typów ogólnych:

- [Edytuj wygenerowany kod testu](#EditingGeneratedTestCode). Ten przykład ma dwie sekcje, Wygenerowano kod testowy i edytowany kod testowy. Pokazuje, jak edytować nieprzetworzony kod testu, który jest generowany z metody ogólnej do przydatnej metody testowej.

- [Użyj ograniczenia typu](#TypeConstraintNotSatisfied). Ten przykład pokazuje test jednostkowy dla metody ogólnej, która używa ograniczenia typu. W tym przykładzie ograniczenie typu nie jest spełnione.

### <a name="example-1-editing-generated-test-code"></a><a name="EditingGeneratedTestCode"></a> Przykład 1: edytowanie wygenerowanego kodu testowego
Kod testu w tej sekcji testuje metodę testową w kodzie pod nazwą `SizeOfLinkedList()` . Ta metoda zwraca liczbę całkowitą, która określa liczba węzłów na liście połączonej.

Pierwszy przykład kodu, w sekcji wygenerowała kod testu, pokazuje Nieedytowany kod testu, ponieważ został wygenerowany przez Visual Studio Enterprise. Drugi przykład w sekcji edytowanego kodu testowego pokazuje, jak można przetestować działanie metody SizeOfLinkedList dla dwóch różnych typów danych `int` i `char` .

Ten kod ilustruje dwie metody:

- metoda pomocnika testowego `SizeOfLinkedListTestHelper<T>()` . Domyślnie metoda pomocnika testowego ma nazwę "TestHelper".

- Metoda testowa, `SizeOfLinkedListTest()` . Każda metoda testowa jest oznaczona przy użyciu atrybutu TestMethod.

#### <a name="generated-test-code"></a>Wygenerowany kod testu
Następujący kod testu został wygenerowany z `SizeOfLinkedList()` metody. Ponieważ jest to nieedytowane wygenerowane testy, należy zmodyfikować, aby prawidłowo przetestować metodę SizeOfLinkedList.

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

W poprzednim kodzie parametr typu ogólnego to `GenericParameterHelper` . Można edytować go w celu dostarczania określonych typów danych, jak pokazano w poniższym przykładzie, można uruchomić test bez edytowania tej instrukcji.

#### <a name="edited-test-code"></a>Edytowano kod testu
W poniższym kodzie metoda testowa i metoda pomocnika testu zostały edytowane w celu pomyślnego przetestowania metody kodu w teście `SizeOfLinkedList()` .

##### <a name="test-helper-method"></a>Metoda pomocnika testu
Metoda pomocnika testu wykonuje następujące czynności, które odnoszą się do wierszy w kodzie oznaczonym krok 1 do kroku 5.

1. Utwórz połączoną listę ogólną.

2. Dołącz cztery węzły do listy połączonej. Typ danych zawartości tych węzłów jest nieznany.

3. Przypisz do zmiennej oczekiwany rozmiar połączonej listy `expected` .

4. Oblicza rzeczywisty rozmiar połączonej listy i przypisz ją do zmiennej `actual` .

5. Porównaj `actual` z elementem `expected` w instrukcji Assert. Jeśli wartość rzeczywista nie jest równa oczekiwanego, test zakończy się niepowodzeniem.

##### <a name="test-method"></a>Metoda testowa
Metoda testowa jest kompilowana do kodu, który jest wywoływany po uruchomieniu testu o nazwie SizeOfLinkedListTest. Wykonuje następujące czynności, które odnoszą się do wierszy w kodzie oznaczonych krok 6 i 7.

1. Określ `<int>` , kiedy wywołujesz metodę pomocnika testowego, aby sprawdzić, czy test działa w przypadku `integer` zmiennych.

2. Określ `<char>` , kiedy wywołujesz metodę pomocnika testowego, aby sprawdzić, czy test działa w przypadku `char` zmiennych.

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
    SizeOfLinkedListTestHelper<int>();  // step 6
    SizeOfLinkedListTestHelper<char>(); // step 7
}
```

> [!NOTE]
> Po każdym uruchomieniu testu SizeOfLinkedListTest jego Metoda TestHelper jest wywoływana dwa razy. Instrukcja Assert musi być szacowana na wartość true za każdym razem, gdy test zostanie przekazany. Jeśli test nie powiedzie się, może nie być jasne, czy wywołanie określone `<int>` lub wywołanie, które zostało określone, `<char>` spowodowało niepowodzenie. Aby znaleźć odpowiedź, można sprawdzić stos wywołań lub ustawić punkty przerwania w metodzie testowej, a następnie debugować podczas wykonywania testu. Aby uzyskać więcej informacji, zobacz [How to: Debug in Test in the ASP.NET Solution](/previous-versions/ms243172(v=vs.140)).

### <a name="example-2-using-a-type-constraint"></a><a name="TypeConstraintNotSatisfied"></a> Przykład 2: użycie ograniczenia typu
Ten przykład pokazuje test jednostkowy dla metody ogólnej, która używa ograniczenia typu, który nie jest spełniony. W pierwszej sekcji jest wyświetlany kod z projektu kodu testowego. Zostanie wyróżnione ograniczenie typu.

Druga sekcja zawiera kod z projektu testowego.

#### <a name="code-under-test-project"></a>Projekt w środowisku testowym

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

Podobnie jak w przypadku wszystkich nowo wygenerowanych testów jednostkowych, należy dodać nieniejednoznaczne instrukcje Assert do tego testu jednostkowego, aby zwracały przydatne wyniki. Nie należy dodawać ich do metody oznaczonej atrybutem TestMethod, ale do metody "TestHelper", która dla tego testu jest nazywana `DataTestHelper<T>()` .

W tym przykładzie parametr typu generycznego `T` ma ograniczenie `where T : Employee` . To ograniczenie nie jest spełnione w metodzie testowej. W związku z tym `DataTest()` Metoda zawiera instrukcję Assert, która powiadamia użytkownika o wymaganiu podania ograniczenia typu, które zostało umieszczone `T` . Komunikat tej instrukcji Assert jest odczytywany w następujący sposób: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

Innymi słowy, gdy wywoływana jest `DataTestHelper<T>()` Metoda z metody testowej, należy `DataTest()` przekazać parametr typu `Employee` lub klasy pochodnej z `Employee` .

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

- [Testowanie jednostkowe kodu](../test/unit-test-your-code.md)