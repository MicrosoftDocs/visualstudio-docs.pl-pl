---
title: 'CA2202: Nie Likwiduj wielokrotnie obiektów | Dokumentacja firmy Microsoft'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3dfe606e3083c937db3ba3d1e6cd49d34bace853
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65697967"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Nie likwiduj obiektów wielokrotnie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategoria|Microsoft.Usage|
|Zmiana kluczowa|Bez podziału|

## <a name="cause"></a>Przyczyna
 Implementacja metody zawiera ścieżki kodu, które powodują wielokrotne wywołania do <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lub równoważnika, na przykład użycie metody Close() na niektórych typów, w tym obiekcie.

## <a name="rule-description"></a>Opis reguły
 A implementowana prawidłowo <xref:System.IDisposable.Dispose%2A> metoda może być wywoływana wiele razy bez zgłoszenia wyjątku. Jednak to nie jest gwarantowana i aby uniknąć generowania <xref:System.ObjectDisposedException?displayProperty=fullName> nie powinien wywoływać <xref:System.IDisposable.Dispose%2A> więcej niż jeden raz na obiekcie.

## <a name="related-rules"></a>Powiązane reguły
 [CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, zmień wdrożenie tak oznacza niezależnie od tego, ścieżka kodu <xref:System.IDisposable.Dispose%2A> jest wywoływana tylko raz dla obiektu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet wtedy, gdy <xref:System.IDisposable.Dispose%2A> dla obiektu jest znany jako bezpiecznie wywoływana wiele razy, implementacja mogą ulec zmianie w przyszłości.

## <a name="example"></a>Przykład
 Zagnieżdżone `using` instrukcji (`Using` w języku Visual Basic) może spowodować naruszenie ostrzeżenie CA2202. Jeśli zasób interfejsu IDisposable zagnieżdżonych wewnętrzny `using` instrukcja zawiera zasób zewnętrzny `using` instrukcji `Dispose` metoda zagnieżdżonych zasobów zwalnia zawartego zasobu. Jeśli taka sytuacja ma miejsce, `Dispose` metoda zewnętrznego `using` instrukcji podejmie próbę usunięcia jego zasób po raz drugi.

 W poniższym przykładzie <xref:System.IO.Stream> obiektu, który jest tworzony w zewnętrznym przy użyciu instrukcji jest zwalniany na końcu wewnętrzny przy użyciu instrukcji w metodzie Dispose <xref:System.IO.StreamWriter> obiekt, który zawiera `stream` obiektu. Na koniec zewnętrzny `using` instrukcji `stream` obiektu jest zwalniany po raz drugi. Drugie wydanie stanowi naruszenie CA2202.

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
 Aby rozwiązać ten problem, należy użyć `try` / `finally` bloku zamiast zewnętrzny `using` instrukcji. W `finally` blokowania, upewnij się, że `stream` zasobów nie ma wartości null.

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
 <xref:System.IDisposable?displayProperty=fullName> [Wzorzec Dispose](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
