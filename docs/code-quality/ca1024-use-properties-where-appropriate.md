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
ms.openlocfilehash: bfedb55c0dcdb1077faea03bca56488ab3da1525
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/17/2019
ms.locfileid: "65842467"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Używaj właściwości, o ile to możliwe

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna

Metoda ma nazwę, która rozpoczyna się od `Get`nie przyjmuje żadnych parametrów i zwraca wartość, która nie jest tablicą.

Domyślnie ta reguła przegląda tylko publiczne i chronione metody, ale jest to [konfigurowalne](#configurability).

## <a name="rule-description"></a>Opis reguły

W większości przypadków właściwości reprezentują danych i metod wykonywania akcji. Właściwości są dostępne, takich jak pola, co ułatwia ich używać. Metoda jest dobrym kandydatem do stają się właściwość, jeśli występuje jeden z tych warunków:

- Nie przyjmuje żadnych argumentów i zwraca informacje o stanie obiektu.

- Akceptuje pojedynczy argument można ustawić część stanu obiektu.

Właściwości, powinny zachowywać się tak, jakby są pola aplikacji; Jeśli metoda nie, nie należy zmienić właściwości. Metody są lepsze niż właściwości w następujących sytuacjach:

- Metoda wykonuje czasochłonna operacja. Metoda jest perceivably wolniej niż czas, który jest wymagany, aby ustawić lub pobrać wartości pola.

- Metoda przeprowadza konwersję. Uzyskiwanie dostępu do pola nie zwraca przekonwertowana wersja danych, które są przechowywane.

- Metoda Get ma dostrzegalnych efekt uboczny. Podczas pobierania wartości pola nie generuje żadnych efektów ubocznych.

- Kolejność wykonywania jest ważna. Ustawienie wartości pola nie zależą od wystąpienia innych operacji.

- Wywołanie metody dwa razy pod rząd tworzy różne wyniki.

- Metoda jest statyczna, ale zwraca obiekt, który może zostać zmieniona przez obiekt wywołujący. Podczas pobierania wartości pola nie zezwala na obiekt wywołujący, aby zmienić dane, które są przechowywane przez pole.

- Metoda zwraca tablicę.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zmienić metodę z właściwością.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Pomijaj ostrzeżeń dla tej reguły, jeśli metoda nie spełnia co najmniej jedną z wcześniej podanych kryteriów.

## <a name="configurability"></a>Konfigurowalne

Po uruchomieniu tej reguły z [analizatory FxCop analizujące kod](install-fxcop-analyzers.md) (a nie przy użyciu statycznej analizy kodu) części, które można skonfigurować Twojej bazy kodu do uruchomienia tej reguły na, oparte na ich dostępność. Na przykład aby określić, że zasady powinny być uruchamiane wyłącznie w odniesieniu do powierzchni interfejsu API niepublicznych, Dodaj następujące pary klucz wartość w pliku .editorconfig w projekcie:

```ini
dotnet_code_quality.ca1024.api_surface = private, internal
```

Można skonfigurować tę opcję tylko reguły dla wszystkich reguł lub dla wszystkich reguł w tej kategorii (projekt). Aby uzyskać więcej informacji, zobacz [analizatory FxCop analizujące kod z skonfigurować](configure-fxcop-analyzers.md).

## <a name="control-property-expansion-in-the-debugger"></a>Rozszerzanie właściwości kontrolki w debugerze

Jest jednym z powodów programistów należy unikać właściwość, ponieważ nie chcą debuger autoexpand go. Na przykład właściwość może obejmować przydzielanie dużego obiektu lub wywołanie metody P/Invoke, ale nie może rzeczywiście być wszelkie dostrzegalnych efekty uboczne.

Można zapobiec debugera przy użyciu właściwości autoexpanding, stosując <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Ten atrybut jest stosowany do właściwości wystąpienia można znaleźć w poniższym przykładzie.

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

Poniższy przykład zawiera kilka metod powinny być konwertowane do właściwości i kilku, należy nie, ponieważ mogą nie zachowywać się jak pola.

[!code-csharp[FxCop.Design.MethodsProperties#1](../code-quality/codesnippet/CSharp/ca1024-use-properties-where-appropriate_1.cs)]