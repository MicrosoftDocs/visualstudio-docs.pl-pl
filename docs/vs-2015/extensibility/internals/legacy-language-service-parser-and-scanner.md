---
title: Starszego języka usługi analizator i skaner | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- parsers, language services [managed package framework]
- language services [managed package framework], Parsers
ms.assetid: 1ac3de27-a23b-438d-9593-389e45839cfa
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1db922974c587cdeadc131d17c44cbab4b49af0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60048544"
---
# <a name="legacy-language-service-parser-and-scanner"></a>Analizator i skaner starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Analizator jest niezwykle usługi języka. Klasy języka zarządzanego pakietu Framework (MPF) wymagają analizatora języka, aby wybrać informacje związane z kodem są wyświetlane. Analizator składni dzieli tekst na tokeny leksykalne, a następnie identyfikuje tych tokenów według typu i funkcje.  
  
## <a name="discussion"></a>Dyskusja  
 Poniżej przedstawiono metodę języka C#.  
  
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
  
 W tym przykładzie tokeny są wyrazy i znaków interpunkcyjnych. Dostępne są następujące typy tokenów.  
  
|Nazwa tokenu|Typ tokenu|  
|----------------|----------------|  
|przestrzeń nazw, klasy, publiczna, void "," int|Słowo kluczowe|  
|=|operator|  
|{ } ( ) ;|Ogranicznik|  
|MyNamespace MyClass, MyFunction, arg1, var1|identyfikator|  
|MyNamespace|— przestrzeń nazw|  
|MyClass|class|  
|MyFunction|— metoda|  
|arg1|parametr|  
|var1|Zmienna lokalna|  
  
 Rola Analizator jest do identyfikowania tokenów. Niektóre tokeny może mieć więcej niż jednego typu. Po analizator zidentyfikowała tokenów, usługa językowa użyć informacji, aby zapewnić przydatne funkcje, takie jak wyróżnianie składni, dopasowywanie nawiasów i operacje IntelliSense.  
  
## <a name="types-of-parsers"></a>Typy analizatory składni  
 Analizatora usługa języka nie jest taka sama jak analizator używany jako część kompilatora. Jednak tego rodzaju analizator musi używać analizator i skaner w taki sam sposób jak analizatora kompilator.  
  
- Skaner służy do identyfikowania typy tokenów. Te informacje są używane, wyróżnianie składni i szybko zidentyfikować typy tokenów, które mogą wyzwalać inne operacje, na przykład, parowanie nawiasów klamrowych. Ten skaner jest reprezentowany przez <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu.  
  
- Analizator jest używany do opisu funkcji i zakresu tokenów. Te informacje jest używany w funkcji IntelliSense, operacjach, aby zidentyfikować elementy języka, takich jak metody, zmiennych, parametrów i deklaracji i zawierają listy elementów członkowskich i podpisy metod na podstawie kontekstu. Ten parser również jest używana do lokalizowania pasujących par elementu języka, takich jak nawiasy i nawiasy. Ten parser odbywa się za pośrednictwem <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.  
  
  Sposób implementacji skanera i analizatora dla usługi w języka zależy od użytkownika. Dostępnych jest kilka zasobów opisujące, jak działają analizatory i jak napisać własny analizator składni. Ponadto są dostępne kilka produktów bezpłatne i komercyjne to pomoże w tworzeniu analizatora składni.  
  
### <a name="the-parsesource-parser"></a>Analizator ParseSource  
 W przeciwieństwie do analizatora, która jest używana jako część kompilatora (gdzie tokeny są konwertowane na jakiegoś kodu wykonywalnego) analizatora usług języka może być wywoływana wiele różnych powodów i w wielu różnych kontekstach. Jak zaimplementować to podejście w <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy zależy od użytkownika. Ważne jest, aby pamiętać, że <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda może być wywoływana w wątku tła.  
  
> [!CAUTION]
>  <xref:Microsoft.VisualStudio.Package.ParseRequest> Struktura zawiera odwołanie do <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu. To <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiektu nie można używać w wątku w tle. W rzeczywistości wielu klas bazowych MPF nie można używać w wątku w tle. Obejmują one <xref:Microsoft.VisualStudio.Package.Source>, <xref:Microsoft.VisualStudio.Package.ViewFilter>, <xref:Microsoft.VisualStudio.Package.CodeWindowManager> klasy i inne klasy, który bezpośrednio lub pośrednio komunikuje się z widoku.  
  
 Ten parser zazwyczaj analizuje czas pliku pierwszy całego źródła, jest on nazywany lub podczas analizy przyczyny wartość <xref:Microsoft.VisualStudio.Package.ParseReason> otrzymuje. Kolejne wywołania <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody obsługi niewielką część przeanalizowany kodu i mogą być wykonywane szybciej przy użyciu wyników poprzedniej operacji pełnej analizy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda komunikuje się wyniki operacji analizowania za pośrednictwem <xref:Microsoft.VisualStudio.Package.AuthoringSink> i <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektów. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Obiekt jest używany do zbierania informacji z określonego powodu analizy, na przykład informacje o zakresy dopasowywanie nawiasów zwykłych lub podpisy metody, które ma listy parametrów. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Zawiera kolekcje deklaracje i podpisy metod oraz pomocy technicznej przejdź do zaawansowanej edycji opcji (**przejdź do definicji**, **przejdź do deklaracji**, **przejdź do Odwołanie**).  
  
### <a name="the-iscanner-scanner"></a>Skaner IScanner  
 Należy także zaimplementować skanera, który implementuje <xref:Microsoft.VisualStudio.Package.IScanner>. Jednakże ponieważ ten skaner działa na zasadzie wiersz po wierszu za pomocą <xref:Microsoft.VisualStudio.Package.Colorizer> klasy, jest zazwyczaj łatwiejsze do wdrożenia. Na początku każdego wiersza, zapewnia MPF <xref:Microsoft.VisualStudio.Package.Colorizer> klasy wartości do użycia jako zmiennej stanu, który jest przekazywany do skanera. Na końcu każdego wiersza skaner zwraca zmienną zaktualizowany stan. MPF buforuje tych informacji o stanie dla każdego wiersza, tak, aby uruchomić skanera analizy z każdego wiersza bez konieczności uruchamiania na początku pliku źródłowego. Szybkie skanowanie jednowierszowym umożliwia szybkie opinii użytkownika w edytorze.  
  
## <a name="parsing-for-matching-braces"></a>Analiza kodu dla dopasowywanie nawiasów klamrowych  
 Ten przykład przedstawia przepływ sterowania do dopasowania zamykającego nawiasu klamrowego, wpisany przez użytkownika. W ramach tego procesu skanera, który jest używany do kolorowania umożliwia również określanie typu tokenu i tego, czy token można wyzwolić operacji nawias klamrowy dopasowania. Jeśli wyzwalacz zostanie znaleziony, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda jest wywoływana w celu znalezienia pasującego nawiasu klamrowego. Na koniec dwa nawiasy klamrowe są wyróżnione.  
  
 Mimo że nawiasy klamrowe są używane w nazwach wyzwalaczy i analizować przyczyny, ten proces nie jest ograniczona do rzeczywistego nawiasów klamrowych. Pary znaków, który jest określony jako pasującą parę jest obsługiwane. Przykłady obejmują (a) \< i >, a [i].  
  
 Załóżmy, że usługa językowa obsługuje pasujące nawiasy klamrowe.  
  
1. Użytkownik wpisuje zamykający nawias klamrowy (}).  
  
2. Nawiasów klamrowych jest wstawiana w lokalizacji kursora w pliku źródłowym i kursora jest zaawansowany o jeden.  
  
3. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Method in Class metoda <xref:Microsoft.VisualStudio.Package.Source> klasy jest wywoływana z kontrolą typów zamykającego nawiasu klamrowego.  
  
4. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.Source> klasy w celu uzyskania tokenu w położeniu tuż przed aktualną pozycją kursora. Ten token odnosi się do typizowanych zamykający nawias klamrowy).  
  
    1. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metody <xref:Microsoft.VisualStudio.Package.Colorizer> obiektu, aby uzyskać wszystkie tokeny w bieżącym wierszu.  
  
    2. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metody <xref:Microsoft.VisualStudio.Package.IScanner> obiekt z tekstem bieżącego wiersza.  
  
    3. <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> Wielokrotnie wywołuje metodę <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metody <xref:Microsoft.VisualStudio.Package.IScanner> obiektu, aby zebrać wszystkie tokeny z bieżącego wiersza.  
  
    4. <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> Metoda wywołuje metodę prywatnej <xref:Microsoft.VisualStudio.Package.Source> klasy do uzyskania tokenu, który zawiera żądanej pozycji, a następnie przekazuje na liście tokenów uzyskany z <xref:Microsoft.VisualStudio.Package.Colorizer.GetLineInfo%2A> metody.  
  
5. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metoda szuka Flaga tokenów wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> na token, który jest zwracany z <xref:Microsoft.VisualStudio.Package.Source.GetTokenInfo%2A> metody; oznacza to, że token, który reprezentuje zamykający nawias klamrowy).  
  
6. Jeśli wyzwalacz flagę <xref:Microsoft.VisualStudio.Package.TokenTriggers> zostanie znaleziony, <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.Source> nosi nazwę klasy.  
  
7. <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> Metoda zaczyna się od operacji analizowania wartości Przyczyna analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Ta operacja ostatecznie wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Jeśli włączono asynchroniczną analizy to wywołanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda występuje w wątku tła.  
  
8. Po zakończeniu operacji analizowania, wewnętrznej procedury obsługi zakończenia (znany także jako metoda wywołania zwrotnego) o nazwie `HandleMatchBracesResponse` jest wywoływana w <xref:Microsoft.VisualStudio.Package.Source> klasy. To wywołanie jest wykonywane automatycznie przez <xref:Microsoft.VisualStudio.Package.LanguageService> podstawowej klasy, nie przez analizator.  
  
9. `HandleMatchBracesResponse` Metoda uzyskuje listę zakresów z <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiekt, który jest przechowywany w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu. (Zakres jest <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> strukturę, która określa zakres wierszy i znaków w pliku źródłowym.) Ta lista zakresy zazwyczaj zawiera dwa zakresy, jeden dla otwierające i zamykające nawiasy klamrowe.  
  
10. `HandleBracesResponse` Wywołania metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> metody <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> obiekt, który jest przechowywany w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiektu. Spowoduje to wyróżnienie danego zakresy.  
  
11. Jeśli <xref:Microsoft.VisualStudio.Package.LanguagePreferences> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> jest włączona, `HandleBracesResponse` metoda uzyskuje tekst, który jest objęty przez zakres dopasowania i wyświetla 80 pierwszych znaków ten zakres na pasku stanu. To działa najlepiej, gdy <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda zawiera element języka, który towarzyszy pasującą parę. Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A> właściwości.  
  
12. Gotowe.  
  
### <a name="summary"></a>Podsumowanie  
 Operacji dopasowywania nawiasów klamrowych jest zazwyczaj ograniczone do prostych pary elementów języka. Bardziej złożone elementy, takie jak dopasowanie trójek ("`if(…)`","`{`"i"`}`", lub "`else`","`{`"i"`}`"), może być wyróżniony jako część operacji dokończenie wyrazu. Na przykład po zakończeniu słowo "else", dopasowywania "`if`" może być wyróżniony instrukcji. Gdyby szereg `if` / `else if` instrukcji, wszystkie z nich może być wyróżniony za pomocą tego samego mechanizmu jako dopasowywanie nawiasów klamrowych. <xref:Microsoft.VisualStudio.Package.Source> Klasa bazowa już obsługuje tę funkcję, w następujący sposób: Skaner musi zwracać wartość tokenów wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> połączeniu z wartością wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> dla tokenu przed pozycja kursora.  
  
 Aby uzyskać więcej informacji, zobacz [parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-colorization"></a>Podczas analizowania kolorowania  
 Kolorowanie kodu źródłowego jest bardzo proste, należy po prostu zidentyfikować typ koloru tokenu i zwracają informacje o danym typie. <xref:Microsoft.VisualStudio.Package.Colorizer> Klasa działa jako pośrednik między edytora i skaner w celu zapewnienia kolor informacji na temat każdy token. <xref:Microsoft.VisualStudio.Package.Colorizer> Klasy używa <xref:Microsoft.VisualStudio.Package.IScanner> obiektu, aby pomóc w kolorowanie linię, a także do zbierania informacji o stanie dla wszystkich wierszy w pliku źródłowym. W klasach usługi języka MPF <xref:Microsoft.VisualStudio.Package.Colorizer> klasa nie ma zostać przesłoniona, ponieważ jego komunikuje się za pomocą skanera usługi tylko za pośrednictwem <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu. Podaj obiekt, który implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu przez zastąpienie <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody <xref:Microsoft.VisualStudio.Package.LanguageService> klasy.  
  
 <xref:Microsoft.VisualStudio.Package.IScanner> Skanera otrzymuje wiersza kodu źródłowego za pomocą <xref:Microsoft.VisualStudio.Package.IScanner.SetSource%2A> metody. Wywołania <xref:Microsoft.VisualStudio.Package.IScanner.ScanTokenAndProvideInfoAboutIt%2A> metoda powtarzają się uzyskać następnego tokenu, w wierszu wyczerpania wiersz tokenów. Kolorowania MPF traktuje każdy kod źródłowy jako sekwencja wierszy. W związku z tym skaner musi mieć możliwość poradzić sobie ze źródłem pochodzące go jako wiersze. Ponadto wiersza mogą być przekazywane do skanera w dowolnym momencie, a jedyną gwarancją jest to, że skaner otrzyma zmiennej stanu z wiersza przed wierszem o do przeskanowania.  
  
 <xref:Microsoft.VisualStudio.Package.Colorizer> Klasa również służy do identyfikowania tokenu wyzwalaczy. Te wyzwalacze Poinformuj MPF, że dany token może zainicjować bardziej złożonych operacji, takich jak uzupełnianie wyrazów lub pasujące nawiasy klamrowe. Ponieważ identyfikowanie tych wyzwalaczy muszą być szybkie i musi wystąpić w dowolnym miejscu, skaner jest najbardziej odpowiednia dla tego zadania.  
  
 Aby uzyskać więcej informacji, zobacz [kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md).  
  
## <a name="parsing-for-functionality-and-scope"></a>Analiza kodu dla funkcji i zakresu  
 Podczas analizowania funkcjonalności i zakres wymaga więcej niż tylko identyfikacji typów tokenów, które zostaną napotkane. Analizator musi zidentyfikować nie tylko typ tokenu, ale także funkcje, dla którego token jest używany. Na przykład identyfikator jest po prostu nazwy, ale w Twoim języku odpowiadającym może być nazwa klasy, przestrzeni nazw, metody lub zmienną, w zależności od kontekstu. Ogólny typ tokenu może być identyfikator, ale identyfikator mogą także mieć inne znaczenie w zależności od tego, co to jest i w którym jest zdefiniowana. Ten identyfikator wymaga analizatora, które mają bardziej rozległe wiedzę na temat języka, które są analizowane. Jest to miejsce <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy pochodzą. <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasy zbiera informacje na temat identyfikatorów, metody, pasujących par języka (na przykład i nawiasów klamrowych) i trójek języka (podobne do kierunki, z tą różnicą, że istnieją trzy części, na przykład "`foreach()`" "`{`"i"`}`"). Ponadto, możesz zastąpić <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy do obsługi identyfikacji kodu, który jest używany w weryfikacji wczesnych punktów przerwania, tak, aby debuger musi być załadowany, oraz **Autos** debugowania okno, które przedstawia lokalnych zmienne i parametry automatycznie kiedy program jest debugowany i wymaga analizatora składni, aby zidentyfikować odpowiednie zmienne lokalne i parametry oprócz tych, które prezentują debugera.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Obiekt jest przekazywany do analizatora jako część <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt i nową <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiekt jest utworzony każdym razem, gdy nowy <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt zostanie utworzony. Ponadto <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metoda musi zwracać <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu, który jest używany do obsługi różnych operacji IntelliSense. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Obiekt utrzymuje listę dla deklaracji i listy dla metod, albo Kolekcja została wypełniona, w zależności od przyczyny do analizy. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Klasy należy zaimplementować.  
  
## <a name="see-also"></a>Zobacz też  
 [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Omówienie usługi starszego języka](../../extensibility/internals/legacy-language-service-overview.md)   
 [Kolorowanie składni w starszej wersji usługi językowej](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)   
 [Parowanie nawiasów klamrowych w starszej wersji usługi językowej](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)
