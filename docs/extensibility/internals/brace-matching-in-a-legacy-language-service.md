---
title: Dopasowywanie nawiasów klamrowych w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0081be3e3ab5a53f7d85f77475d4288aa5c87092
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709816"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Dopasowywanie nawiasów klamrowych w starszej usłudze językowej
Dopasowywanie nawiasów klamrowych pomaga deweloperowi śledzić elementy języka, które muszą występować razem, takie jak nawiasy i nawiasy klamrowe. Gdy deweloper wprowadzi nawias zamykający, wyróżniony jest nawias otwierający.

 Można dopasować dwa lub trzy współnastępujące elementy, zwane parami i trójkami. Trójki to zestawy trzech współnastępujących elementów. Na przykład w języku `foreach` C#instrukcja `foreach()`tworzy `{`potrójną: , , i `}`. Wszystkie trzy elementy są podświetlane po wpisaniu nawiasu klamrowego.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementacji dopasowywania nawiasów klamrowych, zobacz [Przewodnik: Wyświetlanie pasujących nawiasów klamrowych](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

 Klasa <xref:Microsoft.VisualStudio.Package.AuthoringSink> obsługuje zarówno pary, jak <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> i <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> trójki z i metod.

## <a name="implementation"></a>Wdrażanie
 Usługa języka musi zidentyfikować wszystkie dopasowane elementy w języku, a następnie zlokalizować wszystkie pasujące pary. Jest to zazwyczaj realizowane przez <xref:Microsoft.VisualStudio.Package.IScanner> implementowanie do wykrywania dopasowanego języka, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> a następnie przy użyciu metody, aby dopasować elementy.

 Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> wywołuje skanera tokenize wiersza i zwraca token tuż przed caret. Skaner wskazuje, że para elementów języka została znaleziona <xref:Microsoft.VisualStudio.Package.TokenTriggers> przez ustawienie wartości wyzwalacza tokenu na bieżącym tokenie. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> wywołuje <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodę, która z <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> kolei wywołuje metodę z <xref:Microsoft.VisualStudio.Package.ParseReason> wartością przyczyny analizy, aby zlokalizować pasujący element języka. Po znalezieniu pasującego elementu języka oba elementy są wyróżnione.

 Aby uzyskać pełny opis sposobu wpisywania nawiasu klamrowego wyzwala wyróżnianie nawiasu klamrowego, zobacz przykładową *sekcję operacji analizy* w artykule [Starsza analizator usługi języka i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Włącz obsługę dopasowywania nawiasów klamrowych
 Atrybut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> można ustawić **MatchBraces**, **MatchBracesAtCaret**i **ShowMatchingBrace** wpisy rejestru, które <xref:Microsoft.VisualStudio.Package.LanguagePreferences> ustawiają odpowiednie właściwości klasy. Właściwości preferencji językowych mogą być również ustawiane przez użytkownika.

|Wpis rejestru|Właściwość|Opis|
|--------------------|--------------|-----------------|
|MatchBraces ( MatchBraces )|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Umożliwia dopasowywanie nawiasów klamrowych.|
|MatchBracesAtCaret ( MatchBracesAtCaret )|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Włącza dopasowywanie nawiasów klamrowych w miarę przenoszenia się cieczy.|
|ShowMatchingBrace (PokażMatchingBrace)|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Podświetla pasujący nawias klamrowy.|

## <a name="match-conditional-statements"></a>Dopasowywuj instrukcje warunkowe
 Można dopasować instrukcje warunkowe, `else`takie `#if`jak `#elif` `if` `#else`, `#endif` `else if`i , lub , , w taki sam sposób jak pasujące ograniczniki. Można podklasy <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy i podać metodę, która może dodawać zakresy tekstu, a także ograniczniki do wewnętrznej tablicy pasujących elementów.

## <a name="set-the-trigger"></a>Ustawianie wyzwalacza
 W poniższym przykładzie pokazano, jak wykryć pasujące nawiasy, nawiasy klamrowe i nawiasy klamrowe kwadratowe oraz ustawienie wyzwalacza dla niego w skanerze. Metoda <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> w <xref:Microsoft.VisualStudio.Package.Source> klasie wykrywa wyzwalacz i wywołuje analizatora, aby znaleźć pasującą parę (zobacz *sekcję Znajdowanie dopasowania* w tym artykule). Ten przykład służy wyłącznie do celów ilustracyjnych. Przyjęto założenie, że skaner `GetNextToken` zawiera metodę, która identyfikuje i zwraca tokeny z wiersza tekstu.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private const string braces = "()[]{}";
        private Lexer lex;

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar) && token.Length > 0)
                {
                    if (braces.IndexOf(firstChar) != -1)
                    {
                        tokenInfo.Trigger = TokenTriggers.MatchBraces;
                    }
                }
            }
            return foundToken;
        }
```

## <a name="match-the-braces"></a>Dopasuj nawiasy klamrowe
 Oto uproszczony przykład dopasowywania `{ }` `( )`elementów `[ ]`języka i , i <xref:Microsoft.VisualStudio.Package.AuthoringSink> dodawania ich zakresów do obiektu. Takie podejście nie jest zalecane podejście do analizowania kodu źródłowego; wyłącznie w celach ilustracyjnych.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class Parser
    {
         private IList<TextSpan[]> m_braces;
         public IList<TextSpan[]> Braces
         {
             get { return m_braces; }
         }
         private void AddMatchingBraces(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             if IsMatch(braceSpan1, braceSpan2)
                 m_braces.Add(new TextSpan[] { braceSpan1, braceSpan2 });
         }

         private bool IsMatch(TextSpan braceSpan1, TextSpan braceSpan2)
         {
             //definition for matching here
          }
    }

    public class TestLanguageService : LanguageService
    {
         Parser parser = new Parser();
         Source source = (Source) this.GetSource(req.FileName);

         private AuthoringScope ParseSource(ParseRequest req)
         {
             if (req.Sink.BraceMatching)
             {
                 if (req.Reason==ParseReason.MatchBraces)
                 {
                     foreach (TextSpan[] brace in parser.Braces)
                     {
                         req.Sink.MatchPair(brace[0], brace[1], 1);
                     }
                 }
             }
             return new TestAuthoringScope();
         }
    }
}
```

## <a name="see-also"></a>Zobacz też
- [Starsze funkcje usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Starsza usługa obsługi języka analizator i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
