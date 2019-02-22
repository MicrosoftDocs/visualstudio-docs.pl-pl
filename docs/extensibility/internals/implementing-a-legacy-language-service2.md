---
title: Implementowanie starszej wersji usługi językowej2 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8592103bad3f6949f37a190c25633398af89a166
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56622946"
---
# <a name="implementing-a-legacy-language-service"></a>Implementowanie starszej wersji usługi językowej
Aby zaimplementować usługi języka przy użyciu środowiska pakietu zarządzanego (MPF), należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.LanguageService> klasę i zaimplementować następujące metody abstrakcyjne i właściwości:

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> — Metoda

- <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> — Metoda

- <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> — Metoda

- <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> Właściwości

  Zobacz odpowiednią sekcje poniżej, aby uzyskać szczegółowe informacje dotyczące implementowania tych metod i właściwości.

  Aby obsługiwać dodatkowe funkcje, usługi w języka może być konieczne wyprowadzenia klasy z jednej z klas usługi języka MPF; na przykład, aby zapewnić obsługę dodatkowych poleceń, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy i zastąpić niektóre polecenia obsługi metod (zobacz <xref:Microsoft.VisualStudio.Package.ViewFilter> Aby uzyskać szczegółowe informacje). <xref:Microsoft.VisualStudio.Package.LanguageService> Klasa udostępnia szereg metod, które są wywoływane w celu tworzenia nowych wystąpień różnych klas i zastąpić metodę tworzenia odpowiednie, aby zapewnić wystąpienia klasy. Na przykład, należy zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy w celu zwrócenia wystąpienia własne <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy. Zobacz sekcję "Utworzenie wystąpienia klasy niestandardowe", aby uzyskać więcej informacji.

  Usługi języka może też podawać swój własny ikon, które są używane w wielu miejscach. Na przykład gdy jest wyświetlana lista dokańczania IntelliSense, każdy element na liście mogą mieć skojarzone z nią oznaczenie elementu jako metody, klasy, przestrzeni nazw, właściwości, ikona lub niezależnie od rodzaju jest niezbędne dla danego języka. Te ikony są używane na wszystkich listach IntelliSense, **pasek nawigacyjny**, a następnie w **lista błędów** okno zadań. Zobacz sekcję "Obrazy usługi języka" poniżej, aby uzyskać szczegółowe informacje.

## <a name="getlanguagepreferences-method"></a>Metoda GetLanguagePreferences
 <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> Metoda zawsze zwraca to samo wystąpienie elementu <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Możesz użyć podstawowa <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy, jeśli nie potrzebujesz żadnych dodatkowych preferencje dotyczące usługi języka. Klasy usługi w języka MPF przyjęto założenie, co najmniej obecności base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.

### <a name="example"></a>Przykład
 Typowa implementacja metody w tym przykładzie <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metody. W tym przykładzie użyto base <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(TestLanguageService).GUID,
                                                        this.Name );
                m_preferences.Init();
            }
            return m_preferences;
        }
    }
}
```

## <a name="getscanner-method"></a>Metoda GetScanner
 Ta metoda zwraca wystąpienie <xref:Microsoft.VisualStudio.Package.IScanner> obiekt, który implementuje analizator w wierszu lub skaner używane do uzyskiwania tokenów i ich typy i wyzwalacze. Skaner ten jest używany w <xref:Microsoft.VisualStudio.Package.Colorizer> klasy kolorowania, mimo że skaner można również w celu uzyskania typy tokenów i wyzwalacze jako prelude bardziej złożonych operacji analizy. Należy podać klasę, która implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu i musi implementować wszystkie metody na <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu.

### <a name="example"></a>Przykład
 Typowa implementacja metody w tym przykładzie <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody. `TestScanner` Klasy implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejsu (niewyświetlany).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private TestScanner m_scanner;

        public override IScanner GetScanner(IVsTextLines buffer)
        {
            if (m_scanner == null)
            {
                m_scanner = new TestScanner(buffer);
            }
            return m_scanner;
        }
    }
}
    internal class TestScanner : IScanner
    {
        private IVsTextBuffer m_buffer;
        string m_source;

        public TestScanner(IVsTextBuffer buffer)
        {
            m_buffer = buffer;
        }

        bool IScanner.ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo, ref int state)
        {
            tokenInfo.Type = TokenType.Unknown;
            tokenInfo.Color = TokenColor.Text;
            return true;
        }

        void IScanner.SetSource(string source, int offset)
        {
            m_source = source.Substring(offset);
        }
    }

```

## <a name="parsesource-method"></a>Metoda ParseSource
 Analizuje plik źródłowy, na podstawie liczby różnych powodów. Ta metoda otrzymuje <xref:Microsoft.VisualStudio.Package.ParseRequest> obiekt, który w tym artykule opisano, czego oczekuje się od określonej operacji analizy. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda wywołuje analizator bardziej złożone, określająca funkcję tokena i zakresu. <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> Metoda jest używana w obsłudze dla operacji IntelliSense, a także parowanie nawiasów klamrowych. Nawet jeśli nie obsługują takie zaawansowane operacje, możesz nadal musi zwracać prawidłowe <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu i że należy utworzyć klasę, która implementuje <xref:Microsoft.VisualStudio.Package.AuthoringScope> interfejs i implementować wszystkie metody w tym interfejsie. Może zwracać wartości null, ze wszystkich metod, ale <xref:Microsoft.VisualStudio.Package.AuthoringScope> sam obiekt nie może być wartością null.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono minimalne wykonanie <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metody i <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy wystarczające umożliwić usłudze języka skompilować i działać bez faktycznego obsługi bardziej zaawansowanych funkcji.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            return new TestAuthoringScope();
        }
    }

    internal class TestAuthoringScope : AuthoringScope
    {
        public override string GetDataTipText(int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return null;
        }

        public override string Goto(VSConstants.VSStd97CmdID cmd, IVsTextView textView, int line, int col, out TextSpan span)
        {
            span = new TextSpan();
            return null;
        }

        public override Methods GetMethods(int line, int col, string name)
        {
            return null;
        }
}
```

## <a name="name-property"></a>Właściwość nazwy
 Ta właściwość zwraca nazwę usługi w języka. Musi to być tej samej nazwie, biorąc pod uwagę, gdy usługa językowa został zarejestrowany. Ta nazwa jest używana w wielu miejscach, jest najbardziej znaczącym którego <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy, której nazwa jest używana do uzyskania dostępu do rejestru. Nie być zlokalizowana nazwa zwracane przez tę właściwość, ponieważ jest używany w rejestrze dla nazwy klucza i wpisu rejestru.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono jedną możliwą implementację <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> właściwości. Należy pamiętać, że tutaj nazwę ustaloną: rzeczywista nazwa mają być uzyskiwane z pliku zasobów, dzięki czemu mogą służyć podczas rejestrowania usługi językowej (zobacz [rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override string Name
        {
            get { return "Test Language"; }
        }
    }
}
```

## <a name="instantiating-custom-classes"></a>Utworzenie wystąpienia klasy niestandardowe
 Zapewnienie wystąpień własne wersje każdej klasy można zastąpić następujące metody w określonych klas.

### <a name="in-the-languageservice-class"></a>W klasie LanguageService

|Metoda|Klasa zwracane|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Do obsługi niestandardowych dodatki do widoku tekstu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Do obsługi niestandardowe właściwości dokumentu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Aby obsługiwać **pasek nawigacyjny**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Do obsługi funkcji w szablonów fragmentów kodu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Do obsługi fragmentów kodu (tej metody zwykle nie jest zastępowany).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Do obsługi dostosowywania <xref:Microsoft.VisualStudio.Package.ParseRequest> struktury (tej metody zwykle nie jest zastępowany).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Do obsługi formatowania kodu źródłowego, określając znaki komentarza i podpisy metod dostosowywania.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Do obsługi dodatkowych poleceń.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Do obsługi, wyróżnianie składni (tej metody zwykle nie jest zastępowany).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Do obsługi dostępu do preferencji językowych. Ta metoda musi zostać wdrożone, ale może zwrócić wystąpienia klasy bazowej.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Aby zapewnić analizator używany do identyfikacji typów tokenów w wierszu. Ta metoda musi zostać wdrożone i <xref:Microsoft.VisualStudio.Package.IScanner> musi pochodzić od.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Aby zapewnić analizator używany do identyfikowania funkcjonalności i zakresie całego pliku źródłowego. Ta metoda musi zostać wdrożone i musi zwrócić wystąpienie wersję <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy. Jeśli wszystkie mają być obsługiwane jest wyróżnianie składni (co wymaga <xref:Microsoft.VisualStudio.Package.IScanner> analizator składni zwrócił z <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metoda), można nic nie zrobisz w przypadku tej metody innej niż powrotu wersję <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy, w której wszystkie metody zwracała wartości null.|

### <a name="in-the-source-class"></a>W klasie źródła

|Metoda|Klasa zwracane|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Dla niestandardowego wyświetlania listy uzupełniania IntelliSense (tej metody zwykle nie jest zastępowany).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Do obsługi znaczniki na liście zadań Lista błędów w szczególności Obsługa funkcji poza otwierania pliku i przechodzenie do wiersza, które spowodowały błąd.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Dostosowywania wyświetlanie etykietek narzędzi informacji parametru funkcji IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Do obsługi komentowanie kodu.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Do zbierania informacji podczas operacji analizy.|

### <a name="in-the-authoringscope-class"></a>W klasie AuthoringScope

|Metoda|Klasa zwracane|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Lista deklaracji, takich jak elementy Członkowskie lub typów. Ta metoda musi zostać wdrożone, ale może zwrócić wartość null. Jeśli ta metoda zwróci prawidłowego obiektu, obiekt musi być wystąpieniem używanej wersji programu <xref:Microsoft.VisualStudio.Package.Declarations> klasy.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Zawiera listę podpisy metod dla danego kontekstu. Ta metoda musi zostać wdrożone, ale może zwrócić wartość null. Jeśli ta metoda zwróci prawidłowego obiektu, obiekt musi być wystąpieniem używanej wersji programu <xref:Microsoft.VisualStudio.Package.Methods> klasy.|

## <a name="language-service-images"></a>Język obsługi obrazów
 Aby utworzyć listę ikon, które ma być używany w całej usłudze języka, Zastąp <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i zwracają <xref:System.Windows.Forms.ImageList> zawierający ikony. Podstawa <xref:Microsoft.VisualStudio.Package.LanguageService> klasy ładuje domyślny zestaw ikon. Ponieważ określisz indeks dokładnego obrazu w tych miejscach, wymagających ikony, jak zostały rozmieszczone listy obrazu jest całkowicie do Ciebie.

### <a name="images-used-in-intellisense-completion-lists"></a>Obrazy używane w liście uzupełniania IntelliSense
 Na liście uzupełniania IntelliSense, indeks obrazu jest określona dla każdego elementu w <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metody <xref:Microsoft.VisualStudio.Package.Declarations> klasy, która musi zastąpić, jeśli chcesz podać indeks obrazu. Wartość zwracana z <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> metodą jest indeks listy obrazów, dostarczone <xref:Microsoft.VisualStudio.Package.CompletionSet> konstruktora klasy a to znaczy tej samej listy obrazów zwróciło <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy (można zmienić obraz listę, na której na użytek <xref:Microsoft.VisualStudio.Package.CompletionSet> Jeśli zastąpisz <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.Source> klasy, aby podać listę innego obrazu).

### <a name="images-used-in-the-navigation-bar"></a>Obrazy używane na pasku nawigacyjnym
 **Pasek nawigacyjny** Wyświetla listę typów i elementów członkowskich i jest używany dla szybką nawigację można wyświetlić ikon. Te ikony są uzyskiwane z <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy i nie może być zastąpiona specjalnie pod kątem **pasek nawigacyjny**. Indeksy używane dla każdego elementu w polu kombi są określane podczas list reprezentujących pola kombi są wypełniane <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> klasy (zobacz [Obsługa paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Wskaźniki te obrazu są uzyskiwane w jakiś sposób z analizatora, zazwyczaj przez daną wersję <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Jak indeksy są uzyskiwane zależy od całkowicie użytkownika.

### <a name="images-used-in-the-error-list-task-window"></a>Obrazy używane w oknie błędów listy zadań
 Zawsze, gdy <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> analizatora — metoda (zobacz [starszej wersji języka usługi analizator i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) napotka błąd, a następnie przekazuje ten błąd do <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasy, zgłaszany jest błąd w  **Lista błędów** okno zadań. Ikona może być skojarzony z każdego elementu, który pojawia się w oknie zadania i tę ikonę, pochodzi z tej samej listy obrazów zwróciło <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy. Domyślne zachowanie klasy MPF nie będzie wyświetlany obraz z komunikatem o błędzie. Jednak to zachowanie można zastąpić za wyprowadzanie klasy z <xref:Microsoft.VisualStudio.Package.Source> klasy i zastępowanie <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metody. W tej metodzie tworzenia nowego <xref:Microsoft.VisualStudio.Package.DocumentTask> obiektu. Przed zwróceniem tego obiektu, możesz użyć <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> właściwość <xref:Microsoft.VisualStudio.Package.DocumentTask> obiektu, aby ustawić indeks obrazu. To może wyglądać następująco. Należy pamiętać, że `TestIconImageIndex` jest wyliczeniem, wyświetla wszystkie ikony, która zależy od tego przykładu. Może mieć inny sposób identyfikowania z ikony w usłudze języka.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.Shell;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestSource : Source
    {
        public override DocumentTask CreateErrorTaskItem(
            TextSpan          span,
            string            filename,
            string            message,
            TaskPriority      priority,
            TaskCategory      category,
            MARKERTYPE        markerType,
            TaskErrorCategory errorCategory)
        {
            DocumentTask taskItem = base.CreateErrorTaskItem(
                                           span,
                                           filename,
                                           message,
                                           priority,
                                           category,
                                           markerType,
                                           errorCategory);
            if (errorCategory == TaskErrorCategory.Error)
            {
                taskItem.ImageIndex = TestIconImageIndex.Error;
            }
            return taskItem;
        }
    }
}
```

## <a name="the-default-image-list-for-a-language-service"></a>Domyślna lista obrazów dla usługi językowej
 Domyślny obraz listy dostarczonej z usługą klasy bazowe usługi języka MPF zawiera liczbę ikon skojarzonych z typowe elementy języka. Duża część tych ikon są rozmieszczone w zestawach zmian sześć, odpowiadający pojęć z zakresu dostępu publiczne, wewnętrzne, friend, protected, private, i skrót. Na przykład można mieć różne ikony dla metody, w zależności od tego, czy jest publicznych, chronionych lub prywatnych.

 Wyliczenie następujące określa typowe nazwy dla każdego zestawu ikon i określa skojarzonego indeksu. Na przykład, oparty na wyliczeniu, możesz określić indeks obrazu dla chronionych metody jako `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Można zmienić nazwy w tym wyliczeniu zgodnie z potrzebami.

```csharp
public enum IconImageIndex
        {
            // access types
            AccessPublic = 0,
            AccessInternal = 1,
            AccessFriend = 2,
            AccessProtected = 3,
            AccessPrivate = 4,
            AccessShortcut = 5,

            Base = 6,
            // Each of the following icon type has 6 versions,
            //corresponding to the access types
            Class = Base + 0,
            Constant = Base + 1,
            Delegate = Base + 2,
            Enumeration = Base + 3,
            EnumMember = Base + 4,
            Event = Base + 5,
            Exception = Base + 6,
            Field = Base + 7,
            Interface = Base + 8,
            Macro = Base + 9,
            Map = Base + 10,
            MapItem = Base + 11,
            Method = Base + 12,
            OverloadedMethod = Base + 13,
            Module = Base + 14,
            Namespace = Base + 15,
            Operator = Base + 16,
            Property = Base + 17,
            Struct = Base + 18,
            Template = Base + 19,
            Typedef = Base + 20,
            Type = Base + 21,
            Union = Base + 22,
            Variable = Base + 23,
            ValueType = Base + 24,
            Intrinsic = Base + 25,
            JavaMethod = Base + 26,
            JavaField = Base + 27,
            JavaClass = Base + 28,
            JavaNamespace = Base + 29,
            JavaInterface = Base + 30,
            // Miscellaneous icons with one icon for each type.
            Error = 187,
            GreyedClass = 188,
            GreyedPrivateMethod = 189,
            GreyedProtectedMethod = 190,
            GreyedPublicMethod = 191,
            BrowseResourceFile = 192,
            Reference = 193,
            Library = 194,
            VBProject = 195,
            VBWebProject = 196,
            CSProject = 197,
            CSWebProject = 198,
            VB6Project = 199,
            CPlusProject = 200,
            Form = 201,
            OpenFolder = 202,
            ClosedFolder = 203,
            Arrow = 204,
            CSClass = 205,
            Snippet = 206,
            Keyword = 207,
            Info = 208,
            CallBrowserCall = 209,
            CallBrowserCallRecursive = 210,
            XMLEditor = 211,
            VJProject = 212,
            VJClass = 213,
            ForwardedType = 214,
            CallsTo = 215,
            CallsFrom = 216,
            Warning = 217,
        }
```

## <a name="see-also"></a>Zobacz też
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)