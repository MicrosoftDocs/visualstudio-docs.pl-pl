---
title: Informacje o parametrach w starszej usłudze językowej2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e2c40c9ca5c038a70714545f4133db0c0dd686d5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706748"
---
# <a name="parameter-info-in-a-legacy-language-service"></a>Informacje o parametrach w starszej wersji usługi językowej
IntelliSense Parameter Info to etykietka narzędzia, która wyświetla podpis metody, gdy użytkownik wpisuje znak początkowy listy parametrów (zazwyczaj otwarty nawias) dla listy parametrów metody. Po wprowadzeniu każdego parametru i wpisaniu separatora parametrów (zazwyczaj przecinka) etykietka narzędzia jest aktualizowana w celu wyświetlenia następnego parametru pogrubioną czcionką.

 Klasy frameworkum zarządzanego pakietu (MPF) zapewniają obsługę zarządzania etykietką narzędzia Informacje o parametrach. Analizator parser musi wykryć znaki początkowe parametrów, parametrów i końcowych parametrów i musi dostarczyć listę podpisów metody i skojarzonych z nimi parametrów.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="implementation"></a>Wdrażanie
 Analizator parser należy <xref:Microsoft.VisualStudio.Package.TokenTriggers> ustawić wartość wyzwalacza jest ustawiona, gdy znajdzie znak początkowy listy parametrów (często otwarty nawias). Należy ustawić <xref:Microsoft.VisualStudio.Package.TokenTriggers> wyzwalacz, gdy znajdzie separator parametrów (często przecinek). Powoduje to, że etykietka narzędzia Informacje o parametrach ma być aktualizowana i wyświetla następny parametr pogrubioną czcionką. Analizator parser należy <xref:Microsoft.VisualStudio.Package.TokenTriggers> ustawić wartość wyzwalacza, gdy znajdzie znak końcowy listy parametrów (często zamknij nawias).

 Wartość <xref:Microsoft.VisualStudio.Package.TokenTriggers> wyzwalacza inicjuje <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> wywołanie metody, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> która z kolei wywołuje analizator <xref:Microsoft.VisualStudio.Package.ParseReason>metody z powodu analizy . Jeśli analizator stwierdzi, że identyfikator przed znakiem rozpoczęcia listy parametrów jest rozpoznawaną nazwą metody, <xref:Microsoft.VisualStudio.Package.AuthoringScope> zwraca listę pasujących podpisów metod w obiekcie. Jeśli znaleziono podpisy jakiejkolwiek metody, etykietka narzędzia Informacje o parametrach jest wyświetlana z pierwszym podpisem na liście. Ta etykietka narzędzia jest następnie aktualizowana w miarę wpisywania większej liczby podpisów. Po wpisaniu znaku końcowego listy parametrów etykietka narzędzia Informacje o parametrach jest usuwana z widoku.

> [!NOTE]
> Aby upewnić się, że etykietka narzędzia Informacje o parametrach jest <xref:Microsoft.VisualStudio.Package.Methods> poprawnie sformatowana, należy zastąpić właściwości klasy, aby podać odpowiednie znaki. Klasa <xref:Microsoft.VisualStudio.Package.Methods> podstawowa przyjmuje podpis metody w stylu C#. Zobacz <xref:Microsoft.VisualStudio.Package.Methods> klasy szczegółowe informacje na temat tego, jak można to zrobić.

## <a name="enabling-support-for-the-parameter-info"></a>Włączanie obsługi informacji o parametrach
 Aby obsługiwać etykietki narzędzi Informacje `ShowCompletion` o parametrach, należy ustawić nazwany parametr <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> na `true`. Usługa języka odczytuje wartość tego wpisu rejestru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwości.

 Ponadto <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> właściwość musi być `true` ustawiona na dla etykietki narzędzia Informacje o parametrach, które mają być wyświetlane.

### <a name="example"></a>Przykład
 Oto uproszczony przykład wykrywania znaków listy parametrów i ustawiania odpowiednich wyzwalaczy. Ten przykład służy wyłącznie do celów ilustracyjnych. Przyjęto założenie, że skaner `GetNextToken` zawiera metodę, która identyfikuje i zwraca tokeny z wiersza tekstu. Przykładowy kod po prostu ustawia wyzwalacze, gdy widzi odpowiedni rodzaj znaku.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Obsługa etykietki narzędzia Informacje o parametrach w analizatorze
 Klasa <xref:Microsoft.VisualStudio.Package.Source> sprawia, że niektóre założenia <xref:Microsoft.VisualStudio.Package.AuthoringScope> dotyczące <xref:Microsoft.VisualStudio.Package.AuthoringSink> zawartości i klas, gdy etykietka narzędzia Informacje o parametrach jest wyświetlany i aktualizowany.

- Analizator jest podawany <xref:Microsoft.VisualStudio.Package.ParseReason> po wpisaniu znaku początkowego listy parametrów.

- Lokalizacja podana <xref:Microsoft.VisualStudio.Package.ParseRequest> w obiekcie jest natychmiast po znaku początkowego listy parametrów. Analizator parser musi zbierać podpisy wszystkich deklaracji metody dostępnych w tej pozycji <xref:Microsoft.VisualStudio.Package.AuthoringScope> i przechowywać je na liście w wersji obiektu. Ta lista zawiera nazwę metody, typ metody (lub typ zwracany) oraz listę możliwych parametrów. Ta lista jest później wyszukiwana pod kątem podpisu metody lub podpisów do wyświetlenia w etykietce narzędzia Informacje o parametrach.

  Analizator musi następnie przeanalizować wiersz określony <xref:Microsoft.VisualStudio.Package.ParseRequest> przez obiekt, aby zebrać nazwę wprowadzonej metody, a także jak daleko wzdłuż użytkownika jest w parametrach wpisywania. Jest to realizowane przez przekazanie nazwy metody <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> do <xref:Microsoft.VisualStudio.Package.AuthoringSink> metody na obiekcie, a następnie wywołanie <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> metody, gdy <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> znak początkowy listy parametrów jest analizowany, wywołując <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metodę, gdy lista parametrów następny znak jest analizowany, a na koniec wywołanie metody, gdy znak końcowy listy parametrów jest analizowany. Wyniki tych wywołań metody są <xref:Microsoft.VisualStudio.Package.Source> używane przez klasę, aby odpowiednio zaktualizować etykietkę narzędzia Informacje o parametrach.

### <a name="example"></a>Przykład
 Oto wiersz tekstu, który użytkownik może wprowadzić. Liczby poniżej wiersza wskazują, który krok jest podejmowany przez analizator w tej pozycji w wierszu (przy założeniu, że analizowanie przesuwa się od lewej do prawej). Założenie jest takie, że wszystko, zanim wiersz został już przeanalizowany dla podpisów metody, w tym podpis metody "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Kroki, które wykonuje analizator są opisane poniżej:

1. Parser wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> z tekstem "testfunc".

2. Parser wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A>.

3. Parser wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A>.

4. Parser wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A>.
