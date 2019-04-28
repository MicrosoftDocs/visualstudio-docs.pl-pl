---
title: Kolorowanie składni w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
caps.latest.revision: 29
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 64e57ebc80320ccc133261781eb8ee6611c8e2a0
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441226"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Kolorowanie składni w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kolorowanie składni jest funkcją, która powoduje, że różne elementy języka programowania mają być wyświetlane w pliku źródłowego w różnych kolorach i stylów. Aby obsługiwać tę funkcję, musisz podać analizator i skaner identyfikujące typów elementy leksykalne lub tokenów w pliku. Wiele języków rozróżnia słowa kluczowe, ograniczniki (na przykład nawiasów zwykłych lub klamrowych) i komentarze, kolorowanie je na różne sposoby.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie usług edytora i języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
> Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="implementation"></a>Implementacja  
 Aby zapewnić obsługę kolorowania, środowiska pakietu zarządzanego (MPF) obejmuje <xref:Microsoft.VisualStudio.Package.Colorizer> klasy, która implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu. Ta klasa korzysta z <xref:Microsoft.VisualStudio.Package.IScanner> do określenia tokenu i kolorów. Aby uzyskać więcej informacji na temat skanerów, zobacz [starszej wersji języka usługi analizator i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Klasy następnie oznacza każdy znak token z informacji o kolorze i zwraca te informacje do edytora wyświetlania pliku źródłowego.  
  
 Informacje o kolorach powrót do edytora jest indeks listy elementów z możliwością kolorowania. Każdy element z możliwością kolorowania określa wartość koloru i zestaw atrybutów czcionek, takie jak pogrubienie lub przekreślenie. Edytor dostarcza zestaw elementy z możliwością kolorowania domyślne, których można użyć usługi języka. To wszystko, co należy zrobić, należy określić indeks odpowiedni kolor dla każdego typu tokenu. Można jednak udostępniają zestaw niestandardowych elementów z możliwością kolorowania i indeksy, które podasz tokenów i odwoływać się do listy elementów z możliwością kolorowania zamiast domyślnej listy. Należy także ustawić `RequestStockColors` wpisu rejestru na 0 (lub nie określaj `RequestStockColors` wpis w ogóle) do obsługi kolorów niestandardowych. Można ustawić ten wpis rejestru o nazwany parametr do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutów zdefiniowanych przez użytkownika. Aby uzyskać więcej informacji na temat rejestrowania usługi językowej i ustawianie jego opcji, zobacz [rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Niestandardowe elementy z możliwością kolorowania  
 Aby przekazać własne niestandardowe elementy z możliwością kolorowania, konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> i <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metody <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Pierwsza metoda zwraca liczbę niestandardowych elementów z możliwością kolorowania, które obsługuje usługi języka, a druga pobiera niestandardowego elementu z możliwością kolorowania według indeksu. Możesz utworzyć domyślną listę elementów z możliwością kolorowania niestandardowych. W Konstruktorze usługi języka wszystko, co należy zrobić to podać każdego elementu z możliwością kolorowania o nazwie. Program Visual Studio automatycznie obsługuje przypadek, gdy użytkownik wybierze inny zbiór elementów z możliwością kolorowania. Ta nazwa jest wyświetlana w **czcionki i kolory** strony właściwości w **opcje** okno dialogowe (dostępne w programie Visual Studio **narzędzia** menu) i określa tę nazwę, która kolor przesłaniany przez użytkownika. Opcje użytkownika są przechowywane w pamięci podręcznej w rejestrze i uzyskują nazwę koloru. **Czcionki i kolory** strony właściwości wyświetla listę wszystkich nazw kolorów w kolejności alfabetycznej, dzięki czemu można grupować kolory niestandardowe, poprzedzając każda nazwa koloru z Twoją nazwą języka; na przykład "**TestLanguage - Comment**"i"**TestLanguage — słowo kluczowe**". Lub można grupować według typu, z możliwością kolorowania elementów "**komentarz (TestLanguage)**"i"**— słowo kluczowe (TestLanguage)**". Preferowane jest grupowanie według nazwy języka.  
  
> [!CAUTION]
> Zdecydowanie zaleca się obejmują nazwę języka w nazwie elementu z możliwością kolorowania, aby uniknąć konfliktów z już istniejącymi nazwami elementów z możliwością kolorowania.  
  
> [!NOTE]
> Jeśli zmienisz nazwę jednego z kolorów podczas projektowania należy zresetować pamięć podręczną, która Visual Studio stworzył po raz pierwszy uzyskano kolorów. Możesz to zrobić, uruchamiając **resetowania eksperymentalne Hive** polecenia z menu programu Visual Studio SDK.  
  
 Należy pamiętać, że nigdy nie odwołuje się pierwszy element na liście elementów z możliwością kolorowania. Program Visual Studio zawsze dostarcza domyślne kolory tekstu i atrybuty dla tego elementu. Najprostszy sposób radzenia sobie z tym jest umożliwiają określanie wartości elementu z możliwością kolorowania symbolu zastępczego, jako pierwszy element.  
  
### <a name="high-color-colorable-items"></a>Elementy z możliwością kolorowania High Color  
 Elementy z możliwością kolorowania może również obsługiwać kolor 24-bitowego lub o wysokiej wartości za pomocą <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy obsługuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu, a także kolory 24-bitowego są określone w Konstruktorze wraz z normalnym kolorów. Zobacz <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy, aby uzyskać więcej informacji. W poniższym przykładzie pokazano, jak ustawić kolory 24-bitowa słowa kluczowe i komentarze. 24-bitowego kolory 24-bitowego, kolorów jest obsługiwany na pulpicie użytkownika; w przeciwnym razie są używane kolory zwykłego tekstu.  
  
 Należy pamiętać, że są to domyślne kolory dla języka; Użytkownik może zmienić te kolory do ich ma.  
  
### <a name="example"></a>Przykład  
 Ten przykład pokazuje, jak deklarować i wypełnij tablicę niestandardowe elementy z możliwością kolorowania przy użyciu <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy. W tym przykładzie kolorów — słowo kluczowe i komentarz, za pomocą 24-bitowego, kolorów.  
  
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
                new ColorableItem("TestLanguage – Text",  
                                  "Text",  
                                  COLORINDEX.CI_SYSPLAINTEXT_FG,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.Empty,  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_DEFAULT),  
                new ColorableItem("TestLanguage – Keyword",  
                                  "Keyword",  
                                  COLORINDEX.CI_MAROON,  
                                  COLORINDEX.CI_SYSPLAINTEXT_BK,  
                                  System.Drawing.Color.FromArgb(192,32,32),  
                                  System.Drawing.Color.Empty,  
                                  FONTFLAGS.FF_BOLD),  
                new ColorableItem("TestLanguage – Comment",  
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
 Podstawa <xref:Microsoft.VisualStudio.Package.LanguageService> klasa ma <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metody tego instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> klasy. Skaner, który jest zwracany z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda jest przekazywana do <xref:Microsoft.VisualStudio.Package.Colorizer> konstruktora klasy.  
  
 Musisz zaimplementować <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda w wersji produktu <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. <xref:Microsoft.VisualStudio.Package.Colorizer> Klasa korzysta ze skanera kodów uzyskać wszystkie informacje o kolorach tokenu.  
  
 Skaner musi wypełnić <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury dla każdego tokenu ona znajduje. Ta struktura zawiera informacje, takie jak zakres token zajmuje, indeks koloru do użycia, jakiego typu jest wyzwalacze tokenów i tokenów (zobacz <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Kolorowanie, potrzebne są tylko indeks zakresu i kolor <xref:Microsoft.VisualStudio.Package.Colorizer> klasy.  
  
 Indeks koloru przechowywane w <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury jest zazwyczaj wartość z zakresu od <xref:Microsoft.VisualStudio.Package.TokenColor> wyliczenia, która udostępnia wiele indeksów o nazwie odpowiadającej do różnych elementów języka, takich jak słowa kluczowe i operatorów. W przypadku niestandardowych elementów z możliwością kolorowania listy dopasowań elementy są prezentowane w <xref:Microsoft.VisualStudio.Package.TokenColor> wyliczenie, możesz po prostu użyć wyliczenia jako kolor dla każdego tokenu. Jednak jeśli masz dodatkowe elementy z możliwością kolorowania lub nie chcesz używać istniejącej wartości w tej kolejności, można rozmieścić listy niestandardowe elementy z możliwością kolorowania do własnych potrzeb i zwróć odpowiedni indeks do tej listy. Pamiętaj tylko o indeks, aby rzutować <xref:Microsoft.VisualStudio.Package.TokenColor> podczas zapisywania w <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury; [!INCLUDE[vs_current_short](../../includes/vs-current-short-md.md)] widzi tylko indeks.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak skaner może identyfikować trzech typów tokenu: cyfry, znaki interpunkcyjne i identyfikatory (wszystko, co nie jest liczbą ani znaków interpunkcyjnych). W tym przykładzie jest tylko w celach ilustracyjnych i nie stanowi kompleksowe implementacji analizator i skaner. Przyjęto założenie, że istnieje `Lexer` klasy `GetNextToken()` metodę, która zwraca wartość typu ciąg.  
  
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
 [Funkcje usługi starszego języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Starszego języka usługi analizator i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
