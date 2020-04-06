---
title: Obsługa fragmentów kodu w starszej usłudze językowej | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ad871eb73341f6ab87229687e2a6df898ffda32d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704912"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Obsługa fragmentów kodu w starszej wersji usługi językowej
Fragment kodu to fragment kodu wstawiony do pliku źródłowego. Sam fragment kodu jest szablonem opartym na języku XML z zestawem pól. Pola te są wyróżnione po wstawieniu fragmentu kodu i mogą mieć różne wartości w zależności od kontekstu, w którym wstawiany jest fragment kodu. Natychmiast po wstawieniu fragmentu kodu usługa języka może sformatować fragment kodu.

 Fragment kodu jest wstawiany w trybie edycji specjalnej, który umożliwia poruszanie się po polach fragmentu kodu za pomocą klawisza TAB. Pola mogą obsługiwać menu rozwijane w stylu IntelliSense. Użytkownik zatwierdza fragment kodu do pliku źródłowego, wpisując klawisz ENTER lub klawisz ESC. Aby dowiedzieć się więcej o urywkach, zobacz [Fragmenty kodu](../../ide/code-snippets.md).

 Starsze usługi języka są implementowane jako część VSPackage, ale nowszym sposobem implementowania funkcji usługi języka jest użycie rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Instruktaż: Implementowanie fragmentów kodu](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Zaleca się, aby rozpocząć korzystanie z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i umożliwi korzystanie z nowych funkcji edytora.

## <a name="managed-package-framework-support-for-code-snippets"></a>Obsługa struktury pakietu zarządzanego dla urywki kodu
 Struktura pakietu zarządzanego (MPF) obsługuje większość funkcji fragmentu kodu, od odczytu szablonu do wstawiania fragmentu kodu i włączania trybu edycji specjalnej. Obsługa jest zarządzana za pośrednictwem <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasy.

 Po <xref:Microsoft.VisualStudio.Package.Source> wystąpieniu <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> klasy, metoda w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie jest wywoływana <xref:Microsoft.VisualStudio.Package.ExpansionProvider> w celu uzyskania <xref:Microsoft.VisualStudio.Package.LanguageService> obiektu (należy <xref:Microsoft.VisualStudio.Package.ExpansionProvider> zauważyć, <xref:Microsoft.VisualStudio.Package.Source> że klasa podstawowa zawsze zwraca nowy obiekt dla każdego obiektu).

 MPF nie obsługuje funkcji rozszerzenia. Funkcja rozszerzenia jest nazwaną funkcją osadzoną w szablonie fragmentu kodu i zwraca jedną lub więcej wartości, które mają zostać umieszczone w polu. Wartości są zwracane przez samą <xref:Microsoft.VisualStudio.Package.ExpansionFunction> usługę języka za pośrednictwem obiektu. Obiekt <xref:Microsoft.VisualStudio.Package.ExpansionFunction> musi być zaimplementowany przez usługę języka do obsługi funkcji rozszerzenia.

## <a name="providing-support-for-code-snippets"></a>Zapewnienie obsługi fragmentów kodu
 Aby włączyć obsługę fragmentów kodu, należy podać lub zainstalować fragmenty kodu i należy zapewnić użytkownikowi środki do wstawienia tych fragmentów. Istnieją trzy kroki, aby włączyć obsługę fragmentów kodu:

1. Instalowanie plików urywków.

2. Włączanie fragmentów kodu dla usługi językowej.

3. Wywoływanie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiektu.

### <a name="installing-the-snippet-files"></a>Instalowanie plików urywków
 Wszystkie fragmenty kodu języka są przechowywane jako szablony w plikach XML, zazwyczaj jeden szablon urywka na plik. Aby uzyskać szczegółowe informacje na temat schematu XML używanego dla szablonów fragmentów kodu, zobacz [Odwołanie do schematu urywków kodu](../../ide/code-snippets-schema-reference.md). Każdy szablon fragmentu jest identyfikowany za pomocą identyfikatora języka. Ten identyfikator języka jest określony w rejestrze `Language` i jest \<umieszczany w atrybucie tagu Code> w szablonie.

 Zazwyczaj są dwie lokalizacje, w których są przechowywane pliki szablonów fragmentów kodu: 1) gdzie język został zainstalowany i 2) w folderze użytkownika. Te lokalizacje są dodawane do rejestru, dzięki czemu **Menedżer urywków kodu** programu Visual Studio może znaleźć fragmenty kodu. Folder użytkownika to miejsce, w którym są przechowywane fragmenty utworzone przez użytkownika.

 Typowy układ folderu dla zainstalowanych plików szablonów fragmentów kodu wygląda następująco: *[InstallRoot]*\\ *[TestLanguage]* \Urywki\\ *[LCID]* \Urywki.

 *[InstallRoot]* to folder, w który jest zainstalowany język.

 *[TestLanguage]* to nazwa twojego języka jako nazwa folderu.

 *[LCID]* jest identyfikatorem ustawień regionalnych. W ten sposób przechowywane są zlokalizowane wersje urywków. Na przykład identyfikator ustawień regionalnych dla języka angielskiego wynosi 1033, więc *[LCID]* jest zastępowany przez 1033.

 Należy podać jeden dodatkowy plik, który jest plikiem indeksu, zwykle nazywanym 20000.xml lub ExpansionsIndex.xml (można użyć dowolnej prawidłowej nazwy pliku kończącej się na .xml). Ten plik jest zazwyczaj przechowywany w folderze *[InstallRoot]*\\ *[TestLanguage]* i określa dokładną lokalizację folderu urywków, a także identyfikator języka i identyfikator GUID usługi językowej, która używa fragmentów kodu. Dokładna ścieżka pliku indeksu jest umieszczana w rejestrze, jak opisano później w "Instalowanie wpisów rejestru". Oto przykład pliku UrywekIndex.xml:

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

 Tag \<Language> określa identyfikator języka `Lang` (atrybut) i identyfikator GUID usługi języka.

 W tym przykładzie przyjęto założenie, że usługa języka została zainstalowana w folderze instalacyjnym programu Visual Studio. %LCID% zostanie zastąpiony bieżącym identyfikatorem ustawień regionalnych użytkownika. Można \<dodać wiele znaczników Urywek>, po jednym dla każdego katalogu i ustawień regionalnych. Ponadto folder urywka może zawierać podfoldery, z których każdy jest identyfikowany w pliku indeksu \<za pomocą znacznika \<SnippetDir> osadzonego w znaczniku> Urywek.

 Użytkownicy mogą również tworzyć własne fragmenty kodu dla Twojego języka. Są one zazwyczaj przechowywane w folderze ustawień użytkownika, na przykład *[TestDocs]* \Code Urywki\\ *[TestLanguage]* \Test Code Urywki, gdzie *[TestDocs]* jest lokalizacją folderu ustawień użytkownika dla programu Visual Studio.

 Następujące elementy podstawienia można umieścić w ścieżce przechowywanej w tagu \<DirPath> w pliku indeksu.

|Element|Opis|
|-------------|-----------------|
|%LCID%|Identyfikator ustawień regionalnych.|
|%InstallRoot%|Główny folder instalacyjny programu Visual Studio, na przykład C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Folder zawierający bieżący projekt.|
|%ProjItem%|Folder zawierający bieżący element projektu.|
|%TestDocs%|Folder w folderze ustawień użytkownika, na przykład C:\Documents and Settings\\ *[nazwa_ _moja nazwa_* Moje dokumenty\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Włączanie urywków kodu dla usługi językowej
 Można włączyć fragmenty kodu dla usługi języka, <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> dodając atrybut do vspackage (zobacz [Rejestrowanie usługi języka starszego,](../../extensibility/internals/registering-a-legacy-language-service1.md) aby uzyskać szczegółowe informacje). Parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> i są opcjonalne, ale `SearchPaths` należy dołączyć nazwany parametr, aby poinformować **Menedżera urywków kodu** o lokalizacji fragmentów kodu.

 Oto przykład użycia tego atrybutu:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Dzwonienie do dostawcy rozszerzeń
 Usługa języka kontroluje wstawianie dowolnego fragmentu kodu, a także sposób wywoływania wstawiania.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Wywoływanie dostawcy rozszerzenia dla urywki kodu
 Istnieją dwa sposoby wywoływania dostawcy rozszerzenia: za pomocą polecenia menu lub za pomocą skrótu z listy uzupełniania.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Wstawianie fragmentu kodu przy użyciu polecenia menu
 Aby użyć polecenia menu do wyświetlenia przeglądarki urywka, należy <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> dodać polecenie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> menu, a następnie wywołać metodę w interfejsie w odpowiedzi na to polecenie menu.

1. Dodaj polecenie i przycisk do pliku vsct. Instrukcje można znaleźć w temacie [Tworzenie rozszerzenia za pomocą polecenia menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Wyprowadzić klasę z <xref:Microsoft.VisualStudio.Package.ViewFilter> klasy i zastąpić <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A> metodę, aby wskazać obsługę nowego polecenia menu. W tym przykładzie zawsze włącza polecenie menu.

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

3. <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> Zastądnie metody <xref:Microsoft.VisualStudio.Package.ViewFilter> w klasie, aby uzyskać <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiekt i wywołać <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> metodę na tym obiekcie.

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

     Następujące metody w <xref:Microsoft.VisualStudio.Package.ExpansionProvider> klasie są wywoływane przez visual studio w danej kolejności podczas procesu wstawiania fragmentu kodu:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Po <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> wywołaniu metody fragment kodu został wstawiony, a <xref:Microsoft.VisualStudio.Package.ExpansionProvider> obiekt jest w trybie edycji specjalnej używany do modyfikowania fragmentu kodu, który właśnie został wstawiony.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Wstawianie fragmentu kodu przy użyciu skrótu
 Implementacja skrótu z listy uzupełnień jest znacznie bardziej zaangażowana niż implementowanie polecenia menu. Najpierw należy dodać skróty urywka do listy uzupełniania wyrazów IntelliSense. Następnie należy wykryć, kiedy nazwa skrótu fragmentu kodu została wstawiona w wyniku uzupełnienia. Na koniec należy uzyskać tytuł fragmentu kodu i ścieżkę przy użyciu <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> nazwy skrótu i przekazać te informacje do metody. <xref:Microsoft.VisualStudio.Package.ExpansionProvider>

 Aby dodać skróty urywka do listy uzupełnień <xref:Microsoft.VisualStudio.Package.Declarations> wyrazów, dodaj je do obiektu w klasie. <xref:Microsoft.VisualStudio.Package.AuthoringScope> Należy upewnić się, że skrót można zidentyfikować jako nazwę fragmentu kodu. Na przykład zobacz [Instruktaż: Uzyskiwanie listy urywków kodu zainstalowanego (starsza implementacja)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Można wykryć wstawienie skrótu fragmentu <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> kodu <xref:Microsoft.VisualStudio.Package.Declarations> w metodzie klasy. Ponieważ nazwa fragmentu kodu została już wstawiona do pliku źródłowego, należy ją usunąć po wstawieniu rozszerzenia. Metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> przyjmuje zakres, który opisuje punkt wstawiania fragmentu kodu; jeśli zakres zawiera całą nazwę fragmentu kodu w pliku źródłowym, nazwa ta zostanie zastąpiona fragmentem kodu.

 Oto wersja <xref:Microsoft.VisualStudio.Package.Declarations> klasy, która obsługuje wstawianie fragmentu o nazwie skrótu. Inne metody <xref:Microsoft.VisualStudio.Package.Declarations> w klasie zostały pominięte dla jasności. Należy zauważyć, że konstruktor <xref:Microsoft.VisualStudio.Package.LanguageService> tej klasy zajmuje obiekt. To może być przekazywane z <xref:Microsoft.VisualStudio.Package.AuthoringScope> wersji obiektu (na przykład <xref:Microsoft.VisualStudio.Package.AuthoringScope> implementacja klasy <xref:Microsoft.VisualStudio.Package.LanguageService> może podjąć obiekt w jego konstruktora i przekazać ten obiekt do konstruktora `TestDeclarations` klasy).

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

 Gdy usługa języka pobiera nazwę skrótu, wywołuje <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A> metodę, aby uzyskać nazwę pliku i tytuł fragmentu kodu. Usługa języka następnie <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> wywołuje metodę <xref:Microsoft.VisualStudio.Package.ExpansionProvider> w klasie, aby wstawić fragment kodu. Następujące metody są wywoływane przez visual studio <xref:Microsoft.VisualStudio.Package.ExpansionProvider> w danej kolejności w klasie podczas procesu wstawiania fragmentu kodu:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Aby uzyskać więcej informacji na temat uzyskiwania listy zainstalowanych fragmentów kodu dla usługi językowej, zobacz [Instruktaż: Uzyskiwanie listy zainstalowanych fragmentów kodu (starsza implementacja).](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)

## <a name="implementing-the-expansionfunction-class"></a>Implementowanie klasy ExpansionFunction
 Funkcja rozszerzenia jest nazwaną funkcją osadzoną w szablonie fragmentu kodu i zwraca jedną lub więcej wartości, które mają zostać umieszczone w polu. Aby obsługiwać funkcje rozszerzenia w usłudze języka, należy <xref:Microsoft.VisualStudio.Package.ExpansionFunction> wyprowadzić <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A> klasę z klasy i zaimplementować metodę. Następnie należy zastąpić <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> metodę w <xref:Microsoft.VisualStudio.Package.LanguageService> klasie, aby zwrócić nowe wystąpienie wersji <xref:Microsoft.VisualStudio.Package.ExpansionFunction> klasy dla każdej funkcji rozszerzenia, które obsługujesz. Jeśli obsługujesz listę możliwych wartości z funkcji rozszerzania, należy <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> również <xref:Microsoft.VisualStudio.Package.ExpansionFunction> zastąpić metodę w klasie, aby zwrócić listę tych wartości.

 Funkcja rozszerzania, która przyjmuje argumenty lub musi uzyskać dostęp do innych pól, nie powinna być skojarzona z edytowalnym polem, ponieważ dostawca rozszerzeń może nie zostać w pełni zainicjowany przez wywołanie funkcji rozszerzenia. W rezultacie funkcja rozszerzenia nie jest w stanie uzyskać wartości swoich argumentów lub innego pola.

### <a name="example"></a>Przykład
 Oto przykład, jak prosta funkcja `GetName` rozszerzenia wywołana może być zaimplementowana. Ta funkcja rozszerzania dołącza liczbę do nazwy klasy podstawowej za każdym razem, gdy funkcja rozszerzenia jest wystąpienia (co odpowiada za każdym razem, gdy wstawiany jest skojarzony fragment kodu).

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
