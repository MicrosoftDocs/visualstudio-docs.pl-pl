---
title: Tworzenie podstawowego systemu projektów, część 2 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 7823dc949e78cc6d22514a1ba93476fd5f42d076
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739707"
---
# <a name="create-a-basic-project-system-part-2"></a>Tworzenie podstawowego systemu projektów, część 2
Pierwszy instruktaż w tej serii, [Tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md), pokazuje, jak utworzyć podstawowy system projektu. Ten instruktaż opiera się na podstawowym systemie projektu, dodając szablon programu Visual Studio, stronę właściwości i inne funkcje. Przed rozpoczęciem tego przewodnika należy wykonać pierwszy instruktaż.

W tym instruktażu opisano, jak utworzyć typ projektu z rozszerzeniem nazwy pliku projektu *.myproj*. Aby ukończyć instruktaże, nie trzeba tworzyć własnego języka, ponieważ instruktaż zapożycza się z istniejącego systemu projektu języka Visual C#.

W tym przewodniku uczy się, jak wykonać następujące zadania:

- Tworzenie szablonu programu Visual Studio.

- Wdrażanie szablonu programu Visual Studio.

- Tworzenie węzła podrzędnego typu projektu w oknie dialogowym **Nowy projekt.**

- Włącz podstawienie parametrów w szablonie programu Visual Studio.

- Tworzenie strony właściwości projektu.

> [!NOTE]
> Kroki opisane w tym instruktażu są oparte na projekcie języka C#. Jednak z wyjątkiem specyfiki, takich jak rozszerzenia nazw plików i kod, można użyć tych samych kroków dla projektu języka Visual Basic.

## <a name="create-a-visual-studio-template"></a>Tworzenie szablonu programu Visual Studio
- [Utwórz podstawowy system projektu, część 1 pokazuje,](../extensibility/creating-a-basic-project-system-part-1.md) jak utworzyć podstawowy szablon projektu i dodać go do systemu projektu. Pokazano również, jak zarejestrować ten szablon <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> w programie Visual Studio przy użyciu atrybutu, który zapisuje pełną ścieżkę * \\folderu Templates\Projects\SimpleProject\\ * w rejestrze systemowym.

Korzystając z szablonu programu Visual Studio ( plik*vstemplate* zamiast podstawowego szablonu projektu, można kontrolować sposób, w jaki szablon pojawia się w oknie dialogowym **Nowy projekt** i jak są podstawione parametry szablonu. Plik *vstemplate* to plik XML, który opisuje sposób uwzględniania plików źródłowych podczas tworzenia projektu przy użyciu szablonu systemu projektu. Sam system projektu jest zbudowany przez zbieranie pliku *vstemplate* i plików źródłowych w pliku *zip* i wdrażany przez skopiowanie pliku *zip* do lokalizacji znanej programowi Visual Studio. Ten proces jest wyjaśniony bardziej szczegółowo w dalszej części tego przewodnika.

1. W [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]programie otwórz rozwiązanie SimpleProject utworzone przez następujące [tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md).

2. W pliku *SimpleProjectPackage.cs* znajdź atrybut ProvideProjectFactory. Zastąp drugi parametr (nazwę projektu) wartością null, a czwarty parametr (ścieżkę do folderu szablonu projektu) na ". \\\NullPath", w następujący sposób.

    ```
    [ProvideProjectFactory(typeof(SimpleProjectFactory), null,
        "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
        ".\\NullPath",
    LanguageVsTemplate = "SimpleProject")]
    ```

3. Dodaj plik XML o nazwie *SimpleProject.vstemplate* do folderu * \\\\ Templates\Projects\SimpleProject.*

4. Zastempluj zawartość *SimpleProject.vstemplate* następującym kodem.

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

5. W oknie **Właściwości** zaznacz wszystkie pięć plików w folderze * \\Szablony\Projekty\Prosty projekt\\ * i ustaw **akcję kompilacji** na **ZipProject**.

    ![Prosty folder projektu](../extensibility/media/simpproj2.png "SimpProj2 (właśc.")

    Sekcja \<TemplateData> określa lokalizację i wygląd typu projektu SimpleProject w oknie dialogowym **Nowy projekt** w następujący sposób:

- Nazwa \<> element nazwy szablon projektu do aplikacji SimpleProject.

- Element \<Opis> zawiera opis wyświetlany w oknie dialogowym **Nowy projekt** po wybraniu szablonu projektu.

- \<Element Icon> określa ikonę, która pojawia się wraz z typem projektu SimpleProject.

- Element \<> ProjectType nazywa typ projektu w oknie dialogowym **Nowy projekt.** Ta nazwa zastępuje parametr nazwy projektu atrybutu ProvideProjectFactory.

  > [!NOTE]
  > Element \<> ProjectType musi być `LanguageVsTemplate` zgodny `ProvideProjectFactory` z argumentem atrybutu w pliku SimpleProjectPackage.cs.

  Sekcja \<TemplateContent> opisuje te pliki, które są generowane podczas tworzenia nowego projektu:

- *SimpleProject.myproj*

- *Program.cs*

- *AssemblyInfo.cs*

  Wszystkie trzy `ReplaceParameters` pliki zostały ustawione na true, co umożliwia zastępowanie parametrów. Plik *Program.cs* został `OpenInEditor` ustawiony na true, co powoduje, że plik ma być otwarty w edytorze kodu podczas tworzenia projektu.

  Aby uzyskać więcej informacji na temat elementów w schemacie szablonu programu Visual Studio, zobacz [odwołanie do schematu szablonu programu Visual Studio](../extensibility/visual-studio-template-schema-reference.md).

> [!NOTE]
> Jeśli projekt ma więcej niż jeden szablon programu Visual Studio, każdy szablon znajduje się w osobnym folderze. Każdy plik w tym folderze musi mieć ustawioną **akcję kompilacji** na **ZipProject**.

## <a name="adding-a-minimal-vsct-file"></a>Dodawanie minimalnego pliku vsct
 Program Visual Studio musi być uruchomiony w trybie instalacji, aby rozpoznać nowy lub zmodyfikowany szablon programu Visual Studio. Tryb instalacji wymaga obecności pliku *vsct.* W związku z tym należy dodać minimalny plik *vsct* do projektu.

1. Dodaj plik XML o nazwie *SimpleProject.vsct* do projektu SimpleProject.

2. Zastąp zawartość pliku *SimpleProject.vsct* następującym kodem.

    ```
    <?xml version="1.0" encoding="utf-8" ?>
    <CommandTable
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">
    </CommandTable>
    ```

3. Ustaw **akcję kompilacji** tego pliku na **VSCTCompile**. Można to zrobić tylko w pliku *csproj,* a nie w oknie **Właściwości.** Upewnij się, że **akcja kompilacji** tego pliku jest ustawiona na **Brak** w tym momencie.

    1. Kliknij prawym przyciskiem myszy węzeł SimpleProject, a następnie kliknij polecenie **Edytuj plik SimpleProject.csproj**.

    2. W pliku *csproj* znajdź element *SimpleProject.vsct.*

        ```
        <None Include="SimpleProject.vsct" />
        ```

    3. Zmień akcję kompilacji na **VSCTCompile**.

        ```
        <VSCTCompile Include="SimpleProject.vsct" />
        ```

    4. pliku projektu i zamknij edytor.

    5. Zapisz węzeł SimpleProject, a następnie w **Eksploratorze rozwiązań** kliknij pozycję **Załaduj ponownie projekt**.

## <a name="examine-the-visual-studio-template-build-steps"></a>Sprawdzanie kroków kompilacji szablonu programu Visual Studio
 System kompilacji projektu VSPackage zazwyczaj uruchamia program Visual Studio w trybie instalacji po zmianie pliku *vstemplate* lub przebudowie projektu zawierającego plik *vstemplate.* Można śledzić, ustawiając poziom szczegółowości MSBuild na normalny lub wyższy.

1. W menu **Tools** (Narzędzia) kliknij pozycję **Options** (Opcje).

2. Rozwiń węzeł **Projekty i rozwiązania,** a następnie wybierz pozycję **Buduj i uruchamiaj**.

3. Ustaw **szczegółowość wyjściową kompilacji kompilacji projektu MSBuild** na **Normalną**. Kliknij przycisk **OK**.

4. Odbuduj projekt SimpleProject.

    Krok kompilacji, aby utworzyć plik projektu *zip* powinien przypominać poniższy przykład.

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
Szablony programu Visual Studio nie zawierają informacji o ścieżce. W związku z tym plik *.zip* szablonu musi być wdrożony w lokalizacji, która jest znana programowi Visual Studio. Lokalizacja folderu ProjectTemplates jest zazwyczaj *<%LOCALAPPDATA%>\Microsoft\VisualStudio\14.0Exp\ProjectTemplates*.

Aby wdrożyć fabrykę projektu, program instalacyjny musi mieć uprawnienia administratora. Wdraża szablony w węźle instalacji programu Visual Studio: *...\Microsoft Visual Studio 14.0\Common7\IDE\ProjectTemplates*.

## <a name="test-a-visual-studio-template"></a>Testowanie szablonu programu Visual Studio
Przetestuj fabrykę projektu, aby zobaczyć, czy tworzy hierarchię projektu przy użyciu szablonu programu Visual Studio.

1. Resetowanie eksperymentalnego wystąpienia SDK programu Visual Studio.

    W [!INCLUDE[win7](../debugger/includes/win7_md.md)]: W menu **Start** znajdź folder **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools,** a następnie wybierz polecenie **Resetuj wystąpienie eksperymentalne programu Microsoft Visual Studio**.

    W nowszych wersjach systemu Windows: Na ekranie **startowym** wpisz **Resetuj wersję programu Microsoft Visual Studio \<> wystąpienie eksperymentalne**.

2. Zostanie wyświetlenie okna wiersza polecenia. Gdy zobaczysz słowa **Naciśnij dowolny klawisz, aby kontynuować,** kliknij przycisk **ENTER**. Po zamknięciu okna otwórz program Visual Studio.

3. Odbuduj projekt SimpleProject i rozpocznij debugowanie. Pojawi się eksperymentalne wystąpienie.

4. W wystąpieniu eksperymentalnym utwórz projekt SimpleProject. W oknie dialogowym **Nowy projekt** wybierz pozycję **SimpleProject**.

5. Powinien zostać wyświetlony nowe wystąpienie SimpleProject.

    ![Proste nowe wystąpienie projektu](../extensibility/media/simpproj2_newproj.png "SimpProj2_NewProj")

    ![Moje nowe wystąpienie projektu](../extensibility/media/simpproj2_myproj.png "SimpProj2_MyProj")

## <a name="create-a-project-type-child-node"></a>Tworzenie węzła podrzędnego typu projektu
Węzeł podrzędny można dodać do węzła typu projektu w oknie dialogowym **Nowy projekt.** Na przykład dla typu projektu SimpleProject może mieć węzły podrzędne dla aplikacji konsoli, aplikacji okiennych, aplikacji sieci web i tak dalej.

Węzły podrzędne są tworzone przez zmianę \<pliku projektu i dodanie OutputSubPath> elementy podrzędne do \<elementów zipproject>. Gdy szablon jest kopiowany podczas kompilacji lub wdrażania, każdy węzeł podrzędny staje się podfolderem folderu szablonów projektu.

W tej sekcji pokazano, jak utworzyć węzeł podrzędny konsoli dla typu projektu SimpleProject.

1. Zmień nazwę folderu * \\\\ Templates\Projects\SimpleProject* na * \\Templates\Projects\ConsoleApp\\*.

2. W oknie **Właściwości** zaznacz wszystkie pięć plików w folderze * \\\\ Templates\Projects\ConsoleApp* i upewnij się, że **akcja kompilacji** jest ustawiona na **ZipProject**.

3. W pliku SimpleProject.vstemplate dodaj następujący wiersz na \<końcu sekcji TemplateData> tuż przed tagiem zamykającym.

    ```
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>
    ```

    Powoduje to, że szablon aplikacji konsoli pojawiają się zarówno w węźle podrzędnym konsoli, jak i w węźle nadrzędnym SimpleProject, który jest o jeden poziom powyżej węzła podrzędnego.

4. Zapisz plik *SimpleProject.vstemplate.*

5. W pliku *csproj* dodaj \<> OutputSubPath do każdego z elementów ZipProject. Zwolnij projekt, tak jak poprzednio, i edytuj plik projektu.

6. Znajdź \<elementy> ZipProject. Do \<każdego elementu> ZipProject dodaj \<element> OutputSubPath i nadaj mu wartość Konsoli. The ZipProject

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

7. Dodaj \<tę> PropertyGroup do pliku projektu:

    ```
    <PropertyGroup>
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>
    </PropertyGroup>
    ```

8. Zapisz plik projektu i załaduj ponownie projekt.

## <a name="test-the-project-type-child-node"></a>Testowanie węzła podrzędnego typu projektu
Przetestuj zmodyfikowany plik projektu, aby sprawdzić, czy węzeł **podrzędny konsoli** jest wyświetlany w oknie dialogowym **Nowy projekt.**

1. Uruchom narzędzie **Resetowanie wystąpienia eksperymentalnego programu Microsoft Visual Studio.**

2. Odbuduj projekt SimpleProject i rozpocznij debugowanie. Instancja eksperymentalna powinna

3. W oknie dialogowym **Nowy projekt** kliknij węzeł **SimpleProject.** Szablon **aplikacji konsoli** powinien pojawić się w okienku **Szablony.**

4. Rozwiń węzeł **SimpleProject.** Powinien pojawić się węzeł podrzędny **konsoli.** Szablon **aplikacji SimpleProject** nadal pojawia się w okienku **Szablony.**

5. Kliknij **przycisk Anuluj** i zatrzymaj debugowanie.

    ![Prosty zestawienie projektów](../extensibility/media/simpproj2_rollup.png "SimpProj2_Rollup")

    ![Prosty węzeł konsoli projektu](../extensibility/media/simpproj2_subfolder.png "SimpProj2_Subfolder")

## <a name="substitute-project-template-parameters"></a>Zastępowanie parametrów szablonu projektu
- [Tworząc podstawowy system projektu, część 1 pokazała,](../extensibility/creating-a-basic-project-system-part-1.md) jak `ProjectNode.AddFileFromTemplate` zastąpić metodę zastępowania parametrów podstawowych. W tej sekcji opisano, jak używać bardziej zaawansowanych parametrów szablonu programu Visual Studio.

Podczas tworzenia projektu przy użyciu szablonu programu Visual Studio w oknie dialogowym **Nowy projekt** parametry szablonu są zastępowane ciągami w celu dostosowania projektu. Parametr szablonu to specjalny token, który rozpoczyna się i kończy znakiem dolara, na przykład $time$. Następujące dwa parametry są szczególnie przydatne do włączania dostosowywania w projektach, które są oparte na szablonie:

- $GUID[1-10]$ zostaje zastąpiony przez nowego Guida. Można określić maksymalnie 10 unikatowych identyfikatorów GUID, na przykład $guid1$.

- $safeprojectname$ to nazwa podana przez użytkownika w oknie dialogowym **Nowy projekt,** zmodyfikowana w celu usunięcia wszystkich niebezpiecznych znaków i spacji.

  Aby uzyskać pełną listę parametrów szablonu, zobacz [Parametry szablonu](../ide/template-parameters.md).

### <a name="to-substitute-project-template-parameters"></a>Aby zastąpić parametry szablonu projektu

1. W pliku *SimpleProjectNode.cs* usuń `AddFileFromTemplate` metodę.

2. W pliku * \\Templates\Projects\ConsoleApp\SimpleProject.myproj* zlokalizuj właściwość \<> rootnamespace i zmień jej wartość na $safeprojectname$.

    ```
    <RootNamespace>$safeprojectname$</RootNamespace>
    ```

3. W pliku * \\Templates\Projects\SimpleProject\Program.cs* zastąp zawartość pliku następującym kodem:

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

4. Odbuduj projekt SimpleProject i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

5. Utwórz nową aplikację SimpleProject Console. (W **okienku Typy projektu** wybierz pozycję **SimpleProject**. W obszarze **Zainstalowane szablony programu Visual Studio**wybierz pozycję Aplikacja **konsoli.)**

6. W nowo utworzonym projekcie otwórz *Program.cs*. Powinien wyglądać mniej więcej tak, jak poniżej (wartości identyfikatorów GUID w pliku będą się różnić.):

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

## <a name="create-a-project-property-page"></a>Tworzenie strony właściwości projektu
Można utworzyć stronę właściwości dla typu projektu, dzięki czemu użytkownicy mogą wyświetlać i zmieniać właściwości w projektach opartych na szablonie. W tej sekcji pokazano, jak utworzyć stronę właściwości niezależnej od konfiguracji. Ta strona właściwości podstawowej używa siatki właściwości do wyświetlania właściwości publicznych, które można udostępnić w klasie strony właściwości.

Wywodź klasę strony `SettingsPage` właściwości z klasy podstawowej. Siatka właściwości dostarczone `SettingsPage` przez klasę jest świadomy większości typów danych pierwotnych i wie, jak je wyświetlić. Ponadto `SettingsPage` klasa wie, jak utrwalać wartości właściwości do pliku projektu.

Strona właściwości utworzona w tej sekcji umożliwia zmianę i zapisanie tych właściwości projektu:

- Assemblyname

- Outputtype

- Rootnamespace.

1. W pliku *SimpleProjectPackage.cs* dodaj ten `ProvideObject` atrybut do `SimpleProjectPackage` klasy:

    ```
    [ProvideObject(typeof(GeneralPropertyPage))]
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

    Spowoduje to zarejestrowanie `GeneralPropertyPage` klasy strony właściwości w com.

2. W pliku *SimpleProjectNode.cs* dodaj do `SimpleProjectNode` klasy dwie zastąpione metody:

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

    Obie te metody zwracają tablicę identyfikatorów GUID strony właściwości. Identyfikator GUID GeneralPropertyPage jest jedynym elementem w tablicy, więc w oknie dialogowym **Strony właściwości** zostanie wyświetlona tylko jedna strona.

3. Dodaj plik klasy o nazwie *GeneralPropertyPage.cs* do projektu SimpleProject.

4. Zastąp zawartość tego pliku przy użyciu następującego kodu:

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

    Klasa `GeneralPropertyPage` udostępnia trzy właściwości publiczne AssemblyName, OutputType i RootNamespace. Ponieważ AssemblyName nie ma metody zestawu, jest wyświetlany jako właściwość tylko do odczytu. OutputType jest stałą wyliczoną, więc jest wyświetlana jako lista rozwijana.

    Klasa `SettingsPage` podstawowa `ProjectMgr` zapewnia do utrwalania właściwości. Metoda `BindProperties` używa `ProjectMgr` do pobierania wartości właściwości utrwalone i ustawić odpowiednie właściwości. Metoda `ApplyChanges` `ProjectMgr` używa, aby uzyskać wartości właściwości i utrwalić je do pliku projektu. Metoda zestawu właściwości `IsDirty` ustawia true, aby wskazać, że właściwości muszą być utrwalone. Trwałość występuje podczas zapisywania projektu lub rozwiązania.

5. Odbuduj rozwiązanie SimpleProject i rozpocznij debugowanie. Powinno pojawić się wystąpienie eksperymentalne.

6. W wystąpieniu eksperymentalnym utwórz nową aplikację SimpleProject.

7. Visual Studio wywołuje fabryki projektu, aby utworzyć projekt przy użyciu szablonu programu Visual Studio. Nowy plik *Program.cs* zostanie otwarty w edytorze kodu.

8. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań,** a następnie kliknij polecenie **Właściwości**. Wyświetli się okno dialogowe **Strony właściwości**.

    ![Prosta strona właściwości projektu](../extensibility/media/simpproj2_proppage.png "SimpProj2_PropPage")

## <a name="test-the-project-property-page"></a>Testowanie strony właściwości projektu
Teraz można sprawdzić, czy można modyfikować i zmieniać wartości właściwości.

1. W oknie dialogowym **Strony właściwości aplikacji MyConsoleapplication** zmień **obszar DefaultNamespace** na **MyApplication**.

2. Wybierz właściwość **OutputType,** a następnie wybierz polecenie **Biblioteka klas**.

3. Kliknij przycisk **Zastosuj**, a następnie kliknij przycisk **OK**.

4. Otwórz ponownie okno dialogowe **Strony właściwości** i sprawdź, czy zmiany zostały utrwalone.

5. Zamknij eksperymentalne wystąpienie programu Visual Studio.

6. Otwórz ponownie eksperymentalne wystąpienie.

7. Otwórz ponownie okno dialogowe **Strony właściwości** i sprawdź, czy zmiany zostały utrwalone.

8. Zamknij eksperymentalne wystąpienie programu Visual Studio.
    ![Zamykanie wystąpienia eksperymentalnego](../extensibility/media/simpproj2_proppage2.png "SimpProj2_PropPage2")
