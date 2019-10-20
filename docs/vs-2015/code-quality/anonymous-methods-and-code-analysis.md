---
title: Metody anonimowe i analiza kodu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- methods, anonymous
- code analysis, anonymous methods
- anonymous methods, code analysis
ms.assetid: bf0a1a9b-b954-4d46-9c0b-cee65330ad00
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49da7d5e7f6a7731a708accb3d52fb6383ff1017
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652224"
---
# <a name="anonymous-methods-and-code-analysis"></a>Metody anonimowe i analiza kodu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

*Metoda anonimowa* to metoda, która nie ma nazwy. Metody anonimowe są najczęściej używane do przekazywania bloku kodu jako parametru delegata.

 W tym temacie wyjaśniono, jak analiza kodu obsługuje ostrzeżenia i metryki, które są skojarzone z anonimowymi metodami.

## <a name="anonymous-methods-declared-in-a-member"></a>Metody anonimowe zadeklarowane w składowej
 Ostrzeżenia i metryki metody anonimowej, która jest zadeklarowana w elemencie członkowskim, takie jak metoda lub akcesor, są skojarzone z elementem członkowskim, który deklaruje metodę. Nie są one skojarzone z elementem członkowskim, który wywołuje metodę.

 Na przykład w poniższej klasie wszystkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod** powinny być wywoływane względem **Metoda1** , a nie **Method2**.

```vb

      Delegate Function ADelegate(ByVal value As Integer) As Boolean
Class AClass

    Sub Method1()
        Dim anonymousMethod As ADelegate = Function(ByVal value As Integer) value > 5
        Method2(anonymousMethod)
    End SubSub Method2(ByVal anonymousMethod As ADelegate)
        anonymousMethod(10)
    End SubEnd Class
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
 Ostrzeżenia i metryki metody anonimowej zadeklarowanej jako przypisanie wbudowane do pola są skojarzone z konstruktorem. Jeśli pole jest zadeklarowane jako `static` (`Shared` w [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), ostrzeżenia i metryki są skojarzone z konstruktorem klasy; w przeciwnym razie są one skojarzone z konstruktorem wystąpień.

 Na przykład w poniższej klasie wszystkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod1** , zostaną wywołane względem niejawnie wygenerowanego domyślnego konstruktora **klasy**. Natomiast te, które znajdują się w **anonymousMethod2** , zostaną zastosowane do niejawnie wygenerowanego konstruktora klasy.

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass
Dim anonymousMethod1 As ADelegate = Function(ByVal value As    Integer) value > 5
Shared anonymousMethod2 As ADelegate = Function(ByVal value As     Integer) value > 5

Sub Method1()
    anonymousMethod1(10)
    anonymousMethod2(10)
End SubEnd Class
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

 Klasa może zawierać wbudowaną metodę anonimową, która przypisuje wartość do pola, które ma wiele konstruktorów. W takim przypadku ostrzeżenia i metryki są kojarzone ze wszystkimi konstruktorami, chyba że ten Konstruktor łańcucha do innego konstruktora w tej samej klasie.

 Na przykład w poniższej klasie wszystkie ostrzeżenia, które znajdują się w deklaracji **anonymousMethod** powinny być wywoływane względem **klasy (int)** i **klasy (String)** , ale nie do **klasy ()** .

```vb

  Delegate Function ADelegate(ByVal value As Integer) As BooleanClass AClass

Dim anonymousMethod As ADelegate = Function(ByVal value As Integer)
value > 5

SubNew()
    New(CStr(Nothing))
End SubSub New(ByVal a As Integer)
End SubSub New(ByVal a As String)
End SubEnd Class
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

 Chociaż może to wydawać się nieoczekiwane, dzieje się tak, ponieważ kompilator wyprowadza unikatową metodę dla każdego konstruktora, który nie jest powiązany z innym konstruktorem. Ze względu na to zachowanie wszystkie naruszenia, które występują w **anonymousMethod** , muszą być pomijane osobno. Oznacza to również, że w przypadku wprowadzenia nowego konstruktora ostrzeżenia, które były wcześniej pomijane względem **klasy (int)** i **klasy (String)** , również muszą być pomijane dla nowego konstruktora.

 Ten problem można obejść na jeden z dwóch sposobów. Można zadeklarować **anonymousMethod** w typowym konstruktorze, który cały łańcuch konstruktorów. Można też zadeklarować ją w metodzie inicjacji, która jest wywoływana przez wszystkie konstruktory.

## <a name="see-also"></a>Zobacz też
 [Analiza jakości zarządzanego kodu](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)
