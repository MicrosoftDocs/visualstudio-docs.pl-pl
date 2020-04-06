---
title: Kolorystyka składni w starszej usłudze językowej | Dokumenty firmy Microsoft
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
ms.openlocfilehash: 02723a09254255b98291cb921ae5ec091d8b9859
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704704"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Kolorowanie składni w starszej wersji usługi językowej
Kolorystyka składni jest funkcją, która powoduje, że różne elementy języka programowania mają być wyświetlane w pliku źródłowym w różnych kolorach i stylach. Aby obsługiwać tę funkcję, należy podać analizatora lub skanera, który może identyfikować typy elementów leksykalne lub tokeny w pliku. Wiele języków rozróżnia słowa kluczowe, ograniczniki (takie jak nawiasy lub nawiasy klamrowe) i komentarze, kolorując je na różne sposoby.

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="implementation"></a>Wdrażanie
 Do obsługi kolorowania, struktura pakietu zarządzanego <xref:Microsoft.VisualStudio.Package.Colorizer> (MPF) zawiera <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> klasę, która implementuje interfejs. Ta klasa współdziała <xref:Microsoft.VisualStudio.Package.IScanner> z do określenia tokenu i kolorów. Aby uzyskać więcej informacji na temat skanerów, zobacz [Starszy parser usług językowych i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> następnie oznacza każdy znak tokenu z informacjami o kolorze i zwraca te informacje do edytora wyświetlającego plik źródłowy.

 Informacje o kolorze zwrócone do edytora to indeks na liście elementów colorable. Każdy element colorable określa wartość koloru i zestaw atrybutów czcionki, takich jak pogrubienie lub przekreślenie. Edytor dostarcza zestaw domyślnych elementów colorable, które mogą być używane przez usługę językową. Wszystko, co musisz zrobić, to określić odpowiedni indeks kolorów dla każdego typu tokenu. Można jednak podać zestaw niestandardowych elementów colorable i indeksy, które dostarczasz dla tokenów, i odwoływać się do własnej listy elementów colorable zamiast listy domyślnej. Należy również ustawić `RequestStockColors` wpis rejestru na 0 (lub nie określać wpisu `RequestStockColors` w ogóle) do obsługi kolorów niestandardowych. Ten wpis rejestru można ustawić z <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> nazwanym parametrem atrybutu zdefiniowanego przez użytkownika. Aby uzyskać więcej informacji na temat rejestrowania usługi językowej i ustawiania jej opcji, zobacz [Rejestrowanie usługi języka starszego](../../extensibility/internals/registering-a-legacy-language-service1.md).

## <a name="custom-colorable-items"></a>Niestandardowe elementy z możliwością kolorowania
 Aby podać własne niestandardowe elementy colorable, <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> należy <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService> i metody na klasy. Pierwsza metoda zwraca liczbę niestandardowych elementów colorable, które obsługuje usługa języka, a druga pobiera niestandardowy element colorable przez indeks. Utworzysz domyślną listę niestandardowych elementów colorable. W konstruktorze usługi języka, wszystko, co musisz zrobić, to podać każdy element colorable z nazwą. Visual Studio automatycznie obsługuje przypadku, w którym użytkownik wybiera inny zestaw elementów colorable. Ta nazwa jest wyświetlana na stronie właściwości **Czcionki i kolory** w oknie dialogowym **Opcje** (dostępne w menu **Narzędzia** programu Visual Studio) i ta nazwa określa, który kolor został zastąpiony przez użytkownika. Opcje użytkownika są przechowywane w pamięci podręcznej w rejestrze i dostępne przez nazwę koloru. Strona właściwości **Czcionki i kolory** zawiera listę wszystkich nazw kolorów w kolejności alfabetycznej, dzięki czemu można pogrupować kolory niestandardowe, poprzedzając każdą nazwę koloru nazwą języka; na przykład "**TestLanguage- Comment**" i "**TestLanguage- Keyword**". Możesz też pogrupować elementy colorable według typu "**Comment (TestLanguage)**" i "**Keyword (TestLanguage)**". Preferowane jest grupowanie według nazwy języka.

> [!CAUTION]
> Zdecydowanie zaleca się uwzględnienie nazwy języka w nazwie elementu colorable, aby uniknąć kolizji z istniejącymi nazwami elementów colorable.

> [!NOTE]
> Jeśli zmienisz nazwę jednego z kolorów podczas tworzenia, należy zresetować pamięć podręczną, którą program Visual Studio utworzył po raz pierwszy, gdy kolory były dostępne. Można to zrobić, uruchamiając polecenie **Resetuj gałęzię eksperymentalną** z menu programu zestaw SDK programu Visual Studio.

 Należy zauważyć, że pierwszy element na liście elementów colorable nigdy nie odwołuje. Visual Studio zawsze dostarcza domyślne kolory tekstu i atrybuty dla tego elementu. Najprostszym sposobem radzenia sobie z tym jest dostarczenie elementu zastępczego colorable jako pierwszy element.

### <a name="high-color-colorable-items"></a>Elementy o wysokim kolorze
 Elementy colorable mogą również obsługiwać 24-bitowe lub wysokie wartości kolorów za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu. Klasa MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> obsługuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejs i 24-bitowe kolory są określone w konstruktorze wraz z normalnymi kolorami. Zobacz <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy, aby uzyskać więcej informacji. W poniższym przykładzie pokazano, jak ustawić kolory 24-bitowe dla słów kluczowych i komentarzy. Kolory 24-bitowe są używane, gdy kolor 24-bitowy jest obsługiwany na pulpicie użytkownika; w przeciwnym razie używane są normalne kolory tekstu.

 Pamiętaj, że są to kolory domyślne dla twojego języka; użytkownik może zmienić te kolory na co chcesz.

### <a name="example"></a>Przykład
 W tym przykładzie pokazano jeden sposób, aby zadeklarować i <xref:Microsoft.VisualStudio.Package.ColorableItem> wypełnić tablicę niestandardowych elementów colorable przy użyciu klasy. W tym przykładzie ustawia kolory słów kluczowych i komentarzy przy użyciu kolorów 24-bitowych.

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

## <a name="the-colorizer-class-and-the-scanner"></a>Klasa Colorizer i skaner
 Klasa <xref:Microsoft.VisualStudio.Package.LanguageService> podstawowa <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> ma metodę, która <xref:Microsoft.VisualStudio.Package.Colorizer> instantiantes klasy. Skaner, który jest <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> zwracany z <xref:Microsoft.VisualStudio.Package.Colorizer> metody jest przekazywana do konstruktora klasy.

 Należy zaimplementować <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metodę we <xref:Microsoft.VisualStudio.Package.LanguageService> własnej wersji klasy. Klasa <xref:Microsoft.VisualStudio.Package.Colorizer> używa skanera, aby uzyskać wszystkie informacje o kolorze tokenu.

 Skaner musi wypełnić strukturę <xref:Microsoft.VisualStudio.Package.TokenInfo> dla każdego tokenu, który znajdzie. Ta struktura zawiera informacje, takie jak zakres, który zajmuje token, indeks kolorów do użycia, <xref:Microsoft.VisualStudio.Package.TokenTriggers>jaki typ jest tokenem i wyzwalacze tokenów (patrz ). Tylko zakres i indeks kolorów są potrzebne <xref:Microsoft.VisualStudio.Package.Colorizer> do kolorowania przez klasę.

 Indeks kolorów przechowywany <xref:Microsoft.VisualStudio.Package.TokenInfo> w strukturze jest zazwyczaj <xref:Microsoft.VisualStudio.Package.TokenColor> wartością z wyliczenia, która zawiera liczbę nazwanych indeksów odpowiadających różnym elementom języka, takim jak słowa kluczowe i operatory. Jeśli niestandardowa lista elementów colorable <xref:Microsoft.VisualStudio.Package.TokenColor> pasuje do elementów przedstawionych w wyliczeniu, następnie można po prostu użyć wyliczenia jako kolor dla każdego tokenu. Jeśli jednak masz dodatkowe elementy colorable lub nie chcesz używać istniejących wartości w tej kolejności, można rozmieścić listę niestandardowych elementów colorable do własnych potrzeb i zwrócić odpowiedni indeks do tej listy. Po prostu pamiętaj, aby <xref:Microsoft.VisualStudio.Package.TokenColor> oddać indeks do <xref:Microsoft.VisualStudio.Package.TokenInfo> a podczas przechowywania go w strukturze; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] widzi tylko indeks.

### <a name="example"></a>Przykład
 Poniższy przykład pokazuje, jak skaner może zidentyfikować trzy typy tokenów: liczby, znaki interpunkcyjne i identyfikatory (wszystko, co nie jest liczbą lub interpunkcji). Ten przykład służy wyłącznie do celów ilustracyjnych i nie reprezentuje kompleksowej implementacji analizatora i skanera. Przyjęto założenie, że `Lexer` istnieje `GetNextToken()` klasa z metodą, która zwraca ciąg.

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
