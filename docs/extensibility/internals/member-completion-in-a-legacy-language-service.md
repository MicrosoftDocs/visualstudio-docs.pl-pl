---
title: Ukończenie przez członka w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707198"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Uzupełnianie składowych w starszej wersji usługi językowej

IntelliSense Member Completion to wskazówka narzędzia, która wyświetla listę możliwych elementów członkowskich określonego zakresu, takich jak klasa, struktura, wyliczenie lub obszar nazw. Na przykład w języku C#, jeśli użytkownik wpisuje "this", po którym następuje kropka, lista wszystkich członków klasy lub struktury w bieżącym zakresie jest przedstawiona na liście, z której użytkownik może wybrać.

Struktura pakietu zarządzanego (MPF) zapewnia obsługę etykietki narzędzia i zarządzanie listą w etykietce narzędzia; wszystko, co jest potrzebne, to współpraca z analizatorem w celu dostarczenia danych, które pojawiają się na liście.

Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="how-it-works"></a>Jak to działa

Poniżej przedstawiono dwa sposoby, w których lista członków jest wyświetlana przy użyciu klas MPF:

- Pozycjonowanie karetki na identyfikatorze lub po znaku ukończenia elementu członkowskiego i wybranie **listy członków** z menu **IntelliSense.**

- Skaner <xref:Microsoft.VisualStudio.Package.IScanner> wykrywa znak ukończenia elementu członkowskiego i ustawia wyzwalacz tokenu [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) dla tego znaku.

Znak ukończenia elementu członkowskiego wskazuje, że element członkowski klasy, struktury lub wyliczenia jest do naśladowania. Na przykład w języku C# lub Visual `.`Basic znakiem ukończenia elementu członkowskiego jest `.` znak `->`, podczas gdy w języku C++ znak jest znakiem lub . Wartość wyzwalacza jest ustawiana podczas skanowania znaku wyboru elementu członkowskiego.

### <a name="the-intellisense-member-list-command"></a>Polecenie IntelliSense Member List

Polecenie <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> inicjuje wywołanie metody <xref:Microsoft.VisualStudio.Package.Source> na <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> klasy i metoda, <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> z kolei wywołuje analizator metody z powodu analizy [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Analizator określa kontekst bieżącej pozycji, a także tokenu w obszarze lub bezpośrednio przed bieżącą pozycją. Na podstawie tego tokenu przedstawiona jest lista deklaracji. Na przykład w języku C#, jeśli pozycjonujesz daszek na człowiecie i wybierzesz **listę członków**, otrzymasz listę wszystkich członków klasy. Jeśli pozycjonujesz karetkę po okresie, który następuje po zmiennej obiektu, otrzymasz listę wszystkich członków klasy, którą reprezentuje obiekt. Należy zauważyć, że jeśli cieszy jest umieszczony na członka, gdy lista członków jest wyświetlany, wybranie członka z listy zastępuje element członkowski, na którym znajduje się opiekun z jednym na liście.

### <a name="the-token-trigger"></a>Wyzwalacz tokenu

[TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) wyzwala wyzwalania zainicjowania <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> wywołania <xref:Microsoft.VisualStudio.Package.Source> metody <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> na klasy i metoda, z kolei wywołuje analizatora z powodu analizy [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Jeśli wyzwalacz tokenu również [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) flagi, przyczyna analizy jest [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), który łączy wybór elementu członkowskiego i wyróżniania nawiasów klamrowych.

Analizator określa kontekst bieżącej pozycji, a także to, co zostało wpisane przed znakiem wyboru elementu członkowskiego. Na podstawie tych informacji analizator tworzy listę wszystkich elementów członkowskich żądanego zakresu. Ta lista deklaracji jest przechowywana w <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiekcie, który jest zwracany z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Jeśli wszystkie deklaracje są zwracane, zostanie wyświetlona wskazówka narzędzia zakończenia elementu członkowskiego. Etykietka narzędzia jest zarządzana <xref:Microsoft.VisualStudio.Package.CompletionSet> przez wystąpienie klasy.

## <a name="enable-support-for-member-completion"></a>Włącz obsługę ukończenia przez członków

Aby obsługiwać `CodeSense` dowolną operację IntelliSense, musi być ustawiony wpis rejestru na 1. Ten wpis rejestru można ustawić z nazwanym parametrem przekazanym atrybutowi <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> użytkownika skojarzonemu z pakietem językowym. Klasy usługi języka odczytywać wartość tego <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> wpisu <xref:Microsoft.VisualStudio.Package.LanguagePreferences> rejestru z właściwości w klasie.

Jeśli skaner zwraca wyzwalacz tokenu [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>), a analizator zwraca listę deklaracji, zostanie wyświetlona lista ukończenia elementu członkowskiego.

## <a name="support-member-completion-in-the-scanner"></a>Zakończenie członka pomocy technicznej w skanerze

Skaner musi być w stanie wykryć znak ukończenia elementu członkowskiego i ustawić wyzwalacz tokenu [TokenTriggers.MemberSelect,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) gdy ten znak jest analizowany.

### <a name="scanner-example"></a>Przykład skanera

Oto uproszczony przykład wykrywania znaku ukończenia elementu członkowskiego <xref:Microsoft.VisualStudio.Package.TokenTriggers> i ustawiania odpowiedniej flagi. Ten przykład służy wyłącznie do celów ilustracyjnych. Przyjęto założenie, że skaner `GetNextToken` zawiera metodę, która identyfikuje i zwraca tokeny z wiersza tekstu. Przykładowy kod po prostu ustawia wyzwalacz, gdy widzi odpowiedni rodzaj znaku.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>Zakończenie członka pomocy technicznej w analizatorze

W przypadku ukończenia <xref:Microsoft.VisualStudio.Package.Source> elementu <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> członkowskiego klasa wywołuje metodę. Należy zaimplementować listę w klasie, <xref:Microsoft.VisualStudio.Package.Declarations> która pochodzi od klasy. Zobacz <xref:Microsoft.VisualStudio.Package.Declarations> klasy szczegółowe informacje na temat metod, które należy zaimplementować.

Analizator jest wywoływany z [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) lub [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) po wpisaniu znaku wyboru elementu członkowskiego. Lokalizacja podana <xref:Microsoft.VisualStudio.Package.ParseRequest> w obiekcie jest natychmiast po element członkowski wybrać znak. Analizator musi zbierać nazwy wszystkich elementów członkowskich, które mogą pojawić się na liście elementów członkowskich w tym określonym punkcie w kodzie źródłowym. Następnie analizator musi przeanalizować bieżący wiersz, aby określić zakres, który użytkownik chce skojarzony z znakiem wyboru elementu członkowskiego.

Ten zakres jest oparty na typie identyfikatora przed znakiem wyboru elementu członkowskiego. Na przykład w języku C#, `languageService` biorąc pod `LanguageService`uwagę zmienną elementu członkowskiego, która ma typ , wpisując **languageService.** tworzy listę wszystkich członków `LanguageService` klasy. Również w języku C#, wpisując **to.** tworzy listę wszystkich członków klasy w bieżącym zakresie.

### <a name="parser-example"></a>Przykład analizatora

W poniższym przykładzie przedstawiono <xref:Microsoft.VisualStudio.Package.Declarations> jeden ze sposobów wypełniania listy. Ten kod zakłada, że parser konstruuje deklarację i `AddDeclaration` dodaje ją `TestAuthoringScope` do listy, wywołując metodę w klasie.

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
