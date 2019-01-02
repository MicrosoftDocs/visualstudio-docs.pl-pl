---
title: CA1062 Waliduj argumenty metod publicznych
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 1b3b9461c72b21fcb2b77590786f47b90f5a98f5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53860757"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 Waliduj argumenty metod publicznych

|||
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna

Metoda widoczna na zewnątrz wyłuskań, jeden z argumentów odwołania bez sprawdzenia, czy ten argument jest `null` (`Nothing` w języku Visual Basic).

## <a name="rule-description"></a>Opis reguły

Wszystkie argumenty odwołania, które są przekazywane do widocznych zewnętrznie metod powinny zostać sprawdzone `null`. Jeśli to stosowne, throw <xref:System.ArgumentNullException> gdy argument jest `null`.

Jeśli metoda może być wywoływana z nieznanego zestawu, ponieważ jest on zadeklarowany jako publiczny lub chroniony, należy sprawdzić, czy wszystkie parametry metody. Jeśli metoda jest przeznaczone do można wywoływać tylko za pomocą znanych zestawów, należy wprowadzić metody wewnętrznej i zastosować <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut do zestawu, który zawiera metodę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy sprawdzić każdy argument odwołania, względem `null`.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Ostrzeżenie od tej reguły można pominąć, jeśli masz pewność, że parametr wyłuskiwany został zweryfikowany przez inne wywołanie metody w funkcji.

## <a name="example"></a>Przykład

Poniższy kod przedstawia metodę, która narusza regułę określającą, a metoda, która spełnia reguły.

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

Konstruktory kopiujące, służące do wypełniania pola lub właściwości, które są obiektami odwołania można również naruszyć regułę CA1062. Naruszenie występuje, ponieważ może być skopiowany obiekt, który jest przekazywany do konstruktora kopiującego `null` (`Nothing` w języku Visual Basic). Aby rozwiązać naruszenia, należy użyć metody statyczne (Shared w języku Visual Basic) na potrzeby sprawdzania kopiowanego obiektu nie jest null.

W następującym `Person` przykład klasy `other` obiekt, który jest przekazywany do `Person` może być Konstruktor kopiujący `null`.

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

W następujących zmian `Person` przykład `other` obiekt, który jest przekazywany do konstruktora kopiującego najpierw jest sprawdzany pod kątem wartości null w `PassThroughNonNull` metody.

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