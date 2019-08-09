---
title: 'CA1045: Nie przekazuj typów przez odwołanie'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6fd0da0f8b04055622b46087ecb9f12b375d9576
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922850"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Nie przekazuj typów przez odwołanie

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
Metoda publiczna lub chroniona w typie publicznym ma `ref` parametr, który przyjmuje typ pierwotny, typ referencyjny lub typ wartości, który nie jest jednym z typów wbudowanych.

## <a name="rule-description"></a>Opis reguły
Przekazywanie typów przez odwołanie (za `out` pomocą `ref`lub) wymaga środowiska ze wskaźnikami, zrozumienie, jak typy wartości i typy odwołań różnią się i obsługują metody, które mają wiele wartości zwracanych. Ponadto różnice między `out` i `ref` parametrów nie są szeroko zrozumiałe.

Gdy typ odwołania jest przenoszona "przez odwołanie", Metoda zamierza użyć parametru, aby zwrócić inne wystąpienie obiektu. (Przekazywanie typu odwołania przez odwołanie jest również znane jako użycie podwójnego wskaźnika, wskaźnika do wskaźnika lub podwójnego pośrednika). Przy użyciu domyślnej konwencji wywoływania, która jest przekazywany "przez wartość", parametr, który pobiera typ odwołania, już otrzymuje wskaźnik do obiektu. Wskaźnik, a nie obiekt, do którego wskazuje, jest przenoszona przez wartość. Przekazywanie przez wartość oznacza, że metoda nie może zmienić wskaźnika tak, aby wskazywała nowe wystąpienie typu referencyjnego, ale może zmienić zawartość obiektu, do którego wskazuje. W przypadku większości aplikacji jest to wystarczające i zapewnia zachowanie, które chcesz.

Jeśli metoda musi zwrócić inne wystąpienie, użyj wartości zwracanej metody, aby to osiągnąć. Zapoznaj <xref:System.String?displayProperty=fullName> się z klasą dla różnych metod, które działają na ciągach i zwracają nowe wystąpienie ciągu. Przy użyciu tego modelu pozostało do obiektu wywołującego, aby zdecydować, czy oryginalny obiekt jest zachowywany.

Mimo że zwracane wartości są commonplace i intensywnie używane, poprawne stosowanie `out` i `ref` parametrów wymaga pośrednich umiejętności związanych z projektowaniem i programowaniem. Architekty biblioteki, którzy projektują dla ogólnych odbiorców, nie powinni oczekiwać od użytkowników `out` , `ref` aby Master pracował z lub parametrami.

> [!NOTE]
> Podczas pracy z parametrami, które są duże struktury, dodatkowe zasoby, które są wymagane do kopiowania tych struktur, mogą spowodować efekt wydajności podczas przekazywania przez wartość. W takich przypadkach można rozważyć użycie `ref` lub `out` parametry.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
Aby naprawić naruszenie tej zasady, która jest spowodowana przez typ wartości, należy zwrócić obiekt jako wartość zwracaną przez metodę. Jeśli metoda musi zwracać wiele wartości, Zaprojektuj ją w celu zwrócenia pojedynczego wystąpienia obiektu, który zawiera wartości.

Aby naprawić naruszenie tej zasady, która jest spowodowana przez typ referencyjny, należy się upewnić, że zachowanie ma zwrócić nowe wystąpienie odwołania. Jeśli tak jest, metoda powinna używać jej wartości zwracanej, aby to zrobić.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
Można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak ten projekt może powodować problemy z użytecznością.

## <a name="example"></a>Przykład
W poniższej bibliotece przedstawiono dwie implementacje klasy, która generuje odpowiedzi na opinie użytkowników. Pierwsza implementacja (`BadRefAndOut`) wymusza, aby użytkownik biblioteki zarządzał trzema zwracanymi wartościami. Druga implementacja (`RedesignedRefAndOut`) upraszcza środowisko użytkownika, zwracając wystąpienie klasy kontenera (`ReplyData`), które zarządza danymi jako pojedynczą jednostką.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Przykład
W poniższej aplikacji przedstawiono środowisko użytkownika. Wywołanie przeprojektowanej biblioteki (`UseTheSimplifiedClass` Metoda) jest bardziej proste, a informacje zwracane przez metodę są łatwo zarządzane. Dane wyjściowe z dwóch metod są identyczne.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Przykład
W poniższej bibliotece pokazano, jak `ref` są używane parametry typów referencyjnych i przedstawiono lepszy sposób implementacji tej funkcji.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Przykład
Następująca aplikacja wywołuje każdą metodę w bibliotece, aby przedstawić zachowanie.

[!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

Ten przykład generuje następujące wyniki:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="related-rules"></a>Powiązane reguły
[CA1021: Unikaj parametrów out](../code-quality/ca1021-avoid-out-parameters.md)