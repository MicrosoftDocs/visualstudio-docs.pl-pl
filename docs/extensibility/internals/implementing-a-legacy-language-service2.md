---
title: Implementowanie starszej wersji usługi językowej2 | Microsoft Docs
description: Dowiedz się, jak zaimplementować starszą usługę językową, która obsługuje rozszerzone funkcje usługi językowej, przy użyciu struktury pakietów zarządzanych (MPF). Część 2 z 2.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- language services [managed package framework], implementing
ms.assetid: 5bcafdc5-f922-48f6-a12e-6c8507a79a05
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fca2548ddb0c8281241b14de0ec470cfe22db1a1
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900125"
---
# <a name="implementing-a-legacy-language-service-2"></a>Implementowanie starszej wersji usługi językowej 2
Aby zaimplementować usługę językową przy użyciu struktury pakietów zarządzanych (MPF), należy wyprowadzić klasę z klasy i zaimplementować następujące abstrakcyjne metody <xref:Microsoft.VisualStudio.Package.LanguageService> i właściwości:

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>

- Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>

- Właściwość <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A>

  Zapoznaj się z odpowiednimi sekcjami poniżej, aby uzyskać szczegółowe informacje na temat implementowania tych metod i właściwości.

  Aby obsługiwać dodatkowe funkcje, usługa językowa może wymagać wyprowadzenia klasy z jednej z klas usługi językowej MPF; Na przykład, aby obsługiwać dodatkowe polecenia menu, należy wyprowadzić klasę z klasy i zastąpić kilka metod obsługi poleceń <xref:Microsoft.VisualStudio.Package.ViewFilter> (zobacz <xref:Microsoft.VisualStudio.Package.ViewFilter> szczegóły). Klasa udostępnia wiele metod, które są wywoływane w celu utworzenia nowych wystąpień różnych klas i zastępują odpowiednią metodę tworzenia, aby zapewnić <xref:Microsoft.VisualStudio.Package.LanguageService> wystąpienie klasy. Na przykład należy przesłonić metodę w klasie , aby <xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> zwrócić wystąpienie własnej <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy. Aby uzyskać więcej informacji, zobacz sekcję "Wystąpienia klas niestandardowych".

  Usługa językowa może również dostarczać własne ikony, które są używane w wielu miejscach. Jeśli na przykład zostanie wyświetlona lista uzupełniania IntelliSense, każdy element na liście może mieć skojarzoną ikonę, oznaczając element jako metodę, klasę, przestrzeń nazw, właściwość lub coś, co jest niezbędne dla Twojego języka. Te ikony są używane we wszystkich listach funkcji IntelliSense, na **pasku nawigacyjnym** i w **oknie** zadań Lista błędów. Zobacz sekcję "Obrazy usługi językowej" poniżej, aby uzyskać szczegółowe informacje.

## <a name="getlanguagepreferences-method"></a>GetLanguagePreferences, metoda
 Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> zawsze zwraca to samo wystąpienie <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy. Jeśli nie potrzebujesz żadnych dodatkowych preferencji dla usługi językowej, możesz użyć <xref:Microsoft.VisualStudio.Package.LanguagePreferences> klasy bazowej. Klasy usług językowych MPF zakładają obecność co najmniej klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences> bazowej.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono typową implementację <xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A> metody . W tym przykładzie użyto klasy <xref:Microsoft.VisualStudio.Package.LanguagePreferences> bazowej .

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

## <a name="getscanner-method"></a>GetScanner, metoda
 Ta metoda zwraca wystąpienie obiektu, który implementuje parser lub skaner zorientowany na wiersz używany do uzyskiwania tokenów oraz ich <xref:Microsoft.VisualStudio.Package.IScanner> typów i wyzwalaczy. Ten skaner jest używany w klasie do kolorowania, chociaż skaner może również służyć do uzyskiwania typów tokenów i wyzwalaczy jako preludium do bardziej złożonej operacji <xref:Microsoft.VisualStudio.Package.Colorizer> analizowania. Należy podać klasę, która implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejs, i należy zaimplementować wszystkie metody w <xref:Microsoft.VisualStudio.Package.IScanner> interfejsie.

### <a name="example"></a>Przykład
 W tym przykładzie przedstawiono typową implementację <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> metody . Klasa `TestScanner` implementuje <xref:Microsoft.VisualStudio.Package.IScanner> interfejs (nie jest wyświetlany).

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

## <a name="parsesource-method"></a>ParseSource, metoda
 Analizuje plik źródłowy na podstawie różnych przyczyn. Ta metoda ma obiekt <xref:Microsoft.VisualStudio.Package.ParseRequest> , który opisuje, czego oczekuje się od określonej operacji analizowania. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> wywołuje bardziej złożony parser, który określa funkcjonalność i zakres tokenu. Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> jest używana w celu obsługi operacji IntelliSense oraz dopasowywania nawiasów klamrowych. Nawet jeśli nie obsługujesz takich zaawansowanych operacji, nadal musisz zwrócić prawidłowy obiekt i wymaga to utworzenia klasy, która implementuje interfejs i implementuje wszystkie metody w <xref:Microsoft.VisualStudio.Package.AuthoringScope> <xref:Microsoft.VisualStudio.Package.AuthoringScope> tym interfejsie. Można zwrócić wartości null ze wszystkich metod, ale <xref:Microsoft.VisualStudio.Package.AuthoringScope> sam obiekt nie może być wartością null.

### <a name="example"></a>Przykład
 W tym przykładzie pokazano minimalną implementację metody i klasy , wystarczającą do umożliwienia kompilacji i działania usługi językowej bez konieczności obsługi jakichkolwiek bardziej <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> zaawansowanych funkcji.

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
 Ta właściwość zwraca nazwę usługi językowej. Musi to być ta sama nazwa nadana podczas rejestrowania usługi językowej. Ta nazwa jest używana w wielu miejscach, z których najważniejszą jest klasa, w której nazwa jest używana do uzyskiwania dostępu <xref:Microsoft.VisualStudio.Package.LanguagePreferences> do rejestru. Nazwa zwrócona przez tę właściwość nie może być zlokalizowane, ponieważ jest używana w rejestrze dla wpisów rejestru i nazw kluczy.

### <a name="example"></a>Przykład
 W tym przykładzie pokazano jedną z możliwych implementacji <xref:Microsoft.VisualStudio.Package.LanguageService.Name%2A> właściwości . Pamiętaj, że nazwa w tym miejscu jest zakodowana na zawsze: rzeczywista nazwa powinna zostać uzyskana z pliku zasobów, aby można było jej użyć do zarejestrowania usługi językowej (zobacz Rejestrowanie starszej wersji usługi [językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)).

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

## <a name="instantiating-custom-classes"></a>Wystąpienia klas niestandardowych
 Następujące metody w określonych klasach można przesłonić, aby zapewnić wystąpienia własnych wersji każdej klasy.

### <a name="in-the-languageservice-class"></a>W klasie LanguageService

|Metoda|Zwrócona klasa|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateCodeWindowManager%2A>|<xref:Microsoft.VisualStudio.Package.CodeWindowManager>|Obsługa niestandardowych dodatków do widoku tekstu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A>|<xref:Microsoft.VisualStudio.Package.DocumentProperties>|Do obsługi niestandardowych właściwości dokumentu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>|<xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars>|Aby obsługiwać pasek **nawigacyjny**.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionFunction>|Do obsługi funkcji w szablonach fragmentów kodu.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A>|<xref:Microsoft.VisualStudio.Package.ExpansionProvider>|Do obsługi fragmentów kodu (ta metoda zwykle nie jest zastępowa).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateParseRequest%2A>|<xref:Microsoft.VisualStudio.Package.ParseRequest>|W celu obsługi <xref:Microsoft.VisualStudio.Package.ParseRequest> dostosowywania struktury (ta metoda zwykle nie jest zastępowa).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateSource%2A>|<xref:Microsoft.VisualStudio.Package.Source>|Do obsługi formatowania kodu źródłowego, określania znaków komentarza i dostosowywania podpisów metod.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.CreateViewFilter%2A>|<xref:Microsoft.VisualStudio.Package.ViewFilter>|Do obsługi dodatkowych poleceń menu.|
|<xref:Microsoft.VisualStudio.Package.Source.GetColorizer%2A>|<xref:Microsoft.VisualStudio.Package.Colorizer>|Obsługa wyróżniania składni (ta metoda zwykle nie jest zastępowa).|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetLanguagePreferences%2A>|<xref:Microsoft.VisualStudio.Package.LanguagePreferences>|W celu obsługi dostępu do preferencji językowych. Ta metoda musi zostać zaimplementowana, ale może zwrócić wystąpienie klasy bazowej.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A>|<xref:Microsoft.VisualStudio.Package.IScanner>|Aby zapewnić parser używany do identyfikowania typów tokenów w wierszu. Ta metoda musi być zaimplementowana i <xref:Microsoft.VisualStudio.Package.IScanner> musi pochodzić z.|
|<xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringScope>|Aby zapewnić parser używany do identyfikowania funkcjonalności i zakresu w całym pliku źródłowym. Ta metoda musi być zaimplementowana i musi zwracać wystąpienie twojej wersji <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy. Jeśli chcesz tylko obsługiwać wyróżnianie składni (które wymaga, aby parser został zwrócony z metody ), nie możesz nic zrobić w tej metodzie poza zwróceniem wersji klasy, której metody zwracają wartości <xref:Microsoft.VisualStudio.Package.IScanner> <xref:Microsoft.VisualStudio.Package.LanguageService.GetScanner%2A> <xref:Microsoft.VisualStudio.Package.AuthoringScope> null.|

### <a name="in-the-source-class"></a>W klasie źródłowej

|Metoda|Zwrócona klasa|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A>|<xref:Microsoft.VisualStudio.Package.CompletionSet>|W przypadku dostosowywania wyświetlania list uzupełniania IntelliSense (ta metoda nie jest zwykle zastępowa).|
|<xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A>|<xref:Microsoft.VisualStudio.Package.DocumentTask>|Do obsługi znaczników na liście zadań lista błędów; w szczególności obsługa funkcji wykraczających poza otwieranie pliku i przeskakiwanie do wiersza, który spowodował błąd.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateMethodData%2A>|<xref:Microsoft.VisualStudio.Package.MethodData>|Dostosowywanie wyświetlania etykietek narzędzi informacji o parametrach funkcji IntelliSense.|
|<xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A>|<xref:Microsoft.VisualStudio.Package.CommentInfo>|Do obsługi kodu do komentowania.|
|<xref:Microsoft.VisualStudio.Package.Source.CreateAuthoringSink%2A>|<xref:Microsoft.VisualStudio.Package.AuthoringSink>|Do zbierania informacji podczas operacji analizy.|

### <a name="in-the-authoringscope-class"></a>W klasie AuthoringScope

|Metoda|Zwrócona klasa|Opis|
|------------|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A>|<xref:Microsoft.VisualStudio.Package.Declarations>|Zawiera listę deklaracji, takich jak składowe lub typy. Ta metoda musi być zaimplementowana, ale może zwracać wartość null. Jeśli ta metoda zwraca prawidłowy obiekt, obiekt musi być wystąpieniem twojej wersji <xref:Microsoft.VisualStudio.Package.Declarations> klasy.|
|<xref:Microsoft.VisualStudio.Package.AuthoringScope.GetMethods%2A>|<xref:Microsoft.VisualStudio.Package.Methods>|Zawiera listę sygnatur metod dla danego kontekstu. Ta metoda musi być zaimplementowana, ale może zwracać wartość null. Jeśli ta metoda zwraca prawidłowy obiekt, obiekt musi być wystąpieniem twojej wersji <xref:Microsoft.VisualStudio.Package.Methods> klasy.|

## <a name="language-service-images"></a>Obrazy usługi językowej
 Aby udostępnić listę ikon, które mają być używane w całej usłudze językowej, zastąp metodę w klasie i zwróć <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> element zawierający <xref:System.Windows.Forms.ImageList> ikony. Klasa <xref:Microsoft.VisualStudio.Package.LanguageService> bazowa ładuje domyślny zestaw ikon. Ponieważ określasz dokładny indeks obrazów w tych miejscach, które wymagają ikon, sposób rozmieszczania własnej listy obrazów zależy całkowicie od Ciebie.

### <a name="images-used-in-intellisense-completion-lists"></a>Obrazy używane na listach uzupełniania IntelliSense
 W przypadku list uzupełniania IntelliSense indeks obrazu jest określony dla każdego elementu w metodzie klasy , który należy przesłonić, jeśli chcesz <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.Declarations> podać indeks obrazu. Wartość zwrócona z metody jest indeksem na liście obrazów dostarczonej do konstruktora klasy i jest to ta sama lista obrazów zwrócona z metody w klasie (można zmienić listę obrazów, która ma być stosowana dla klasy , jeśli zastąpisz metodę w klasie, aby podać inną listę <xref:Microsoft.VisualStudio.Package.Declarations.GetGlyph%2A> <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CompletionSet> <xref:Microsoft.VisualStudio.Package.Source.CreateCompletionSet%2A> <xref:Microsoft.VisualStudio.Package.Source> obrazów).

### <a name="images-used-in-the-navigation-bar"></a>Obrazy używane na pasku nawigacyjnym
 Na **pasku nawigacyjnym** są wyświetlane listy typów i elementów członkowskich, które są używane do szybkiej nawigacji i mogą pokazywać ikony. Te ikony są uzyskiwane z metody w klasie i nie można ich zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> specjalnie dla paska **nawigacyjnego**. Indeksy używane dla każdego elementu w polach kombi są określane, gdy listy reprezentujące pola kombi są wypełnione w metodzie w klasie (zobacz Obsługa paska nawigacji w starszej wersji usługi <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> [językowej](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)). Te indeksy obrazów są w jakiś sposób uzyskiwane z parsera, zazwyczaj za pośrednictwem wersji <xref:Microsoft.VisualStudio.Package.Declarations> klasy . Sposób, w jaki uzyskuje się indeksy, zależy całkowicie od Ciebie.

### <a name="images-used-in-the-error-list-task-window"></a>Obrazy używane w oknie zadania lista błędów
 Za każdym razem, gdy <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser metod (zobacz [parser](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)i skaner starszej wersji usługi językowej ) napotyka błąd i przekazuje ten błąd do metody w klasie , ten błąd jest zgłaszany w oknie zadań Lista <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddError%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink> błędów.  Z każdym elementem wyświetlanym w oknie zadania można skojarzyć ikonę, która pochodzi z tej samej listy obrazów zwróconej przez <xref:Microsoft.VisualStudio.Package.LanguageService.GetImageList%2A> metodę w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie . Domyślnym zachowaniem klas MPF jest nie pokazywanie obrazu z komunikatem o błędzie. Można jednak przesłonić to zachowanie, wyprowadzając klasę z <xref:Microsoft.VisualStudio.Package.Source> klasy i przesłaniając <xref:Microsoft.VisualStudio.Package.Source.CreateErrorTaskItem%2A> metodę . W tej metodzie tworzysz nowy <xref:Microsoft.VisualStudio.Package.DocumentTask> obiekt. Przed zwróceniem tego obiektu można użyć właściwości <xref:Microsoft.VisualStudio.Shell.Task.ImageIndex%2A> w <xref:Microsoft.VisualStudio.Package.DocumentTask> obiekcie , aby ustawić indeks obrazu. Będzie to wyglądać podobnie do poniższego przykładu. Należy `TestIconImageIndex` pamiętać, że jest to wyliczenie, które wyświetla listę wszystkich ikon i jest specyficzne dla tego przykładu. W usłudze językowej możesz identyfikować ikony w inny sposób.

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
 Domyślna lista obrazów dostarczana z bazowymi klasami usługi językowej MPF zawiera wiele ikon skojarzonych z bardziej wspólnymi elementami języka. Większość tych ikon jest rozmieszczona w zestawach sześciu odmian odpowiadających koncepcjom dostępu publicznym, wewnętrznym, przyjaznym, chronionym, prywatnym i skrótowym. Na przykład można mieć różne ikony dla metody w zależności od tego, czy jest publiczna, chroniona, czy prywatna.

 Następujące wyliczenie określa typowe nazwy dla każdego zestawu ikon i określa skojarzony indeks. Na przykład na podstawie wyliczenia można określić indeks obrazu dla metody chronionej jako `(int)IconImageIndex.Method + (int)IconImageIndex.AccessProtected` . Nazwy w tym wyliczeniu można zmienić zgodnie z potrzebami.

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
