---
title: CA1062 Waliduj argumenty metod publicznych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology: vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d8c3e14318f1c483011bc1134fbcd22963df8a42
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53913209"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062 Waliduj argumenty metod publicznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Przykład
 W [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)], ta zasada wykrywa, czy parametry są przekazywana do innej metody, która wykonuje sprawdzanie poprawności.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Przykład
 Konstruktory kopiujące, służące do wypełniania pola lub właściwości, które są obiektami odwołania można również naruszyć regułę CA1062. Naruszenie występuje, ponieważ może być skopiowany obiekt, który jest przekazywany do konstruktora kopiującego `null` (`Nothing` w języku Visual Basic). Aby rozwiązać naruszenia, należy użyć metody statyczne (Shared w języku Visual Basic) na potrzeby sprawdzania kopiowanego obiektu nie jest null.

 W następującym `Person` przykład klasy `other` obiekt, który jest przekazywany do `Person` może być Konstruktor kopiujący `null`.

```

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

```
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
