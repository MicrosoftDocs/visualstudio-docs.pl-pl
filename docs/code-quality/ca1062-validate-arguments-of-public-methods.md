---
title: 'CA1062: Waliduj argumenty metod publicznych'
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
ms.openlocfilehash: 3868061a01572d0b1adadec6619f88269d353dff
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922435"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Waliduj argumenty metod publicznych

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna

Widoczna na zewnątrz Metoda odwołuje się do jednego z argumentów odwołania bez weryfikowania, czy ten argument `null` jest`Nothing` (w Visual Basic).

## <a name="rule-description"></a>Opis reguły

Wszystkie argumenty odwołania, które są przekazane do widocznych zewnętrznie metod, powinny `null`być sprawdzane względem. W razie potrzeby throw <xref:System.ArgumentNullException> , gdy argument ma `null`wartość.

Jeśli metodę można wywołać z nieznanego zestawu, ponieważ jest ona zadeklarowana jako publiczna lub chroniona, należy zweryfikować wszystkie parametry metody. Jeśli metoda jest przeznaczona do wywoływania tylko przez znane zestawy, należy wprowadzić metodę wewnętrzną i zastosować <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut do zestawu, który zawiera metodę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej reguły, sprawdź poprawność każdego argumentu odwołania `null`względem.

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
                throw new ArgumentNullException("input");
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
                Throw New ArgumentNullException("input")
            End If

            If input.Length <> 0 Then
                Console.WriteLine(input)
            End If

        End Sub

    End Class

End Namespace
```

## <a name="example"></a>Przykład

Konstruktory kopiujące wypełniające pola lub właściwości, które są obiektami odniesienia, mogą również naruszać regułę CA1062. Naruszenie występuje, ponieważ skopiowany obiekt, który jest przesyłany do konstruktora kopiującego, `null` może`Nothing` być (w Visual Basic). Aby rozwiązać ten problem, należy użyć statycznej metody udostępnionej w Visual Basic), aby sprawdzić, czy skopiowany obiekt nie ma wartości null.

W poniższym `Person` przykładzie `other` klasy obiekt, `Person` który jest przesyłany do konstruktora kopiującego może być `null`.

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

W poniższym `Person` `PassThroughNonNull` , zmienionym przykładzie, obiekt,któryjestprzesyłanydokonstruktorakopiującego,jestnajpierwsprawdzanypodkątemwartościnullwmetodzie.`other`

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
            throw new ArgumentNullException("person");
        return person;
    }
}
```