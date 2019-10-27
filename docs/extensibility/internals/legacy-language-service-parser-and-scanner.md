---
title: Analizator i skaner starszej usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11b172fee8f6f5cf1c80d306a8a8b154f7316bf8
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726737"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analizator i skaner starszej wersji usługi językowej
Analizator jest sercem usługi językowej. Klasy języka Managed Package Framework (MPF) wymagają parsera języka w celu wybrania informacji o wyświetlanym kodzie. Parser oddziela tekst do tokenów leksykalnych, a następnie identyfikuje te tokeny według typu i funkcji.

## <a name="discussion"></a>Dyskusji
 Poniżej przedstawiono C# metodę.

```csharp
namespace MyNamespace
{
    class MyClass
    {
        public void MyFunction(int arg1)
        {
            int var1 = arg1;
        }
    }
}
```

 W tym przykładzie tokeny są słowami i znakami interpunkcyjnych. Rodzaje tokenów są następujące.

|Nazwa tokenu|Typ tokenu|
|----------------|----------------|
|Przestrzeń nazw, Klasa, Public, void, int|Kodu|
|=|operator|
|{ } ( ) ;|Ogranicznik|
|Przestrzeń nazw, MyClass, myFunction, arg1, var1|identyfikator|
|MyNamespace|— przestrzeń nazw|
|MyClass|class|
|MyFunction|— metoda|
|arg1|parametr|
|var1|Zmienna lokalna|

 Rolą parsera jest zidentyfikowanie tokenów. Niektóre tokeny mogą mieć więcej niż jeden typ. Po zidentyfikowaniu tokenów przez analizator, usługa języka może używać informacji w celu zapewnienia użytecznych funkcji, takich jak wyróżnianie składni, dopasowywanie nawiasów klamrowych i operacje IntelliSense.

## <a name="types-of-parsers"></a>Typy analizatorów
 Analizator usługi językowej nie jest taki sam jak parser używany jako część kompilatora. Jednak ten rodzaj parsera musi używać skanera i analizatora w taki sam sposób jak parser kompilatora.

- Skaner służy do identyfikowania typów tokenów. Te informacje są używane do wyróżniania składni i szybkiego identyfikowania typów tokenów, które mogą wyzwalać inne operacje, na przykład Dopasowywanie nawiasów klamrowych. Ten skaner jest reprezentowany przez interfejs <xref:Microsoft.VisualStudio.Package.IScanner>.

- Parser służy do opisywania funkcji i zakresu tokenów. Te informacje są używane w operacjach IntelliSense do identyfikowania elementów języka, takich jak metody, zmienne, parametry i deklaracje, oraz do udostępniania list elementów członkowskich i sygnatur metod opartych na kontekście. Ten parser jest również używany do lokalizowania pasujących par elementów języka, takich jak nawiasy klamrowe i nawiasy. Dostęp do tego parsera można uzyskać za pomocą metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService>.

  Zaimplementowanie skanera i parsera dla usługi językowej jest możliwe. Dostępnych jest kilka zasobów, które opisują, jak działają analizatory i jak pisać własne parsery. Ponadto dostępne są kilka bezpłatnych i komercyjnych produktów, które ułatwiają tworzenie parsera.

### <a name="the-parsesource-parser"></a>Analizator ParseSource
 W przeciwieństwie do analizatora, który jest używany jako część kompilatora (w którym tokeny są konwertowane na pewną postać kodu wykonywalnego), Analizator usługi językowej można wywołać z wielu różnych powodów i w wielu różnych kontekstach. Sposób implementacji tego podejścia w metodzie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService> jest do Ciebie. Należy pamiętać, że metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> może być wywoływana w wątku w tle.

> [!CAUTION]
> Struktura <xref:Microsoft.VisualStudio.Package.ParseRequest> zawiera odwołanie do obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>. Tego obiektu <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> nie można użyć w wątku w tle. W rzeczywistości wiele podstawowych klas MPF nie można używać w wątku w tle. Należą do nich klasy <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> i wszelkie inne klasy, które bezpośrednio lub pośrednio komunikują się z widokiem.

 Ten parser zwykle analizuje cały plik źródłowy przy pierwszym wywołaniu lub gdy zostanie podana wartość przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Kolejne wywołania metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> obsługują niewielką część przeanalizowanego kodu i mogą być wykonywane znacznie szybciej przy użyciu wyników poprzedniej operacji pełnej analizy. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> komunikuje wyniki operacji analizowania za pomocą obiektów <xref:Microsoft.VisualStudio.Package.AuthoringSink> i <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Obiekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> służy do zbierania informacji o konkretnym przyczynie analizy, na przykład informacje o zakresach pasujących nawiasów klamrowych lub sygnaturach metod, które mają listy parametrów. <xref:Microsoft.VisualStudio.Package.AuthoringScope> zawiera kolekcje deklaracji i sygnatur metod, a także obsługę opcji przejdź do zaawansowanej edycji (**Przejdź do definicji**, przejdź do **deklaracji**, **Przejdź do odwołania**).

### <a name="the-iscanner-scanner"></a>Skaner ispuszker
 Należy również zaimplementować skaner, który implementuje <xref:Microsoft.VisualStudio.Package.IScanner>. Jednak ponieważ ten skaner działa w oparciu o linię po wierszu za pomocą klasy <xref:Microsoft.VisualStudio.Package.Colorizer>, jest to zwykle prostsze do wdrożenia. Na początku każdego wiersza MPF nadaje klasie <xref:Microsoft.VisualStudio.Package.Colorizer> wartość, która będzie używana jako zmienna stanu, która jest przenoszona do skanera. Na końcu każdego wiersza skaner zwraca zaktualizowaną zmienną stanu. MPF buforuje informacje o stanie dla każdego wiersza, dzięki czemu skaner może rozpocząć analizowanie z dowolnego wiersza bez konieczności uruchamiania na początku pliku źródłowego. To szybkie skanowanie pojedynczego wiersza umożliwia edytorowi szybkie przesyłanie opinii do użytkownika.

## <a name="parsing-for-matching-braces"></a>Analizowanie pasujących nawiasów klamrowych
 Ten przykład pokazuje przepływ sterowania do dopasowania zamykającego nawiasu klamrowego wpisanego przez użytkownika. W tym procesie skaner używany do kolorowania jest również używany do określenia typu tokenu oraz tego, czy token może wyzwolić operację dopasowywania nawiasów klamrowych. Jeśli wyzwalacz zostanie znaleziony, wywoływana jest metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>, aby znaleźć pasujący nawias klamrowy. Na koniec dwa nawiasy klamrowe są wyróżnione.

 Mimo że nawiasy klamrowe są używane w nazwach wyzwalaczy i z powodów analizy, ten proces nie jest ograniczony do rzeczywistych nawiasów klamrowych. Obsługiwana jest jakakolwiek para znaków określona jako pasująca para. Przykłady obejmują (i), \< i > oraz [i].

 Załóżmy, że usługa językowa obsługuje pasujące nawiasy klamrowe.

1. Użytkownik wpisze zamykający nawias klamrowy (}).

2. Nawias klamrowy zostanie wstawiony do kursora w pliku źródłowym, a kursor jest zaawansowany o jeden.

3. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> w klasie <xref:Microsoft.VisualStudio.Package.Source> jest wywoływana przy użyciu zamykającego nawiasu klamrowego.

4. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> wywołuje metodę <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> w klasie <xref:Microsoft.VisualStudio.Package.Source> w celu uzyskania tokenu w pozycji tuż przed bieżącą pozycją kursora. Ten token odnosi się do wpisanego zamykającego nawiasu klamrowego.

    1. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> wywołuje metodę <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> na obiekcie <xref:Microsoft.VisualStudio.Package.Colorizer>, aby uzyskać wszystkie tokeny w bieżącym wierszu.

    2. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> wywołuje metodę <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> na obiekcie <xref:Microsoft.VisualStudio.Package.IScanner> z tekstem bieżącego wiersza.

    3. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> wielokrotnie wywołuje metodę <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> w obiekcie <xref:Microsoft.VisualStudio.Package.IScanner>, aby zebrać wszystkie tokeny z bieżącego wiersza.

    4. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> wywołuje prywatną metodę w klasie <xref:Microsoft.VisualStudio.Package.Source> w celu uzyskania tokenu, który zawiera pożądaną pozycję, i przekazuje listę tokenów uzyskanych z metody <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>.

5. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> szuka flagi wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> na tokenie, który jest zwracany przez metodę <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>; oznacza to, że token reprezentuje nawias zamykający.

6. Jeśli zostanie znaleziona flaga wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers>, Metoda <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> w klasie <xref:Microsoft.VisualStudio.Package.Source> jest wywoływana.

7. Metoda <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> rozpoczyna operację analizowania z powodu wartości przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Ta operacja ostatecznie wywołuje metodę <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> na klasie <xref:Microsoft.VisualStudio.Package.LanguageService>. Jeśli jest włączone analizowanie asynchroniczne, to wywołanie metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> występuje w wątku w tle.

8. Po zakończeniu operacji analizowania wewnętrzna procedura obsługi uzupełniania (znana również jako metoda wywołania zwrotnego) o nazwie `HandleMatchBracesResponse` jest wywoływana w klasie <xref:Microsoft.VisualStudio.Package.Source>. To wywołanie jest wykonywane automatycznie przez klasę bazową <xref:Microsoft.VisualStudio.Package.LanguageService>, a nie przez parser.

9. Metoda `HandleMatchBracesResponse` uzyskuje listę zakresów z obiektu <xref:Microsoft.VisualStudio.Package.AuthoringSink>, który jest przechowywany w obiekcie <xref:Microsoft.VisualStudio.Package.ParseRequest>. (Zakres jest strukturą <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>, która określa zakres wierszy i znaków w pliku źródłowym). Ta lista zakresów obejmuje zazwyczaj dwa zakresy, jeden z nich dla otwierających i zamykających nawiasów klamrowych.

10. Metoda `HandleBracesResponse` wywołuje metodę <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> na obiekcie <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>, który jest przechowywany w obiekcie <xref:Microsoft.VisualStudio.Package.ParseRequest>. Powoduje to wyróżnienie określonych zakresów.

11. Jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> jest włączona, Metoda `HandleBracesResponse` Pobiera tekst, który jest objęty zakresem dopasowywania i wyświetla pierwsze 80 znaków tego zakresu na pasku stanu. To działa najlepiej, jeśli metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> zawiera element języka, który towarzyszy pasującej parze. Aby uzyskać więcej informacji, zobacz Właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>.

12. Odbywać.

### <a name="summary"></a>Podsumowanie
 Operacje pasujących nawiasów klamrowych zwykle są ograniczone do prostych par elementów języka. Bardziej złożone elementy, takie jak Dopasowywanie potrójnych ("`if(...)`", "`{`" i "`}`", "`else`", "`{`" i "`}`"), można podróżnić w ramach operacji uzupełniania wyrazów. Na przykład po zakończeniu słowa "else" można wyróżnić pasującą instrukcję "`if`". Jeśli wystąpiły serie `if`/`else if`, wszystkie z nich można podróżnić przy użyciu tego samego mechanizmu co pasujące nawiasy klamrowe. Klasa bazowa <xref:Microsoft.VisualStudio.Package.Source> już obsługuje następujące: skaner musi zwrócić wartość wyzwalacza tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> połączoną z wartością wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> dla tokenu, który jest przed pozycją kursora.

 Aby uzyskać więcej informacji, zobacz [dopasowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analizowanie na potrzeby kolorowania
 Kolorowanie kodu źródłowego jest proste, po prostu Zidentyfikuj typ tokenu i zwróć informacje o kolorach tego typu. Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> pełni rolę pośrednika między edytorem a skanerem, aby dostarczyć informacje o kolorach każdego tokenu. Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> używa obiektu <xref:Microsoft.VisualStudio.Package.IScanner>, aby ułatwić kolorowanie linii, a także zbierać informacje o stanie dla wszystkich wierszy w pliku źródłowym. W klasach usługi językowej MPF Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> nie musi zostać zastąpiona, ponieważ komunikuje się ze skanerem tylko za pomocą interfejsu <xref:Microsoft.VisualStudio.Package.IScanner>. Należy podać obiekt implementujący interfejs <xref:Microsoft.VisualStudio.Package.IScanner>, zastępując metodę <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> na klasie <xref:Microsoft.VisualStudio.Package.LanguageService>.

 Skaner <xref:Microsoft.VisualStudio.Package.IScanner> otrzymuje wiersz kodu źródłowego za pomocą metody <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A>. Wywołania metody <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> są powtórzone w celu uzyskania następnego tokenu w wierszu do momentu wyczerpania wiersza tokenów. W przypadku kolorowania MPF traktuje cały kod źródłowy jako sekwencję wierszy. W związku z tym skaner musi być w stanie poradzić sobie ze źródłem, tak jak linie. Ponadto każda linia może być przenoszona do skanera w dowolnym momencie, a jedyną gwarancją jest, że skaner otrzymuje zmienną stanu z wiersza przed przeskanowaniem wiersza.

 Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> jest również używana do identyfikowania wyzwalaczy tokenów. Te wyzwalacze informują MPF, że określony token może inicjować bardziej skomplikowaną operację, taką jak uzupełnianie wyrazów lub pasujące nawiasy klamrowe. Ponieważ takie wyzwalacze muszą być szybkie i muszą wystąpić w dowolnym miejscu, skaner jest najlepiej dostosowany do tego zadania.

 Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analizowanie funkcjonalności i zakresu
 Analizowanie funkcjonalności i zakresu wymaga większego nakładu pracy niż zidentyfikowanie typów tokenów, które są napotkane. Analizator ma identyfikować nie tylko typ tokenu, ale również funkcje, dla których token jest używany. Na przykład identyfikator jest tylko nazwą, ale w Twoim języku Identyfikator może być nazwą klasy, przestrzeni nazw, metody lub zmiennej, w zależności od kontekstu. Ogólny typ tokenu może być identyfikatorem, ale identyfikator może również mieć inne znaczenie, w zależności od tego, co jest i gdzie jest zdefiniowane. Ta identyfikacja wymaga, aby Analizator miał bardziej obszerną wiedzę o analizowanym języku. Jest to miejsce, w którym znajduje się Klasa <xref:Microsoft.VisualStudio.Package.AuthoringSink>. Klasa <xref:Microsoft.VisualStudio.Package.AuthoringSink> zbiera informacje o identyfikatorach, metodach, pasujących parach językowych (takich jak nawiasy klamrowe i nawiasy) oraz potrójnie w języku (podobnie jak w przypadku par językowych, z wyjątkiem tego, że istnieją trzy części, na przykład "`foreach()`" "`{`" i "`}`"). Ponadto można przesłonić klasę <xref:Microsoft.VisualStudio.Package.AuthoringSink>, aby obsługiwała identyfikację kodu, która jest używana podczas wczesnej walidacji punktów przerwania, tak aby debuger nie musiał być ładowany, oraz okno debugowanie **Automatyczne** , które pokazuje zmienne lokalne i parametry automatycznie, gdy program jest debugowany i wymaga analizatora do identyfikowania odpowiednich zmiennych lokalnych i parametrów oprócz tych, które prezentuje debuger.

 Obiekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> jest przesyłany do analizatora jako część obiektu <xref:Microsoft.VisualStudio.Package.ParseRequest>, a nowy obiekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> jest tworzony za każdym razem, gdy tworzony jest nowy obiekt <xref:Microsoft.VisualStudio.Package.ParseRequest>. Ponadto Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> musi zwracać obiekt <xref:Microsoft.VisualStudio.Package.AuthoringScope>, który jest używany do obsługi różnych operacji IntelliSense. Obiekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> zachowuje listę deklaracji i listę metod, z których każda jest wypełniona, w zależności od przyczyny analizy. Należy zaimplementować klasę <xref:Microsoft.VisualStudio.Package.AuthoringScope>.

## <a name="see-also"></a>Zobacz także
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)