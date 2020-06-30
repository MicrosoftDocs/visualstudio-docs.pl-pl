---
title: 'CA1062: Weryfikuj argumenty metod publicznych | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
- Validate arguments of public methods
helpviewer_keywords:
- CA1062
- ValidateArgumentsOfPublicMethods
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 377906675d70a712f8ca72b0b6e4d8a6864c1fbc
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85533240"
---
# <a name="ca1062-validate-arguments-of-public-methods"></a>CA1062: Waliduj argumenty metod publicznych
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|ValidateArgumentsOfPublicMethods|
|CheckId|CA1062|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Widoczna na zewnątrz Metoda odwołuje się do jednego z argumentów odwołania bez weryfikowania, czy ten argument jest `null` ( `Nothing` w Visual Basic).

## <a name="rule-description"></a>Opis reguły
 Wszystkie argumenty odwołania, które są przekazane do widocznych zewnętrznie metod, powinny być sprawdzane względem `null` . W razie potrzeby throw, <xref:System.ArgumentNullException> gdy argument ma wartość `null` .

 Jeśli metodę można wywołać z nieznanego zestawu, ponieważ jest ona zadeklarowana jako publiczna lub chroniona, należy zweryfikować wszystkie parametry metody. Jeśli metoda jest przeznaczona do wywoływania tylko przez znane zestawy, należy wprowadzić metodę wewnętrzną i zastosować <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut do zestawu, który zawiera metodę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, sprawdź poprawność każdego argumentu odwołania względem `null` .

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Możesz pominąć ostrzeżenie z tej reguły, jeśli masz pewność, że odwołanie do parametru zostało zweryfikowane przez inne wywołanie metody w funkcji.

## <a name="example"></a>Przykład
 Poniższy przykład pokazuje metodę, która narusza regułę i metodę, która spełnia kryteria.

 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#1)]
 [!code-csharp[FxCop.Design.ValidateArguments#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#1)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#1)]

## <a name="example"></a>Przykład
 W programie [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] Ta reguła nie wykrywa, że parametry są przesyłane do innej metody, która sprawdza poprawność.

 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/fxcop.design.validatearguments.copyctors.cs#2)]
 [!code-csharp[FxCop.Design.ValidateArguments#2](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/cs/FxCop.Design.ValidateArguments.cs#2)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.ValidateArguments/vb/FxCop.Design.ValidateArguments.vb#2)]

## <a name="example"></a>Przykład
 Konstruktory kopiujące wypełniające pola lub właściwości, które są obiektami odniesienia, mogą również naruszać regułę CA1062. Naruszenie występuje, ponieważ skopiowany obiekt, który jest przesyłany do konstruktora kopiującego, może być `null` ( `Nothing` w Visual Basic). Aby rozwiązać ten problem, należy użyć statycznej metody udostępnionej w Visual Basic), aby sprawdzić, czy skopiowany obiekt nie ma wartości null.

 W poniższym `Person` przykładzie klasy `other` obiekt, który jest przesyłany do `Person` konstruktora kopiującego może być `null` .

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
 W poniższym, zmienionym `Person` przykładzie, `other` obiekt, który jest przesyłany do konstruktora kopiującego, jest najpierw sprawdzany pod kątem wartości null w `PassThroughNonNull` metodzie.

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
