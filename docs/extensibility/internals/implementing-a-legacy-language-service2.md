---
title: Implementowanie starszej wersji językowej Językowej2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 053ca367776c811dd1192814c5f928bb294eefb4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727240"
---
# <a name="implementing-a-legacy-language-service"></a>Implementowanie starszej wersji usługi językowej
Aby zaimplementować usługę językową przy użyciu struktury zarządzanego pakietu (MPF), należy utworzyć klasę z klasy <xref:Microsoft.VisualStudio.Package.LanguageService> i zaimplementować następujące metody abstrakcyjne i właściwości:

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Właściwość <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Zapoznaj się z odpowiednimi sekcjami poniżej, aby uzyskać szczegółowe informacje na temat implementowania tych metod i właściwości.

  Aby zapewnić obsługę dodatkowych funkcji, może być konieczne uzyskanie klasy z jednej z klas usługi językowej MPF. na przykład aby obsługiwać dodatkowe polecenia menu, należy utworzyć klasę z klasy <xref:Microsoft.VisualStudio.Package.ViewFilter> i zastąpić kilka metod obsługi poleceń (zobacz <xref:Microsoft.VisualStudio.Package.ViewFilter>, aby uzyskać szczegółowe informacje). Klasa <xref:Microsoft.VisualStudio.Package.LanguageService> zawiera wiele metod, które są wywoływane w celu utworzenia nowych wystąpień różnych klas i przesłonięcia odpowiedniej metody tworzenia w celu zapewnienia wystąpienia klasy. Na przykład należy przesłonić metodę <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService>, aby zwracała wystąpienie własnej klasy <xref:Microsoft.VisualStudio.Package.ViewFilter>. Aby uzyskać więcej informacji, zobacz sekcję "Tworzenie wystąpień klas niestandardowych".

  Usługa językowa może również dostarczać własne ikony, które są używane w wielu miejscach. Na przykład gdy zostanie wyświetlona lista uzupełniania IntelliSense, każdy element na liście może mieć skojarzoną z nią ikonę, oznaczanie elementu jako metody, klasy, przestrzeni nazw, właściwości lub dowolnego, co jest niezbędne dla danego języka. Te ikony są używane we wszystkich listach IntelliSense, na **pasku nawigacyjnym**i w oknie zadania **Lista błędów** . Aby uzyskać szczegółowe informacje, zobacz sekcję "obrazy usługi językowej" poniżej.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences, Metoda
 Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> zawsze zwraca to samo wystąpienie klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. Klasy bazowej <xref:Microsoft.VisualStudio.Package.LanguagePreferences> można użyć, jeśli nie są potrzebne dodatkowe preferencje dotyczące usługi językowej. Klasy usługi języka MPF zakładają obecność co najmniej podstawowej klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

### <a name="example"></a>Przykład
 Ten przykład przedstawia typową implementację metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>. Ten przykład używa klasy bazowej <xref:Microsoft.VisualStudio.Package.LanguagePreferences>.

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

## <a name="getscanner-method"></a>Getskaner, Metoda
 Ta metoda zwraca wystąpienie obiektu <xref:Microsoft.VisualStudio.Package.IScanner>, który implementuje parser z zorientowanym na wierszu lub skaner używany do uzyskiwania tokenów i ich typów i wyzwalaczy. Ten skaner jest używany w klasie <xref:Microsoft.VisualStudio.Package.Colorizer> do kolorowania, mimo że skaner może być również używany do uzyskiwania typów tokenów i wyzwalaczy jako preludium do bardziej złożonej operacji analizowania. Należy podać klasę, która implementuje interfejs <xref:Microsoft.VisualStudio.Package.IScanner> i należy zaimplementować wszystkie metody w interfejsie <xref:Microsoft.VisualStudio.Package.IScanner>.

### <a name="example"></a>Przykład
 Ten przykład przedstawia typową implementację metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>. Klasa `TestScanner` implementuje interfejs <xref:Microsoft.VisualStudio.Package.IScanner> (niepokazywany).

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

## <a name="parsesource-method"></a>ParseSource, Metoda
 Analizuje plik źródłowy na podstawie wielu różnych przyczyn. W tej metodzie jest przyznany obiekt <xref:Microsoft.VisualStudio.Package.ParseRequest>, który opisuje, co jest oczekiwane w określonej operacji analizowania. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wywołuje bardziej skomplikowany parser, który określa funkcjonalność i zakres tokenu. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> jest używana w obsłudze operacji IntelliSense, a także do dopasowywania nawiasów klamrowych. Nawet jeśli nie obsługujesz takich operacji zaawansowanych, nadal musisz zwrócić prawidłowy obiekt <xref:Microsoft.VisualStudio.Package.AuthoringScope>, który wymaga utworzenia klasy implementującej interfejs <xref:Microsoft.VisualStudio.Package.AuthoringScope> i zaimplementowania wszystkich metod w tym interfejsie. Można zwrócić wartości null ze wszystkich metod, ale sam obiekt <xref:Microsoft.VisualStudio.Package.AuthoringScope> nie może być wartością null.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono minimalną implementację metody <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> i klasy <xref:Microsoft.VisualStudio.Package.AuthoringScope>, co jest wystarczające, aby umożliwić Kompilowanie i działanie usługi języka bez faktycznego obsłudze jakichkolwiek bardziej zaawansowanych funkcji.

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

## <a name="name-property"></a>Właściwość Name
 Ta właściwość zwraca nazwę usługi językowej. Ta nazwa musi być taka sama, jak w przypadku rejestracji usługi językowej. Ta nazwa jest używana w wielu miejscach, najbardziej widocznym dla klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences>, w której nazwa jest używana do uzyskiwania dostępu do rejestru. Nazwa zwrócona przez tę właściwość nie może być lokalizowana, ponieważ jest używana w rejestrze dla wpisów rejestru i nazw kluczy.

### <a name="example"></a>Przykład
 Ten przykład pokazuje jedną z możliwych implementacji właściwości <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>. Należy zauważyć, że nazwa w tym miejscu jest zakodowana: rzeczywista nazwa powinna zostać uzyskana z pliku zasobów, dzięki czemu może być używana do rejestrowania usługi języka (zobacz [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Tworzenie wystąpień klas niestandardowych
 Następujące metody z określonych klas można zastąpić, aby zapewnić wystąpienia własnych wersji każdej klasy.

### <a name="in-the-languageservice-class"></a>W klasie LanguageService

|Metoda|Zwrócono klasę|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Do obsługi niestandardowych dodatków do widoku tekstu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Do obsługi niestandardowych właściwości dokumentu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Do obsługi **paska nawigacyjnego**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Do obsługi funkcji w szablonach fragmentów kodu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Do obsługi fragmentów kodu (Ta metoda nie jest zwykle zastępowana).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|Do obsługi dostosowywania struktury <xref:Microsoft.VisualStudio.Package.ParseRequest> (Ta metoda nie jest zwykle zastępowana).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Do obsługi formatowania kodu źródłowego, określania znaków komentarzy i dostosowywania sygnatur metod.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Do obsługi dodatkowych poleceń menu.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Aby obsłużyć wyróżnianie składni (Ta metoda nie jest zwykle zastępowana).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|Aby zapewnić obsługę dostępu do preferencji językowych. Ta metoda musi być zaimplementowana, ale może zwrócić wystąpienie klasy bazowej.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Aby zapewnić parser używany do identyfikowania typów tokenów w wierszu. Ta metoda musi być zaimplementowana, a <xref:Microsoft.VisualStudio.Package.IScanner> musi pochodzić od klasy.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Aby zapewnić parser używany do identyfikowania funkcjonalności i zakresu w całym pliku źródłowym. Ta metoda musi być zaimplementowana i musi zwracać wystąpienie używanej wersji klasy <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Jeśli wszystko, co chcesz obsługiwać, ma wyróżnianie składni (które wymaga analizatora <xref:Microsoft.VisualStudio.Package.IScanner> zwróconego z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>), możesz nic nie robić w tej metodzie inne niż zwracają wersję klasy <xref:Microsoft.VisualStudio.Package.AuthoringScope>, której metody wszystkie zwracają wartości null.|

### <a name="in-the-source-class"></a>W klasie źródłowej

|Metoda|Zwrócono klasę|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|W celu dostosowania wyświetlania list uzupełniania IntelliSense (Ta metoda nie jest zwykle zastępowana).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Dla znaczników pomocniczych na liście zadań Lista błędów. w celu obsługi funkcji wykraczających poza otwieranie pliku i przechodzenie do wiersza, który spowodował błąd.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|W celu dostosowania wyświetlania etykietek narzędzi informacji o parametrach IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Do obsługi kodu komentowania.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Do zbierania informacji podczas operacji analizowania.|

### <a name="in-the-authoringscope-class"></a>W klasie AuthoringScope

|Metoda|Zwrócono klasę|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Zawiera listę deklaracji, takich jak elementy członkowskie lub typy. Ta metoda musi być wdrożona, ale może zwracać wartość null. Jeśli ta metoda zwraca prawidłowy obiekt, obiekt musi być wystąpieniem używanej wersji klasy <xref:Microsoft.VisualStudio.Package.Declarations>.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Zawiera listę sygnatur metod dla danego kontekstu. Ta metoda musi być wdrożona, ale może zwracać wartość null. Jeśli ta metoda zwraca prawidłowy obiekt, obiekt musi być wystąpieniem używanej wersji klasy <xref:Microsoft.VisualStudio.Package.Methods>.|

## <a name="language-service-images"></a>Obrazy usługi językowej
 Aby podać listę ikon, które mają być używane w całej usłudze językowej, Zastąp metodę <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService> i zwróć <xref:System.Windows.Forms.ImageList> zawierającą ikony. Klasa bazowa <xref:Microsoft.VisualStudio.Package.LanguageService> ładuje domyślny zestaw ikon. Ze względu na to, że w tych miejscach należy określić dokładny indeks obrazu, w jaki sposób rozmieszczać własną listę obrazów w całości.

### <a name="images-used-in-intellisense-completion-lists"></a>Obrazy używane na listach uzupełniania IntelliSense
 Dla list uzupełniania IntelliSense indeks obrazu jest określany dla każdego elementu w metodzie <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> klasy <xref:Microsoft.VisualStudio.Package.Declarations>, które należy zastąpić, jeśli chcesz podać indeks obrazu. Wartość zwrócona przez metodę <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> jest indeksem do listy obrazów dostarczonej do konstruktora klasy <xref:Microsoft.VisualStudio.Package.CompletionSet> i jest to taka sama lista obrazów zwracana z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService> (można zmienić listę obrazów do użycia dla @no__ t_4 Jeśli zastąpisz metodę <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> w klasie <xref:Microsoft.VisualStudio.Package.Source>, aby podać inną listę obrazów).

### <a name="images-used-in-the-navigation-bar"></a>Obrazy używane na pasku nawigacyjnym
 Na **pasku nawigacyjnym** są wyświetlane listy typów i elementów członkowskich, które są używane na potrzeby szybkiej nawigacji. Te ikony są uzyskiwane z metody <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService> i nie mogą zostać przesłonięte w odniesieniu do **paska nawigacyjnego**. Indeksy używane dla każdego elementu w polach kombi są określone, gdy listy reprezentujące pola kombi są wypełnione metodami <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> w klasie <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> (zobacz [Pomoc techniczna dla paska nawigacyjnego w starszej wersji usługi językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Te indeksy obrazu są uzyskiwane z parserem, zazwyczaj za pośrednictwem używanej wersji klasy <xref:Microsoft.VisualStudio.Package.Declarations>. Sposób uzyskiwania indeksów jest całkowicie do Ciebie.

### <a name="images-used-in-the-error-list-task-window"></a>Obrazy używane w oknie zadania Lista błędów
 Za każdym razem, gdy analizator <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metod (zobacz [Analizator starszej usługi językowej i skaner](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)) napotka błąd i przekazuje błąd do metody <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> w klasie <xref:Microsoft.VisualStudio.Package.AuthoringSink>, w oknie zadania **Lista błędów** zostanie zgłoszony błąd. Ikona może być skojarzona z każdym elementem, który pojawia się w oknie zadania, a ta ikona pochodzi z tej samej listy obrazu zwróconej przez metodę <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService>. Domyślnym zachowaniem klas MPF jest nie wyświetlaj obrazu z komunikatem o błędzie. Można jednak zastąpić to zachowanie, wprowadzając klasę z klasy <xref:Microsoft.VisualStudio.Package.Source> i zastępując metodę <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>. W tej metodzie utworzysz nowy obiekt <xref:Microsoft.VisualStudio.Package.DocumentTask>. Przed zwróceniem tego obiektu można użyć właściwości <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> w obiekcie <xref:Microsoft.VisualStudio.Package.DocumentTask>, aby ustawić indeks obrazu. Będzie to wyglądać podobnie do poniższego przykładu. Należy zauważyć, że `TestIconImageIndex` jest wyliczeniem, które wyświetla wszystkie ikony i jest specyficzne dla tego przykładu. Może istnieć inny sposób identyfikacji ikon w usłudze językowej.

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
 Domyślna lista obrazów dostarczana z podstawowymi klasami usługi językowej MPF zawiera wiele ikon skojarzonych z bardziej typowymi elementami języka. Większość tych ikon jest uporządkowana w zestawach sześciu odmian, odpowiadających koncepcjom dostępu publicznym, wewnętrznym, znajomemu, chronionemu, prywatnemu i skrótowi. Na przykład można mieć różne ikony dla metody w zależności od tego, czy jest on publiczny, chroniony czy prywatny.

 Następujące Wyliczenie określa typowe nazwy dla każdego zestawu ikon i określa skojarzony indeks. Na przykład na podstawie wyliczenia można określić indeks obrazu dla metody chronionej jako `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected`. Nazwy w tym wyliczeniu można zmienić zgodnie z potrzebami.

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

## <a name="see-also"></a>Zobacz także
- [Implementowanie starszej wersji usługi językowej](../../extensibility/internals/implementing-a-legacy-language-service1.md)
- [Omówienie starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-overview.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Analizator i skaner starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)