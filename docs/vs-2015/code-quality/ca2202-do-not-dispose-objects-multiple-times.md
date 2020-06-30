---
title: 'CA2202: nie usuwaj obiektów wiele razy | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2202
- Do not dispose objects multiple times
- DoNotDisposeObjectsMultipleTimes
helpviewer_keywords:
- CA2202
ms.assetid: fa85349a-cf1e-42c8-a86b-eacae1f8bd96
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 31bf7fe33aa59c3a713d2da81ddbd11ed6899723
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546292"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Nie likwiduj obiektów wielokrotnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Implementacja metody zawiera ścieżki kodu, które mogą spowodować wielokrotne wywołania <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lub równoważne metody Dispose, takie jak metoda Close () dla niektórych typów, w tym samym obiekcie.

## <a name="rule-description"></a>Opis reguły
 Prawidłowo zaimplementowaną <xref:System.IDisposable.Dispose%2A> metodę można wywołać wiele razy bez zgłaszania wyjątku. Nie jest to jednak gwarantowane i aby uniknąć generowania, <xref:System.ObjectDisposedException?displayProperty=fullName> nie należy wywoływać <xref:System.IDisposable.Dispose%2A> więcej niż jeden raz w obiekcie.

## <a name="related-rules"></a>Powiązane reguły
 [CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić implementację, tak aby niezależnie od ścieżki kodu <xref:System.IDisposable.Dispose%2A> jest wywoływana tylko raz dla obiektu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet wtedy <xref:System.IDisposable.Dispose%2A> , gdy dla obiektu wiadomo, że jest on bezpiecznie wielokrotnie wywoływany, implementacja może ulec zmianie w przyszłości.

## <a name="example"></a>Przykład
 `using`Instrukcje zagnieżdżone ( `Using` w Visual Basic) mogą spowodować naruszenia ostrzeżenia CA2202. Jeśli zasób IDisposable zagnieżdżonej `using` instrukcji wewnętrznej zawiera zasób `using` instrukcji zewnętrznej, `Dispose` Metoda zagnieżdżonego zasobu zwalnia zawartego zasobu. Gdy wystąpi taka sytuacja, `Dispose` Metoda `using` instrukcji zewnętrznej próbuje usunąć zasób po raz drugi.

 W poniższym przykładzie <xref:System.IO.Stream> obiekt tworzony w instrukcji zewnętrznej using jest wydawany na końcu wewnętrznej instrukcji using w metodzie Dispose <xref:System.IO.StreamWriter> obiektu, który zawiera `stream` obiekt. Na końcu `using` instrukcji zewnętrznej `stream` obiekt jest wydawany po raz drugi. Druga wersja stanowi naruszenie CA2202.

```
using (Stream stream = new FileStream("file.txt", FileMode.OpenOrCreate))
{
    using (StreamWriter writer = new StreamWriter(stream))
    {
        // Use the writer object...
    }
}
```

## <a name="example"></a>Przykład
 Aby rozwiązać ten problem, należy użyć `try` / `finally` bloku zamiast `using` instrukcji zewnętrznej. Upewnij `finally` się, że `stream` zasób nie ma wartości null w bloku.

```
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
    if(stream != null)
        stream.Dispose();
}
```

## <a name="see-also"></a>Zobacz też
 <xref:System.IDisposable?displayProperty=fullName>Usuń [wzorzec](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
