---
title: 'CA2202: Nie likwiduj obiektów wielokrotnie'
ms.date: 07/16/2019
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b5fb70baa17bee484dc3c31d7c6ce9b302019403
ms.sourcegitcommit: 2bbcba305fd0f8800fd3d9aa16f7647ee27f3a4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2019
ms.locfileid: "68300601"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Nie likwiduj obiektów wielokrotnie

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna

Implementacja metody zawiera ścieżki kodu, które mogą spowodować wielokrotne wywołania <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lub równoważne metody Dispose, takie jak metoda Close () dla niektórych typów, w tym samym obiekcie.

## <a name="rule-description"></a>Opis reguły

Prawidłowo zaimplementowaną <xref:System.IDisposable.Dispose%2A> metodę można wywołać wiele razy bez zgłaszania wyjątku. Nie jest to jednak gwarantowane i aby uniknąć generowania <xref:System.ObjectDisposedException?displayProperty=fullName> , nie należy wywoływać <xref:System.IDisposable.Dispose%2A> więcej niż jeden raz w obiekcie.

## <a name="related-rules"></a>Powiązane reguły

- [CA2000: Usuń obiekty przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia

Aby naprawić naruszenie tej zasady, należy zmienić implementację, tak aby niezależnie od ścieżki <xref:System.IDisposable.Dispose%2A> kodu jest wywoływana tylko raz dla obiektu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia

Nie pomijaj ostrzeżeń dla tej reguły. Nawet wtedy <xref:System.IDisposable.Dispose%2A> , gdy dla obiektu wiadomo, że jest on bezpiecznie wielokrotnie wywoływany, implementacja może ulec zmianie w przyszłości.

## <a name="example"></a>Przykład

Instrukcje `using` zagnieżdżone (`Using` w Visual Basic) mogą spowodować naruszenia ostrzeżenia CA2202. Jeśli zasób IDisposable zagnieżdżonej instrukcji wewnętrznej `using` zawiera zasób instrukcji zewnętrznej `using` , `Dispose` Metoda zagnieżdżonego zasobu zwalnia zawartego zasobu. Gdy wystąpi taka sytuacja, `Dispose` Metoda instrukcji zewnętrznej `using` próbuje usunąć zasób po raz drugi.

W poniższym przykładzie <xref:System.IO.Stream> obiekt tworzony w instrukcji zewnętrznej using jest wydawany na końcu wewnętrznej instrukcji using w metodzie <xref:System.IO.StreamWriter> Dispose obiektu, który zawiera `stream` obiekt. Na końcu instrukcji `using` `stream` zewnętrznej obiekt jest wydawany po raz drugi. Druga wersja stanowi naruszenie CA2202.

```csharp
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Przykład

Aby rozwiązać ten problem, należy użyć `try` / `finally` bloku zamiast instrukcji zewnętrznej `using` . Upewnij się, `stream` że zasób nie ma wartości null w bloku.`finally`

```csharp
Stream stream = null;
try
{
    stream = new FileStream("file.txt", FileMode.OpenOrCreate);
    using (StreamWriter writer = new StreamWriter(stream))
    {
        stream = null;
        // Use the writer object...
    }
}
finally
{
    stream?.Dispose();
}
```

> [!TIP]
> Powyższa składnia jest operatorem warunkowym o [wartości null.](/dotnet/csharp/language-reference/operators/member-access-operators#null-conditional-operators--and-) `?.`

## <a name="see-also"></a>Zobacz także

- <xref:System.IDisposable?displayProperty=fullName>
- [Wzorzec Dispose](/dotnet/standard/design-guidelines/dispose-pattern)