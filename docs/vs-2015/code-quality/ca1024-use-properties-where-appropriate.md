---
title: 'CA1024: Użyj właściwości, jeśli jest to odpowiednie | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b190e007cfdb016e54148cf0295c68baf68c5033
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661965"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Używaj właściwości wszędzie, gdzie jest to odpowiednie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona ma nazwę rozpoczynającą się od `Get`, nie przyjmuje parametrów i zwraca wartość, która nie jest tablicą.

## <a name="rule-description"></a>Opis reguły
 W większości przypadków właściwości reprezentują dane i metody wykonują działania. Właściwości są dostępne, podobnie jak pola, które ułatwiają korzystanie z nich. Metoda jest dobrym kandydatem, aby stał się właściwością w przypadku obecności jednego z następujących warunków:

- Nie przyjmuje argumentów ani nie zwraca informacji o stanie obiektu.

- Akceptuje pojedynczy argument, aby ustawić część stanu obiektu.

  Właściwości powinny zachowywać się tak, jakby były polami; Jeśli metoda nie może, nie powinna być zmieniana na właściwość. Metody są lepsze niż właściwości w następujących sytuacjach:

- Metoda wykonuje czasochłonną operację. Metoda jest postrzegana wolniej niż czas wymagany do ustawienia lub pobrania wartości pola.

- Metoda wykonuje konwersję. Uzyskanie dostępu do pola nie zwraca skonwertowanej wersji przechowywanych danych.

- Metoda get ma zauważalny efekt uboczny. Pobieranie wartości pola nie powoduje wygenerowania żadnych efektów ubocznych.

- Kolejność wykonywania jest ważna. Ustawienie wartości pola nie polega na wystąpieniu innych operacji.

- Wywołanie metody dwa razy w wyniku sukcesu tworzy różne wyniki.

- Metoda jest statyczna, ale zwraca obiekt, który może zostać zmieniony przez wywołującego. Pobieranie wartości pola nie zezwala obiektowi wywołującemu na zmianę danych przechowywanych w polu.

- Metoda zwraca tablicę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, Zmień metodę na właściwość.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Pomiń ostrzeżenie z tej reguły, jeśli metoda spełnia co najmniej jedno z wcześniej wymienionych kryteriów.

## <a name="controlling-property-expansion-in-the-debugger"></a>Kontrolowanie rozszerzania właściwości w debugerze
 Jednym z powodów programiści nie należy używać właściwości, ponieważ nie chce, aby debuger miał Autorozszerzanie. Na przykład właściwość może polegać na przydzieleniu dużego obiektu lub wywołaniu P/Invoke, ale może nie mieć w rzeczywistości żadnych zauważalnych efektów ubocznych.

 Można uniemożliwić debugerowi możliwość autorozszerzania właściwości, stosując <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Poniższy przykład pokazuje, że ten atrybut jest stosowany do właściwości wystąpienia.

```vb
Imports System
Imports System.Diagnostics

Namespace Microsoft.Samples

    Public Class TestClass

        ' [...]

        <DebuggerBrowsable(DebuggerBrowsableState.Never)> _
        Public ReadOnly Property LargeObject() As LargeObject
            Get
                ' Allocate large object
                ' [...]
            End Get
        End Property

    End Class

End Namespace
```

```csharp

      using System;
using System.Diagnostics;

namespace Microsoft.Samples
{
    publicclass TestClass
    {
        // [...]

        [DebuggerBrowsable(DebuggerBrowsableState.Never)]
        public LargeObject LargeObject
        {
            get
            {
                // Allocate large object
                // [...]

        }
    }
}
```

## <a name="example"></a>Przykład
 Poniższy przykład zawiera kilka metod, które należy przekonwertować na właściwości, i kilka, które nie powinny, ponieważ nie zachowują się one jak pola.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
