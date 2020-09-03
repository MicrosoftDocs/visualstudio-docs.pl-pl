---
title: 'CA1021: Unikaj parametrów out | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: f8f1b0c17fe9135bf534b9f30bf4e54c8c286ada
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85546695"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Unikaj parametrów out
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma `out` parametr.

## <a name="rule-description"></a>Opis reguły
 Przekazywanie typów przez odwołanie (za pomocą `out` lub `ref` ) wymaga środowiska ze wskaźnikami, zrozumienie, jak typy wartości i typy odwołań różnią się i obsługują metody z wieloma zwracanymi wartościami. Ponadto różnice między `out` i `ref` parametrów nie są szeroko zrozumiałe.

 Gdy typ odwołania jest przenoszona "przez odwołanie", Metoda zamierza użyć parametru, aby zwrócić inne wystąpienie obiektu. Przekazywanie typu odwołania przez odwołanie jest również znane jako użycie podwójnego wskaźnika, wskaźnika do wskaźnika lub podwójnego pośrednika. Przy użyciu domyślnej konwencji wywoływania, która jest przekazywany "przez wartość", parametr, który pobiera typ odwołania, już otrzymuje wskaźnik do obiektu. Wskaźnik, a nie obiekt, do którego wskazuje, jest przenoszona przez wartość. Wartość Pass by oznacza, że metoda nie może zmienić wskaźnika tak, aby wskazywała nowe wystąpienie typu odwołania. Można jednak zmienić zawartość obiektu, do którego się odwołuje. W przypadku większości aplikacji jest to wystarczające i daje odpowiednie zachowanie.

 Jeśli metoda musi zwrócić inne wystąpienie, użyj wartości zwracanej metody, aby to osiągnąć. Zapoznaj się z <xref:System.String?displayProperty=fullName> klasą dla różnych metod, które działają na ciągach i zwracają nowe wystąpienie ciągu. Gdy ten model jest używany, obiekt wywołujący musi zdecydować, czy oryginalny obiekt jest zachowywany.

 Mimo że zwracane wartości są commonplace i intensywnie używane, poprawne stosowanie `out` i `ref` parametrów wymaga pośrednich umiejętności związanych z projektowaniem i programowaniem. Architekty biblioteki, którzy projektują dla ogólnych odbiorców, nie powinni oczekiwać od użytkowników, aby Master pracował z `out` lub `ref` parametrami.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, która jest spowodowana przez typ wartości, należy zwrócić obiekt jako wartość zwracaną przez metodę. Jeśli metoda musi zwracać wiele wartości, Zaprojektuj ją w celu zwrócenia pojedynczego wystąpienia obiektu, który zawiera wartości.

 Aby naprawić naruszenie tej zasady, która jest spowodowana przez typ referencyjny, upewnij się, że żądane zachowanie ma zwrócić nowe wystąpienie odwołania. Jeśli tak jest, metoda powinna używać jej wartości zwracanej, aby to zrobić.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak ten projekt może powodować problemy z użytecznością.

## <a name="example"></a>Przykład
 Następująca Biblioteka pokazuje dwie implementacje klasy, która generuje odpowiedzi na Opinie użytkownika. Pierwsza implementacja ( `BadRefAndOut` ) wymusza, aby użytkownik biblioteki zarządzał trzema zwracanymi wartościami. Druga implementacja ( `RedesignedRefAndOut` ) upraszcza środowisko użytkownika, zwracając wystąpienie klasy kontenera ( `ReplyData` ), które zarządza danymi jako pojedynczą jednostką.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Przykład
 W poniższej aplikacji przedstawiono środowisko użytkownika. Wywołanie przeprojektowanej biblioteki ( `UseTheSimplifiedClass` Metoda) jest bardziej proste, a informacje zwracane przez metodę są łatwo zarządzane. Dane wyjściowe z dwóch metod są identyczne.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Przykład
 W poniższej bibliotece pokazano, jak `ref` są używane parametry typów referencyjnych i przedstawiono lepszy sposób implementacji tej funkcji.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja wywołuje każdą metodę w bibliotece, aby przedstawić zachowanie.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Zmiana wskaźnika — wartość minęła:** 
 **12345** 
 **12345** 
 **Zmiana wskaźnika — przekazywanie przez odwołanie:** 
 **12345** 
 **12345 ABCD** 
 **Przekazywanie przez wartość zwracaną:** 
 **12345 ABCD**
## <a name="try-pattern-methods"></a>Metody wzorców try

### <a name="description"></a>Opis
 Metody implementujące wzorzec **try \<Something> ** , takie jak <xref:System.Int32.TryParse%2A?displayProperty=fullName> , nie powodują tego naruszenia. W poniższym przykładzie pokazano strukturę (typ wartości) implementującą <xref:System.Int32.TryParse%2A?displayProperty=fullName> metodę.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>Powiązane reguły
 [CA1045: Nie przekazuj typów przez odwołanie](../code-quality/ca1045-do-not-pass-types-by-reference.md)
