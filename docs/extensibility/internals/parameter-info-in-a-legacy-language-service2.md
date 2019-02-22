---
title: Informacje o parametrach w starszej wersji usługi językowej2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 57c5516c70819f8f86d56e93f78ec5d877c72a78
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56640379"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informacje o parametrach w starszej wersji usługi językowej
Informacje o parametrach funkcji IntelliSense jest znak (zazwyczaj nawias otwierający) na liście parametrów metody początkowy etykietkę narzędzia, która zawiera podpis metody, gdy użytkownik wpisuje listy parametrów. Każdy parametr jest wprowadzana i został wpisany parametr separatora (zazwyczaj przecinkami), etykietki narzędzia jest aktualizowana w celu wyświetlenia następny parametr pogrubioną czcionką.

 Klasy framework (MPF) pakietu zarządzanego zapewniają obsługę zarządzania Parameter Info etykietki narzędzia. Analizator musi wykryć, parametr uruchamianie, parametr następnie i znaki końcowe parametru i musisz podać listę podpisy metod i ich skojarzone parametry.

 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie usług edytora i języka](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.

## <a name="implementation"></a>Implementacja
 Analizator należy określić wartość wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> jest ustawiona, gdy znajdzie znaku początkowego listy parametrów (często nawias otwierający). Powinny one ustawione <xref:Microsoft.VisualStudio.Package.TokenTriggers> wyzwalania, gdy znajdzie parametr separatora (często przecinkami). To powoduje, że informacje o parametrach etykietkę narzędzia do zaktualizowania i Pokaż następny parametr pogrubioną czcionką. Analizator należy określić wartość wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> podczas jeśli znajdzie znak końcowy listy parametrów (często nawiasu zamykającego).

 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wartość wyzwalacza inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metody, która z kolei wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora metoda przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>. Jeżeli analizator Określa, czy identyfikator przed znak początkowy listy parametrów jest nazwę metody rozpoznany, zwraca listę zgodnych podpisy metod w <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu. Jeśli znaleziono żadnych podpisów metody, informacje o parametrach zostanie wyświetlony podpisem pierwszy na liście. Ta etykietka narzędzia jest następnie aktualizowany jako jeden podpis jest wpisane. Po wpisaniu znaku zakończenia listy parametrów Parameter Info etykietki narzędzia jest usuwany z widoku.

> [!NOTE]
>  Aby upewnić się, że informacje o parametrach etykietki narzędzia jest poprawnie sformatowana, konieczne jest przesłonięcie właściwości na <xref:Microsoft.VisualStudio.Package.Methods> klasy, aby podać odpowiednie znaki. Podstawa <xref:Microsoft.VisualStudio.Package.Methods> klasa działa według założenia C# — styl podpis metody. Zobacz <xref:Microsoft.VisualStudio.Package.Methods> klasy, aby uzyskać szczegółowe informacje, w jaki sposób można to zrobić.

## <a name="enabling-support-for-the-parameter-info"></a>Włączanie obsługi, aby uzyskać informacje o parametrach
 Aby zapewnić obsługę etykietek narzędzi Parameter Info, należy ustawić `ShowCompletion` o nazwie parametru <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> do `true`. Usługa językowa odczytuje wartość tego wpisu rejestru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwości.

 Ponadto <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> właściwość musi być równa `true` dla etykietki narzędzi Parameter Info, który będzie wyświetlany.

### <a name="example"></a>Przykład
 Oto uproszczony przykład wykrywanie znaków listy parametrów i ustawianie odpowiedniego wyzwalaczy. Ten przykład dotyczy tylko w celach ilustracyjnych. Zakłada się, że skaner zawiera metodę `GetNextToken` , identyfikuje i zwraca tokenów z wiersza tekstu. Przykładowy kod po prostu ustawia wyzwalacze zawsze wtedy, gdy jej widzi właściwego rodzaju znak.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char parameterListStartChar = '(';
        private const char parameterListEndChar   = ')';
        private const char parameterNextChar      = ',';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (Char.IsPunctuation(c))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                    tokenInfo.EndIndex = index;

                    if (c == parameterListStartChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterStart;
                    }
                    else if (c == parameterListNextChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterNext;
                    else if (c == parameterListEndChar)
                    {
                        tokenInfo.Trigger |= TokenTriggers.ParameterEnd;
                    }
                }
            return foundToken;
        }
    }
}
```

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Obsługa etykietki narzędzia informacji parametru w analizatorze składni
 <xref:Microsoft.VisualStudio.Package.Source> Klasy zakłada pewne informacje o zawartości <xref:Microsoft.VisualStudio.Package.AuthoringScope> i <xref:Microsoft.VisualStudio.Package.AuthoringSink> klas, gdy informacje o parametrach etykietki narzędzia jest wyświetlany i aktualizacji.

- Biorąc pod uwagę analizator <xref:Microsoft.VisualStudio.Package.ParseReason> po wpisaniu znaku początkowego listy parametrów.

- Lokalizacji określonej <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt jest po liście parametrów znak początkowy. Analizator musi zebrać podpisy wszystkie dostępne w deklaracji metody, których położenie i przechowywać je na liście w używanej wersji programu <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu. Ta lista zawiera nazwę metody, metody typu (lub zwracany typ) oraz listę możliwych parametrów. Ta lista jest później wyszukiwana podpis metody lub podpisy do wyświetlenia w etykietce narzędzia informacje o parametrach.

  Analizator należy następnie przeanalizować wiersza określonego przez parametr <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt, aby zebrać nazwę metody wprowadzanych, a także jak daleko wzdłuż użytkownika znajduje się w wpisywania parametrów. Jest to realizowane przez przekazanie nazwy metody <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metody <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiektu, a następnie wywołując <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> jest analizowany metody, gdy znak początkowy listy parametrów wywołania <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> metody podczas listy parametrów Następny znak jest przeanalizowany, a na koniec wywołania <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metody, gdy znak końcowy listy parametrów jest analizowany. Wyniki tych wywołań metody są używane przez <xref:Microsoft.VisualStudio.Package.Source> klasy odpowiednio zaktualizować informacje o parametrach etykietki narzędzia.

### <a name="example"></a>Przykład
 Oto wiersza tekstu, który użytkownik może wprowadzić. Numery poniżej wiersza wskazują, który krok jest pobierana przez analizator, w tym miejscu w wierszu (przy założeniu analizy Przenosi od lewej do prawej). Zakładamy to, że wszystko przed wierszem ma już parsowane do podpisów metod, w tym podpis metody "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Kroki, które przyjmuje analizatora są opisane poniżej:

1.  Wywołuje analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> z tekstem "testfunc".

2.  Wywołuje analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.

3.  Wywołuje analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.

4.  Wywołuje analizator <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.