---
title: Kolorowanie składni w usłudze języka starszych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], syntax highlighting
- colorization, supporting in language services [managed package framework]
- syntax highlighting, supporting in language services [managed package framework]
- language services [managed package framework], colorization
ms.assetid: 1ca1736a-f554-42e4-a9c7-fe8c3c1717df
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1d82a85958fd979a3d9d44375656b08356ef09d9
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
ms.locfileid: "31135951"
---
# <a name="syntax-colorizing-in-a-legacy-language-service"></a>Kolorowanie składni w starsza wersja usługi języka
Kolorowanie składni to funkcja, która powoduje, że różne elementy języka programowania, który będzie wyświetlany w pliku źródłowym w różnych kolorach i style. Do obsługi tej funkcji, należy podać analizator lub skanera, który można określić typy elementów leksykalne lub tokenów w pliku. Wiele języków rozróżnienia słowa kluczowe, ograniczniki (na przykład lub nawiasy klamrowe nawiasy) i komentarze przez kolorowanie je na różne sposoby.  
  
 Usługi w starszej wersji języka są zaimplementowane jako część pakiet VSPackage, ale jest nowsza sposób implementowania funkcji usługi języka Aby korzystać z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Zaleca się zacząć Edytor nowy interfejs API tak szybko, jak to możliwe. Spowoduje to poprawić wydajność usługi języka i pozwala korzystać z nowych funkcji edytora.  
  
## <a name="implementation"></a>Implementacja  
 Aby obsługiwać kolorowania, struktura zarządzanego pakietu (MPF) obejmuje <xref:Microsoft.VisualStudio.Package.Colorizer> klasy, która implementuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> interfejsu. Ta klasa współdziała z <xref:Microsoft.VisualStudio.Package.IScanner> do określenia tokenu i kolory. Aby uzyskać więcej informacji na skanerów, zobacz [analizatora usługi języka starszych i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md). <xref:Microsoft.VisualStudio.Package.Colorizer> Klasy następnie oznacza każdego znaku token z informacji o kolorze i zwraca te informacje do edytora wyświetlania pliku źródłowego.  
  
 Kolor informacje zwrócone z edytora jest indeks do listy elementów colorable. Każdy element colorable określa wartość koloru i zestaw atrybutów czcionek, takie jak pogrubienie lub przekreślenia. Edytor dostarcza zestaw elementy colorable domyślne, których można użyć usługi języka. To wszystko, co należy zrobić, określ indeks kolor odpowiednie dla każdego typu tokenu. Można jednak udostępniają zestaw niestandardowych elementów colorable i indeksów, które należy podać tokenów i listy elementów colorable zamiast domyślnej listy odwołania. Należy także ustawić `RequestStockColors` wpisu rejestru na 0 (lub nie określaj `RequestStockColors` wpis na wszystkich) do obsługi kolorów niestandardowych. Można ustawić ten wpis rejestru z nazwanym parametrem <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu zdefiniowane przez użytkownika. Aby uzyskać więcej informacji na zarejestrowanie usługi języka i ustawienie jej opcji, zobacz [zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
## <a name="custom-colorable-items"></a>Niestandardowe elementy Colorable  
 Aby podać własne niestandardowe elementy colorable, konieczne jest przesłonięcie <xref:Microsoft.VisualStudio.Package.LanguageService.GetItemCount%2A> i <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorableItem%2A> metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Pierwsza metoda zwraca liczbę niestandardowych colorable elementy, które obsługuje usługi języka oraz drugi pobiera niestandardowego elementu colorable według indeksu. Utworzysz domyślnej listy elementów colorable niestandardowych. W Konstruktorze usługi języka wszystko, co należy zrobić jest podanie każdego colorable elementu o nazwie. Visual Studio automatycznie obsługuje sytuacji, gdy użytkownik wybierze inny zestaw colorable elementów. Ta nazwa jest wyświetlana w **czcionki i kolory** strony właściwości na **opcje** okno dialogowe (dostępne w programie Visual Studio **narzędzia** menu) i określa tej nazwy, który kolor, który zastąpił użytkownika. Wybór użytkownika są przechowywane w pamięci podręcznej w rejestrze i dostępny przez nazwę koloru. **Czcionki i kolory** strony właściwości zawiera listę wszystkich nazw kolorów w kolejności alfabetycznej, kolory niestandardowe można grupować wg poprzedzających każdej nazwie kolor nazwę języka; na przykład "**TestLanguage — komentarz**"i"**TestLanguage — słowo kluczowe**". Lub grupę, Twoje colorable elementów według typów, "**komentarz (TestLanguage)**"i"**— słowo kluczowe (TestLanguage)**". Grupowanie według nazwy języka jest preferowana.  
  
> [!CAUTION]
>  Zdecydowanie zaleca się uwzględnić nazwę języka w nazwie elementu colorable w celu uniknięcia konfliktów z już istniejącymi nazwami colorable elementu.  
  
> [!NOTE]
>  Jeśli zmienisz nazwę jednego z kolorów podczas tworzenia, należy zresetować pamięci podręcznej programu Visual Studio utworzony przy pierwszym uruchomieniu korzystał kolorów. Możesz to zrobić, uruchamiając **Zresetuj eksperymentalne Hive** polecenia w menu programu Visual Studio SDK.  
  
 Należy pamiętać, że nigdy nie odwołuje się pierwszy element na liście elementów colorable. Visual Studio udostępnia zawsze domyślne kolory tekstu i atrybuty dla tego elementu. Najprostszy sposób postępowania z tym jest podanie symbol zastępczy elementu colorable jako pierwszy element.  
  
### <a name="high-color-colorable-items"></a>Elementy Colorable High Color  
 Elementy colorable może również obsługiwać wartości 24-bitowego lub wysoki kolorów za pośrednictwem <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu. MPF <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy obsługuje <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfejsu i kolory 24-bitowego są określone w Konstruktorze wraz z normalnym kolorów. Zobacz <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy, aby uzyskać więcej informacji. W poniższym przykładzie pokazano, jak ustawić kolory 24-bitowego słowa kluczowe i komentarze. Kolory 24-bitowego są używane, gdy 24-bitowe jest obsługiwany na pulpicie użytkownika; w przeciwnym razie są używane kolory zwykłego tekstu.  
  
 Należy pamiętać, że są to domyślne kolory dla danego języka; Użytkownik może zmienić kolory do ich mają.  
  
### <a name="example"></a>Przykład  
 Ten przykład przedstawia sposób deklarowanie i wypełnić tablicę niestandardowych elementów colorable za pomocą <xref:Microsoft.VisualStudio.Package.ColorableItem> klasy. W tym przykładzie kolorów — słowo kluczowe i komentarza, za pomocą kolorów 24-bitowego.  
  
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
  
## <a name="the-colorizer-class-and-the-scanner"></a>Klasa Colorizer i skanera  
 Podstawowym <xref:Microsoft.VisualStudio.Package.LanguageService> klasa ma <xref:Microsoft.VisualStudio.Package.LanguageService.GetColorizer%2A> metoda tego instantiantes <xref:Microsoft.VisualStudio.Package.Colorizer> klasy. Skaner, która jest zwracana z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody jest przekazywany do <xref:Microsoft.VisualStudio.Package.Colorizer> konstruktora klasy.  
  
 Musisz zaimplementować <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody w wersji produktu <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. <xref:Microsoft.VisualStudio.Package.Colorizer> Klasy używa skanera uzyskanie wszystkich informacji o kolorze tokenu.  
  
 Skaner musi wypełnić <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury dla każdego tokenu znalezione. Ta struktura zawiera informacje, takie jak zakres token zajmuje indeksu kolor do używania, jakiego typu jest wyzwalaczy token i token (zobacz <xref:Microsoft.VisualStudio.Package.TokenTriggers>). Wymagane są tylko indeks zakresu i kolor kolorowania przez <xref:Microsoft.VisualStudio.Package.Colorizer> klasy.  
  
 Indeks koloru przechowywane w <xref:Microsoft.VisualStudio.Package.TokenInfo> struktura jest zwykle wartość z zakresu od <xref:Microsoft.VisualStudio.Package.TokenColor> wyliczenia, która udostępnia wiele indeksów o nazwie odpowiadającej różnych elementów języka, takich jak słowa kluczowe i operatory. Jeśli Twoje własne elementy colorable listy dopasowań elementy przedstawionych w <xref:Microsoft.VisualStudio.Package.TokenColor> wyliczenia, możesz użyć wyliczenia jako kolor dla każdego tokenu. Jednak jeśli masz dodatkowe elementy colorable lub nie chcesz użyć istniejących wartości w tej kolejności, można rozmieścić listy niestandardowe elementy colorable do własnych potrzeb i zwróć odpowiedni indeks do tej listy. Po prostu upewnij się, można rzutować indeks <xref:Microsoft.VisualStudio.Package.TokenColor> podczas zapisywania w <xref:Microsoft.VisualStudio.Package.TokenInfo> struktury; [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] widzi tylko indeksu.  
  
### <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak skanera może identyfikować trzy typy tokenów: cyfry, znaki interpunkcyjne i identyfikatorów (wszystko, co nie jest liczbą ani znaków interpunkcyjnych). W tym przykładzie jest tylko w celach ilustracyjnych i nie stanowi kompleksowe analizatora i skanera implementacji programu. Przyjęto założenie, że istnieje `Lexer` klasy z `GetNextToken()` metodę, która zwraca wartość typu ciąg.  
  
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
 [Funkcje usługi starszej wersji języka](../../extensibility/internals/legacy-language-service-features1.md)   
 [Analizatora usługi starszej wersji języka i skanera](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)   
 [Zarejestrowanie starsza wersja usługi języka](../../extensibility/internals/registering-a-legacy-language-service1.md)