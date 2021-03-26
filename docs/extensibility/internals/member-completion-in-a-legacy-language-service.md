---
title: Ukończenie elementu członkowskiego w starszej wersji usługi językowej | Microsoft Docs
description: Dowiedz się, jak etykietka narzędzia do uzupełniania elementów członkowskich IntelliSense działa w starszej wersji usługi językowej i jak jest obsługiwana przez strukturę pakietu zarządzanego (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5279b3a96cb9658b968a5d51bbd8b1c2a41862b6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095137"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Uzupełnianie składowych w starszej wersji usługi językowej

Uzupełnienie elementu członkowskiego IntelliSense to etykietka narzędzia, która wyświetla listę możliwych członków określonego zakresu, takich jak Klasa, struktura, Wyliczenie lub przestrzeń nazw. Na przykład w języku C#, jeśli użytkownik wpisze "This", a po nim kropka, lista wszystkich elementów członkowskich klasy lub struktury w bieżącym zakresie zostanie przedstawiona na liście, z której użytkownik może wybrać.

Struktura pakietu zarządzanego (MPF) zapewnia obsługę etykietki narzędzia i zarządzanie listą w etykietce narzędzia. wymagana jest współpraca z analizatora, aby dostarczyć dane, które pojawiają się na liście.

Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie edytora i usług językowych](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="how-it-works"></a>Jak to działa

Poniżej przedstawiono dwa sposoby wyświetlania listy elementów członkowskich przy użyciu klas MPF:

- Pozycjonowanie karetki na identyfikatorze lub po znaku uzupełniania elementu członkowskiego i wybieranie **listy członków** z menu **IntelliSense** .

- <xref:Microsoft.VisualStudio.Package.IScanner>Skaner wykrywa znak uzupełniający elementu członkowskiego i ustawia wyzwalacz tokenu [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) dla tego znaku.

Znak uzupełniania elementu członkowskiego wskazuje, że element członkowski klasy, struktury lub wyliczenia ma być przestrzegany. Na przykład w języku C# lub Visual Basic znak uzupełniania elementu członkowskiego jest `.` , a w języku C++ znak jest albo `.` lub `->` . Wartość wyzwalacza jest ustawiana podczas skanowania elementu członkowskiego SELECT.

### <a name="the-intellisense-member-list-command"></a>Polecenie list elementów członkowskich IntelliSense

<xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID>Polecenie inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody <xref:Microsoft.VisualStudio.Package.Source> klasy i <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody, z kolei wywołuje <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser metody z przyczyną analizy [ParseReason. DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Analizator określa kontekst bieżącego położenia oraz token w obszarze lub bezpośrednio przed bieżącą pozycją. Na podstawie tego tokenu przedstawiono listę deklaracji. Na przykład w języku C#, Jeśli umieszczasz karetkę na elemencie członkowskim klasy i wybierzesz **listę członków**, otrzymujesz listę wszystkich elementów członkowskich klasy. Jeśli podasz karetkę po okresie, który następuje po zmiennej obiektu, otrzymujesz listę wszystkich elementów członkowskich klasy reprezentowanej przez obiekt. Należy zauważyć, że jeśli karetka jest umieszczona na elemencie członkowskim, gdy lista składowych jest pokazywana, wybranie elementu członkowskiego z listy spowoduje zamienienie elementu członkowskiego karetki na liście.

### <a name="the-token-trigger"></a>Wyzwalacz tokenu

Wyzwalacz [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody <xref:Microsoft.VisualStudio.Package.Source> klasy i <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody, z kolei wywołuje parser z przyczyną analizy [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Jeśli wyzwalacz tokenu zawiera również flagę [TokenTriggers. MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) , powód analizy to [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), który łączy wybór członków i wyróżnianie nawiasów klamrowych.

Analizator określa kontekst bieżącego położenia, a także to, co zostało wpisane przed wybraniem znaku elementu członkowskiego. Z tych informacji Analizator tworzy listę wszystkich członków żądanego zakresu. Ta lista deklaracji jest przechowywana w <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiekcie, który jest zwracany z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. W przypadku zwrócenia jakichkolwiek deklaracji zostanie wyświetlona etykietka narzędzia do uzupełniania elementu członkowskiego. Etykietka narzędzia jest zarządzana przez wystąpienie <xref:Microsoft.VisualStudio.Package.CompletionSet> klasy.

## <a name="enable-support-for-member-completion"></a>Włącz obsługę ukończenia dla elementu członkowskiego

Aby można było `CodeSense` obsługiwać dowolną operację IntelliSense, wpis rejestru musi mieć wartość 1. Ten wpis rejestru można ustawić przy użyciu nazwanego parametru przesłanego do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybutu użytkownika skojarzonego z pakietem języka. Klasy usługi językowej odczytują wartość tego wpisu rejestru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwości <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.

Jeśli skaner zwraca wyzwalacz tokenu [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)i Analizator zwraca listę deklaracji, zostanie wyświetlona lista uzupełniania elementów członkowskich.

## <a name="support-member-completion-in-the-scanner"></a>Obsługa uzupełniania elementów członkowskich w skanerze

Skaner musi być w stanie wykryć znak uzupełniania elementu członkowskiego i ustawić wyzwalacz tokenu [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) , gdy ten znak jest analizowany.

### <a name="scanner-example"></a>Przykład skanera

Poniżej przedstawiono uproszczony przykład wykrywania znaku zakończenia elementu członkowskiego i ustawiania odpowiedniej <xref:Microsoft.VisualStudio.Package.TokenTriggers> flagi. Ten przykład służy tylko do celów informacyjnych. Przyjęto założenie, że skaner zawiera metodę `GetNextToken` , która identyfikuje i zwraca tokeny z wiersza tekstu. Przykładowy kod po prostu ustawia wyzwalacz za każdym razem, gdy widzi właściwy rodzaj znaku.

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

## <a name="support-member-completion-in-the-parser"></a>Obsługa uzupełniania elementu członkowskiego w analizatorze

W przypadku wykonania elementu członkowskiego <xref:Microsoft.VisualStudio.Package.Source> Klasa wywołuje <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodę. Należy zaimplementować listę w klasie, która jest pochodną <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Zapoznaj się z <xref:Microsoft.VisualStudio.Package.Declarations> klasą, aby uzyskać szczegółowe informacje o metodach, które należy zaimplementować.

Analizator składni jest wywoływany z [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) lub [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) , gdy zostanie wprowadzony znak SELECT elementu członkowskiego. Lokalizacja określona w <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekcie jest natychmiast po zaznaczeniu elementu członkowskiego. Analizator musi zbierać nazwy wszystkich elementów członkowskich, które mogą znajdować się na liście elementów członkowskich w tym konkretnym miejscu w kodzie źródłowym. Następnie analizator musi analizować bieżący wiersz, aby określić zakres, który użytkownik chce skojarzyć z elementem członkowskim SELECT.

Ten zakres jest oparty na typie identyfikatora przed wybraniem znaku elementu członkowskiego. Na przykład w języku C#, dana zmienna elementu członkowskiego `languageService` ma typ `LanguageService` , wpisując **languageService.** tworzy listę wszystkich elementów członkowskich `LanguageService` klasy. W języku C# wpisz **to.** tworzy listę wszystkich elementów członkowskich klasy w bieżącym zakresie.

### <a name="parser-example"></a>Przykład parsera

W poniższym przykładzie pokazano jeden ze sposobów wypełniania <xref:Microsoft.VisualStudio.Package.Declarations> listy. Ten kod zakłada, że analizator tworzy deklarację i dodaje ją do listy przez wywołanie `AddDeclaration` metody w `TestAuthoringScope` klasie.

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
