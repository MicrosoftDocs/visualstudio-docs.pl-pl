---
title: Dopasowywanie nawiasów klamrowych w starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się więcej na temat dopasowywania nawiasów klamrowych w starszej wersji usługi językowej, która ułatwia śledzenie elementów języka, które muszą występować razem, takich jak nawiasy i nawiasy klamrowe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a92a3ca34e6314463bbfecbd8c4236789f213635
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086108"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Dopasowywanie nawiasów klamrowych w starszej wersji usługi językowej
Dopasowywanie nawiasów klamrowych pomaga elementom języka śledzenia dla deweloperów, które muszą występować razem, takich jak nawiasy i nawiasy klamrowe. Gdy programista wprowadzi zamykający nawias klamrowy, otwierający nawias klamrowy zostanie wyróżniony.

 Można dopasować dwa lub trzy elementy wspólne, nazywane parami i potrójną. Potrójne są zestawami trzech elementów współpracujących. Na przykład w języku C# `foreach` instrukcja tworzy trzy: `foreach()` , `{` , i `}` . Wszystkie trzy elementy są podświetlane po wpisaniu zamykającego nawiasu klamrowego.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej o nowym sposobie implementowania dopasowywania nawiasów klamrowych, zobacz [Przewodnik: wyświetlanie pasujących nawiasów klamrowych](../../extensibility/walkthrough-displaying-matching-braces.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

 <xref:Microsoft.VisualStudio.Package.AuthoringSink>Klasa obsługuje obie pary i trzykrotnie przy użyciu <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> metod i <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> .

## <a name="implementation"></a>Implementacja
 Usługa językowa musi identyfikować wszystkie dopasowane elementy w języku, a następnie lokalizować wszystkie zgodne pary. Jest to zazwyczaj realizowane przez implementację <xref:Microsoft.VisualStudio.Package.IScanner> w celu wykrycia dopasowanego języka, a następnie zastosowania <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody do dopasowania do elementów.

 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda wywołuje skaner, aby tokenize wiersz i zwracać token tuż przed karetką. Skaner wskazuje, że para elementów języka została znaleziona przez ustawienie wartości wyzwalacza tokenu <xref:Microsoft.VisualStudio.Package.TokenTriggers> dla bieżącego tokenu. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda wywołuje <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodę, która z kolei wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metodę z wartością przyczyny analizy, <xref:Microsoft.VisualStudio.Package.ParseReason> Aby zlokalizować pasujący element języka. Gdy zostanie znaleziony pasujący element języka, oba elementy są wyróżnione.

 Pełny opis sposobu pisania nawiasów klamrowych wyzwala wyróżnianie nawiasów klamrowych, zapoznaj się z sekcją *Przykładowa operacja analizy* w artykule [Starsza wersja programu Service parser i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).

## <a name="enable-support-for-brace-matching"></a>Włącz obsługę dopasowania nawiasów klamrowych
 Ten <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybut może ustawiać wpisy rejestru **MatchBraces**, **MatchBracesAtCaret** i **ShowMatchingBrace** , które ustawiają odpowiednie właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Właściwości preferencji języka mogą być również ustawiane przez użytkownika.

|Wpis rejestru|Właściwość|Opis|
|--------------------|--------------|-----------------|
|MatchBraces|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Włącza Dopasowywanie nawiasów klamrowych.|
|MatchBracesAtCaret|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Włącza Dopasowywanie nawiasów klamrowych w miarę przesuwania karetki.|
|ShowMatchingBrace|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Podświetla pasujący nawias klamrowy.|

## <a name="match-conditional-statements"></a>Dopasuj instrukcje warunkowe
 Można dopasować instrukcje warunkowe, takie jak `if` , `else if` , i `else` , lub `#if` ,,, `#elif` w taki `#else` `#endif` sam sposób jak ograniczniki. Można podtworzyć podklasę <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy i udostępnić metodę, która może dodawać zakresy tekstu, a także ograniczniki do wewnętrznej tablicy pasujących elementów.

## <a name="set-the-trigger"></a>Ustawianie wyzwalacza
 Poniższy przykład pokazuje, jak wykrywać pasujące nawiasy, nawiasy klamrowe i kwadratowe nawiasy klamrowe oraz ustawić wyzwalacz dla niego w skanerze. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A>Metoda <xref:Microsoft.VisualStudio.Package.Source> klasy wykrywa wyzwalacz i wywołuje parser, aby znaleźć pasującą parę (zobacz sekcję *Znajdowanie dopasowania* w tym artykule). Ten przykład służy tylko do celów informacyjnych. Przyjęto założenie, że skaner zawiera metodę `GetNextToken` , która identyfikuje i zwraca tokeny z wiersza tekstu.

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

## <a name="match-the-braces"></a>Dopasowuje nawiasy klamrowe
 Poniżej przedstawiono uproszczony przykład dopasowywania elementów języka `{ }` , `( )` i i `[ ]` dodawania ich zakresów do <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu. Takie podejście nie jest zalecanym podejściem do analizowania kodu źródłowego; jest to tylko do celów informacyjnych.

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
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Analizator i skaner starszej usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
