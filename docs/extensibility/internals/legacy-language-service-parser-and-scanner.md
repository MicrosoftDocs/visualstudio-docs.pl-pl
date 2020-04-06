---
title: Starsza usługa językowa parser i skaner | Dokumenty firmy Microsoft
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
ms.openlocfilehash: c87f447a4b8bca804d27aae4967f4adaf389c627
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707314"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analizator i skaner starszej wersji usługi językowej
Analizator jest sercem usługi językowej. Klasy języka frameworka zarządzanego pakietu (MPF) wymagają analizatora języka, aby wybrać informacje o wyświetlanym kodzie. Analizator oddziela tekst do tokenów leksykalne, a następnie identyfikuje te tokeny według typu i funkcjonalności.

## <a name="discussion"></a>Dyskusji
 Poniżej znajduje się metoda języka C#:

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

 W tym przykładzie tokeny są słowa i znaki interpunkcyjne. Rodzaje tokenów są następujące.

|Nazwa tokenu|Typ tokenu|
|----------------|----------------|
|przestrzeni nazw, klasa, publiczny, nieważny, int|Słowa kluczowego|
|=|operator|
|{ } ( ) ;|ogranicznik|
|MyNamespace, MyClass, MyFunction, arg1, var1|identyfikator|
|Mynamespace|namespace|
|Myclass|class|
|Funkcja MyFunction|method|
|argument1|parametr|
|var1|zmienna lokalna|

 Rolą analizatora jest identyfikowanie tokenów. Niektóre tokeny mogą mieć więcej niż jeden typ. Po zidentyfikowaniu tokenów analizatora usługa języka może używać informacji w celu zapewnienia przydatnych funkcji, takich jak wyróżnianie składni, dopasowywanie nawiasów klamrowych i operacje IntelliSense.

## <a name="types-of-parsers"></a>Rodzaje parserów
 Analizator usługi języka nie jest taki sam jak analizator używany jako część kompilatora. Jednak tego rodzaju analizatora parser musi używać skanera i analizatora, w taki sam sposób jak analizator kompilatora.

- Skaner służy do identyfikowania typów tokenów. Te informacje są używane do wyróżniania składni i szybkiego identyfikowania typów tokenów, które mogą wyzwalać inne operacje, na przykład dopasowywanie nawiasów klamrowych. Ten skaner jest reprezentowany przez <xref:Microsoft.VisualStudio.Package.IScanner> interfejs.

- Analizator jest używany do opisywania funkcji i zakresu tokenów. Te informacje są używane w operacjach IntelliSense do identyfikowania elementów języka, takich jak metody, zmienne, parametry i deklaracje, a także do dostarczania list elementów członkowskich i podpisów metod na podstawie kontekstu. Ten analizator jest również używany do lokalizowania pasujących par elementów języka, takich jak nawiasy klamrowe i nawiasy. Ten analizator jest dostępny <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguageService> metody w klasie.

  Jak wdrożyć skaner i analizator dla usługi językowej zależy od Ciebie. Dostępnych jest kilka zasobów, które opisują, jak działają analizatory i jak napisać własny analizator. Ponadto, kilka darmowych i komercyjnych produktów są dostępne, które pomagają w tworzeniu analizatora.

### <a name="the-parsesource-parser"></a>Analizator parsesource
 W przeciwieństwie do analizatora, który jest używany jako część kompilatora (gdzie tokeny są konwertowane na jakąś formę kodu wykonywalnego), analizator usługi języka może być wywoływana z wielu różnych powodów i w wielu różnych kontekstach. Jak zaimplementować <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> to <xref:Microsoft.VisualStudio.Package.LanguageService> podejście w metodzie w klasie zależy od Ciebie. Ważne jest, aby pamiętać, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> że metoda może być wywoływana w wątku w tle.

> [!CAUTION]
> Struktura <xref:Microsoft.VisualStudio.Package.ParseRequest> zawiera odwołanie do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu. Ten <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiekt nie może być używany w wątku tła. W rzeczywistości wiele podstawowych klas MPF nie może być używany w wątku w tle. Należą do <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.ViewFilter>nich <xref:Microsoft.VisualStudio.Package.CodeWindowManager> , , klasy i inne klasy, które bezpośrednio lub pośrednio komunikuje się z widokiem.

 Ten analizator zazwyczaj analizuje cały plik źródłowy po raz pierwszy jest wywoływany lub <xref:Microsoft.VisualStudio.Package.ParseReason> gdy podano wartość przyczyny analizy. Kolejne wywołania <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody obsługują niewielką część analizowanego kodu i mogą być wykonywane znacznie szybciej przy użyciu wyników poprzedniej pełnej analizy operacji. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> komunikuje wyniki operacji analizowania za <xref:Microsoft.VisualStudio.Package.AuthoringSink> <xref:Microsoft.VisualStudio.Package.AuthoringScope> pośrednictwem i obiektów. Obiekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> jest używany do zbierania informacji dla określonego powodu analizy, na przykład informacje o zakresach pasujących nawiasów klamrowych lub podpisów metod, które mają listy parametrów. Zapewnia <xref:Microsoft.VisualStudio.Package.AuthoringScope> kolekcje deklaracji i podpisów metod, a także obsługę opcji Przejdź do edycji zaawansowanej **(Przejdź do definicji**, **Przejdź do deklaracji,** **Przejdź do odwołania).**

### <a name="the-iscanner-scanner"></a>Skaner IScanner
 Należy również zaimplementować <xref:Microsoft.VisualStudio.Package.IScanner>skaner, który implementuje . Jednak ponieważ ten skaner działa na podstawie wiersz po <xref:Microsoft.VisualStudio.Package.Colorizer> wierszu za pośrednictwem klasy, jest zazwyczaj łatwiejsze do zaimplementowania. Na początku każdego wiersza MPF <xref:Microsoft.VisualStudio.Package.Colorizer> daje klasy wartość do użycia jako zmiennej stanu, który jest przekazywany do skanera. Na końcu każdego wiersza skaner zwraca zaktualizowaną zmienną stanu. MPF buforuje te informacje o stanie dla każdego wiersza, dzięki czemu skaner może rozpocząć analizowanie z dowolnego wiersza bez konieczności uruchamiania na początku pliku źródłowego. To szybkie skanowanie pojedynczej linii pozwala edytorowi na szybkie przekazywanie informacji zwrotnych do użytkownika.

## <a name="parsing-for-matching-braces"></a>Analizowanie pasujących nawiasów klamrowych
 W tym przykładzie pokazano przepływ kontroli dopasowywania nawiasu klamrowego zamknięcia, który użytkownik wpisał. W tym procesie skaner, który jest używany do kolorowania jest również używany do określenia typu tokenu i czy token może wyzwolić operację dopasowania nawiasu klamrowego. Jeśli wyzwalacz zostanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> znaleziony, metoda jest wywoływana, aby znaleźć pasujące nawiasy klamrowe. Na koniec dwa nawiasy klamrowe są podświetlone.

 Mimo że nawiasy klamrowe są używane w nazwach wyzwalaczy i przyczyn analizy, proces ten nie jest ograniczony do rzeczywistych nawiasów klamrowych. Każda para znaków, która jest określona jako pasująca para jest obsługiwana. Przykłady obejmują ( \< i ) i >, i [ i ].

 Załóżmy, że usługa języka obsługuje pasujące nawiasy klamrowe.

1. Użytkownik wpisuje zamykający nawias klamrowy (}).

2. Nawias klamrowy jest wstawiany kursorem w pliku źródłowym, a kursor jest zaawansowany o jeden.

3. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> w <xref:Microsoft.VisualStudio.Package.Source> klasie jest wywoływana z wpisanym nawiasem klamrowym zamknięcia.

4. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> wywołuje <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metodę w <xref:Microsoft.VisualStudio.Package.Source> klasie, aby uzyskać token w pozycji tuż przed bieżącą pozycję kursora. Ten token odpowiada wpisanego nawiasu klamrowego zamykającego).

    1. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> wywołuje <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metodę na <xref:Microsoft.VisualStudio.Package.Colorizer> obiekcie, aby uzyskać wszystkie tokeny w bieżącym wierszu.

    2. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> wywołuje <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metodę na <xref:Microsoft.VisualStudio.Package.IScanner> obiekcie z tekstem bieżącego wiersza.

    3. Metoda <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> wielokrotnie wywołuje <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metodę na <xref:Microsoft.VisualStudio.Package.IScanner> obiekcie, aby zebrać wszystkie tokeny z bieżącego wiersza.

    4. Metoda <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> wywołuje metodę prywatną <xref:Microsoft.VisualStudio.Package.Source> w klasie, aby uzyskać token, który zawiera żądaną pozycję <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> i przekazuje na liście tokenów uzyskanych z metody.

5. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> wyszukuje flagę <xref:Microsoft.VisualStudio.Package.TokenTriggers> wyzwalacza tokenu na <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> tokenie, który jest zwracany z metody; oznacza to, że token, który reprezentuje nawias klamrowy zamknięcia).

6. Jeśli zostanie znaleziona <xref:Microsoft.VisualStudio.Package.TokenTriggers> flaga <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> wyzwalacza, wywoływana jest metoda w <xref:Microsoft.VisualStudio.Package.Source> klasie.

7. Metoda <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> rozpoczyna operację analizy z wartością przyczyny analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Ta operacja ostatecznie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService> metodę w klasie. Jeśli analizowanie asynchroniczne jest włączone, to <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wywołanie metody występuje w wątku w tle.

8. Po zakończeniu analizy operacja wewnętrznej obsługi zakończenia (znany również jako metoda `HandleMatchBracesResponse` wywołania zwrotnego) o nazwie jest wywoływana w <xref:Microsoft.VisualStudio.Package.Source> klasie. To wywołanie jest automatycznie <xref:Microsoft.VisualStudio.Package.LanguageService> dokonywane przez klasę podstawową, a nie przez analizatora.

9. Metoda `HandleMatchBracesResponse` uzyskuje listę zakresów z <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu, który jest <xref:Microsoft.VisualStudio.Package.ParseRequest> przechowywany w obiekcie. (Zakres to <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> struktura określająca zakres linii i znaków w pliku źródłowym). Ta lista zakresów zazwyczaj zawiera dwa zakresy, po jednym dla nawiasów klamrowych otwierania i zamykania.

10. Metoda `HandleBracesResponse` wywołuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metodę na <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiekcie, który <xref:Microsoft.VisualStudio.Package.ParseRequest> jest przechowywany w obiekcie. To podkreśla podane przęsła.

11. Jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> jest włączona, `HandleBracesResponse` metoda uzyskuje tekst, który jest objęty pasującym zakresem i wyświetla pierwsze 80 znaków tego zakresu na pasku stanu. To działa najlepiej, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> jeśli metoda zawiera element języka, który towarzyszy pasującej pary. Aby uzyskać więcej <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> informacji, zobacz właściwość.

12. Gotowe.

### <a name="summary"></a>Podsumowanie
 Pasujące działanie nawiasów klamrowych jest zazwyczaj ograniczona do prostych par elementów języka. Bardziej złożone elementy, takie jak`if(...)`pasujące`{`trójki`}`("`else`",`{`"`}`i " ", lub " ", " i " "), mogą być podświetlane w ramach operacji uzupełniania wyrazów. Na przykład po zakończeniu słowa "else" można`if`wyróżnić pasujące instrukcje " ".For example, when the "else" word is finished, the matching " " statement can be highlighted. Jeśli istnieje seria `if` / `else if` instrukcji, wszystkie z nich mogą być wyróżnione przy użyciu tego samego mechanizmu jako pasujące nawiasy klamrowe. Klasa <xref:Microsoft.VisualStudio.Package.Source> podstawowa już obsługuje to, w następujący sposób: <xref:Microsoft.VisualStudio.Package.TokenTriggers> Skaner musi <xref:Microsoft.VisualStudio.Package.TokenTriggers> zwracać wartość wyzwalacza tokenu w połączeniu z wartością wyzwalacza dla tokenu, który znajduje się przed położeniem kursora.

 Aby uzyskać więcej informacji, zobacz [Dopasowywanie nawiasów klamrowych w starszej usłudze językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).

## <a name="parsing-for-colorization"></a>Analizowanie kolorowania
 Kolorowanie kodu źródłowego jest proste, wystarczy zidentyfikować typ tokenu i zwrócić informacje o kolorze tego typu. Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> działa jako pośrednik między edytorem a skanerem, aby zapewnić informacje o kolorze dla każdego tokenu. Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> używa obiektu, <xref:Microsoft.VisualStudio.Package.IScanner> aby pomóc w kolorowanie linii, a także do zbierania informacji o stanie dla wszystkich wierszy w pliku źródłowym. W klasach usługi języka <xref:Microsoft.VisualStudio.Package.Colorizer> MPF klasa nie musi być zastąpiona, ponieważ komunikuje się ze skanerem tylko za pośrednictwem <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu. Podać obiekt, który implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejs, zastępując <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodę <xref:Microsoft.VisualStudio.Package.LanguageService> w klasie.

 Skaner <xref:Microsoft.VisualStudio.Package.IScanner> otrzymuje linię kodu źródłowego <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> za pomocą metody. Wywołania <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metody są powtarzane w celu uzyskania następnego tokenu w wierszu, dopóki wiersz nie zostanie wyczerpany tokenów. Do koloryzacji MPF traktuje cały kod źródłowy jako sekwencję wierszy. Dlatego skaner musi być w stanie poradzić sobie ze źródłem pochodzącym na niego jako linie. Ponadto dowolna linia może być przekazywana do skanera w dowolnym momencie, a jedyną gwarancją jest to, że skaner odbiera zmienną stanu z linii przed wierszem, który ma zostać zeskanowany.

 Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> jest również używana do identyfikowania wyzwalaczy tokenu. Te wyzwalacze powiedzieć MPF, że określony token może zainicjować bardziej złożoną operację, takich jak uzupełnianie wyrazów lub pasujące nawiasy klamrowe. Ponieważ identyfikowanie takich wyzwalaczy musi być szybkie i musi wystąpić w dowolnym miejscu, skaner najlepiej nadaje się do tego zadania.

 Aby uzyskać więcej informacji, zobacz [Kolorowanie składni w starszej usłudze językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).

## <a name="parsing-for-functionality-and-scope"></a>Analizowanie funkcjonalności i zakresu
 Analizowanie funkcjonalności i zakresu wymaga więcej wysiłku niż tylko identyfikowanie typów tokenów, które występują. Analizator musi zidentyfikować nie tylko typ tokenu, ale także funkcje, dla których jest używany token. Na przykład identyfikator to tylko nazwa, ale w twoim języku identyfikator może być nazwą klasy, obszaru nazw, metody lub zmiennej, w zależności od kontekstu. Ogólny typ tokenu może być identyfikatorem, ale identyfikator może mieć również inne znaczenie, w zależności od tego, co jest i gdzie jest zdefiniowany. Ta identyfikacja wymaga analizatora mieć bardziej obszerną wiedzę na temat języka, który jest analizowany. W tym <xref:Microsoft.VisualStudio.Package.AuthoringSink> miejscu pojawia się klasa. Klasa <xref:Microsoft.VisualStudio.Package.AuthoringSink> zbiera informacje o identyfikatorach, metodach, pasujących parach językowych (takich jak nawiasy klamrowe i nawiasy) oraz trójkach`foreach()`języka`{`(podobnych`}`do par językowych, z tą różnicą, że istnieją trzy części, na przykład " " " i " "). Ponadto można zastąpić <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy do obsługi identyfikacji kodu, który jest używany we wczesnych sprawdzania poprawności punktów przerwania, tak aby debuger nie musi być ładowany i auto **debugowania** okna, który pokazuje zmienne lokalne i parametry automatycznie, gdy program jest debugowany i wymaga analizatora do identyfikowania odpowiednich zmiennych lokalnych i parametrów oprócz tych, które debuger prezentuje.

 Obiekt <xref:Microsoft.VisualStudio.Package.AuthoringSink> jest przekazywany do analizatora <xref:Microsoft.VisualStudio.Package.ParseRequest> jako część <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu, a nowy obiekt <xref:Microsoft.VisualStudio.Package.ParseRequest> jest tworzony za każdym razem, gdy tworzony jest nowy obiekt. Ponadto <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda musi zwracać <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiekt, który jest używany do obsługi różnych operacji IntelliSense. Obiekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> przechowuje listę deklaracji i listę metod, z których każda jest wypełniona, w zależności od przyczyny analizy. Klasa <xref:Microsoft.VisualStudio.Package.AuthoringScope> musi zostać zaimplementowana.

## <a name="see-also"></a>Zobacz też
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)
- [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)
- [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
