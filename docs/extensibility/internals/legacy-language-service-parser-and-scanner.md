---
title: Analizator i skaner starszej usługi językowej | Microsoft Docs
description: Dowiedz się więcej na temat analizatora i skanera starszej usługi językowej, który wybiera informacje o wyświetlanym kodzie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 20c8c58a98887e5509026641ba0295fc167435e3
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204608"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analizator i skaner starszej wersji usługi językowej
Analizator jest sercem usługi językowej. Klasy języka Managed Package Framework (MPF) wymagają parsera języka w celu wybrania informacji o wyświetlanym kodzie. Parser oddziela tekst do tokenów leksykalnych, a następnie identyfikuje te tokeny według typu i funkcji.

## <a name="discussion"></a>Dyskusja
 Poniżej znajduje się Metoda języka C#.

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
|Przestrzeń nazw, Klasa, Public, void, int|kodu|
|=|operator|
|{ } ( ) ;|ogranicznik|
|Przestrzeń nazw, MyClass, myFunction, arg1, var1|identyfikator|
|MyNamespace|namespace|
|MyClass|class|
|MyFunction|method|
|arg1|parametr|
|var1|Zmienna lokalna|

 Rolą parsera jest zidentyfikowanie tokenów. Niektóre tokeny mogą mieć więcej niż jeden typ. Po zidentyfikowaniu tokenów przez analizator, usługa języka może używać informacji w celu zapewnienia użytecznych funkcji, takich jak wyróżnianie składni, dopasowywanie nawiasów klamrowych i operacje IntelliSense.

## <a name="types-of-parsers"></a>Typy analizatorów
 Analizator usługi językowej nie jest taki sam jak parser używany jako część kompilatora. Jednak ten rodzaj parsera musi używać skanera i analizatora w taki sam sposób jak parser kompilatora.

- Skaner służy do identyfikowania typów tokenów. Te informacje są używane do wyróżniania składni i szybkiego identyfikowania typów tokenów, które mogą wyzwalać inne operacje, na przykład Dopasowywanie nawiasów klamrowych. Ten skaner jest reprezentowany przez <xref:Microsoft.VisualStudio.Package.IScanner> interfejs.

- Parser służy do opisywania funkcji i zakresu tokenów. Te informacje są używane w operacjach IntelliSense do identyfikowania elementów języka, takich jak metody, zmienne, parametry i deklaracje, oraz do udostępniania list elementów członkowskich i sygnatur metod opartych na kontekście. Ten parser jest również używany do lokalizowania pasujących par elementów języka, takich jak nawiasy klamrowe i nawiasy. Dostęp do tego parsera uzyskuje się za pomocą <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie.

  Zaimplementowanie skanera i parsera dla usługi językowej jest możliwe. Dostępnych jest kilka zasobów, które opisują, jak działają analizatory i jak pisać własne parsery. Ponadto dostępne są kilka bezpłatnych i komercyjnych produktów, które ułatwiają tworzenie parsera.

### <a name="the-parsesource-parser"></a>Analizator ParseSource
 W przeciwieństwie do analizatora, który jest używany jako część kompilatora (w którym tokeny są konwertowane na pewną postać kodu wykonywalnego), Analizator usługi językowej można wywołać z wielu różnych powodów i w wielu różnych kontekstach. Sposób implementacji tego podejścia w <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodzie w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie jest do użytkownika. Należy pamiętać, że <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda może być wywoływana w wątku w tle.

> [!CAUTION]
> <xref:Microsoft.VisualStudio.Package.ParseRequest>Struktura zawiera odwołanie do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu. <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>Nie można użyć tego obiektu w wątku w tle. W rzeczywistości wiele podstawowych klas MPF nie można używać w wątku w tle. Obejmują one <xref:Microsoft.VisualStudio.Package.Source> , <xref:Microsoft.VisualStudio.Package.ViewFilter> , <xref:Microsoft.VisualStudio.Package.CodeWindowManager> klasy i inne klasy, które bezpośrednio lub pośrednio komunikują się z widokiem.

 Ten parser zwykle analizuje cały plik źródłowy przy pierwszym wywołaniu lub w przypadku podaniu wartości przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason> . Kolejne wywołania <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody obsługują niewielką część przeanalizowanego kodu i mogą być wykonywane znacznie szybciej przy użyciu wyników poprzedniej operacji pełnej analizy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>Metoda przekazuje wyniki operacji analizowania za pomocą <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektów i. <xref:Microsoft.VisualStudio.Package.AuthoringSink>Obiekt służy do zbierania informacji o konkretnym przyczynie analizy, na przykład informacje o zakresach pasujących nawiasów klamrowych lub sygnaturach metod, które mają listy parametrów. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Zawiera kolekcje deklaracji i sygnatur metod, a także obsługę opcji przejdź do zaawansowanej edycji (**Przejdź do definicji**, przejdź do **deklaracji**, **Przejdź do odwołania**).

### <a name="the-iscanner-scanner"></a>Skaner ispuszker
 Należy również zaimplementować skaner, który implementuje <xref:Microsoft.VisualStudio.Package.IScanner> . Jednak ponieważ ten skaner działa w oparciu o linię po wierszu przez <xref:Microsoft.VisualStudio.Package.Colorizer> klasę, zazwyczaj łatwiej jest zaimplementować. Na początku każdego wiersza MPF nadaje klasie wartości, która <xref:Microsoft.VisualStudio.Package.Colorizer> ma być używana jako zmienna stanu, która jest przenoszona do skanera. Na końcu każdego wiersza skaner zwraca zaktualizowaną zmienną stanu. MPF buforuje informacje o stanie dla każdego wiersza, dzięki czemu skaner może rozpocząć analizowanie z dowolnego wiersza bez konieczności uruchamiania na początku pliku źródłowego. To szybkie skanowanie pojedynczego wiersza umożliwia edytorowi szybkie przesyłanie opinii do użytkownika.

## <a name="parsing-for-matching-braces"></a>Analizowanie pasujących nawiasów klamrowych
 Ten przykład pokazuje przepływ sterowania do dopasowania zamykającego nawiasu klamrowego wpisanego przez użytkownika. W tym procesie skaner używany do kolorowania jest również używany do określenia typu tokenu oraz tego, czy token może wyzwolić operację dopasowywania nawiasów klamrowych. Jeśli wyzwalacz zostanie znaleziony, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda jest wywoływana w celu znalezienia pasującego nawiasu klamrowego. Na koniec dwa nawiasy klamrowe są wyróżnione.

 Mimo że nawiasy klamrowe są używane w nazwach wyzwalaczy i z powodów analizy, ten proces nie jest ograniczony do rzeczywistych nawiasów klamrowych. Obsługiwana jest jakakolwiek para znaków określona jako pasująca para. Przykłady obejmują (i), \< and > i [oraz].

 Załóżmy, że usługa językowa obsługuje pasujące nawiasy klamrowe.

1. Użytkownik wpisze zamykający nawias klamrowy (}).

2. Nawias klamrowy zostanie wstawiony do kursora w pliku źródłowym, a kursor jest zaawansowany o jeden.

3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda w <xref:Microsoft.VisualStudio.Package.Source> klasie jest wywoływana przy użyciu zamykającego nawiasu klamrowego.

4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda wywołuje <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodę w <xref:Microsoft.VisualStudio.Package.Source> klasie w celu uzyskania tokenu w pozycji tuż przed bieżącą pozycją kursora. Ten token odnosi się do wpisanego zamykającego nawiasu klamrowego.

    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Metoda wywołuje <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodę w <xref:Microsoft.VisualStudio.Package.Colorizer> obiekcie, aby uzyskać wszystkie tokeny w bieżącym wierszu.

    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Metoda wywołuje <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodę na <xref:Microsoft.VisualStudio.Package.IScanner> obiekcie z tekstem bieżącego wiersza.

    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A>Metoda wielokrotnie wywołuje <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodę na <xref:Microsoft.VisualStudio.Package.IScanner> obiekcie, aby zebrać wszystkie tokeny z bieżącego wiersza.

    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A>Metoda wywołuje metodę prywatną w klasie w <xref:Microsoft.VisualStudio.Package.Source> celu uzyskania tokenu, który zawiera pożądaną pozycję, i przekazuje listę tokenów uzyskanych z <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metody.

5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda szuka flagi wyzwalacza tokena w odniesieniu <xref:Microsoft.VisualStudio.Package.TokenTriggers> do tokenu zwracanego z <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metody; oznacza to, że token reprezentuje nawias zamykający.

6. Jeśli <xref:Microsoft.VisualStudio.Package.TokenTriggers> zostanie znaleziona flaga wyzwalacza, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> wywoływana jest metoda w <xref:Microsoft.VisualStudio.Package.Source> klasie.

7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A>Metoda rozpoczyna operację analizowania z powodu wartości przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason> . Ta operacja ostatecznie wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie. Jeśli jest włączone analizowanie asynchroniczne, to wywołanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody odbywa się w wątku w tle.

8. Gdy operacja analizowania zostanie zakończona, wewnętrzna procedura obsługi uzupełniania (znana również jako metoda wywołania zwrotnego) nazywa `HandleMatchBracesResponse` się w <xref:Microsoft.VisualStudio.Package.Source> klasie. To wywołanie jest wykonywane automatycznie przez <xref:Microsoft.VisualStudio.Package.LanguageService> klasę bazową, a nie przez analizatora.

9. `HandleMatchBracesResponse`Metoda uzyskuje listę zakresów z <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu, który jest przechowywany w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekcie. (Zakres jest <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> strukturą, która określa zakres wierszy i znaków w pliku źródłowym). Ta lista zakresów obejmuje zazwyczaj dwa zakresy, jeden z nich dla otwierających i zamykających nawiasów klamrowych.

10. `HandleBracesResponse`Metoda wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodę dla <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu, który jest przechowywany w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekcie. Powoduje to wyróżnienie określonych zakresów.

11. Jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences> Właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> jest włączona, `HandleBracesResponse` metoda uzyskuje tekst obejmujący pasujący zakres i wyświetla pierwsze 80 znaków tego zakresu na pasku stanu. To działa najlepiej, jeśli <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda zawiera element języka, który towarzyszy pasującej parze. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> Właściwość.

12. Gotowe.

### <a name="summary"></a>Podsumowanie
 Operacje pasujących nawiasów klamrowych zwykle są ograniczone do prostych par elementów języka. Bardziej złożone elementy, takie jak Dopasowywanie potrójnych (" `if(...)` ", "" i "", "", `{` "" i " `}` `else` `{` `}` "), można podróżnić w ramach operacji uzupełniania wyrazów. Na przykład po zakończeniu słowa "" else " `if` można wyróżnić pasującą instrukcję" ". Jeśli wystąpiły serie `if` / `else if` instrukcji, wszystkie z nich można podróżnić przy użyciu tego samego mechanizmu, co pasujące nawiasy klamrowe. <xref:Microsoft.VisualStudio.Package.Source>Klasa bazowa jest już obsługiwana w następujący sposób: skaner musi zwrócić wartość wyzwalacza tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> połączonej z wartością wyzwalającą <xref:Microsoft.VisualStudio.Package.TokenTriggers> dla tokenu, który jest przed pozycją kursora.

 Aby uzyskać więcej informacji, zobacz [dopasowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analizowanie na potrzeby kolorowania
 Kolorowanie kodu źródłowego jest proste, po prostu Zidentyfikuj typ tokenu i zwróć informacje o kolorach tego typu. <xref:Microsoft.VisualStudio.Package.Colorizer>Klasa pełni rolę pośrednika między edytorem a skanerem, aby dostarczyć informacje o kolorach każdego tokenu. <xref:Microsoft.VisualStudio.Package.Colorizer>Klasa używa obiektu, <xref:Microsoft.VisualStudio.Package.IScanner> Aby ułatwić kolorowanie linii, a także zbierać informacje o stanie dla wszystkich wierszy w pliku źródłowym. W klasach usługi językowej MPF <xref:Microsoft.VisualStudio.Package.Colorizer> Klasa nie musi zostać zastąpiona, ponieważ komunikuje się z skanerem tylko za pomocą <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu. Należy podać obiekt implementujący <xref:Microsoft.VisualStudio.Package.IScanner> interfejs poprzez zastąpienie <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.

 Skaner uzyskuje <xref:Microsoft.VisualStudio.Package.IScanner> wiersz kodu źródłowego za pomocą <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metody. Wywołania <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metody są powtórzone w celu uzyskania następnego tokenu w wierszu do momentu wyczerpania wiersza tokenów. W przypadku kolorowania MPF traktuje cały kod źródłowy jako sekwencję wierszy. W związku z tym skaner musi być w stanie poradzić sobie ze źródłem, tak jak linie. Ponadto każda linia może być przenoszona do skanera w dowolnym momencie, a jedyną gwarancją jest, że skaner otrzymuje zmienną stanu z wiersza przed przeskanowaniem wiersza.

 <xref:Microsoft.VisualStudio.Package.Colorizer>Klasa jest również używana do identyfikowania wyzwalaczy tokenów. Te wyzwalacze informują MPF, że określony token może inicjować bardziej skomplikowaną operację, taką jak uzupełnianie wyrazów lub pasujące nawiasy klamrowe. Ponieważ takie wyzwalacze muszą być szybkie i muszą wystąpić w dowolnym miejscu, skaner jest najlepiej dostosowany do tego zadania.

 Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analizowanie funkcjonalności i zakresu
 Analizowanie funkcjonalności i zakresu wymaga większego nakładu pracy niż zidentyfikowanie typów tokenów, które są napotkane. Analizator ma identyfikować nie tylko typ tokenu, ale również funkcje, dla których token jest używany. Na przykład identyfikator jest tylko nazwą, ale w Twoim języku Identyfikator może być nazwą klasy, przestrzeni nazw, metody lub zmiennej, w zależności od kontekstu. Ogólny typ tokenu może być identyfikatorem, ale identyfikator może również mieć inne znaczenie, w zależności od tego, co jest i gdzie jest zdefiniowane. Ta identyfikacja wymaga, aby Analizator miał bardziej obszerną wiedzę o analizowanym języku. Jest to miejsce, w którym znajduje się <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasa. <xref:Microsoft.VisualStudio.Package.AuthoringSink>Klasa zbiera informacje o identyfikatorach, metodach, pasujących parach języka (takich jak nawiasy klamrowe i nawiasy) oraz potrójnie w języku (podobnie jak w przypadku par językowych, z wyjątkiem takich jak "" " `foreach()` `{` i" `}` "). Ponadto można przesłonić <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasę, aby obsługiwała identyfikację kodu, która jest używana podczas wczesnej walidacji punktów przerwania, tak aby debuger nie musiał być ładowany, oraz okno debugowanie **Automatyczne** , które wyświetla zmienne lokalne i parametry automatycznie, gdy program jest debugowany i wymaga analizatora do identyfikowania odpowiednich zmiennych lokalnych i parametrów oprócz tych, które są wyświetlane przez debuger.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Obiekt jest przesyłany do analizatora jako część <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu, a nowy <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiekt jest tworzony za każdym razem, gdy <xref:Microsoft.VisualStudio.Package.ParseRequest> tworzony jest nowy obiekt. Ponadto <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda musi zwracać <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiekt, który jest używany do obsługi różnych operacji IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Obiekt zachowuje listę deklaracji i listę metod, z których każdy jest wypełniony, w zależności od przyczyny analizy. <xref:Microsoft.VisualStudio.Package.AuthoringScope>Należy zaimplementować klasę.

## <a name="see-also"></a>Zobacz też
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
