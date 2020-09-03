---
title: 'CA1045: nie przekazuj typów przez odwołanie | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: dad2f90a51a4247a4c111ef51e85a28ba1a118ce
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548476"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Nie przekazuj typów przez odwołanie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wartość|
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Kategoria|Microsoft. Design|
|Zmiana kluczowa|Kluczowa|

## <a name="cause"></a>Przyczyna
 Metoda publiczna lub chroniona w typie publicznym ma `ref` parametr, który przyjmuje typ pierwotny, typ referencyjny lub typ wartości, który nie jest jednym z typów wbudowanych.

## <a name="rule-description"></a>Opis reguły
 Przekazywanie typów przez odwołanie (za pomocą `out` lub `ref` ) wymaga środowiska ze wskaźnikami, zrozumienie, jak typy wartości i typy odwołań różnią się i obsługują metody, które mają wiele wartości zwracanych. Ponadto różnice między `out` i `ref` parametrów nie są szeroko zrozumiałe.

 Gdy typ odwołania jest przenoszona "przez odwołanie", Metoda zamierza użyć parametru, aby zwrócić inne wystąpienie obiektu. (Przekazywanie typu odwołania przez odwołanie jest również znane jako użycie podwójnego wskaźnika, wskaźnika do wskaźnika lub podwójnego pośrednika). Przy użyciu domyślnej konwencji wywoływania, która jest przekazywany "przez wartość", parametr, który pobiera typ odwołania, już otrzymuje wskaźnik do obiektu. Wskaźnik, a nie obiekt, do którego wskazuje, jest przenoszona przez wartość. Przekazywanie przez wartość oznacza, że metoda nie może zmienić wskaźnika tak, aby wskazywała nowe wystąpienie typu referencyjnego, ale może zmienić zawartość obiektu, do którego wskazuje. W przypadku większości aplikacji jest to wystarczające i zapewnia zachowanie, które chcesz.

 Jeśli metoda musi zwrócić inne wystąpienie, użyj wartości zwracanej metody, aby to osiągnąć. Zapoznaj się z <xref:System.String?displayProperty=fullName> klasą dla różnych metod, które działają na ciągach i zwracają nowe wystąpienie ciągu. Przy użyciu tego modelu pozostało do obiektu wywołującego, aby zdecydować, czy oryginalny obiekt jest zachowywany.

 Mimo że zwracane wartości są commonplace i intensywnie używane, poprawne stosowanie `out` i `ref` parametrów wymaga pośrednich umiejętności związanych z projektowaniem i programowaniem. Architekty biblioteki, którzy projektują dla ogólnych odbiorców, nie powinni oczekiwać od użytkowników, aby Master pracował z `out` lub `ref` parametrami.

> [!NOTE]
> Podczas pracy z parametrami, które są duże struktury, dodatkowe zasoby, które są wymagane do kopiowania tych struktur, mogą spowodować efekt wydajności podczas przekazywania przez wartość. W takich przypadkach można rozważyć użycie `ref` lub `out` parametry.

## <a name="how-to-fix-violations"></a>Jak naprawić naruszenia
 Aby naprawić naruszenie tej zasady, która jest spowodowana przez typ wartości, należy zwrócić obiekt jako wartość zwracaną przez metodę. Jeśli metoda musi zwracać wiele wartości, Zaprojektuj ją w celu zwrócenia pojedynczego wystąpienia obiektu, który zawiera wartości.

 Aby naprawić naruszenie tej zasady, która jest spowodowana przez typ referencyjny, należy się upewnić, że zachowanie ma zwrócić nowe wystąpienie odwołania. Jeśli tak jest, metoda powinna używać jej wartości zwracanej, aby to zrobić.

## <a name="when-to-suppress-warnings"></a>Kiedy pominąć ostrzeżenia
 Można bezpiecznie pominąć ostrzeżenie z tej reguły. Jednak ten projekt może powodować problemy z użytecznością.

## <a name="example"></a>Przykład
 W poniższej bibliotece przedstawiono dwie implementacje klasy, która generuje odpowiedzi na opinie użytkowników. Pierwsza implementacja ( `BadRefAndOut` ) wymusza, aby użytkownik biblioteki zarządzał trzema zwracanymi wartościami. Druga implementacja ( `RedesignedRefAndOut` ) upraszcza środowisko użytkownika, zwracając wystąpienie klasy kontenera ( `ReplyData` ), które zarządza danymi jako pojedynczą jednostką.

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
## <a name="related-rules"></a>Powiązane reguły
 [CA1021: Unikaj parametrów out](../code-quality/ca1021-avoid-out-parameters.md)
