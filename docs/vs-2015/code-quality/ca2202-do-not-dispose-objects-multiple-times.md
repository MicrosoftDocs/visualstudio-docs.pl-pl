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
ms.openlocfilehash: e0be715d8aea84fac53ea2a796e71850b961730c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667403"
---
# <a name="ca2202-do-not-dispose-objects-multiple-times"></a>CA2202: Nie należy usuwać obiektów wiele razy
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotDisposeObjectsMultipleTimes|
|CheckId|CA2202|
|Kategoria|Microsoft. Usage|
|Zmiana kluczowa|Bez przerywania|

## <a name="cause"></a>Przyczyna
 Implementacja metody zawiera ścieżki kodu, które mogą spowodować wielokrotne wywołania <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> lub równoważne metody Dispose, takie jak metoda Close () dla niektórych typów, w tym samym obiekcie.

## <a name="rule-description"></a>Opis reguły
 Prawidłowo zaimplementowaną metodę <xref:System.IDisposable.Dispose%2A> można wywołać wiele razy bez zgłaszania wyjątku. Nie jest to jednak gwarantowane i aby uniknąć generowania <xref:System.ObjectDisposedException?displayProperty=fullName> nie należy wywoływać <xref:System.IDisposable.Dispose%2A> więcej niż jeden raz w obiekcie.

## <a name="related-rules"></a>Powiązane reguły
 [CA2000: Likwiduj obiekty przed utratą zakresu](../code-quality/ca2000-dispose-objects-before-losing-scope.md)

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, należy zmienić implementację, tak aby niezależnie od ścieżki kodu <xref:System.IDisposable.Dispose%2A> jest wywoływana tylko raz dla obiektu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Nie pomijaj ostrzeżeń dla tej reguły. Nawet jeśli <xref:System.IDisposable.Dispose%2A> dla obiektu jest znany, że będzie można go bezpiecznie wywołać wielokrotnie, implementacja może ulec zmianie w przyszłości.

## <a name="example"></a>Przykład
 Zagnieżdżone instrukcje `using` (`Using` w Visual Basic) mogą spowodować naruszenia ostrzeżenia CA2202. Jeśli zasób interfejsu IDisposable zagnieżdżonej wewnętrznej `using` zawiera zasób instrukcji Outer `using`, Metoda `Dispose` zasobu zagnieżdżonego zwalnia zawartego zasobu. Gdy wystąpi taka sytuacja, Metoda `Dispose` instrukcji Outer `using` próbuje usunąć zasób po raz drugi.

 W poniższym przykładzie obiekt <xref:System.IO.Stream>, który jest tworzony w instrukcji zewnętrznej using jest wydawany na końcu wewnętrznej instrukcji using w metodzie Dispose obiektu <xref:System.IO.StreamWriter>, który zawiera obiekt `stream`. Na końcu zewnętrznej instrukcji `using` obiekt `stream` jest wydawany sekundowo. Druga wersja stanowi naruszenie CA2202.

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
 Aby rozwiązać ten problem, należy użyć bloku `try` / `finally` zamiast zewnętrznej instrukcji `using`. W bloku `finally` upewnij się, że zasób `stream` nie ma wartości null.

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
 <xref:System.IDisposable?displayProperty=fullName> — [wzorzec usuwania](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
