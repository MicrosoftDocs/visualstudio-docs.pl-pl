---
title: Testy jednostkowe dla metod ogólnych | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- generics, and unit tests
- unit tests, and generics
ms.assetid: ffc89814-a7df-44fc-aef5-dd3dfeb28a9b
caps.latest.revision: 49
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2619e975dbfd22d96db2cc382a7cebbf04a05223
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657277"
---
# <a name="unit-tests-for-generic-methods"></a>Testy jednostkowe metod ogólnych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Można generować testy jednostkowe dla metod ogólnych dokładnie tak samo jak w przypadku innych metod, zgodnie z opisem w [instrukcje: Tworzenie i uruchamianie testu jednostkowego](https://msdn.microsoft.com/5e0f43cf-5e51-48e2-9c98-0eb9324bdc48). Poniższe sekcje zawierają informacje o i przykłady tworzenia testów jednostkowych dla metod ogólnych.

## <a name="type-arguments-and-type-constraints"></a>Argumenty typu i ograniczenia typu
 Gdy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] generuje test jednostkowy dla klasy generycznej, takiej jak `MyList<T>`, generuje dwie metody: pomocnik generyczny i metodę testową. Jeśli `MyList<T>` ma co najmniej jedno ograniczenie typu, argument typu musi spełniać wszystkie ograniczenia typu. Aby upewnić się, że kod generyczny w teście działa zgodnie z oczekiwaniami dla wszystkich dopuszczalnych danych wejściowych, metoda testowa wywołuje ogólną metodę pomocnika ze wszystkimi ograniczeniami, które mają zostać przetestowane.

## <a name="examples"></a>Przykłady
 Poniższe przykłady ilustrują testy jednostkowe dla typów ogólnych:

- [Edytowanie wygenerowanego kodu testu](#EditingGeneratedTestCode). Ten przykład ma dwie sekcje, Wygenerowano kod testowy i edytowany kod testowy. Pokazuje, jak edytować nieprzetworzony kod testu, który jest generowany z metody ogólnej do przydatnej metody testowej.

- [Przy użyciu ograniczenia typu](#TypeConstraintNotSatisfied). Ten przykład pokazuje test jednostkowy dla metody ogólnej, która używa ograniczenia typu. W tym przykładzie ograniczenie typu nie jest spełnione.

### <a name="EditingGeneratedTestCode"></a>Przykład 1: edytowanie wygenerowanego kodu testowego
 Kod testu w tej sekcji testuje metodę testową w kodzie pod nazwą `SizeOfLinkedList()`. Ta metoda zwraca liczbę całkowitą, która określa liczba węzłów na liście połączonej.

 Pierwszy przykład kodu, w sekcji wygenerowała kod testu, pokazuje Nieedytowany kod testu, ponieważ został wygenerowany przez Visual Studio Enterprise. Drugi przykład w sekcji edytowanego kodu testowego pokazuje, jak można przetestować działanie metody SizeOfLinkedList dla dwóch różnych typów danych, `int` i `char`.

 Ten kod ilustruje dwie metody:

- metoda pomocnika testowego, `SizeOfLinkedListTestHelper<T>()`. Domyślnie metoda pomocnika testowego ma nazwę "TestHelper".

- Metoda testowa, `SizeOfLinkedListTest()`. Każda metoda testowa jest oznaczona przy użyciu atrybutu TestMethod.

#### <a name="generated-test-code"></a>Wygenerowany kod testu
 Następujący kod testowy został wygenerowany z metody `SizeOfLinkedList()`. Ponieważ jest to nieedytowane wygenerowane testy, należy zmodyfikować, aby prawidłowo przetestować metodę SizeOfLinkedList.

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

 W poprzednim kodzie parametr typu generycznego jest `GenericParameterHelper`. Można edytować go w celu dostarczania określonych typów danych, jak pokazano w poniższym przykładzie, można uruchomić test bez edytowania tej instrukcji.

#### <a name="edited-test-code"></a>Edytowano kod testu
 W poniższym kodzie metoda testowa i metoda pomocnika testu zostały edytowane w celu pomyślnego przetestowania metody kodu pod `SizeOfLinkedList()`.

##### <a name="test-helper-method"></a>Metoda pomocnika testu
 Metoda pomocnika testu wykonuje następujące czynności, które odnoszą się do wierszy w kodzie oznaczonym krok 1 do kroku 5.

1. Utwórz połączoną listę ogólną.

2. Dołącz cztery węzły do listy połączonej. Typ danych zawartości tych węzłów jest nieznany.

3. Przypisz oczekiwany rozmiar listy połączonej do zmiennej `expected`.

4. Oblicza rzeczywisty rozmiar połączonej listy i przypisz ją do zmiennej `actual`.

5. Porównaj `actual` z `expected` w instrukcji Assert. Jeśli wartość rzeczywista nie jest równa oczekiwanego, test zakończy się niepowodzeniem.

##### <a name="test-method"></a>Metoda testowa
 Metoda testowa jest kompilowana do kodu, który jest wywoływany po uruchomieniu testu o nazwie SizeOfLinkedListTest. Wykonuje następujące czynności, które odnoszą się do wierszy w kodzie oznaczonych krok 6 i 7.

1. Określ `<int>`, gdy wywołasz metodę pomocnika testowego, aby sprawdzić, czy test działa dla zmiennych `integer`.

2. Określ `<char>`, gdy wywołasz metodę pomocnika testowego, aby sprawdzić, czy test działa dla zmiennych `char`.

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
> Po każdym uruchomieniu testu SizeOfLinkedListTest jego Metoda TestHelper jest wywoływana dwa razy. Instrukcja Assert musi być szacowana na wartość true za każdym razem, gdy test zostanie przekazany. Jeśli test nie powiedzie się, może to nie być jasne, czy wywołanie określone `<int>` lub wywołanie określone `<char>` spowodowało niepowodzenie. Aby znaleźć odpowiedź, można sprawdzić stos wywołań lub ustawić punkty przerwania w metodzie testowej, a następnie debugować podczas wykonywania testu. Aby uzyskać więcej informacji, zobacz [How to: Debug in Test in the ASP.NET Solution](https://msdn.microsoft.com/library/de4d7aa1-4a1e-467e-a19b-4a85ec245b8b).

### <a name="TypeConstraintNotSatisfied"></a>Przykład 2: użycie ograniczenia typu
 Ten przykład pokazuje test jednostkowy dla metody ogólnej, która używa ograniczenia typu, który nie jest spełniony. W pierwszej sekcji jest wyświetlany kod z projektu kodu testowego. Zostanie wyróżnione ograniczenie typu.

 Druga sekcja zawiera kod z projektu testowego.

#### <a name="code-under-test-project"></a>Projekt w środowisku testowym

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
 Podobnie jak w przypadku wszystkich nowo wygenerowanych testów jednostkowych, należy dodać nieniejednoznaczne instrukcje Assert do tego testu jednostkowego, aby zwracały przydatne wyniki. Nie należy dodawać ich do metody oznaczonej atrybutem TestMethod, ale do metody "TestHelper", która dla tego testu nosi nazwę `DataTestHelper<T>()`.

 W tym przykładzie parametr typu ogólnego `T` ma `where T : Employee` ograniczenia. To ograniczenie nie jest spełnione w metodzie testowej. W związku z tym Metoda `DataTest()` zawiera instrukcję Assert, która powiadamia użytkownika o wymaganiu podania ograniczenia typu, które zostało umieszczone w `T`. Komunikat tej instrukcji Assert jest odczytywany w następujący sposób: `("No appropriate type parameter is found to satisfies the type constraint(s) of T. " + "Please call DataTestHelper<T>() with appropriate type parameters.");`

 Innymi słowy, gdy wywoływana jest metoda `DataTestHelper<T>()` z metody testowej, `DataTest()`, należy przekazać parametr typu `Employee` lub klasy pochodnej przez `Employee`.

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
 [Anatomia testu jednostki testów jednostkowych](https://msdn.microsoft.com/a03d1ee7-9999-4e7c-85df-7d9073976144) [](../test/unit-test-your-code.md)
