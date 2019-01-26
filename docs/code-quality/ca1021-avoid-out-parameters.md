---
title: 'CA1021: Unikaj parametrów out'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f654af804ea48089a3a27e154d70c118b22fecb7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957757"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Unikaj parametrów out

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategoria|Microsoft.Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma `out` parametru.

## <a name="rule-description"></a>Opis reguły
 Przekazywanie typów przez odwołanie (używając `out` lub `ref`) wymaga doświadczenia w zakresie wskaźników, zrozumienie, jak różnią się typami wartości i typami odwołania oraz umiejętności obsługi metod z wieloma wartościami zwracanymi. Ponadto różnica między `out` i `ref` parametrów nie jest powszechnie zrozumiała.

 Gdy typ odwołania jest przekazywany "przez odwołanie", metoda zamierza użyć parametru, aby powrócić do innego wystąpienia obiektu. Przekazywanie typu odwołania przez odwołanie jest nazywany również za pomocą podwójnego wskaźnika, wskaźnik do wskaźnika lub pośredni double. Za pomocą domyślna konwencja wywoływania, który jest przekazać "value", parametr, który przyjmuje typ odwołania już otrzymuje wskaźnik do obiektu. Wskaźnik, a nie obiekt, na który wskazuje, jest przekazywany przez wartość. Przekaż przez wartość oznacza metody nie można zmienić wskaźnik, aby wskazywała do nowego wystąpienia typu referencyjnego. Jednak jego zawartość można zmienić obiektu, na którą wskazuje. W przypadku większości aplikacji jest wystarczająca i daje żądane zachowanie.

 Jeśli metoda musi zwracać inne wystąpienie, w tym celu należy użyć wartość zwracaną metody. Zobacz <xref:System.String?displayProperty=fullName> klasy dla różnych metod, które działają na ciągi i zwrócić nowe wystąpienie ciągu. Gdy używany jest ten model, obiekt wywołujący należy zdecydować, czy oryginalnego obiektu są zachowywane.

 Mimo że wartości zwracane są powszechne i intensywnie używane, odpowiednia `out` i `ref` parametrów wymaga pośrednich projektu i umiejętności kodowania. Architektów biblioteki, którzy tworzą dla wszystkich nie powinni oczekiwać od użytkowników do wzorca pracę z `out` lub `ref` parametrów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, która jest spowodowany przez typ wartości, należy mieć metoda może zwracać obiektu jako jego wartość zwracaną. Jeśli metoda musi zwracać wiele wartości, należy ponownie zaprojektować go do zwrócenia pojedynczego wystąpienia obiektu, który przechowuje wartości.

 Aby naprawić naruszenie tej reguły, która jest spowodowany przez typ odwołania, upewnij się, że żądane zachowanie ma zwrócić nowe wystąpienie klasy odwołania. Jeśli tak jest, metody użyć jego zwracanej wartości w tym celu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Jest bezpieczne pominąć ostrzeżenie od tej reguły. Jednak w tym projekcie może spowodować problemy z użytecznością.

## <a name="example"></a>Przykład
 Następująca biblioteka zawiera dwie implementacje klasy, która generuje odpowiedzi na opinie użytkowników. Pierwszy implementacji (`BadRefAndOut`) wymusza na użytkowniku biblioteki zarządzania trzy wartości zwracane. Drugi implementacji (`RedesignedRefAndOut`) upraszcza środowisko użytkownika, zwraca wystąpienie klasy kontenera (`ReplyData`) która zarządza danymi jako pojedyncza jednostka.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Przykład
 Następująca aplikacja ilustruje środowisko użytkownika. Wywołania do biblioteki przeprojektowana (`UseTheSimplifiedClass` metody) jest bardziej bezpośredni informacji zwracany przez metodę jest łatwe w zarządzaniu. Dane wyjściowe z dwóch metod jest taka sama.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Przykład
 Następujące biblioteki przykład ilustruje sposób `ref` parametrów dla typów referencyjnych są używane i pokazuje lepszy sposób w celu zaimplementowania tej funkcji.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Przykład
 Następująca aplikacja wywołuje każdej metody w bibliotece, aby zademonstrować zachowanie.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

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

## <a name="try-pattern-methods"></a>Wypróbuj metody wzorca

### <a name="description"></a>Opis
 Metody, które implementują **spróbuj\<coś >** wzorca, takich jak <xref:System.Int32.TryParse%2A?displayProperty=fullName>, nie wywołuj tego naruszenia. Poniższy przykład pokazuje strukturę (typ wartości), który implementuje <xref:System.Int32.TryParse%2A?displayProperty=fullName> metody.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1045: Nie przekazuj typów przez odwołanie](../code-quality/ca1045-do-not-pass-types-by-reference.md)