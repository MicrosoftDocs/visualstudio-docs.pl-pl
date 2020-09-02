---
title: Tworzenie systemu podstawowego projektu, część 2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2b9d5ce673e0ee44e888905239c12251241015ab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903830"
---
# <a name="create-a-basic-project-system-part-2"></a>Tworzenie podstawowego systemu projektu, część 2
Pierwsze wskazówki w tej serii, [Tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md), pokazuje, jak utworzyć podstawowy system projektu. Ten przewodnik jest oparty na podstawowym systemie projektu przez dodanie szablonu programu Visual Studio, strony właściwości i innych funkcji. Przed rozpoczęciem tego procesu należy wykonać pierwszą Instruktaż.

W tym instruktażu przedstawiono sposób tworzenia typu projektu, który ma rozszerzenie nazwy pliku projektu *. proj*. Aby ukończyć przewodnik, nie musisz tworzyć własnego języka, ponieważ przewodnik jest pożyczany z istniejącego systemu projektu Visual C#.

W tym instruktażu przedstawiono sposób wykonywania następujących zadań:

- Utwórz szablon programu Visual Studio.

- Wdróż szablon programu Visual Studio.

- Utwórz węzeł podrzędny typ projektu w oknie dialogowym **Nowy projekt** .

- Włącz podstawianie parametrów w szablonie programu Visual Studio.

- Utwórz stronę właściwości projektu.

> [!NOTE]
> Kroki opisane w tym instruktażu są oparte na projekcie w języku C#. Jednak z wyjątkiem określonych, takich jak rozszerzenia nazw plików i kod, można użyć tych samych kroków dla projektu Visual Basic.

## <a name="create-a-visual-studio-template"></a>Tworzenie szablonu programu Visual Studio
- [Utwórz podstawowy system projektu, część 1 pokazuje,](../extensibility/creating-a-basic-project-system-part-1.md) jak utworzyć podstawowy szablon projektu i dodać go do systemu projektu. Pokazano również, jak zarejestrować ten szablon w programie Visual Studio przy użyciu <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutu, który zapisuje pełną ścieżkę folderu * \\ Templates\Projects\SimpleProject \\ * w rejestrze systemowym.

Przy użyciu szablonu programu Visual Studio (plik *. vstemplate* ) zamiast podstawowego szablonu projektu można kontrolować sposób wyświetlania szablonu w oknie dialogowym **Nowy projekt** oraz jak zastępuje się parametry szablonu. Plik *. vstemplate* jest plikiem XML, który opisuje, jak pliki źródłowe mają być uwzględniane podczas tworzenia projektu przy użyciu szablonu systemu projektu. Sam system projektu jest kompilowany przez zebranie pliku *. vstemplate* i plików źródłowych w pliku *zip* oraz wdrożenie przez skopiowanie pliku *zip* do lokalizacji znanej dla programu Visual Studio. Ten proces został szczegółowo opisany w dalszej części tego przewodnika.

1. W programie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Otwórz rozwiązanie SimpleProject utworzone w następujący sposób: [Utwórz podstawowy system projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. W pliku *SimpleProjectPackage.cs* Znajdź atrybut ProvideProjectFactory. Zastąp drugi parametr (nazwę projektu) wartością null, a czwarty parametr (ścieżka do folderu szablonu projektu) z ". \\ \NullPath "w następujący sposób.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Dodaj plik XML o nazwie *SimpleProject. vstemplate* do folderu * \\ Templates\Projects\SimpleProject \\ * .

4. Zastąp zawartość *SimpleProject. vstemplate* następującym kodem.

    ```xml
    <VSTemplate Version="2.0.0" Type="Project"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
      <TemplateData>
        <Name>SimpleProject Application</Name>
        <Description>
          A project for creating a SimpleProject application
        </Description>
        <Icon>SimpleProject.ico</Icon>
        <ProjectType>SimpleProject</ProjectType>
      </TemplateData>
      <TemplateContent>
        <Project File="SimpleProject.myproj" ReplaceParameters="true">
          <ProjectItem ReplaceParameters="true" OpenInEditor="true">
            Program.cs
          </ProjectItem>
          <ProjectItem ReplaceParameters="true" OpenInEditor="false">
            AssemblyInfo.cs
          </ProjectItem>
        </Project>
      </TemplateContent>
    </VSTemplate>
    ```

5. W oknie **Właściwości** zaznacz wszystkie pięć plików w folderze * \\ Templates\Projects\SimpleProject \\ * i ustaw **akcję kompilacja** na **ZipProject**.

    ![Prosty folder projektu](../extensibility/media/simpproj2.png "SimpProj2")

    \<TemplateData>Sekcja określa lokalizację i wygląd typu projektu SimpleProject w oknie dialogowym **Nowy projekt** w następujący sposób:

- \<Name>Element nazywa szablon projektu, który ma być aplikacją SimpleProject.

- \<Description>Element zawiera opis, który pojawia się w oknie dialogowym **Nowy projekt** w przypadku wybrania szablonu projektu.

- \<Icon>Element określa ikonę, która pojawia się razem z typem projektu SimpleProject.

- \<ProjectType>Element nazwa typ projektu w oknie dialogowym **Nowy projekt** . Ta nazwa zastępuje parametr nazwy projektu atrybutu ProvideProjectFactory.

  > [!NOTE]
  > \<ProjectType>Element musi być zgodny z `LanguageVsTemplate` argumentem `ProvideProjectFactory` atrybutu w pliku SimpleProjectPackage.cs.

  \<TemplateContent>Sekcja opisuje te pliki, które są generowane podczas tworzenia nowego projektu:

- *SimpleProject. proj*

- *Program.cs*

- *AssemblyInfo.cs*

  Wszystkie trzy pliki mają `ReplaceParameters` ustawioną wartość true, co umożliwia podstawianie parametrów. Plik *program.cs* ma `OpenInEditor` wartość true, co powoduje, że plik zostanie otwarty w edytorze kodu podczas tworzenia projektu.

  Aby uzyskać więcej informacji na temat elementów w schemacie szablonu programu Visual Studio, zobacz [Dokumentacja schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Jeśli projekt zawiera więcej niż jeden szablon programu Visual Studio, każdy szablon znajduje się w osobnym folderze. Każdy plik w tym folderze musi mieć ustawioną **akcję kompilacji** równą **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Dodawanie pliku o minimalnej vsct
 Program Visual Studio musi być uruchomiony w trybie Instalatora, aby można było rozpoznać nowy lub zmodyfikowany szablon programu Visual Studio. Tryb instalacji wymaga obecności pliku *. vsct* . W związku z tym należy dodać plik o minimalnej *vsct* do projektu.

1. Dodaj plik XML o nazwie *SimpleProject. vsct* do projektu SimpleProject.

2. Zastąp zawartość pliku *SimpleProject. vsct* następującym kodem.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Ustaw **akcję kompilacji** tego pliku na **VSCTCompile**. Można to zrobić tylko w pliku *. csproj* , a nie w oknie **Właściwości** . Upewnij się, że w tym momencie **Akcja kompilacji** tego pliku jest ustawiona na **none** .

    1. Kliknij prawym przyciskiem myszy węzeł SimpleProject, a następnie kliknij polecenie **Edytuj SimpleProject. csproj**.

    2. W pliku *. csproj* Znajdź element *SimpleProject. vsct* .

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Zmień akcję kompilacji na **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. plik projektu i Zamknij Edytor.

    5. Zapisz węzeł SimpleProject, a następnie w **Eksplorator rozwiązań** kliknij pozycję **Załaduj ponownie projekt**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Przejrzyj kroki kompilacji szablonu programu Visual Studio
 System kompilacji projektu pakietu VSPackage zazwyczaj uruchamia program Visual Studio w trybie Instalatora, gdy plik *. vstemplate* został zmieniony lub projekt zawierający plik *. vstemplate* zostanie odbudowany. Można postępować zgodnie z ustawieniem poziomu szczegółowości MSBuild na normalny lub wyższy.

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Rozwiń węzeł **projekty i rozwiązania** , a następnie wybierz opcję **Kompiluj i uruchom**.

3. Ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** na **normalny**. Kliknij przycisk **OK**.

4. Skompiluj ponownie projekt SimpleProject.

    Krok kompilacji do utworzenia pliku projektu *. zip* powinien wyglądać podobnie do poniższego przykładu.

```
ZipProjects:
1>  Zipping ProjectTemplates
1>  Zipping <path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip...
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates\\\\SimpleProject.zip".
1>  Copying file from "<path>\SimpleProject\SimpleProject\obj\Debug\SimpleProject.zip" to "bin\Debug\\ProjectTemplates\\\\SimpleProject.zip".
1>  SimpleProject -> <path>\SimpleProject\SimpleProject\bin\Debug\ProjectTemplates\SimpleProject.zip
1>ZipItems:
1>  Zipping ItemTemplates
1>  SimpleProject ->
```

## <a name="deploy-a-visual-studio-template"></a>Wdrażanie szablonu programu Visual Studio
Szablony programu Visual Studio nie zawierają informacji o ścieżce. W związku z tym plik template *. zip* musi zostać wdrożony w lokalizacji znanej dla programu Visual Studio. Lokalizacja folderu ProjectTemplates jest zwykle *<% LocalAppData% > \microsoft\visualstudio\14.0exp\projecttemplates*.

Aby wdrożyć fabrykę projektu, program instalacyjny musi mieć uprawnienia administratora. Wdraża szablony w węźle instalacyjnym programu Visual Studio: *. ..\Microsoft Visual Studio 14.0 \ Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testowanie szablonu programu Visual Studio
Przetestuj fabrykę projektu, aby zobaczyć, czy tworzy hierarchię projektu przy użyciu szablonu programu Visual Studio.

1. Zresetuj wystąpienie eksperymentalne zestawu Visual Studio SDK.

    Na [!INCLUDE[win7](../debugger/includes/win7_md.md)] : w menu **Start** Znajdź folder **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** , a następnie wybierz pozycję **Zresetuj Microsoft Visual Studio wystąpienie eksperymentalne**.

    W nowszych wersjach systemu Windows: na ekranie **startowym** wpisz **Zresetuj Microsoft Visual Studio \<version> wystąpienie eksperymentalne**.

2. Zostanie wyświetlone okno wiersza polecenia. Gdy zobaczysz słowa, **naciśnij dowolny klawisz, aby kontynuować**, kliknij przycisk **Enter**. Po zamknięciu okna Otwórz program Visual Studio.

3. Skompiluj ponownie projekt SimpleProject i Rozpocznij debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.

4. W eksperymentalnym wystąpieniu Utwórz projekt SimpleProject. W oknie dialogowym **Nowy projekt** wybierz pozycję **SimpleProject**.

5. Powinno zostać wyświetlone nowe wystąpienie elementu SimpleProject.

    ![Proste nowe wystąpienie projektu](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Nowe wystąpienie mojego projektu](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Utwórz węzeł podrzędny typu projektu
Węzeł podrzędny można dodać do węzła typ projektu w oknie dialogowym **Nowy projekt** . Na przykład dla typu projektu SimpleProject można mieć węzły podrzędne dla aplikacji konsolowych, aplikacji okna, aplikacji sieci Web i tak dalej.

Węzły podrzędne są tworzone przez zmianę pliku projektu i dodanie \<OutputSubPath> elementów podrzędnych do \<ZipProject> elementów. Gdy szablon jest kopiowany podczas kompilacji lub wdrożenia, każdy węzeł podrzędny będzie podfolderem folderu szablonów projektu.

W tej sekcji pokazano, jak utworzyć węzeł podrzędny konsoli dla typu projektu SimpleProject.

1. Zmień nazwę folderu * \\ Templates\Projects\SimpleProject \\ * na * \\ Templates\Projects\ConsoleApp \\ *.

2. W oknie **Właściwości** zaznacz wszystkie pięć plików w folderze * \\ Templates\Projects\ConsoleApp \\ * i upewnij się, że **Akcja kompilacja** jest ustawiona na **ZipProject**.

3. W pliku SimpleProject. vstemplate Dodaj następujący wiersz na końcu \<TemplateData> sekcji tuż przed tagiem zamykającym.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Powoduje to, że szablon aplikacji konsoli pojawia się zarówno w węźle podrzędnym konsoli, jak i w węźle nadrzędnym SimpleProject, który znajduje się na poziomie powyżej węzła podrzędnego.

4. Zapisz plik *SimpleProject. vstemplate* .

5. W pliku *. csproj* Dodaj \<OutputSubPath> do każdego z elementów ZipProject. Zwolnij projekt, tak jak wcześniej, i edytuj plik projektu.

6. Znajdź \<ZipProject> elementy. Do każdego \<ZipProject> elementu, Dodaj \<OutputSubPath> element i nadaj mu konsolę wartości. ZipProject

    ```
    <ZipProject Include="Templates\Projects\ConsoleApp\AssemblyInfo.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\Program.cs">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.myproj">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.vstemplate">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    <ZipProject Include="Templates\Projects\ConsoleApp\SimpleProject.ico">
      <OutputSubPath>Console</OutputSubPath>
    </ZipProject>
    ```

7. Dodaj ten \<PropertyGroup> plik do pliku projektu:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Zapisz plik projektu i ponownie Załaduj projekt.

## <a name="test-the-project-type-child-node"></a>Testowanie węzła podrzędnego typu projektu
Przetestuj zmodyfikowany plik projektu, aby zobaczyć, czy węzeł podrzędny **konsoli** pojawia się w oknie dialogowym **Nowy projekt** .

1. Uruchom narzędzie **resetowania wystąpienia eksperymentalnego Microsoft Visual Studio** .

2. Skompiluj ponownie projekt SimpleProject i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne

3. W oknie dialogowym **Nowy projekt** kliknij węzeł **SimpleProject** . Szablon **aplikacji konsoli** powinien pojawić się w okienku **Szablony** .

4. Rozwiń węzeł **SimpleProject** . Powinien pojawić się węzeł podrzędny **konsoli** . Szablon **aplikacji SimpleProject** nadal pojawia się w okienku **Szablony** .

5. Kliknij przycisk **Anuluj** i Zatrzymaj debugowanie.

    ![Prosty pakiet zbiorczy projektu](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Prosty węzeł konsoli projektu](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Podstawianie parametrów szablonu projektu
- W [przypadku tworzenia podstawowego systemu projektu część 1](../extensibility/creating-a-basic-project-system-part-1.md) pokazała, jak zastąpić `ProjectNode.AddFileFromTemplate` metodę, aby wykonać podstawowy rodzaj podstawiania parametrów szablonu. Ta sekcja uczy się, jak używać bardziej zaawansowanych parametrów szablonu programu Visual Studio.

Podczas tworzenia projektu przy użyciu szablonu programu Visual Studio w oknie dialogowym **Nowy projekt** , parametry szablonu są zastępowane ciągami, aby dostosować projekt. Parametr szablonu jest specjalnym tokenem rozpoczynającym się i kończącym znakiem dolara, na przykład $time $. Poniższe dwa parametry są szczególnie przydatne do włączania dostosowywania w projektach, które są oparte na szablonie:

- $GUID [1-10] $ jest zastępowany przez nowy identyfikator GUID. Można określić maksymalnie 10 unikatowych identyfikatorów GUID, na przykład $guid $1.

- $safeprojectname $ to nazwa podana przez użytkownika w oknie dialogowym **Nowy projekt** , zmodyfikowana w celu usunięcia wszystkich niebezpiecznych znaków i spacji.

  Aby uzyskać pełną listę parametrów szablonu, zobacz [Parametry szablonu](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Aby zastąpić parametry szablonu projektu

1. W pliku *SimpleProjectNode.cs* Usuń `AddFileFromTemplate` metodę.

2. W pliku * \\ Templates\Projects\ConsoleApp\SimpleProject.myproj* Znajdź \<RootNamespace> Właściwość i zmień jej wartość na $safeprojectname $.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. W pliku * \\ Templates\Projects\SimpleProject\Program.cs* Zastąp zawartość pliku następującym kodem:

    ```
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace $safeprojectname$
    {
        [Guid("$guid1$")]
        public class $safeprojectname$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

4. Skompiluj ponownie projekt SimpleProject i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.

5. Utwórz nową aplikację konsolową SimpleProject. (W okienku **typy projektów** wybierz pozycję **SimpleProject**. W obszarze **zainstalowane szablony programu Visual Studio**wybierz pozycję **Aplikacja konsolowa**.

6. W nowo utworzonym projekcie Otwórz *program.cs*. Powinien wyglądać podobnie do poniższego (wartości identyfikatorów GUID w pliku będą się różnić).

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using System.Runtime.InteropServices;    // Guid

    namespace Console_Application1
    {
        [Guid("00000000-0000-0000-00000000-00000000)"]
        public class Console_Application1
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

## <a name="create-a-project-property-page"></a>Utwórz stronę właściwości projektu
Można utworzyć stronę właściwości dla typu projektu, aby użytkownicy mogli wyświetlać i zmieniać właściwości w projektach, które są oparte na szablonie. W tej sekcji pokazano, jak utworzyć stronę właściwości niezależną od konfiguracji. Ta podstawowa Strona właściwości używa siatki właściwości do wyświetlania publicznych właściwości, które można uwidocznić w klasie strony właściwości.

Utwórz klasę strony właściwości z `SettingsPage` klasy bazowej. Siatka właściwości dostarczana przez `SettingsPage` klasę ma świadomość większości typów danych pierwotnych i wie, jak je wyświetlać. Ponadto `SettingsPage` Klasa wie, jak utrwalać wartości właściwości w pliku projektu.

Strona właściwości utworzona w tej sekcji pozwala modyfikować i zapisywać następujące właściwości projektu:

- AssemblyName

- OutputType

- RootNamespace.

1. W pliku *SimpleProjectPackage.cs* Dodaj ten `ProvideObject` atrybut do `SimpleProjectPackage` klasy:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Spowoduje to zarejestrowanie klasy strony właściwości `GeneralPropertyPage` z modelem com.

2. W pliku *SimpleProjectNode.cs* Dodaj te dwie zastąpione metody do `SimpleProjectNode` klasy:

    ```csharp
    protected override Guid[] GetConfigurationIndependentPropertyPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    protected override Guid[] GetPriorityProjectDesignerPages()
    {
        Guid[] result = new Guid[1];
        result[0] = typeof(GeneralPropertyPage).GUID;
        return result;
    }
    ```

    Obie te metody zwracają tablicę identyfikatorów GUID strony właściwości. Identyfikator GUID GeneralPropertyPage jest jedynym elementem w tablicy, dlatego w oknie dialogowym **strony właściwości** zostanie wyświetlona tylko jedna strona.

3. Dodaj plik klasy o nazwie *GeneralPropertyPage.cs* do projektu SimpleProject.

4. Zastąp zawartość tego pliku następującym kodem:

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Project;
    using System.ComponentModel;

    namespace SimpleProject
    {
        [ComVisible(true)]
        [Guid("6BC7046B-B110-40d8-9F23-34263D8D2936")]
        public class GeneralPropertyPage : SettingsPage
        {
            private string assemblyName;
            private OutputType outputType;
            private string defaultNamespace;

            public GeneralPropertyPage()
            {
                this.Name = "General";
            }

            [Category("AssemblyName")]
            [DisplayName("AssemblyName")]
            [Description("The output file holding assembly metadata.")]
            public string AssemblyName
            {
                get { return this.assemblyName; }
            }
            [Category("Application")]
            [DisplayName("OutputType")]
            [Description("The type of application to build.")]
            public OutputType OutputType
            {
                get { return this.outputType; }
                set { this.outputType = value; this.IsDirty = true; }
            }
            [Category("Application")]
            [DisplayName("DefaultNamespace")]
            [Description("Specifies the default namespace for added items.")]
            public string DefaultNamespace
            {
                get { return this.defaultNamespace; }
                set { this.defaultNamespace = value; this.IsDirty = true; }
            }

            protected override void BindProperties()
            {
                this.assemblyName = this.ProjectMgr.GetProjectProperty("AssemblyName", true);
                this.defaultNamespace = this.ProjectMgr.GetProjectProperty("RootNamespace", false);

                string outputType = this.ProjectMgr.GetProjectProperty("OutputType", false);
                this.outputType = (OutputType)Enum.Parse(typeof(OutputType), outputType);
            }

            protected override int ApplyChanges()
            {
                this.ProjectMgr.SetProjectProperty("AssemblyName", this.assemblyName);
                this.ProjectMgr.SetProjectProperty("OutputType", this.outputType.ToString());
                this.ProjectMgr.SetProjectProperty("RootNamespace", this.defaultNamespace);
                this.IsDirty = false;

                return VSConstants.S_OK;
            }
        }
    }
    ```

    `GeneralPropertyPage`Klasa ujawnia trzy właściwości publiczne AssemblyName, OutputType i rootNamespace. Ponieważ AssemblyName nie ma metody Set, jest ona wyświetlana jako właściwość tylko do odczytu. OutputType jest stałą wyliczaną, więc jest wyświetlana jako lista rozwijana.

    `SettingsPage`Klasa bazowa zapewnia `ProjectMgr` trwałe właściwości. `BindProperties`Metoda używa `ProjectMgr` do pobierania utrwalonych wartości właściwości i ustawiania odpowiednich właściwości. `ApplyChanges`Metoda używa `ProjectMgr` do pobierania wartości właściwości i utrwalania ich w pliku projektu. Właściwość Set ustawia `IsDirty` wartość true, aby wskazać, że właściwości muszą być utrwalone. Trwałość występuje podczas zapisywania projektu lub rozwiązania.

5. Skompiluj ponownie rozwiązanie SimpleProject i Rozpocznij debugowanie. Powinno zostać wyświetlone wystąpienie eksperymentalne.

6. W eksperymentalnym wystąpieniu Utwórz nową aplikację SimpleProject.

7. Program Visual Studio wywołuje fabrykę projektu, aby utworzyć projekt przy użyciu szablonu programu Visual Studio. Nowy plik *program.cs* zostanie otwarty w edytorze kodu.

8. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań**, a następnie kliknij polecenie **Właściwości**. Wyświetli się okno dialogowe **Strony właściwości**.

    ![Prosta strona właściwości projektu](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testowanie strony właściwości projektu
Teraz można sprawdzić, czy można modyfikować i zmieniać wartości właściwości.

1. W oknie dialogowym **MyConsoleApplication strony właściwości** Zmień **DefaultNamespace** na moje **aplikacje**.

2. Wybierz właściwość **OutputType** , a następnie wybierz pozycję **Biblioteka klas**.

3. Kliknij przycisk **Zastosuj**, a następnie kliknij przycisk **OK**.

4. Otwórz ponownie okno dialogowe **strony właściwości** i sprawdź, czy zmiany zostały utrwalone.

5. Zamknij wystąpienie eksperymentalne programu Visual Studio.

6. Otwórz ponownie wystąpienie eksperymentalne.

7. Otwórz ponownie okno dialogowe **strony właściwości** i sprawdź, czy zmiany zostały utrwalone.

8. Zamknij wystąpienie eksperymentalne programu Visual Studio.
    ![Zamknij wystąpienie eksperymentalne](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
