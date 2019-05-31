---
title: 'CA1045: Nie przekazuj typów przez odwołanie | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 6bbdcb2e2ac8f905a2b52cfb41ed90217d215b4b
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63431542"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Nie przekazuj typów przez odwołanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
> Podczas pracy z parametrami, które są duże struktury dodatkowe zasoby, które są wymagane, aby skopiować te struktury może spowodować wpływ na wydajność podczas przekazywania przez wartość. W takich przypadkach należy rozważyć przy użyciu `ref` lub `out` parametrów.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej reguły, która jest spowodowany przez typ wartości, należy mieć metoda może zwracać obiektu jako jego wartość zwracaną. Jeśli metoda musi zwracać wiele wartości, należy ponownie zaprojektować go do zwrócenia pojedynczego wystąpienia obiektu, który przechowuje wartości.

 Aby naprawić naruszenie tej reguły, która jest spowodowany przez typ odwołania, upewnij się, że zachowanie, które chcesz, aby zwrócić nowe wystąpienie klasy odwołania. Jeśli tak jest, metody użyć jego zwracanej wartości w tym celu.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Bezpiecznie Pomijaj ostrzeżeń dla tej reguły; Jednak w tym projekcie może spowodować problemy z użytecznością.

## <a name="example"></a>Przykład
 Następująca biblioteka zawiera dwie implementacje klasy, która generuje odpowiedzi na opinie użytkownika. Pierwszy implementacji (`BadRefAndOut`) wymusza na użytkowniku biblioteki zarządzania trzy wartości zwracane. Drugi implementacji (`RedesignedRefAndOut`) upraszcza środowisko użytkownika, zwraca wystąpienie klasy kontenera (`ReplyData`) która zarządza danymi jako pojedyncza jednostka.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja ilustruje środowisko użytkownika. Wywołania do biblioteki przeprojektowana (`UseTheSimplifiedClass` metody) jest bardziej bezpośredni informacji, który jest zwracany przez metodę jest łatwe w zarządzaniu. Dane wyjściowe z dwóch metod jest taka sama.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Przykład
 Następujące biblioteki przykład ilustruje sposób `ref` parametrów dla typów referencyjnych są używane i pokazuje lepszy sposób w celu zaimplementowania tej funkcji.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Przykład
 Następująca aplikacja wywołuje każdej metody w bibliotece, aby zademonstrować zachowanie.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Ten przykład generuje następujące dane wyjściowe.

 **Zmiana wskaźnik - przekazywane przez wartość:** 
**12345**
**12345**
**wskaźnik zmiana - przekazywany przez odwołanie:** 
**12345**
**12345 ABCDE**
**przekazywanie poprzez wartość zwracana:** 
**12345 ABCDE**
## <a name="related-rules"></a>Powiązane reguły
 [CA1021: Unikaj parametrów out](../code-quality/ca1021-avoid-out-parameters.md)
