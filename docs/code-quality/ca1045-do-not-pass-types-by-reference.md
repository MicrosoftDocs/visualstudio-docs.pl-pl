---
title: 'CA1045: Nie przekazuj typów przez odwołanie'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: df104a7360c15de1c6d68ff5ae7d3c9f07340ace
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54953253"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Nie przekazuj typów przez odwołanie

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma `ref` parametru, która przyjmuje typ pierwotny, typem referencyjnym lub typem wartości, który nie jest jedną z wbudowanych typów.

## <a name="rule-description"></a>Opis reguły
 Przekazywanie typów przez odwołanie (używając `out` lub `ref`) wymaga doświadczenia w zakresie za pomocą wskaźników, zrozumienie, jak różnią się typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Ponadto różnica między `out` i `ref` parametrów nie jest powszechnie zrozumiała.

 Gdy typ odwołania jest przekazywany "przez odwołanie", metoda zamierza użyć parametru, aby powrócić do innego wystąpienia obiektu. (Przekazywanie typu odwołania przez odwołanie jest również znany jako za pomocą podwójnego wskaźnika, wskaźnik do wskaźnika lub podwójne pośredniego.) Przy użyciu domyślnego Konwencja wywoływania, który jest przekazać "value", parametr, który przyjmuje typ odwołania już otrzymuje wskaźnik do obiektu. Wskaźnik, a nie obiekt, na który wskazuje, jest przekazywany przez wartość. Przekazywanie poprzez wartość oznacza, że metody nie można zmienić wskaźnik, aby wskazywała na nowe wystąpienie odwołania do typu, ale można zmienić zawartość obiektu, na którą wskazuje. W przypadku większości aplikacji jest wystarczająca i daje zachowanie, które chcesz.

 Jeśli metoda musi zwracać inne wystąpienie, w tym celu należy użyć wartość zwracaną metody. Zobacz <xref:System.String?displayProperty=fullName> klasy dla różnych metod, które działają na ciągi i zwrócić nowe wystąpienie ciągu. Za pomocą tego modelu, pozostało do obiektu wywołującego zdecydować, czy jest zachowywana oryginalnego obiektu.

 Mimo że wartości zwracane są powszechne i intensywnie używane, odpowiednia `out` i `ref` parametrów wymaga pośrednich projektu i umiejętności kodowania. Architektów biblioteki, którzy tworzą dla wszystkich nie powinni oczekiwać od użytkowników do wzorca pracę z `out` lub `ref` parametrów.

> [!NOTE]
>  Podczas pracy z parametrami, które są duże struktury dodatkowe zasoby, które są wymagane, aby skopiować te struktury może spowodować wpływ na wydajność podczas przekazywania przez wartość. W takich przypadkach należy rozważyć przy użyciu `ref` lub `out` parametrów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, która jest spowodowany przez typ wartości, należy mieć metoda może zwracać obiektu jako jego wartość zwracaną. Jeśli metoda musi zwracać wiele wartości, należy ponownie zaprojektować go do zwrócenia pojedynczego wystąpienia obiektu, który przechowuje wartości.

 Aby naprawić naruszenie tej reguły, która jest spowodowany przez typ odwołania, upewnij się, że zachowanie, które chcesz, aby zwrócić nowe wystąpienie klasy odwołania. Jeśli tak jest, metody użyć jego zwracanej wartości w tym celu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie Pomijaj ostrzeżeń dla tej reguły; Jednak w tym projekcie może spowodować problemy z użytecznością.

## <a name="example"></a>Przykład
 Następująca biblioteka zawiera dwie implementacje klasy, która generuje odpowiedzi na opinie użytkownika. Pierwszy implementacji (`BadRefAndOut`) wymusza na użytkowniku biblioteki zarządzania trzy wartości zwracane. Drugi implementacji (`RedesignedRefAndOut`) upraszcza środowisko użytkownika, zwraca wystąpienie klasy kontenera (`ReplyData`) która zarządza danymi jako pojedyncza jednostka.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Przykład
 Następująca aplikacja ilustruje środowisko użytkownika. Wywołania do biblioteki przeprojektowana (`UseTheSimplifiedClass` metody) jest bardziej bezpośredni informacji, który jest zwracany przez metodę jest łatwe w zarządzaniu. Dane wyjściowe z dwóch metod jest taka sama.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Przykład
 Następujące biblioteki przykład ilustruje sposób `ref` parametrów dla typów referencyjnych są używane i pokazuje lepszy sposób w celu zaimplementowania tej funkcji.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Przykład
 Następująca aplikacja wywołuje każdej metody w bibliotece, aby zademonstrować zachowanie.

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