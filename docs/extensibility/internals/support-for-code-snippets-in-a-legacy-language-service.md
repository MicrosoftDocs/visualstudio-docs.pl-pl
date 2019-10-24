---
title: Obsługa fragmentów kodu w starszej wersji usługi językowej | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- snippets, supporting in language services
- code snippets, supporting in language services [managed package framework]
- language services [managed package framework], supporting code snippets
ms.assetid: 7490325b-acee-4c2d-ac56-1cd5db1a1083
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d771db166baa66426c7a6d03b344c4bc7b74b27
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72723112"
---
# <a name="support-for-code-snippets-in-a-legacy-language-service"></a>Obsługa fragmentów kodu w starszej wersji usługi językowej
Fragment kodu jest fragmentem kodu, który jest wstawiany do pliku źródłowego. Sam fragment kodu jest szablonem opartym na formacie XML zawierającym zestaw pól. Te pola są wyróżniane po wstawieniu fragmentu i mogą mieć różne wartości w zależności od kontekstu, w którym wstawiany jest fragment kodu. Natychmiast po wstawieniu fragmentu, usługa języka może sformatować fragment kodu.

 Fragment kodu zostanie wstawiony w specjalnym trybie edycji, który umożliwia nawigowanie w polach fragmentu przy użyciu klawisza TAB. Pola mogą obsługiwać menu rozwijane w stylu IntelliSense. Użytkownik zatwierdza fragment kodu do pliku źródłowego przez wpisanie klawisza ENTER lub ESC. Aby dowiedzieć się więcej na temat wstawek, zobacz [fragmenty kodu](../../ide/code-snippets.md).

 Starsze usługi językowe są implementowane w ramach pakietu VSPackage, ale nowszym sposobem implementacji funkcji usługi językowej jest korzystanie z rozszerzeń MEF. Aby dowiedzieć się więcej, zobacz [Przewodnik: implementowanie fragmentów kodu](../../extensibility/walkthrough-implementing-code-snippets.md).

> [!NOTE]
> Zalecamy rozpoczęcie korzystania z nowego interfejsu API edytora tak szybko, jak to możliwe. Poprawi to wydajność usługi językowej i pozwala korzystać z nowych funkcji edytora.

## <a name="managed-package-framework-support-for-code-snippets"></a>Obsługa struktury pakietów zarządzanych dla fragmentów kodu
 Struktura pakietu zarządzanego (MPF) obsługuje większość funkcji fragmentowania kodu, od odczytu szablonu do wstawienia fragmentu i włączenia specjalnego trybu edycji. Pomoc techniczna jest zarządzana za pomocą klasy <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

 Po utworzeniu wystąpienia klasy <xref:Microsoft.VisualStudio.Package.Source>, Metoda <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionProvider%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService> jest wywoływana w celu uzyskania obiektu <xref:Microsoft.VisualStudio.Package.ExpansionProvider> (należy zauważyć, że klasa podstawowa <xref:Microsoft.VisualStudio.Package.LanguageService> zawsze zwraca nowy obiekt <xref:Microsoft.VisualStudio.Package.ExpansionProvider> dla każdego obiektu <xref:Microsoft.VisualStudio.Package.Source>).

 MPF nie obsługuje funkcji rozszerzających. Funkcja rozszerzająca to nazwana funkcja, która jest osadzona w szablonie fragmentu i zwraca co najmniej jedną wartość, która ma zostać umieszczona w polu. Wartości są zwracane przez usługę języka za pomocą obiektu <xref:Microsoft.VisualStudio.Package.ExpansionFunction>. Obiekt <xref:Microsoft.VisualStudio.Package.ExpansionFunction> musi być zaimplementowany przez usługę języka w celu obsługi funkcji rozszerzających.

## <a name="providing-support-for-code-snippets"></a>Zapewnianie pomocy technicznej dla fragmentów kodu
 Aby włączyć obsługę fragmentów kodu, należy dostarczyć lub zainstalować fragmenty wstawek, a użytkownik musi podać środki, aby wstawić te fragmenty. Aby włączyć obsługę fragmentów kodu, należy wykonać trzy czynności:

1. Instalowanie plików fragmentów kodu.

2. Włączanie fragmentów kodu dla usługi językowej.

3. Wywoływanie obiektu <xref:Microsoft.VisualStudio.Package.ExpansionProvider>.

### <a name="installing-the-snippet-files"></a>Instalowanie plików fragmentów kodu
 Wszystkie fragmenty kodu dla języka są przechowywane jako szablony w plikach XML, zazwyczaj jeden szablon fragmentu na plik. Aby uzyskać szczegółowe informacje o schemacie XML używanym do szablonów fragmentów kodu, zobacz [Dokumentacja schematu fragmentów kodu](../../ide/code-snippets-schema-reference.md). Każdy szablon fragmentu kodu jest identyfikowany za pomocą identyfikatora języka. Ten identyfikator języka jest określony w rejestrze i jest umieszczany w atrybucie `Language` tagu \<Code > w szablonie.

 Istnieją zwykle dwie lokalizacje, w których są przechowywane pliki szablonów fragmentów: 1), w których język został zainstalowany i 2) w folderze użytkownika. Te lokalizacje są dodawane do rejestru, aby **Menedżer fragmentów kodu** programu Visual Studio znalazł fragmenty. Folder użytkownika to miejsce, w którym są przechowywane fragmenty kodu utworzone przez użytkownika.

 Typowy układ folderu dla zainstalowanych plików szablonów fragmentów wygląda następująco: *[element InstallRoot]* \\ *[TestLanguage]* \Snippets \\ *[LCID]* \Snippets.

 *[Element InstallRoot]* to folder, w którym jest zainstalowany język.

 *[TestLanguage]* to nazwa Twojego języka jako nazwa folderu.

 *[LCID]* jest identyfikatorem ustawień regionalnych. W ten sposób są przechowywane zlokalizowane wersje fragmentów kodu. Na przykład identyfikator ustawień regionalnych dla języka angielskiego to 1033, więc *[LCID]* jest zastępowany przez 1033.

 Należy podać jeden dodatkowy plik i jest to plik indeksu, zwykle nazywany SnippetsIndex. XML lub ExpansionsIndex. XML (można użyć dowolnego prawidłowej nazwy pliku kończącego się na. xml). Ten plik jest zazwyczaj przechowywany w folderze *[element InstallRoot]* \\ *[TestLanguage]* i określa dokładną lokalizację folderu WSTAWEK, a także identyfikator języka i GUID usługi językowej, która używa fragmentów kodu. Dokładna ścieżka pliku indeksu jest umieszczana w rejestrze zgodnie z opisem w dalszej części "Instalowanie wpisów rejestru". Oto przykład pliku SnippetsIndex. XML:

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

 Tag \<Language > określa identyfikator języka (atrybut `Lang`) i identyfikator GUID usługi językowej.

 W tym przykładzie przyjęto założenie, że zainstalowano usługę języka w folderze instalacyjnym programu Visual Studio. Wartość% LCID% jest zastępowana bieżącym IDENTYFIKATORem ustawień regionalnych użytkownika. Można dodać wiele tagów > \<SnippetDir, jeden dla każdego katalogu i ustawień regionalnych. Ponadto folder fragmentowania może zawierać podfoldery, z których każdy jest identyfikowany w pliku indeksu z tagiem \<SnippetSubDir >, który jest osadzony w tagu \<SnippetDir >.

 Użytkownicy mogą również tworzyć własne fragmenty kodu dla danego języka. Są one zazwyczaj przechowywane w folderze ustawień użytkownika, na przykład *[TestDocs]* wstawek \Code \\ *[TestLanguage]* \Test fragmenty kodu, gdzie *[TestDocs]* jest lokalizacją folderu ustawień użytkownika dla programu Visual Studio.

 Następujące elementy podstawiania można umieścić w ścieżce przechowywanej w tagu \<DirPath > w pliku indeksu.

|Element|Opis|
|-------------|-----------------|
|ISTNIEJĄCYCH|Identyfikator ustawień regionalnych.|
|Element InstallRoot|Folder główny instalacji programu Visual Studio, na przykład C:\Program Files\Microsoft Visual Studio 8.|
|%ProjDir%|Folder zawierający bieżący projekt.|
|%ProjItem%|Folder zawierający bieżący element projektu.|
|%TestDocs%|Folder w folderze ustawień użytkownika, na przykład C:\Dokumenty i ustawienia \\ *[username]* \Moje Documents\Visual Studio\8.|

### <a name="enabling-code-snippets-for-your-language-service"></a>Włączanie fragmentów kodu dla usługi językowej
 Fragmenty kodu dla usługi językowej można włączyć, dodając do pakietu VSPackage atrybut <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute> (zobacz [Rejestrowanie starszej wersji usługi językowej,](../../extensibility/internals/registering-a-legacy-language-service1.md) Aby uzyskać szczegółowe informacje). Parametry <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.ShowRoots%2A> i <xref:Microsoft.VisualStudio.Shell.ProvideLanguageCodeExpansionAttribute.SearchPaths%2A> są opcjonalne, ale należy uwzględnić `SearchPaths` nazwany parametr w celu informowania **Menedżera fragmentów kodu** o lokalizacji wstawek.

 Poniżej przedstawiono przykład sposobu użycia tego atrybutu:

```
[ProvideLanguageCodeExpansion(
         typeof(TestSnippetLanguageService),
         "Test Snippet Language",          // Name of language used as registry key
         0,                               // Resource ID of localized name of language service
         "Test Snippet Language",        // Name of Language attribute in snippet template
         @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\SnippetsIndex.xml",  // Path to snippets index
         SearchPaths = @"%InstallRoot%\Test Snippet Language\Snippets\%LCID%\")]    // Path to snippets
```

### <a name="calling-the-expansion-provider"></a>Wywoływanie dostawcy rozbudowy
 Usługa językowa kontroluje Wstawianie dowolnego fragmentu kodu, a także sposób wywoływania wstawiania.

## <a name="calling-the-expansion-provider-for-code-snippets"></a>Wywoływanie dostawcy rozwinięcia dla fragmentów kodu
 Istnieją dwa sposoby wywoływania dostawcy rozwinięcia: za pomocą polecenia menu lub za pomocą skrótu z listy uzupełniania.

### <a name="inserting-a-code-snippet-by-using-a-menu-command"></a>Wstawianie fragmentu kodu za pomocą polecenia menu
 Aby użyć polecenia menu do wyświetlenia przeglądarki fragmentu kodu, Dodaj polecenie menu, a następnie Wywołaj metodę <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> w interfejsie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> w odpowiedzi na to polecenie menu.

1. Dodaj polecenie i przycisk do pliku. vsct. Instrukcje dotyczące tego działania można znaleźć w temacie [Tworzenie rozszerzenia za pomocą polecenia menu](../../extensibility/creating-an-extension-with-a-menu-command.md).

2. Utwórz klasę z klasy <xref:Microsoft.VisualStudio.Package.ViewFilter> i Zastąp metodę <xref:Microsoft.VisualStudio.Package.ViewFilter.QueryCommandStatus%2A>, aby wskazać obsługę nowego polecenia menu. Ten przykład zawsze włącza polecenie menu.

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

3. Zastąp metodę <xref:Microsoft.VisualStudio.Package.ViewFilter.HandlePreExec%2A> w klasie <xref:Microsoft.VisualStudio.Package.ViewFilter>, aby uzyskać obiekt <xref:Microsoft.VisualStudio.Package.ExpansionProvider> i wywołać metodę <xref:Microsoft.VisualStudio.Package.ExpansionProvider.DisplayExpansionBrowser%2A> dla tego obiektu.

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

     Następujące metody klasy <xref:Microsoft.VisualStudio.Package.ExpansionProvider> są wywoływane przez program Visual Studio w danej kolejności podczas procesu wstawiania fragmentu kodu:

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnItemChosen%2A>

5. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

6. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

7. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

8. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

     Po wywołaniu metody <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A> fragment został wstawiony, a obiekt <xref:Microsoft.VisualStudio.Package.ExpansionProvider> jest w specjalnym trybie edycji używanym do modyfikacji fragmentu, który został właśnie wstawiony.

### <a name="inserting-a-code-snippet-by-using-a-shortcut"></a>Wstawianie fragmentu kodu przy użyciu skrótu
 Implementacja skrótu z listy uzupełniania jest znacznie większa niż implementowanie polecenia menu. Najpierw należy dodać skróty wstawek do listy uzupełniania słów IntelliSense. Następnie należy wykryć, kiedy wstawiono nazwę skrótu fragmentu w wyniku wykonania. Na koniec należy uzyskać tytuł wstawki i ścieżkę przy użyciu nazwy skrótu i przekazać te informacje do metody <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> na <xref:Microsoft.VisualStudio.Package.ExpansionProvider> metodzie.

 Aby dodać skróty wstawek do listy uzupełniania wyrazów, Dodaj je do obiektu <xref:Microsoft.VisualStudio.Package.Declarations> w klasie <xref:Microsoft.VisualStudio.Package.AuthoringScope>. Musisz się upewnić, że można zidentyfikować skrót jako nazwę fragmentu kodu. Aby zapoznać się z przykładem, zobacz [Przewodnik: Pobieranie listy zainstalowanych fragmentów kodu (starsza implementacja)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

 Można wykryć Wstawianie skrótu fragmentu kodu w metodzie <xref:Microsoft.VisualStudio.Package.Declarations.OnAutoComplete%2A> klasy <xref:Microsoft.VisualStudio.Package.Declarations>. Ponieważ nazwa fragmentu została już wstawiona do pliku źródłowego, należy ją usunąć po wstawieniu rozszerzenia. Metoda <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> przyjmuje zakres, który opisuje punkt wstawiania dla fragmentu kodu; Jeśli zakres obejmuje całą nazwę fragmentu kodu w pliku źródłowym, ta nazwa zostanie zastąpiona fragmentem.

 Oto wersja klasy <xref:Microsoft.VisualStudio.Package.Declarations>, która obsługuje wstawianie wstawek przy użyciu nazwy skrótu. Inne metody klasy <xref:Microsoft.VisualStudio.Package.Declarations> zostały pominięte w celu przejrzystości. Należy zauważyć, że Konstruktor tej klasy przyjmuje obiekt <xref:Microsoft.VisualStudio.Package.LanguageService>. Może to być przekazane z wersji obiektu <xref:Microsoft.VisualStudio.Package.AuthoringScope> (na przykład implementacja klasy <xref:Microsoft.VisualStudio.Package.AuthoringScope> może przyjmować obiekt <xref:Microsoft.VisualStudio.Package.LanguageService> w jego konstruktorze i przekazać go do konstruktora klasy `TestDeclarations`).

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

 Gdy usługa języka Pobiera nazwę skrótu, wywołuje metodę <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FindExpansionByShortcut%2A>, aby uzyskać nazwę pliku i tytuł fragmentu kodu. Usługa językowa następnie wywołuje metodę <xref:Microsoft.VisualStudio.Package.ExpansionProvider.InsertNamedExpansion%2A> w klasie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> w celu wstawienia fragmentu kodu. Następujące metody są wywoływane przez program Visual Studio w danej kolejności w klasie <xref:Microsoft.VisualStudio.Package.ExpansionProvider> podczas procesu wstawiania fragmentu kodu:

1. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.IsValidKind%2A>

2. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnBeforeInsertion%2A>

3. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.FormatSpan%2A>

4. <xref:Microsoft.VisualStudio.Package.ExpansionProvider.OnAfterInsertion%2A>

   Aby uzyskać więcej informacji na temat pobierania listy zainstalowanych fragmentów kodu dla usługi językowej, zobacz [Przewodnik: Pobieranie listy zainstalowanych fragmentów kodu (starsza implementacja)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md).

## <a name="implementing-the-expansionfunction-class"></a>Implementowanie klasy ExpansionFunction
 Funkcja rozszerzająca to nazwana funkcja, która jest osadzona w szablonie fragmentu i zwraca co najmniej jedną wartość, która ma zostać umieszczona w polu. Aby można było obsługiwać funkcje rozszerzania w usłudze językowej, należy utworzyć klasę z klasy <xref:Microsoft.VisualStudio.Package.ExpansionFunction> i zaimplementować metodę <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetCurrentValue%2A>. Następnie należy zastąpić metodę <xref:Microsoft.VisualStudio.Package.LanguageService.CreateExpansionFunction%2A> w klasie <xref:Microsoft.VisualStudio.Package.LanguageService>, aby zwracała nowe wystąpienie klasy <xref:Microsoft.VisualStudio.Package.ExpansionFunction> dla każdej obsługiwanej funkcji rozszerzania. Jeśli obsługujesz listę możliwych wartości z funkcji rozszerzającej, należy również zastąpić metodę <xref:Microsoft.VisualStudio.Package.ExpansionFunction.GetIntellisenseList%2A> w klasie <xref:Microsoft.VisualStudio.Package.ExpansionFunction>, aby zwrócić listę tych wartości.

 Funkcja rozszerzająca, która przyjmuje argumenty lub muszą uzyskać dostęp do innych pól, nie powinna być skojarzona z edytowalnym polem, ponieważ dostawca rozwinięcia może nie być w pełni zainicjowany przez czas, gdy wywoływana jest funkcja rozszerzania. W związku z tym funkcja rozszerzania nie jest w stanie uzyskać wartości argumentów ani innych pól.

### <a name="example"></a>Przykład
 Oto przykład sposobu, w jaki prosta funkcja rozszerzająca o nazwie `GetName` może zostać zaimplementowana. Ta funkcja rozszerzania dołącza liczbę do nazwy klasy bazowej za każdym razem, gdy jest tworzona Funkcja rozszerzania (która odnosi się do każdej chwili wstawienia skojarzonego fragmentu kodu).

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

## <a name="see-also"></a>Zobacz także
- [Funkcje starszej wersji usługi językowej](../../extensibility/internals/legacy-language-service-features1.md)
- [Rejestrowanie starszej wersji usługi językowej](../../extensibility/internals/registering-a-legacy-language-service1.md)
- [Fragmenty kodu](../../ide/code-snippets.md)
- [Przewodnik: pobieranie listy zainstalowanych fragmentów kodu (starsza wersja implementacji)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)