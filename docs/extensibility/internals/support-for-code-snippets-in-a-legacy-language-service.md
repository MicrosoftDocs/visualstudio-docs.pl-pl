---
title: Obsługa fragmentów kodu w starszej wersji usługi językowej | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08c30f723c6dbdb7359b1fd1d7648a38e71ab161
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63428816"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Obsługa fragmentów kodu w starszej wersji usługi językowej
Fragment kodu jest fragmentem kodu, który jest wstawiany do pliku źródłowego. Fragmentem jest oparty na składni XML szablonu przy użyciu zestawu pól. Te pola są wyróżnione po tym fragmencie kodu jest wstawiany i mogą mieć różne wartości w zależności od kontekstu, w którym wstawieniu fragmentu kodu. Po wstawieniu fragmentu kodu, usługa językowa można sformatować fragment kodu.

 Fragment kodu jest wstawiana w trybie edycji specjalne, który umożliwia pola fragment kodu, aby można go znaleźć za pomocą klawisza TAB. Pola może obsługiwać menu rozwijane w stylu funkcji IntelliSense. Użytkownik zobowiązuje fragment kodu do pliku źródłowego, wpisując ENTER lub klawisz ESC. Aby dowiedzieć się więcej na temat fragmentów kodu, zobacz [fragmenty kodu](../../ide/code-snippets.md).

 Usługi starszego języka są implementowane jako część pakietu VSPackage, ale nowszych sposobem realizowania funkcji Usługa języka jest użycie rozszerzenia MEF. Aby dowiedzieć się więcej, zobacz [instruktażu: Implementowanie fragmentów kodu](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Zalecamy zacząć tak szybko, jak to możliwe za pomocą edytora nowego interfejsu API. Spowoduje to poprawić wydajność usługi języka i pozwalają korzystać z nowych funkcji edytora.

## <a name="managed-package-framework-support-for-code-snippets"></a>Obsługa fragmentów kodu w ramach pakietu zarządzane
 Środowiska pakietu zarządzanego (MPF) obsługuje większość funkcji fragment kodu, na podstawie odczytu szablon do wstawiania fragmentu kodu i włączeniu specjalne trybu edycji. Obsługa odbywa się za pośrednictwem <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy.

 Gdy <xref:Microsoft.VisualStudio.Package.Source> tworzenia wystąpienia klasy <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy jest wywoływana w celu uzyskania <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiektu (należy pamiętać, że base <xref:Microsoft.VisualStudio.Package.LanguageService> klasy zawsze zwraca nowy <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiekt dla każdego <xref:Microsoft.VisualStudio.Package.Source> obiekt).

 MPF nie obsługuje rozszerzania funkcji. Funkcja rozszerzenia jest o nazwie funkcji, zostanie osadzony w szablon fragmentu kodu, która zwraca jedną lub więcej wartości do umieszczenia w polu. Wartości są zwracane przez język usługi za pośrednictwem <xref:Microsoft.VisualStudio.Package.ExpansionFunction> obiektu. <xref:Microsoft.VisualStudio.Package.ExpansionFunction> Obiekt musi zostać wdrożone przez usługę języka do obsługi funkcji rozszerzenia.

## <a name="providing-support-for-code-snippets"></a>Zapewnianie obsługi w przypadku fragmentów kodu
 Aby włączyć obsługę fragmenty kodu, należy podać albo zainstalować program fragmenty kodu i podać oznacza, że dla użytkownika wstawić tych fragmentów kodu. Istnieją trzy kroki, aby włączyć obsługę fragmenty kodu:

1. Instalowanie plików fragmentu kodu.

2. Włączanie fragmentów kodu usługi języka.

3. Wywoływanie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiektu.

### <a name="installing-the-snippet-files"></a>Instalowanie plików fragmentu kodu
 Wszystkie fragmenty kodu w języku są przechowywane jako szablonów w plikach XML zwykle jeden szablon fragmentu kodu na plik. Aby uzyskać szczegółowe informacje dotyczące schematu XML, używany do szablonów fragmentów kodu, zobacz [dokumentacja schematu fragmentów kodu](../../ide/code-snippets-schema-reference.md). Każdy szablon fragmentu kodu jest identyfikowany za pomocą identyfikatora języka. Ten język identyfikator jest określone w rejestrze i są umieszczane w `Language` atrybutu \<kodu > tagu w szablonie.

 Zwykle istnieją dwie lokalizacje, w którym są przechowywane pliki szablon fragmentu kodu: (1) gdy język został zainstalowany i 2) w folderze użytkownika. Te lokalizacje są dodawane w rejestrze tak, program Visual Studio **Menedżera wstawek kodu** można znaleźć fragmenty kodu. Folder użytkownika jest przechowywania fragmenty utworzone przez użytkownika.

 Układ typowy folder plików szablonów zainstalowanych fragment kodu wygląda następująco: *[InstallRoot]*\\ *[TestLanguage]* \Snippets\\ *[LCID]* \Snippets.

 *[Element InstallRoot]*  jest folderem, język jest zainstalowany w.

 *[TestLanguage]*  to nazwa języka jako nazwa folderu.

 *[LCID]*  to identyfikator ustawień regionalnych. Jest to jak zlokalizowane wersje swoje fragmenty są przechowywane. Na przykład identyfikator ustawień regionalnych dla języka angielskiego to 1033, więc *[LCID]* zastępuje 1033.

 Należy podać jeden dodatkowy plik i który jest plikiem indeksu pliku, zwykle nazywane SnippetsIndex.xml lub ExpansionsIndex.xml (możesz użyć dowolnego prawidłowe pliku z rozszerzeniem .xml). Ten plik zwykle znajduje się w *[InstallRoot]*\\ *[TestLanguage]* folder i umożliwia określenie dokładnej lokalizacji folderu fragmentów kodu, jak również identyfikator języka i identyfikator GUID języka Usługa, która używa fragmenty kodu. Dokładnej ścieżki pliku indeksu są umieszczane w rejestrze, zgodnie z opisem w dalszej części "Instalowanie wpisy rejestru". Poniżej przedstawiono przykładowy plik SnippetsIndex.xml:

```
<?xml version="1.0" encoding="utf-8" ?>
<SnippetCollection>
    <Language Lang="Testlanguage" Guid="{b614a40a-80d9-4fac-a6ad-fc2868fff7cd}">
        <SnippetDir>
            <OnOff>On</OnOff>
            <Installed>true</Installed>
            <Locale>1033</Locale>
            <DirPath>%InstallRoot%\TestLanguage\Snippets\%LCID%\Snippets\</DirPath>
            <LocalizedName>Snippets</LocalizedName>
        </SnippetDir>
    </Language>
</SnippetCollection>
```

 \<Języka > tag Określa identyfikator języka ( `Lang` atrybutu) i usługi językowej identyfikatora GUID.

 W tym przykładzie przyjęto założenie, że zainstalowano usługi języka w folderze instalacyjnym programu Visual Studio. Identyfikator LCID % jest zastępowana identyfikatorem ustawień regionalnych z bieżącego użytkownika Wiele \<SnippetDir > tagi mogą być dodawane, jeden dla każdego innego katalogu i ustawień regionalnych. Ponadto folder fragment może zawierać podfoldery, z których każdy jest identyfikowana w pliku indeksu z \<SnippetSubDir > tag, który jest osadzony w \<SnippetDir > tag.

 Użytkownicy mogą również tworzyć własne fragmentów dla danego języka. Te są zwykle przechowywane w folderze Ustawienia użytkownika, na przykład *[TestDocs]* \Code fragmenty\\ *[TestLanguage]* \Test fragmenty kodu, gdzie *[TestDocs]* to lokalizacja folderu Ustawienia użytkownika dla programu Visual Studio.

 Następujące elementy podstawienia można umieścić w ścieżce, przechowywane w \<DirPath > znacznika w pliku indeksu.

|Element|Opis|
|-------------|-----------------|
|IDENTYFIKATOR LCID %|Identyfikator ustawień regionalnych.|
|%InstallRoot%|Główny folder instalacji programu Visual Studio, na przykład C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Folder zawierający bieżącego projektu.|
|%ProjItem%|Folder zawierający bieżącego elementu projektu.|
|%TestDocs%|Folderu w folderze Ustawienia użytkownika, na przykład C:\Documents and Settings\\ *[username]* \My Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Włączanie fragmentów kodu dla usługi w języka
 Fragmenty kodu można włączyć usługi języka, dodając <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> atrybutu do Twojego pakietu VSPackage (zobacz [rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md) Aby uzyskać szczegółowe informacje). <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> i <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> parametry są opcjonalne, ale powinien zawierać `SearchPaths` o nazwie parametru, aby poinformować **Menedżera wstawek kodu** lokalizacji z fragmentów kodu.

 Oto przykład sposobu użycia tego atrybutu:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Wywoływania dostawcy rozszerzeń
 Usługa językowa steruje wstawiania wszystkie fragmenty kodu, a także sposób wstawiania jest wywoływana.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>W przypadku fragmentów kodu podczas wywoływania dostawcy rozszerzeń
 Istnieją dwa sposoby, aby wywołać dostawcę rozszerzeń: za pomocą polecenia menu lub za pomocą skrótu z listy uzupełniania.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Wstawianie fragmentu kodu przy użyciu polecenia Menu
 Aby polecenie menu do wyświetlenia w przeglądarce fragment kodu, możesz dodać polecenie menu a następnie wywołać <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider> interfejsu w odpowiedzi na polecenie menu.

1. Dodaj przycisk i polecenia do pliku vsct. Można znaleźć instrukcje dotyczące wykonywania, dlatego w [Tworzenie rozszerzenia za pomocą polecenia Menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy, a także Przesłoń <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> metodę w celu wskazania obsługę nowego polecenia menu. W tym przykładzie zawsze uruchamia polecenia menu.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public TestViewFilter(CodeWindowManager mgr, IVsTextView view)
                : base(mgr, view)
            {
            }

            protected override int QueryCommandStatus(ref Guid guidCmdGroup,
                                                      uint nCmdId)
            {
                int hr = base.QueryCommandStatus(ref guidCmdGroup, nCmdId);
                // If the base class did not recognize the command then
                // see if we can handle the command.
                if (hr == (int)Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP)
                {
                    if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                    {
                        if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                        {
                            hr = (int)(OLECMDF.OLECMDF_SUPPORTED | OLECMDF.OLECMDF_ENABLED);
                        }
                    }
                }
                return hr;
            }
        }
    }
    ```

3. Zastąp <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy w celu uzyskania <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiektu, a następnie wywołać <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metody dla tego obiektu.

    ```csharp
    using Microsoft.VisualStudio.Package;

    namespace TestLanguagePackage
    {
        class TestViewFilter : ViewFilter
        {
            public override bool HandlePreExec(ref Guid guidCmdGroup,
                                               uint nCmdId,
                                               uint nCmdexecopt,
                                               IntPtr pvaIn,
                                               IntPtr pvaOut)
            {
                if (base.HandlePreExec(ref guidCmdGroup,
                                       nCmdId,
                                       nCmdexecopt,
                                       pvaIn,
                                       pvaOut))
                {
                    // Base class handled the command.  Do nothing more here.
                    return true;
                }

                if (guidCmdGroup == GuidList.guidTestLanguagePackageCmdSet)
                {
                    if (nCmdId == PkgCmdIDList.InvokeCodeSnippetsBrowser)
                    {
                        ExpansionProvider ep = this.GetExpansionProvider();
                        if (this.TextView != null && ep != null)
                        {
                            bool bDisplayed = ep.DisplayExpansionBrowser(
                                this.TextView,
                                "TestLanguagePackage Snippet:",
                                null,
                                false,
                                null,
                                false);
                        }
                        return true;   // Handled the command.
                    }
                }
                return false;   // Did not handle the command.
            }
        }
    }

    ```

     Następujące metody w klasie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy są wywoływane przez program Visual Studio w podanej kolejności podczas wstawiania fragmentu kodu:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Po <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> metoda jest wywoływana, fragment kodu został wstawiony i <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiekt jest w trybie edycji specjalne, używane do modyfikowania fragment kodu, który właśnie został wstawiony.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Wstawianie fragmentu kodu przy użyciu skrótu
 Implementacja skrótu z listy uzupełniania jest znacznie bardziej skomplikowane niż wdrażanie polecenia menu. Skrótach do fragmentów kodu należy najpierw dodać do listy uzupełniania IntelliSense programu word. Następnie musi wykryć, kiedy nazwa skrótu fragmentu kodu został wstawiony w wyniku zakończenia. Na koniec należy uzyskać tytuł fragmentu kodu i ścieżki przy użyciu nazwy skrótu i przekazać te informacje do <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> metody <xref:Microsoft.VisualStudio.Package.ExpansionProvider> metody.

 Aby dodać skrótach do fragmentów kodu do listy uzupełniania słów, należy dodać je do <xref:Microsoft.VisualStudio.Package.Declarations> obiektu w swojej <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy. Musi upewnij się, że można zidentyfikować skrót jako nazwy fragmentu kodu. Aby uzyskać przykład, zobacz [instruktażu: Pobieranie listy zainstalowane fragmenty kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Można wykryć wstawiania skrótów fragmentu kodu w <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> metody <xref:Microsoft.VisualStudio.Package.Declarations> klasy. Ponieważ nazwy fragmentu kodu został już wstawiony do pliku źródłowego, należy usunąć, gdy rozszerzenie zostanie wstawiona. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> Metoda przyjmuje zakres, który opisuje punkt wstawiania fragmentu; Jeśli zakres zawiera nazwy całego fragmentu kodu w pliku źródłowym, że nazwa zostanie zastąpiona przez fragment.

 W tym miejscu jest wersją <xref:Microsoft.VisualStudio.Package.Declarations> klasa, która obsługuje wstawiania fragmentu kodu, otrzymuje nazwę skrótów. Inne metody w <xref:Microsoft.VisualStudio.Package.Declarations> dla jasności pominięto klasy. Należy zauważyć, że Konstruktor tej klasy przyjmuje <xref:Microsoft.VisualStudio.Package.LanguageService> obiektu. To mogą być przekazane z wersją programu <xref:Microsoft.VisualStudio.Package.AuthoringScope> obiektu (na przykład implementacji <xref:Microsoft.VisualStudio.Package.AuthoringScope> klasy może potrwać <xref:Microsoft.VisualStudio.Package.LanguageService> w jego konstruktorze i przekazać ten obiekt do Twojej `TestDeclarations` konstruktora klasy).

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclarations : Declarations
    {
        private ArrayList       declarations;
        private LanguageService languageService;
        private TextSpan        commitSpan;

        public TestDeclarations(LanguageService langService)
            : base()
        {
            languageService = langService;
            declarations = new ArrayList();
        }

        // This method is used to add declarations to the internal list.
        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        // This method is called to get the string to commit to the source buffer.
        // Note that the initial extent is only what the user has typed so far.
        public override string OnCommit(IVsTextView textView,
                                        string textSoFar,
                                        char commitCharacter,
                                        int index,
                                        ref TextSpan initialExtent)
        {
            // We intercept this call only to get the initial extent
            // of what was committed to the source buffer.
            commitSpan = initialExtent;

            return base.OnCommit(textView,
                                 textSoFar,
                                 commitCharacter,
                                 index,
                                 ref initialExtent);
        }

        // This method is called after the string has been committed to the source buffer.
        public override char OnAutoComplete(IVsTextView textView,
                                            string committedText,
                                            char commitCharacter,
                                            int index)
        {
            TestDeclaration item = declarations[index] as TestDeclaration;
            if (item != null)
            {
                // In this example, TestDeclaration identifies types with a string.
                // You can choose a different approach.
                if (item.Type == "snippet")
                {
                    Source src = languageService.GetSource(textView);
                    if (src != null)
                    {
                        ExpansionProvider ep = src.GetExpansionProvider();
                        if (ep != null)
                        {
                            string title;
                            string path;
                            int commitLength = commitSpan.iEndIndex - commitSpan.iStartIndex;
                            if (commitLength < committedText.Length)
                            {
                                // Replace everything that was inserted
                                // so calculate the span of the full
                                // insertion, taking into account what
                                // was inserted when the commitSpan
                                // was obtained in the first place.
                                commitSpan.iEndIndex += (committedText.Length - commitLength);
                            }

                            if (ep.FindExpansionByShortcut(textView,
                                                           committedText,
                                                           commitSpan,
                                                           true,
                                                           out title,
                                                           out path))
                            {
                                ep.InsertNamedExpansion(textView,
                                                        title,
                                                        path,
                                                        commitSpan,
                                                        false);
                            }
                        }
                    }
                }
            }
            return '\0';
        }
    }
}
```

 Gdy usługa językowa pobiera nazwę skrótów, wywołuje <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> metodę, aby uzyskać nazwę pliku i kod tytuł fragmentu kodu. Następnie wywołuje usługa językowa <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy, aby wstawić fragment kodu. Następujące metody są wywoływane przez program Visual Studio w podanej kolejności w <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy podczas wstawiania fragmentu kodu:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Aby uzyskać więcej informacji na temat pobierania listy zainstalowanych fragmentów kodu dla usługi w języka, zobacz [instruktażu: Pobieranie listy zainstalowane fragmenty kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementacja klasy ExpansionFunction
 Funkcja rozszerzenia jest o nazwie funkcji, zostanie osadzony w szablon fragmentu kodu, która zwraca jedną lub więcej wartości do umieszczenia w polu. W celu obsługi funkcji rozszerzeń w usłudze języka, należy wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.ExpansionFunction> klasę i zaimplementować <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> metody. Musisz przesłonić <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.LanguageService> klasy w celu zwracania nowego wystąpienia wersji <xref:Microsoft.VisualStudio.Package.ExpansionFunction> klasy dla każdej funkcji rozszerzenia, które obsługujesz. Jeśli obsługujesz listę możliwych wartości z funkcji rozszerzenia, konieczne jest również przesłonięcie <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> method in Class metoda <xref:Microsoft.VisualStudio.Package.ExpansionFunction> klasy, aby powrócić do listy tych wartości.

 Funkcja rozszerzenia, która przyjmuje argumenty musi uzyskać dostęp do innych pól lub nie powinien być skojarzony z polem edycji, jako dostawca rozszerzeń może nie być w pełni zainicjowana przez czas, gdy zostanie wywołana funkcja rozszerzenia. W wyniku funkcji rozszerzania nie będzie mógł uzyskać wartości argumentów lub każdego innego pola.

### <a name="example"></a>Przykład
 Oto przykład jak funkcja proste rozszerzenie wywoływana `GetName` mogą zostać zaimplementowane. Ta funkcja rozszerzania dołącza numer na nazwę klasy bazowej każdorazowo zostanie uruchomiony, funkcja rozszerzenia (co odpowiada każdorazowo fragment kodu skojarzone jest wstawiany).

```csharp
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        private int classNameCounter = 0;

        public override ExpansionFunction CreateExpansionFunction(
            ExpansionProvider provider,
            string functionName)
        {
            ExpansionFunction function = null;
            if (functionName == "GetName")
            {
                ++classNameCounter;
                function = new TestGetNameExpansionFunction(provider, classNameCounter);
            }
            return function;
        }
    }

    internal class TestGetNameExpansionFunction : ExpansionFunction
    {
        private int nameCount;

        TestGetNameExpansionFunction(ExpansionProvider provider, int counter)
            : base(provider)
        {
            nameCount = counter;
        }

        public override string GetCurrentValue()
        {
            string name = "TestClass";
            name += nameCount.ToString();
            return name;
        }
    }
}
```

## <a name="see-also"></a>Zobacz też
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Fragmenty kodu](../../ide/code-snippets.md)
- [Przewodnik: pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)