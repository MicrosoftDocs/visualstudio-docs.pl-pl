---
title: Parowanie nawiasów klamrowych w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- brace matching
- language services [managed package framework], brace matching
ms.assetid: 4e3d0a70-f22f-49dd-92d8-edf48ab62b52
caps.latest.revision: 28
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 70ad3062a4cbbce8ef46c3afe8851382949fe3f3
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51753211"
---
# <a name="brace-matching-in-a-legacy-language-service"></a>Parowanie nawiasów klamrowych w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Parowanie nawiasów klamrowych pomaga dla deweloperów, śledzenie elementów języka, które muszą zostać wykonane ze sobą, takich jak nawiasy i nawiasy klamrowe. Gdy deweloper wprowadza zamykającego nawiasu klamrowego, jest wyróżniona otwierający nawias klamrowy.  
  
 Można dopasować do dwóch lub trzech elementów występujących w tej samej, o nazwie pary i trójek. Trójek to zestawy trzech elementów występujących w tej samej. Na przykład w języku C# `foreach` instrukcji formularzy triple: "`foreach()`","`{`", a "`}`". Wszystkie trzy elementy wyróżniono po wpisaniu zamykającego nawiasu klamrowego.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej na temat nowych sposobem realizowania parowanie nawiasów klamrowych, zobacz [wskazówki: wyświetlanie Parowanych nawiasów klamrowych](../../extensibility/walkthrough-displaying-matching-braces.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
 <xref:Microsoft.VisualStudio.Package.AuthoringSink> Klasa obsługuje pary i triples z <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchPair%2A> i <xref:Microsoft.VisualStudio.Package.AuthoringSink.MatchTriple%2A> metody.  
  
## <a name="implementation"></a>Implementacja  
 Usługa językowa musi zidentyfikować wszystkie dopasowane elementy w języku, a następnie Znajdź wszystkie pary dopasowania. Zazwyczaj jest to osiągane przez zaimplementowanie <xref:Microsoft.VisualStudio.Package.IScanner> wykryć język dopasowane, a następnie za pomocą <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodę, aby dopasować elementy.  
  
 <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metoda wywołuje skanera tokenizację wiersz do zwracania tokenu tuż przed karetką. Skaner wskazuje znaleziono pary elementów języka, ustawiając wartość tokenów wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> na bieżący token. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Wywołania metody <xref:Microsoft.VisualStudio.Package.Source.MatchBraces%2A> metodę, która z kolei wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.BeginParse%2A> metody z analizy wartość Przyczyna <xref:Microsoft.VisualStudio.Package.ParseReason> zlokalizować pasujący element języka. Gdy zostanie znaleziony pasujący element języka, oba te elementy są wyróżnione.  
  
 Aby uzyskać pełny opis sposobu pisania nawiasu klamrowego wyzwala wyróżnianie nawiasów klamrowych, zobacz sekcję "Przykład analizy operacji" w temacie [starszej wersji języka usługi analizator i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md).  
  
## <a name="enabling-support-for-brace-matching"></a>Włączanie obsługi parowanie nawiasów klamrowych  
 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> Atrybut można określać `MatchBraces`, `MatchBracesAtCaret`, i `ShowMatchingBrace` nazwanych parametrów, które Ustaw odpowiednie właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Można również ustawić właściwości preferencji języka przez użytkownika.  
  
|Wpis rejestru|Właściwość|Opis|  
|--------------------|--------------|-----------------|  
|`MatchBraces`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBraces%2A>|Parowanie umożliwia nawiasów klamrowych|  
|`MatchBracesAtCaret`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableMatchBracesAtCaret%2A>|Umożliwia parowanie nawiasów klamrowych co karetka przenosi.|  
|`ShowMatchingBrace`|<xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableShowMatchingBrace%2A>|Wyróżnia pasującego nawiasu klamrowego.|  
  
## <a name="matching-conditional-statements"></a>Dopasowywanie instrukcje warunkowe  
 Użytkownik może odnosić się do instrukcji warunkowych, takich jak `if`, `else if`, i `else`, lub `#if`, `#elif`, `#else`, `#endif`, w taki sam sposób jak dopasowania ograniczników. Możesz podklasy <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy i zapewnia metodę, która można dodać tekst obejmuje oraz ograniczników do tablicy wewnętrznej pasujących elementów.  
  
## <a name="setting-the-trigger"></a>Ustawienia wyzwalacza  
 Poniższy przykład pokazuje, jak wykrywać pasujące nawiasy, nawiasów klamrowych i nawiasy kwadratowe i ustawienie wyzwalacza dla niego skanera. <xref:Microsoft.VisualStudio.Package.Source.OnCommand%2A> Metody <xref:Microsoft.VisualStudio.Package.Source> klasy wykrywa wyzwalacza i wywołuje analizator, aby znaleźć pasującą parę (zobacz sekcję "Znajdowanie dopasowany" w tym temacie). Ten przykład dotyczy tylko w celach ilustracyjnych. Zakłada się, że skaner zawiera metodę `GetNextToken` , identyfikuje i zwraca tokenów z wiersza tekstu.  
  
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
  
## <a name="matching-the-braces"></a>Dopasowywanie nawiasów klamrowych  
 Oto uproszczony przykład pasujących do {} elementów języka, () i [], a następnie dodanie ich zakresy w celu <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu. To podejście nie jest zalecane podejście do analizowania kodu źródłowego; jest tylko w celach ilustracyjnych.  
  
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
 [Funkcje usługi starszego języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)

