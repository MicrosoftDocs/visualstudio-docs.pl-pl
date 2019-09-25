---
title: 'CA1024: Używaj właściwości, o ile to możliwe'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- UsePropertiesWhereAppropriate
- CA1024
helpviewer_keywords:
- CA1024
- UsePropertiesWhereAppropriate
ms.assetid: 3a04f765-af7c-4872-87ad-9cc29e8e657f
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: d312618c80abb6a4ce6e1a2676903d85867f4989
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236158"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Używaj właściwości, o ile to możliwe

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategoria|Microsoft.Design|
|Zmiana podziału|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda ma nazwę rozpoczynającą się od `Get`, nie przyjmuje parametrów i zwraca wartość, która nie jest tablicą.

Domyślnie ta reguła sprawdza tylko metody publiczne i chronione, ale [można to skonfigurować](#configurability).

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

## <a name="configurability"></a>Określając

Jeśli uruchamiasz tę regułę z [analizatorów FxCop](install-fxcop-analyzers.md) (a nie ze starszą analizą), możesz skonfigurować, które części bazy kodu mają uruchamiać tę regułę, na podstawie ich dostępności. Na przykład aby określić, że reguła powinna być uruchamiana tylko względem powierzchni niepublicznego interfejsu API, Dodaj następującą parę klucz-wartość do pliku editorconfig w projekcie:

```ini
dotnet_code_quality.ca1024.api_surface = private, internal
```

Tę opcję można skonfigurować tylko dla tej reguły, dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [Konfigurowanie analizatorów FxCop](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Rozszerzanie właściwości kontrolki w debugerze

Jednym z powodów programiści nie należy używać właściwości, ponieważ nie chce, aby debuger miał Autorozszerzanie. Na przykład właściwość może polegać na przydzieleniu dużego obiektu lub wywołaniu P/Invoke, ale może nie mieć w rzeczywistości żadnych zauważalnych efektów ubocznych.

Można uniemożliwić debugerowi możliwość autorozszerzania właściwości poprzez zastosowanie <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Poniższy przykład pokazuje, że ten atrybut jest stosowany do właściwości wystąpienia.

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
}
```

## <a name="example"></a>Przykład

Poniższy przykład zawiera kilka metod, które należy przekonwertować na właściwości, a kilka, które nie powinny, ponieważ nie zachowują się one jak pola.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]