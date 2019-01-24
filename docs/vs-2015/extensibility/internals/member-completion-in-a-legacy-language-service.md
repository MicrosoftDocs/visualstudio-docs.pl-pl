---
title: Uzupełnianie składowych w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a1fb236a4ce3b88f97dd94867b8ff5b7403db328
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54776461"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Uzupełnianie składowych w starszej wersji usługi językowej
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Uzupełnianie składowych IntelliSense jest etykietka narzędzia, która zawiera listę możliwych elementów członkowskich z określonego zakresu, takich jak klasy, struktury, wyliczenia lub przestrzeni nazw. Na przykład w języku C#, jeśli użytkownik wpisze "this" następuje kropka, listę wszystkich elementów członkowskich klasy lub struktury w bieżącym zakresie jest przedstawiona na liście, z którego użytkownik może wybrać.  
  
 Środowiska pakietu zarządzanego (MPF) zapewnia obsługę etykietki narzędzia i zarządzanie nimi na liście w etykietce narzędzia; wszystko, co jest potrzebne jest współpraca z analizatora do dostarczania danych, który pojawia się na liście.  
  
 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [rozszerzanie usług edytora i języka](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.  
  
## <a name="how-it-works"></a>Jak to działa  
 Poniżej przedstawiono dwa sposoby, w których lista składowych jest wyświetlana przy użyciu klas MPF:  
  
- Pozycjonowanie karetkę na identyfikator lub po znaku zakończenia elementu członkowskiego i wybierając polecenie **List Members** z **IntelliSense** menu.  
  
- <xref:Microsoft.VisualStudio.Package.IScanner> Skanera wykrywa znak zakończenia elementu członkowskiego i ustawia token wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> dla tego znaku.  
  
  Znak zakończenia elementu członkowskiego wskazuje członek klasy, struktury lub wyliczenia z. Na przykład w języku C# lub Visual Basic znak zakończenia elementu członkowskiego jest `.`, a w języku C++ znak albo `.` lub `->`. Wyzwalacz ma wartość po znaku wybierz element członkowski jest skanowany.  
  
### <a name="the-intellisense-member-list-command"></a>Polecenie List Członkowskich IntelliSense  
 <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> Polecenie inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody <xref:Microsoft.VisualStudio.Package.Source> klasy i <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> z kolei wywołuje metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora metoda przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
 Analizator Określa kontekst aktualnej pozycji, a także token w obszarze lub bezpośrednio przed bieżącej pozycji. Oparte na ten token, zobaczy listy deklaracji. Na przykład w języku C#, jeśli położenie karetki na składowej klasy i wybierz **List Members**, zostanie wyświetlona lista wszystkich elementów członkowskich klasy. Jeśli umieścisz karetki, po upływie czasu, który następuje po zmiennej obiektu, masz dostęp do listy wszystkich elementów członkowskich klasy, które reprezentuje obiekt. Należy pamiętać, że karetka jest ustawiana na elemencie członkowskim, gdy jest wyświetlana lista członków, wybierając członka z listy zastąpienie elementu członkowskiego, który karetka znajduje się na każdy z nich na liście.  
  
### <a name="the-token-trigger"></a>Token wyzwalacza  
 <xref:Microsoft.VisualStudio.Package.TokenTriggers> Wyzwalacza inicjuje wywołanie <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody <xref:Microsoft.VisualStudio.Package.Source> klasy i <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metody, z kolei wywołuje analizator przyczynę analizy <xref:Microsoft.VisualStudio.Package.ParseReason> (jeśli dołączone do tokenów wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> flagi Przyczyna analizy <xref:Microsoft.VisualStudio.Package.ParseReason> łączy które Wybór elementu członkowskiego i wyróżnianie nawiasów klamrowych).  
  
 Analizator Określa kontekst bieżącej pozycji, a także został wpisany należy wybrać znak. Z tej informacji analizator tworzy listę wszystkich elementów członkowskich w żądanym zakresie. Ta lista deklaracji jest przechowywany w <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiekt, który jest zwracany z <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody. Jeśli zwracane są wszystkie deklaracje, jest wyświetlana etykietka narzędzia elementu członkowskiego ukończenia. Etykietka narzędzia która jest zarządzana przez wystąpienie <xref:Microsoft.VisualStudio.Package.CompletionSet> klasy.  
  
## <a name="enabling-support-for-member-completion"></a>Włączanie obsługi uzupełnianie składowych  
 Konieczne jest posiadanie `CodeSense` wpis rejestru równa 1, aby obsługiwać dowolną operację funkcji IntelliSense. Ten wpis rejestru można ustawić za pomocą nazwany parametr przekazywany do <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> atrybut użytkownika skojarzonego z pakietem języka. Klasy usługi w języka odczytać wartości wpisu rejestru z <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> właściwość <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.  
  
 Jeśli skaner zwróci tokenów wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers>, Twoje analizatora zwraca listę deklaracje, a następnie jest wyświetlany na liście uzupełniania elementu członkowskiego.  
  
## <a name="supporting-member-completion-in-the-scanner"></a>Obsługa uzupełnianie składowych w skanera  
 Skaner musi być w stanie wykryć znak zakończenia elementu członkowskiego i ustaw tokenów wyzwalacza <xref:Microsoft.VisualStudio.Package.TokenTriggers> po znaku jest analizowany.  
  
### <a name="example"></a>Przykład  
 Oto uproszczony przykład wykrywanie znaku zakończenia elementu członkowskiego i ustawiając odpowiednią <xref:Microsoft.VisualStudio.Package.TokenTriggers> flagi. Ten przykład dotyczy tylko w celach ilustracyjnych. Zakłada się, że skaner zawiera metodę `GetNextToken` , identyfikuje i zwraca tokenów z wiersza tekstu. Przykładowy kod po prostu ustawia wyzwalacz zawsze wtedy, gdy jej widzi właściwego rodzaju znak.  
  
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
  
## <a name="supporting-member-completion-in-the-parser"></a>Obsługa uzupełnianie składowych w analizatorze składni  
 Na zakończenie elementu członkowskiego <xref:Microsoft.VisualStudio.Package.Source> klasy wywołania <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metody. Listy należy zaimplementować w klasie, która jest pochodną <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Zobacz <xref:Microsoft.VisualStudio.Package.Declarations> klasy, aby uzyskać szczegółowe informacje o metodach, należy zaimplementować.  
  
 Analizator jest wywoływana z <xref:Microsoft.VisualStudio.Package.ParseReason> lub <xref:Microsoft.VisualStudio.Package.ParseReason> po wpisaniu znaku wybierz element członkowski. Lokalizacji określonej <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt jest natychmiast po zakończeniu elementu członkowskiego, wybierz znak. Analizator musi zebrać nazwy wszystkich elementów członkowskich, które mogą być wyświetlane na liście składowych w konkretnym momencie w kodzie źródłowym. Następnie analizator musi przeanalizować bieżący wiersz, aby określić zakres, który użytkownik chce skojarzone ze znakiem wybierz element członkowski.  
  
 Ten zakres opiera się na typ identyfikatora, należy wybrać znaków. Na przykład w języku C#, biorąc pod uwagę zmiennej składowej `languageService` zawierający typ `LanguageService`, wpisz **languageService.** Tworzy listę wszystkich członków `LanguageService` klasy. Również w języku C# wpisując **to.** Tworzy listę wszystkich elementów członkowskich klasy w bieżącym zakresie.  
  
### <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wypełnić <xref:Microsoft.VisualStudio.Package.Declarations> listy. Ten kod przyjęto założenie, że analizator tworzy deklarację i dodaje go do listy, wywołując `AddDeclaration` metody `TestAuthoringScope` klasy.  
  
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
