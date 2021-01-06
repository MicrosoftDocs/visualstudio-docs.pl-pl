---
title: Kolorowanie składni w starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się, jak obsługiwać kolorowanie składni w starszej wersji usługi językowej, dostarczając Analizator lub skaner, który może identyfikować typy elementów leksykalnych lub tokenów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c51885e593fabffab80d11c930100f3cc719dff8
ms.sourcegitcommit: 0c9155e9b9408fb7481d79319bf08650b610e719
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97877757"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Kolorowanie składni w starszej wersji usługi językowej
Kolorowanie składni to funkcja, która powoduje, że różne elementy języka programowania będą wyświetlane w pliku źródłowym w różnych kolorach i stylach. Aby obsługiwać tę funkcję, należy dostarczyć Analizator lub skaner, który może identyfikować typy elementów leksykalnych lub tokenów w pliku. Wiele języków rozróżnia słowa kluczowe, ograniczniki (takie jak nawiasy lub nawiasy klamrowe) i komentarze poprzez kolorowanie ich na różne sposoby.

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="implementation"></a>Implementacja
 Aby można było obsłużyć kolorowanie, Struktura pakietu zarządzanego (MPF) zawiera <xref:Microsoft.VisualStudio.Package.Colorizer> klasę, która implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejs. Ta klasa współdziała z, <xref:Microsoft.VisualStudio.Package.IScanner> Aby określić token i kolory. Aby uzyskać więcej informacji na temat skanerów, zobacz [starsze wersje analizatora i skanera usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer>Następnie Klasa oznacza każdy znak tokenu z informacjami o kolorze i zwraca te informacje do edytora wyświetlającego plik źródłowy.

 Informacje o kolorach zwracane do edytora są indeksem do listy elementów z możliwością nakolorowania. Każdy element z możliwością kolorowania określa wartość koloru i zestaw atrybutów czcionki, takich jak pogrubienie lub przekreślenie. Edytor dostarcza zestaw domyślnych elementów, które mogą być używane przez usługę języka. Wystarczy określić odpowiedni indeks koloru dla każdego typu tokenu. Można jednak udostępnić zestaw niestandardowych elementów i indeksów, które są dostarczane dla tokenów, i odwoływać się do własnej listy elementów do przykolorowania, a nie do listy domyślnej. Należy również ustawić `RequestStockColors` wpis rejestru na 0 (lub nie określać `RequestStockColors` we wszystkich), aby obsługiwał kolory niestandardowe. Można ustawić ten wpis rejestru z nazwanym parametrem w <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybucie zdefiniowanym przez użytkownika. Aby uzyskać więcej informacji na temat rejestrowania usługi językowej i ustawiania jej opcji, zobacz [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Niestandardowe elementy z możliwością kolorowania
 Aby podać własne niestandardowe elementy, należy zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metodę i <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Pierwsza metoda zwraca liczbę elementów niestandardowych, które są obsługiwane przez usługę języka, a drugi pobiera niestandardowy element z możliwością kolorowania według indeksu. Można utworzyć domyślną listę niestandardowych elementów z możliwością kolorowania. W konstruktorze usługi językowej wszystko, co należy zrobić, to każdy element, który ma zostać poddany kolorem, musi mieć nazwę. Program Visual Studio automatycznie obsługuje przypadek, w którym użytkownik wybiera inny zestaw elementów z możliwością kolorowania. Ta nazwa jest wyświetlana na stronie właściwości **czcionki i kolory** w oknie dialogowym **Opcje** (dostępne z menu **Narzędzia** programu Visual Studio) i ta nazwa określa, który kolor został zastąpiony przez użytkownika. Wybory użytkownika są przechowywane w pamięci podręcznej w rejestrze i uzyskuje do niej dostęp za pomocą nazwy koloru. Na stronie właściwości **czcionki i kolory** znajduje się lista wszystkich nazw kolorów w kolejności alfabetycznej, aby można było grupować kolory niestandardowe według poprzedzającej nazwy języka; na przykład "**TestLanguage-Comment**" i "**TestLanguage-słowo kluczowe**". Można też grupować elementy z możliwością kolorowania według typu, "**comment (TestLanguage)**" i "**słowo kluczowe (TestLanguage)**". Preferowane jest grupowanie według nazwy języka.

> [!CAUTION]
> Stanowczo zaleca się uwzględnienie nazwy języka w nazwie elementu, aby uniknąć kolizji z istniejącymi nazwami elementów.

> [!NOTE]
> Jeśli zmienisz nazwę jednego z kolorów podczas opracowywania, musisz zresetować pamięć podręczną utworzoną przez program Visual Studio po raz pierwszy dostęp do kolorów. Możesz to zrobić, uruchamiając polecenie **Zresetuj pakiet eksperymentalny** z menu programu Visual Studio SDK.

 Należy zauważyć, że pierwszy element na liście elementów z możliwością kolorowania nigdy nie jest przywoływany. Program Visual Studio zawsze dostarcza domyślne kolory tekstu i atrybuty dla tego elementu. Najprostszym sposobem postępowania z tym jest podawanie elementów zastępczych jako pierwszy element.

### <a name="high-color-colorable-items"></a>Kolory o wysokim kolorze
 Elementy z możliwością kolorowania mogą również obsługiwać 24-bitowe lub wysokie wartości koloru za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu. Klasa MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> obsługuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejs i 24-bitowe kolory są określone w konstruktorze wraz z normalnymi kolorami. Aby uzyskać <xref:Microsoft.VisualStudio.Package.ColorableItem> szczegółowe informacje, zobacz klasę. W poniższym przykładzie pokazano, jak ustawić 24-bitowe kolory dla słów kluczowych i komentarzy. Kolory 24-bitowe są używane, gdy kolor 24-bitowy jest obsługiwany na pulpicie użytkownika. w przeciwnym razie są używane normalne kolory tekstu.

 Należy pamiętać, że są to domyślne kolory dla danego języka. Użytkownik może zmienić te kolory na dowolne z nich.

### <a name="example"></a>Przykład
 Ten przykład pokazuje jeden ze sposobów deklarowania i wypełniania tablicy niestandardowych elementów z możliwością kolorowania przy użyciu <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy. W tym przykładzie ustawiono kolor słów kluczowych i komentarzy przy użyciu kolorów 24-bitowych.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private ColorableItem[] m_colorableItems;

        TestLanguageService() : base()
        {
            m_colorableItems = new ColorableItem[] {
                new ColorableItem("TestLanguage - Text",
                                  "Text",
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.Empty,
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT),
                new ColorableItem("TestLanguage - Keyword",
                                  "Keyword",
                                  COLORINDEX.CI_MAROON,
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,
                                  System.Drawing.Color.FromArgb(192,32,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_BOLD),
                new ColorableItem("TestLanguage - Comment",
                                  "Comment",
                                  COLORINDEX.CI_DARKGREEN,
                                  COLORINDEX.CI_LIGHTGRAY,
                                  System.Drawing.Color.FromArgb(32,128,32),
                                  System.Drawing.Color.Empty,
                                  FONTFLAGS.FF_DEFAULT)
                // ...
                // Add as many colorable items as you want to support.
            };
        }
    }
}
```

## <a name="the-colorizer-class-and-the-scanner"></a>Kolorowanie klasy i skanera
 Klasa bazowa <xref:Microsoft.VisualStudio.Package.LanguageService> ma <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metodę, która instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> klasę. Skaner, który jest zwracany z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody, jest przesyłany do <xref:Microsoft.VisualStudio.Package.Colorizer> konstruktora klasy.

 Należy zaimplementować <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodę we własnej wersji <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. <xref:Microsoft.VisualStudio.Package.Colorizer>Klasa używa skanera, aby uzyskać wszystkie informacje o kolorach tokenu.

 Skaner musi wypełnić <xref:Microsoft.VisualStudio.Package.TokenInfo> strukturę dla każdego znalezionego tokenu. Ta struktura zawiera informacje, takie jak zakres zajmowany przez token, indeks koloru, który ma być używany, typ tokenu i wyzwalacze tokenów (zobacz <xref:Microsoft.VisualStudio.Package.TokenTriggers> ). Tylko indeks zakresu i koloru są zbędny do kolorowania przez <xref:Microsoft.VisualStudio.Package.Colorizer> klasę.

 Indeks koloru przechowywany w <xref:Microsoft.VisualStudio.Package.TokenInfo> strukturze jest zwykle wartością z <xref:Microsoft.VisualStudio.Package.TokenColor> wyliczenia, która zapewnia wiele indeksów o nazwach odpowiadających różnym elementom języka, takim jak słowa kluczowe i operatory. Jeśli lista elementów niestandardowych kolorów jest zgodna z elementami przedstawionymi w <xref:Microsoft.VisualStudio.Package.TokenColor> wyliczeniu, można po prostu użyć wyliczenia jako koloru dla każdego tokenu. Jeśli jednak masz dodatkowe elementy z możliwością przykolorowania lub nie chcesz używać istniejących wartości w tej kolejności, możesz rozmieścić listę elementów niestandardowych, które można dostosować do własnych potrzeb, i zwrócić odpowiedni indeks na tę listę. Upewnij się, że indeks jest rzutowany na <xref:Microsoft.VisualStudio.Package.TokenColor> czas przechowywania w strukturze. program <xref:Microsoft.VisualStudio.Package.TokenInfo> [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] widzi tylko ten indeks.

### <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak skaner może identyfikować trzy typy tokenów: cyfry, znaki interpunkcyjne i identyfikatory (wszystkie elementy, które nie są liczbami ani interpunkcją). Ten przykład służy tylko do celów informacyjnych i nie reprezentuje kompleksowej implementacji analizatora i skanera. Przyjęto założenie, że istnieje `Lexer` Klasa z `GetNextToken()` metodą zwracającą ciąg.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    private Lexer lex;

    public class TestScanner : IScanner
    {
        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false;
            string token = lex.GetNextToken();
            if (token != null)
            {
                char firstChar = token[0];
                if (Char.IsPunctuation(firstChar))
                {
                    tokenInfo.Type = TokenType.Operator;
                    tokenInfo.Color = TokenColor.Keyword;
                }
                else if (Char.IsNumber(firstChar))
                {
                    tokenInfo.Type = TokenType.Literal;
                    tokenInfo.Color = TokenColor.Number;
                }
                else
                {
                    tokenInfo.Type = TokenType.Identifier;
                    tokenInfo.Color = TokenColor.Identifier;
                }
            }
            return foundToken;
        }
```

## <a name="see-also"></a>Zobacz też
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
