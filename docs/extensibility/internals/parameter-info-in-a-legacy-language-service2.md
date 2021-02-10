---
title: Informacje o parametrach w starszej wersji językowej Językowej2 | Microsoft Docs
description: Dowiedz się, jak obsłużyć operację informacji o parametrach IntelliSense służącą do wyświetlania sygnatury metody jako metody wpisanej w starszej wersji usługi językowej.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Parameter Info tool tip
- language services [managed package framework], IntelliSense Parameter Info
- Parameter Info (IntelliSense), supporting in language services [managed package framework]
ms.assetid: a117365d-320d-4bb5-b61d-3e6457b8f6bc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 60e24162407c4daeb8643bf106c385f76b11c7d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99954530"
---
# <a name="parameter-info-in-a-legacy-language-service-2"></a>Informacje o parametrach w starszej wersji usługi językowej 2
Informacje o parametrach IntelliSense to etykietka narzędzia, która wyświetla podpis metody, gdy użytkownik wpisze znak początkowy listy parametrów (zwykle jest to otwarty nawias) dla listy parametrów metody. Gdy jest wprowadzany każdy parametr, a separator parametru (zwykle przecinek) jest wpisywany, etykietka narzędzia jest aktualizowana, aby pokazać następny parametr pogrubioną czcionką.

 Klasy struktury zarządzanego pakietu (MPF) zapewniają obsługę zarządzania etykietami narzędzi informacji o parametrach. Parser musi wykryć parametry Start, Next i End parametrów, a następnie musi podać listę sygnatur metod i ich skojarzonych parametrów.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="implementation"></a>Implementacja
 Analizator powinien ustawić wartość wyzwalacza, <xref:Microsoft.VisualStudio.Package.TokenTriggers> gdy odnajdzie znak początkowy listy parametrów (często otwarty nawias). Należy ustawić <xref:Microsoft.VisualStudio.Package.TokenTriggers> wyzwalacz po znalezieniu separatora parametrów (często przecinkiem). Spowoduje to zaktualizowanie etykietki narzędzia informacji o parametrach i pokazywanie następnego parametru pogrubioną czcionką. Analizator powinien ustawić wartość wyzwalacza, <xref:Microsoft.VisualStudio.Package.TokenTriggers> gdy odnajdzie znak końcowy listy parametrów (często nawias zamykający).

 <xref:Microsoft.VisualStudio.Package.TokenTriggers>Wartość wyzwalacza inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.MethodTip%2A> metody, która z kolei wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser metody z przyczyną analizy <xref:Microsoft.VisualStudio.Package.ParseReason> . Jeśli analizator określi, że identyfikator przed znakiem początkowym listy parametrów jest rozpoznawaną nazwą metody, zwraca listę zgodnych sygnatur metod w <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiekcie. Jeśli zostaną znalezione jakiekolwiek sygnatury metod, etykietka narzędzia informacji o parametrach jest wyświetlana z pierwszym podpisem na liście. Ta etykietka narzędzia jest następnie aktualizowana w miarę wpisywania większej liczby sygnatur. Po wpisaniu znaku końcowego listy parametrów, etykietka narzędzia informacje o parametrach jest usuwana z widoku.

> [!NOTE]
> Aby upewnić się, że etykietka narzędzia informacje o parametrach jest poprawnie sformatowana, należy zastąpić właściwości w <xref:Microsoft.VisualStudio.Package.Methods> klasie, aby podać odpowiednie znaki. Klasa bazowa <xref:Microsoft.VisualStudio.Package.Methods> przyjmuje sygnaturę metody w stylu C#. Zapoznaj się z <xref:Microsoft.VisualStudio.Package.Methods> klasą, aby uzyskać szczegółowe informacje na temat tego, jak to zrobić.

## <a name="enabling-support-for-the-parameter-info"></a>Włączanie obsługi informacji o parametrach
 Aby można było obsługiwać etykietki narzędzi informacji o parametrach, należy ustawić `ShowCompletion` parametr nazwany elementu <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> na `true` . Usługa języka odczytuje wartość tego wpisu rejestru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwości.

 Ponadto <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ParameterInformation%2A> Właściwość musi być ustawiona na wartość `true` dla etykietki narzędzia informacje o parametrach, która ma być wyświetlana.

### <a name="example"></a>Przykład
 Poniżej przedstawiono uproszczony przykład wykrywania znaków listy parametrów i ustawiania odpowiednich wyzwalaczy. Ten przykład służy tylko do celów informacyjnych. Przyjęto założenie, że skaner zawiera metodę `GetNextToken` , która identyfikuje i zwraca tokeny z wiersza tekstu. Przykładowy kod po prostu ustawia wyzwalacze za każdym razem, gdy widzi właściwy rodzaj znaku.

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

## <a name="supporting-the-parameter-info-tooltip-in-the-parser"></a>Obsługa etykietki narzędzia informacji o parametrach w analizatorze
 <xref:Microsoft.VisualStudio.Package.Source>Klasa przyjmuje pewne założenia dotyczące zawartości <xref:Microsoft.VisualStudio.Package.AuthoringScope> klas i, <xref:Microsoft.VisualStudio.Package.AuthoringSink> gdy zostanie wyświetlona i zaktualizowana etykietka narzędzia informacji o parametrach.

- Analizator jest podawany, <xref:Microsoft.VisualStudio.Package.ParseReason> gdy wpisano znak początkowy listy parametrów.

- Lokalizacja określona w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekcie jest natychmiast po znaku początkowego listy parametrów. Analizator musi zbierać sygnatury wszystkich deklaracji metod dostępnych w tym położeniu i przechowywać je na liście w używanej wersji <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu. Ta lista zawiera nazwę metody, typ metody (lub zwracany typ) oraz listę możliwych parametrów. Ta lista jest później przeszukiwana sygnatury metody lub podpisy do wyświetlenia w etykietce narzędzia informacji o parametrach.

  Analizator musi następnie przeanalizować wiersz określony przez <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt, aby zebrać nazwę wprowadzonej metody, a także czas, w jakim użytkownik jest w trakcie wpisywania parametrów. W tym celu należy przekazać nazwę metody do <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> metody na <xref:Microsoft.VisualStudio.Package.AuthoringSink> obiekcie, a następnie wywołać <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> metodę, gdy zostanie przeanalizowany znak początkowy listy parametrów, wywołując metodę, gdy zostanie przeanalizowany <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> Następny znak listy parametrów, a następnie wywołując <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> metodę, gdy zostanie przeanalizowany znak końcowy listy parametrów. Wyniki tych wywołań metod są używane przez <xref:Microsoft.VisualStudio.Package.Source> klasę do odpowiedniej aktualizacji etykietki narzędzia informacji o parametrach.

### <a name="example"></a>Przykład
 Oto wiersz tekstu, który użytkownik może wprowadzić. Liczby poniżej wiersza wskazują, który krok jest wykonywany przez analizator w tej pozycji w wierszu (przy założeniu, że analiza przesuwa się od lewej do prawej). W tym miejscu założono, że wszystko przed wierszem jest już analizowane dla sygnatur metod, w tym sygnatury metody "testfunc".

```
testfunc("a string",3);
     ^^          ^ ^
     12          3 4
```

 Poniżej przedstawiono kroki, które wykonuje analizator składni:

1. Analizator wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartName%2A> z tekstem "testfunc".

2. Parser wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.StartParameters%2A> .

3. Parser wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.NextParameter%2A> .

4. Parser wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringSink.EndParameters%2A> .
