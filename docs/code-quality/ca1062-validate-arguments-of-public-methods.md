---
title: CA1062 Walidacja argumentów metod publicznych
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 6019956d37d420b72275223148c2a3468a820884
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440707"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 Walidacja argumentów metod publicznych

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategoria|Microsoft. Design|
|Zmiana podziału|Nieprzerwanie|

## <a name="cause"></a>Przyczyna

Widoczna na zewnątrz Metoda odwołuje się do jednego z argumentów odwołania bez sprawdzania, czy ten argument jest `null` (`Nothing` w Visual Basic).

## <a name="rule-description"></a>Opis reguły

Wszystkie argumenty odwołania, które są przekazane do widocznych zewnętrznie metod, powinny być sprawdzane pod kątem `null`. W razie potrzeby Zgłoś <xref:System.ArgumentNullException>, gdy argument jest `null`.

Jeśli metodę można wywołać z nieznanego zestawu, ponieważ jest ona zadeklarowana jako publiczna lub chroniona, należy zweryfikować wszystkie parametry metody. Jeśli metoda jest przeznaczona do wywoływania tylko przez znane zestawy, należy wprowadzić metodę wewnętrzną i zastosować <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu do zestawu, który zawiera metodę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, sprawdź poprawność każdego argumentu odwołania dla `null`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Możesz pominąć ostrzeżenie z tej reguły, jeśli masz pewność, że odwołanie do parametru zostało zweryfikowane przez inne wywołanie metody w funkcji.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje metodę, która narusza regułę i metodę, która spełnia kryteria.

```csharp
using System;

namespace DesignLibrary
{
    public class Test
    {
        // This method violates the rule.
        public void DoNotValidate(string input)
        {
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }

        // This method satisfies the rule.
        public void Validate(string input)
        {
            if (input == null)
            {
                throw new ArgumentNullException(nameof(input));
            }
            if (input.Length != 0)
            {
                Console.WriteLine(input);
            }
        }
    }
}
```

```vb
Imports System

Namespace DesignLibrary

    Public Class Test

        ' This method violates the rule.
        Sub DoNotValidate(ByVal input As String)

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

        ' This method satisfies the rule.
        Sub Validate(ByVal input As String)

            If input Is Nothing Then
                Throw New ArgumentNullException(NameOf(input))
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Przykład

Konstruktory kopiujące wypełniające pola lub właściwości, które są obiektami odniesienia, mogą również naruszać regułę CA1062. Naruszenie występuje, ponieważ skopiowany obiekt, który jest przesyłany do konstruktora kopiującego, może być `null` (`Nothing` w Visual Basic). Aby rozwiązać ten problem, należy użyć statycznej metody udostępnionej w Visual Basic), aby sprawdzić, czy skopiowany obiekt nie ma wartości null.

W poniższym przykładzie klasy `Person` obiekt `other`, który jest przesyłany do konstruktora kopiującego `Person` może być `null`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor CA1062 fires because other is dereferenced
    // without being checked for null
    public Person(Person other)
        : this(other.Name, other.Age)
    {
    }
}
```

## <a name="example"></a>Przykład

W poniższym przykładzie zmienionym `Person`, obiekt `other`, który jest przesyłany do konstruktora kopiującego, jest najpierw sprawdzany pod kątem wartości null w metodzie `PassThroughNonNull`.

```csharp
public class Person
{
    public string Name { get; private set; }
    public int Age { get; private set; }

    public Person(string name, int age)
    {
        Name = name;
        Age = age;
    }

    // Copy constructor
    public Person(Person other)
        : this(PassThroughNonNull(other).Name,
          PassThroughNonNull(other).Age)
    {
    }

    // Null check method
    private static Person PassThroughNonNull(Person person)
    {
        if (person == null)
            throw new ArgumentNullException(nameof(person));
        return person;
    }
}
```
