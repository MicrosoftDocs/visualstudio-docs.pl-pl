---
title: Implementowanie usługi języka starszego 2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e435af68a893c923eafef744762c9da8505c3fb7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707674"
---
# <a name="implementing-a-legacy-language-service"></a>Implementowanie starszej wersji usługi językowej
Aby zaimplementować usługę języka przy użyciu struktury pakietu zarządzanego <xref:Microsoft.VisualStudio.Package.LanguageService> (MPF), należy wyprowadzić klasę z klasy i zaimplementować następujące metody abstrakcyjne i właściwości:

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Właściwość <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Zobacz odpowiednie sekcje poniżej, aby uzyskać szczegółowe informacje na temat wdrażania tych metod i właściwości.

  Aby obsługiwać dodatkowe funkcje, usługa języka może być konieczne wyprowadzenie klasy z jednej z klas usługi języka MPF; na przykład do obsługi dodatkowych poleceń menu, należy <xref:Microsoft.VisualStudio.Package.ViewFilter> wyprowadzić klasę z klasy i zastąpić <xref:Microsoft.VisualStudio.Package.ViewFilter> kilka metod obsługi polecenia (zobacz szczegóły). Klasa <xref:Microsoft.VisualStudio.Package.LanguageService> zawiera szereg metod, które są wywoływane do tworzenia nowych wystąpień różnych klas i zastąpić odpowiednią metodę tworzenia, aby zapewnić wystąpienie klasy. Na przykład należy zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> metodę w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie, aby zwrócić wystąpienie <xref:Microsoft.VisualStudio.Package.ViewFilter> własnej klasy. Aby uzyskać więcej informacji, zobacz sekcję "Tworzenie wystąpienia klas niestandardowych".

  Usługa językowa może również dostarczać własne ikony, które są używane w wielu miejscach. Na przykład po wyświetleniu listy uzupełnień IntelliSense każdy element na liście może mieć skojarzoną z nią ikonę, oznaczającą element jako metodę, klasę, obszar nazw, właściwość lub cokolwiek jest niezbędne dla twojego języka. Ikony te są używane na wszystkich listach IntelliSense, **na pasku nawigacyjnym**i w oknie zadań **Lista błędów.** Szczegółowe informacje można znaleźć w sekcji "Obrazy usług językowych" poniżej.

## <a name="getlanguagepreferences-method"></a>Metoda GetLanguagePreferences
 Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> zawsze zwraca to samo <xref:Microsoft.VisualStudio.Package.LanguagePreferences> wystąpienie klasy. Można użyć klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences> podstawowej, jeśli nie potrzebujesz żadnych dodatkowych preferencji dla usługi języka. Klasy usługi języka MPF zakładają obecność <xref:Microsoft.VisualStudio.Package.LanguagePreferences> co najmniej klasy podstawowej.

### <a name="example"></a>Przykład
 W tym przykładzie pokazano <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> typowe implementacji metody. W tym przykładzie <xref:Microsoft.VisualStudio.Package.LanguagePreferences> użyto klasy podstawowej.

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
 Ta metoda zwraca wystąpienie <xref:Microsoft.VisualStudio.Package.IScanner> obiektu, który implementuje analizatora zorientowanego na wiersz lub skanera używanego do uzyskiwania tokenów i ich typów i wyzwalaczy. Ten skaner jest <xref:Microsoft.VisualStudio.Package.Colorizer> używany w klasie do koloryzacji, chociaż skaner może być również używany do uzyskiwania typów tokenów i wyzwalaczy jako preludium do bardziej złożonej operacji analizowania. Należy podać klasę, która <xref:Microsoft.VisualStudio.Package.IScanner> implementuje interfejs i należy zaimplementować wszystkie metody w interfejsie. <xref:Microsoft.VisualStudio.Package.IScanner>

### <a name="example"></a>Przykład
 W tym przykładzie pokazano <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> typowe implementacji metody. Klasa `TestScanner` implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejs (nie pokazano).

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

## <a name="parsesource-method"></a>Metoda parsesource
 Analizuje plik źródłowy na podstawie wielu różnych powodów. Ta metoda jest <xref:Microsoft.VisualStudio.Package.ParseRequest> podana obiekt, który opisuje, co jest oczekiwane od określonej operacji analizy. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wywołuje bardziej złożony analizator, który określa funkcjonalność tokenu i zakres. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> jest używana w obsłudze operacji IntelliSense, a także dopasowywania nawiasów klamrowych. Nawet jeśli nie obsługuje takich zaawansowanych operacji, <xref:Microsoft.VisualStudio.Package.AuthoringScope> nadal musi zwracać prawidłowy obiekt i <xref:Microsoft.VisualStudio.Package.AuthoringScope> wymaga utworzenia klasy, która implementuje interfejs i zaimplementować wszystkie metody w tym interfejsie. Wartości null można zwracać ze <xref:Microsoft.VisualStudio.Package.AuthoringScope> wszystkich metod, ale sam obiekt nie może być wartością null.

### <a name="example"></a>Przykład
 W tym przykładzie pokazano <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> minimalną <xref:Microsoft.VisualStudio.Package.AuthoringScope> implementację metody i klasy, wystarczające, aby umożliwić usługi języka do kompilacji i funkcji bez faktycznie obsługujących żadnych bardziej zaawansowanych funkcji.

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
 Ta właściwość zwraca nazwę usługi języka. Musi to być ta sama nazwa, podana podczas rejestracji usługi językowej. Ta nazwa jest używana w wielu miejscach, z <xref:Microsoft.VisualStudio.Package.LanguagePreferences> których najbardziej widoczna jest klasa, w której nazwa jest używana do uzyskiwania dostępu do rejestru. Nazwa zwrócona przez tę właściwość nie może być zlokalizowana, ponieważ jest używana w rejestrze dla wpisu rejestru i nazw kluczy.

### <a name="example"></a>Przykład
 W tym przykładzie pokazano <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> jedną możliwą implementację właściwości. Należy zauważyć, że nazwa w tym miejscu jest zakodowany na czas: rzeczywista nazwa powinna być uzyskana z pliku zasobów, dzięki czemu może być używana do rejestrowania usługi językowej (zobacz [Rejestrowanie usługi języka starszego](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Tworzenie wystąpienia klas niestandardowych
 Następujące metody w określonych klasach można zastąpić, aby zapewnić wystąpienia własnych wersji każdej klasy.

### <a name="in-the-languageservice-class"></a>W klasie LanguageService

|Metoda|Klasa zwrócona|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Do obsługi niestandardowych dodatków do widoku tekstu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Do obsługi właściwości dokumentu niestandardowego.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Aby obsługiwać **pasek nawigacyjny**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Do obsługi funkcji w szablonach fragmentów kodu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Do obsługi fragmentów kodu (ta metoda zazwyczaj nie jest zastępowana).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Do obsługi dostosowywania <xref:Microsoft.VisualStudio.Package.ParseRequest> struktury (ta metoda zazwyczaj nie jest zastępowana).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Aby obsługiwać formatowanie kodu źródłowego, określanie znaków komentarza i dostosowywanie podpisów metod.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Do obsługi dodatkowych poleceń menu.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Do obsługi podświetlania składni (ta metoda zazwyczaj nie jest zastępowana).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Aby wspierać dostęp do preferencji językowych. Ta metoda musi być zaimplementowana, ale może zwrócić wystąpienie klasy podstawowej.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Aby zapewnić analizator używany do identyfikowania typów tokenów w wierszu. Ta metoda musi być <xref:Microsoft.VisualStudio.Package.IScanner> zaimplementowana i musi pochodzić z.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Aby zapewnić analizator używany do identyfikowania funkcji i zakresu w całym pliku źródłowym. Ta metoda musi zostać zaimplementowana i <xref:Microsoft.VisualStudio.Package.AuthoringScope> musi zwrócić wystąpienie wersji klasy. Jeśli wszystko, co chcesz obsługiwać jest wyróżnianie <xref:Microsoft.VisualStudio.Package.IScanner> składni (co <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> wymaga analizatora zwróconego z metody), można <xref:Microsoft.VisualStudio.Package.AuthoringScope> nic nie zrobić w tej metodzie innych niż zwracanie wersji klasy, której metody wszystkie zwracają wartości null.|

### <a name="in-the-source-class"></a>W klasie source

|Metoda|Klasa zwrócona|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|Do dostosowywania wyświetlania list ukończenia IntelliSense (ta metoda zazwyczaj nie jest zastępowana).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Do obsługi znaczników na liście zadań listy błędów; w szczególności obsługa funkcji poza otwarciem pliku i przeskakiwaniem do linii, która spowodowała błąd.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Dostosowywanie wyświetlania etykietek narzędzi informacji o parametrach IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Do obsługi kodu komentowania.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Do zbierania informacji podczas operacji analizy.|

### <a name="in-the-authoringscope-class"></a>W klasie AuthoringScope

|Metoda|Klasa zwrócona|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Zawiera listę deklaracji, takich jak elementy członkowskie lub typy. Ta metoda musi być zaimplementowana, ale może zwrócić wartość null. Jeśli ta metoda zwraca prawidłowy obiekt, obiekt musi być <xref:Microsoft.VisualStudio.Package.Declarations> wystąpieniem wersji klasy.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Zawiera listę podpisów metod dla danego kontekstu. Ta metoda musi być zaimplementowana, ale może zwrócić wartość null. Jeśli ta metoda zwraca prawidłowy obiekt, obiekt musi być <xref:Microsoft.VisualStudio.Package.Methods> wystąpieniem wersji klasy.|

## <a name="language-service-images"></a>Obrazy usług językowych
 Aby zapewnić listę ikon, które mają być używane w całej <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> usłudze <xref:Microsoft.VisualStudio.Package.LanguageService> języka, <xref:System.Windows.Forms.ImageList> należy zastąpić metodę w klasie i zwrócić zawierające ikony. Klasa <xref:Microsoft.VisualStudio.Package.LanguageService> podstawowa ładuje domyślny zestaw ikon. Ponieważ określisz dokładny indeks obrazu w tych miejscach, które potrzebują ikon, sposób rozmieszczenia własnej listy obrazów zależy wyłącznie od Ciebie.

### <a name="images-used-in-intellisense-completion-lists"></a>Obrazy używane na listach ukończenia intellisense
 Dla list ukończenia IntelliSense indeks obrazu jest określony <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> dla <xref:Microsoft.VisualStudio.Package.Declarations> każdego elementu w metodzie klasy, które należy zastąpić, jeśli chcesz podać indeks obrazu. Wartość zwrócona <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> z metody jest indeksem do <xref:Microsoft.VisualStudio.Package.CompletionSet> listy obrazów dostarczonych do konstruktora <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> klasy <xref:Microsoft.VisualStudio.Package.LanguageService> i jest to ta sama lista <xref:Microsoft.VisualStudio.Package.CompletionSet> obrazów zwrócona z <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> metody <xref:Microsoft.VisualStudio.Package.Source> w klasie (można zmienić listę obrazów, która ma być używana dla metody w klasie w celu dostarczenia innej listy obrazów).

### <a name="images-used-in-the-navigation-bar"></a>Obrazy używane na pasku nawigacyjnym
 Pasek **nawigacyjny** wyświetla listy typów i członków i służy do szybkiej nawigacji może wyświetlać ikony. Ikony te są <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> uzyskiwane z metody w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie i nie można zastąpić specjalnie dla **paska nawigacyjnego**. Indeksy używane dla każdego elementu w polach kombi są określane, gdy listy reprezentujące <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> pola <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> kombi są wypełniane w metodzie w klasie (zobacz [Obsługa paska nawigacyjnego w usłudze języka starszego).](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md) Te indeksy obrazów są uzyskiwane w jakiś sposób z <xref:Microsoft.VisualStudio.Package.Declarations> analizatora, zazwyczaj za pośrednictwem wersji klasy. Sposób zdobywania indeksów zależy wyłącznie od Ciebie.

### <a name="images-used-in-the-error-list-task-window"></a>Obrazy używane w oknie zadania lista błędów
 Za każdym <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> razem, gdy analizator metody (zobacz [Starsza usługa parser i skaner)](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)napotka błąd i przekazuje ten błąd do <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> metody w <xref:Microsoft.VisualStudio.Package.AuthoringSink> klasie, błąd jest zgłaszany w oknie zadań Lista **błędów.** Ikona może być skojarzona z każdym elementem, który pojawia się w oknie <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> zadania <xref:Microsoft.VisualStudio.Package.LanguageService> i że ikona pochodzi z tej samej listy obrazów zwróconych z metody w klasie. Domyślnym zachowaniem klas MPF jest nie wyświetlanie obrazu z komunikatem o błędzie. Jednak można zastąpić to zachowanie, wyprowadzając klasę <xref:Microsoft.VisualStudio.Package.Source> z klasy i <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> zastępując metodę. W tej metodzie należy <xref:Microsoft.VisualStudio.Package.DocumentTask> utworzyć nowy obiekt. Przed zwróceniem tego obiektu można <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> użyć <xref:Microsoft.VisualStudio.Package.DocumentTask> właściwości obiektu, aby ustawić indeks obrazu. Będzie to wyglądać mniej więcej jak w poniższym przykładzie. Należy `TestIconImageIndex` zauważyć, że jest wyliczenie, które zawiera listę wszystkich ikon i jest specyficzne dla tego przykładu. W usłudze językowej możesz mieć inny sposób identyfikowania ikon.

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

## <a name="the-default-image-list-for-a-language-service"></a>Domyślna lista obrazów usługi językowej
 Domyślna lista obrazów dostarczona z podstawowymi klasami usługi języka MPF zawiera szereg ikon skojarzonych z bardziej typowymi elementami języka. Większość tych ikon są rozmieszczone w zestawach sześciu odmian, odpowiadających koncepcji dostępu publicznych, wewnętrznych, przyjaciel, chronione, prywatne i skróty. Na przykład można mieć różne ikony dla metody w zależności od tego, czy jest publiczny, chroniony lub prywatny.

 Poniższe wyliczenie określa typowe nazwy dla każdego zestawu ikon i określa skojarzony indeks. Na przykład na podstawie wyliczenia można określić indeks obrazu dla `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`chronionej metody jako . Nazwy w tym wyliczeniu można zmienić zgodnie z potrzebami.

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
