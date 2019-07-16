---
title: 'CA1024: Korzystanie z właściwości, gdzie jest to odpowiednie | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 43487aa97afcd41a5375bacc26efba705cbaa76c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68144808"
---
# <a name="ca1024-use-properties-where-appropriate"></a>CA1024: Używaj właściwości, o ile to możliwe
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UsePropertiesWhereAppropriate|
|CheckId|CA1024|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona ma nazwę, która rozpoczyna się od `Get`nie przyjmuje żadnych parametrów i zwraca wartość, która nie jest tablicą.

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

## <a name="controlling-property-expansion-in-the-debugger"></a>Kontrolowanie właściwości rozszerzenia w debugerze
 Jednym z powodów programistów należy unikać właściwość jest, ponieważ nie chcesz debuger ma automatycznie rozwijać go. Na przykład właściwość może obejmować przydzielanie dużego obiektu lub wywołanie metody P/Invoke, ale nie może rzeczywiście być wszelkie dostrzegalnych efekty uboczne.

 Można uniemożliwić rozwijanie automatycznie przez debuger właściwości, stosując <xref:System.Diagnostics.DebuggerBrowsableAttribute?displayProperty=fullName>. Ten atrybut jest stosowany do właściwości wystąpienia można znaleźć w poniższym przykładzie.

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
 Poniższy przykład zawiera kilka metod powinny być konwertowane do właściwości i kilku, należy nie, ponieważ nie zachowywać się jak pola.

 [!code-csharp[FxCop.Design.MethodsProperties#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.MethodsProperties/cs/FxCop.Design.MethodsProperties.cs#1)]
