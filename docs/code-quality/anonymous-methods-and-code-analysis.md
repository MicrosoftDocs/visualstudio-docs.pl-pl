---
title: Ostrzeżenia analizy kodu dla metody anonimowej
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
dev_langs:
- CSharp
- VB
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a10c5baaed3a98e44d581b6ddb8d6e3a1883d079
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55940493"
---
# <a name="anonymous-methods-and-code-analysis"></a>Metody anonimowe i analiza kodu

*Metody anonimowej* to metoda, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametr delegata. W tym artykule wyjaśniono, jak analiza kodu obsługuje ostrzeżenia i metryki dla metod anonimowych.

## <a name="anonymous-methods-declared-in-a-member"></a>Metody anonimowe zadeklarowane w składowej

Ostrzeżenia i metryki dla metody anonimowej, która jest zadeklarowana w elemencie członkowskim, na przykład metodę lub metodę dostępu, są skojarzone z elementu członkowskiego, która deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.

Na przykład w następującej klasy wszelkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod** powinien być wywoływany przed **metoda1** i nie **Method2**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass
    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End Sub
    Sub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    void Method1()
    {
        Delegate anonymousMethod = delegate()
        {
          Console.WriteLine("");
        }
        Method2(anonymousMethod);
    }

    void Method2(Delegate anonymousMethod)
    {
        anonymousMethod();
    }
}
```

## <a name="inline-anonymous-methods"></a>Wbudowane metody anonimowe

Ostrzeżenia i metryki dla metody anonimowej, która jest zadeklarowana jako wbudowany przypisanie do pola są skojarzone z konstruktora. Jeśli pole jest zadeklarowany jako `static` (`Shared` w języku Visual Basic), ostrzeżenia i metryki są skojarzone z konstruktora klasy. W przeciwnym razie są one skojarzone z konstruktora wystąpienia.

Na przykład w następującej klasy wszelkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod1** zostaną wywołane względem niejawnie wygenerowany domyślny konstruktor obiektu **klasy**. Ostrzeżenia, które znajdują się w **anonymousMethod2** zostaną zastosowane względem konstruktora niejawnie wygenerowanej klasy.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass
    Dim anonymousMethod1 As ADelegate = Function(ByVal value As Integer) value > 5
    Shared anonymousMethod2 As ADelegate = Function(ByVal value As Integer) value > 5

    Sub Method1()
        anonymousMethod1(10)
        anonymousMethod2(10)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod1 = delegate()
    {
       Console.WriteLine("");
    }

    static Delegate anonymousMethod2 = delegate()
    {
       Console.WriteLine("");
    }

    void Method()
    {
       anonymousMethod1();
       anonymousMethod2();
    }
}
```

Klasa może zawierać metodę anonimową wbudowane, która przypisuje wartość do pola, które ma wiele konstruktorów. W tym przypadku ostrzeżeń i metryki są skojarzone z wszystkie konstruktory, chyba że ten konstruktor jest dołączony do innego konstruktora w tej samej klasie.

Na przykład w następującej klasy wszelkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod** powinien być wywoływany przed **Class(int)** i **Class(string)**, ale nie względem **Class()**.

```vb
Delegate Function ADelegate(ByVal value As Integer) As Boolean

Class AClass

    Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5

    SubNew()
        New(CStr(Nothing))
    End Sub

    Sub New(ByVal a As Integer)
    End Sub

    Sub New(ByVal a As String)
    End Sub
End Class
```

```csharp
delegate void Delegate();

class Class
{
    Delegate anonymousMethod = delegate()
    {
       Console.WriteLine("");
    }

    Class() : this((string)null)
    {
    }

    Class(int a)
    {
    }

    Class(string a)
    {
    }
}
```

Ostrzeżenia są wywoływane z konstruktorów, ponieważ kompilator generuje metodę unikatowy dla każdego Konstruktor, który nie jest powiązany do innego konstruktora. Ze względu na to zachowanie, naruszenia występuje w **anonymousMethod** można pominąć oddzielnie. Oznacza to również, jeśli nowy konstruktor jest wprowadzona, ostrzeżeń, które wcześniej zostały pominięte przed **Class(int)** i **Class(string)** musi również pomijane dla nowego konstruktora.

Można obejść ten problem w jeden z dwóch sposobów:

- Zadeklaruj **anonymousMethod** w Konstruktorze wspólne, wszystkie konstruktory łańcucha.
- Zadeklaruj **anonymousMethod** w metodzie inicjalizacji, która jest wywoływana przez wszystkie konstruktory.

## <a name="see-also"></a>Zobacz także

- [Analiza jakości zarządzanego kodu](../code-quality/code-analysis-for-managed-code-overview.md)