---
title: Tworzenie systemu podstawowego projektu, część 1 | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9fd695c5a33ea8ea7bb9895d34995abd37db7019
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843964"
---
# <a name="create-a-basic-project-system-part-1"></a>Tworzenie systemu podstawowego projektu, część 1
W programie Visual Studio projekty są kontenerami, używanych przez deweloperów do organizowania plików kodu źródłowego i inne zasoby. Projekty są traktowane jako elementy podrzędne rozwiązań w **Eksploratora rozwiązań**. Projekty umożliwiają organizowanie, tworzenie, debugowanie i wdrażanie kodu źródłowego i utworzyć odwołania do usług sieci Web, baz danych i innych zasobów.

 Projekty są zdefiniowane w plikach projektu, na przykład *.csproj* plik projektu języka Visual C#. Można utworzyć swój własny typ projektu, który ma własne rozszerzenia nazw plików projektu. Aby uzyskać więcej informacji na temat typów projektów, zobacz [typów projektów](../extensibility/internals/project-types.md).

> [!NOTE]
>  Jeśli zachodzi potrzeba Rozszerzanie programu Visual Studio przy użyciu typu niestandardowego projektu, zdecydowanie zalecamy korzystanie z [systemu projektu programu Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS) który ma kilka zalet w stosunku do tworzenia projektu systemu od zera:
>
> - Łatwiejsze dołączanie.  Nawet systemu podstawowego projektu wymaga dziesiątki tysięcy wierszy kodu.  Wykorzystując VSPS zmniejsza koszty dołączania do kilku kliknięć, zanim można przystąpić do go dostosować do swoich potrzeb.
> - Łatwiejsze konserwacji.  Dzięki wykorzystaniu VSPS, wystarczy do obsługi własnych scenariuszy.  My zajmujemy utrzymania wszystkich infrastruktury systemu projektu.
>
>   Jeśli potrzebujesz do wersji docelowej programu Visual Studio starszych niż program Visual Studio 2013, nie można wykorzystać VSPS w rozszerzeniu Visual Studio.  Jeśli tak jest rzeczywiście, ten przewodnik jest dobrym miejscem, aby rozpocząć pracę.

 W tym instruktażu dowiesz się, jak utworzyć typ projektu, który ma rozszerzenie nazwy pliku projektu *.myproj*. W tym przewodniku pożycza z istniejącego systemu projektów języka Visual C#.

> [!NOTE]
>  Aby uzyskać więcej przykładów projektów rozszerzeń, zobacz [przykłady VSSDK](https://aka.ms/vs2015sdksamples).

 Ten przewodnik omawia sposób wykonywania tych zadań:

-   Tworzenie typu podstawowego projektu.

-   Utwórz szablon podstawowy projekt.

-   Szablon projektu należy zarejestrować w usłudze Visual Studio.

-   Utwórz wystąpienie projektu, otwierając **nowy projekt** okno dialogowe, a następnie za pomocą szablonu.

-   Tworzenie fabryki projektu w systemie projektu.

-   Utwórz węzeł projektu w systemie projektu.

-   Dodaj niestandardowe ikony system projektu.

-   Implementuje podstawowy szablon Podstawienie parametru.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalacji programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Należy również pobrać kod źródłowy [zarządzanego środowiska pakietu dla projektów](https://github.com/tunnelvisionlabs/MPFProj10). Wyodrębnij plik do lokalizacji, który jest dostępny do rozwiązania, które chcesz utworzyć.

## <a name="create-a-basic-project-type"></a>Tworzenie typu podstawowego projektu
 Utwórz projekt VSIX języka C# o nazwie **SimpleProject**. (**Pliku** > **nowe** > **projektu** i następnie **Visual C#**  >   **Rozszerzalność** > **projekt VSIX**). Dodawanie szablonu elementu projektu pakietu Visual Studio (na **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł projektu i wybierz **Dodaj** > **nowy element**, a następnie przejdź do **Rozszerzalności** > **pakietu Visual Studio**). Nadaj plikowi nazwę *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Tworzenie podstawowego projektu szablonu
 Teraz można zmodyfikować tego podstawowego pakietu VSPackage wdrożyć nowy *.myproj* typ projektu. Aby utworzyć projekt, który jest oparty na *.myproj* typu projektu programu Visual Studio musi wiedzieć, które pliki, zasobów i odwołania do dodania do nowego projektu. Aby podać te informacje, należy umieścić pliki projektu w folderze szablonu projektu. Gdy użytkownik używa *.myproj* projekt do tworzenia projektu, pliki są kopiowane do nowego projektu.

### <a name="to-create-a-basic-project-template"></a>Aby utworzyć szablon podstawowy projekt

1. Dodaj trzy foldery w projekcie, jeden pod innymi: *Templates\Projects\SimpleProject*. (W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **SimpleProject** węzła projektu, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy Folder**. Nazwa folderu *szablony*. W *szablony* folderu, Dodaj folder o nazwie *projektów*. W *projektów* folderu, Dodaj folder o nazwie *SimpleProject*.)

2. W *Templates\Projects\SimpleProject* folderu, Dodaj plik obrazu mapy bitowej jako ikony o nazwie *SimpleProject.ico*. Po kliknięciu **Dodaj**, zostanie otwarty Edytor ikon.

3. Ikona szczególne. Ta ikona pojawi się w **nowy projekt** okno dialogowe w dalszej części przewodnika.

    ![Ikona prostego projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Ikonę Zapisz i zamknij Edytor ikon.

5. W *Templates\Projects\SimpleProject* folderu, Dodaj **klasy** element o nazwie *Program.cs*.

6. Zastąp istniejący kod z następującymi wierszami.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Text;

   namespace $nameSpace$
   {
       public class $className$
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

   > [!IMPORTANT]
   >  Nie jest ostatnim formie *Program.cs* kod; zastąpienia parametrów, zostaną omówione w dalszej części. Może zostać wyświetlony błędy kompilacji, ale tak długo, jak plik **BuildAction** jest **zawartości**, powinno być możliwe skompilować i uruchomić projekt w zwykły sposób.

7. Zapisz plik.

8. Kopiuj *AssemblyInfo.cs* plik wchodzącej w skład *właściwości* folder *Projects\SimpleProject* folderu.

9. W *Projects\SimpleProject* folderu Dodaj plik XML o nazwie *SimpleProject.myproj*.

   > [!NOTE]
   >  Rozszerzenie nazwy pliku dla wszystkich projektów tego typu jest *.myproj*. Jeśli chcesz ją zmienić, należy zmienić go wszędzie tam, gdzie jest wymieniony w instruktażu.

10. Zastąp istniejącą zawartość z następującymi wierszami.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
      <PropertyGroup>
        <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>
        <SchemaVersion>2.0</SchemaVersion>
        <ProjectGuid></ProjectGuid>
        <OutputType>Exe</OutputType>
        <RootNamespace>MyRootNamespace</RootNamespace>
        <AssemblyName>MyAssemblyName</AssemblyName>
        <EnableUnmanagedDebugging>false</EnableUnmanagedDebugging>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">
        <DebugSymbols>true</DebugSymbols>
        <OutputPath>bin\Debug\</OutputPath>
      </PropertyGroup>
      <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
        <DebugSymbols>false</DebugSymbols>
        <OutputPath>bin\Release\</OutputPath>
      </PropertyGroup>
      <ItemGroup>
        <Reference Include="mscorlib" />
        <Reference Include="System" />
        <Reference Include="System.Data" />
        <Reference Include="System.Xml" />
      </ItemGroup>
      <ItemGroup>
        <Compile Include="AssemblyInfo.cs">
          <SubType>Code</SubType>
        </Compile>
        <Compile Include="Program.cs">
          <SubType>Code</SubType>
        </Compile>
      </ItemGroup>
      <Import Project="$(MSBuildBinPath)\Microsoft.CSharp.targets" />
    </Project>
    ```

11. Zapisz plik.

12. W **właściwości** oknie **Build Action** z *AssemblyInfo.cs*, *Program.cs*, *SimpleProject.ico* , i *SimpleProject.myproj* do **zawartości**i ustaw ich **Include w VSIX** właściwości **True**.

    Ten szablon projektu w tym artykule opisano podstawowe Visual C# projekt, który ma zarówno konfigurację debugowania, jak i konfiguracji wydania. Projekt zawiera dwa pliki źródłowe, *AssemblyInfo.cs* i *Program.cs*oraz kilka odwołań do zestawów. Gdy projekt jest tworzony na podstawie tego szablonu, wartość ProjectGuid jest automatycznie zastępowany przez nowy identyfikator GUID.

    W **Eksploratora rozwiązań**, rozwiniętym okienku **szablony** folderu powinna wyglądać następująco:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Utwórz fabrykę podstawowego projektu
 Musisz poinformować lokalizacji folderu szablonu projektu programu Visual Studio. Aby to zrobić, należy dodać atrybut do klasy pakietu VSPackage, która implementuje fabryka projektu, dzięki czemu lokalizacja szablonu są zapisywane w rejestrze systemu podczas tworzenia pakietu VSPackage. Rozpocznij od utworzenia fabryki podstawowego projektu, która jest identyfikowana przez fabrykę projektu identyfikatora GUID. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutu, aby połączyć fabryki projektu, aby `SimpleProjectPackage` klasy.

### <a name="to-create-a-basic-project-factory"></a>Umożliwia ono utworzenie fabryki podstawowego projektu

1. Tworzenie identyfikatorów GUID fabryki projekt (na **narzędzia** menu, kliknij przycisk **Utwórz GUID**), lub użyj w poniższym przykładzie. Dodaj identyfikatory GUID do `SimpleProjectPackage` klasy obok sekcji z już zdefiniowanym `PackageGuidString`. Identyfikatory GUID musi być zarówno w formie GUID, jak i w postaci ciągu. Po modyfikacji kod powinien wyglądać następująco.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Dodaj klasę do góry *SimpleProject* folder o nazwie *SimpleProjectFactory.cs*.

3. Dodaj następujące instrukcje using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Dodaj atrybut GUID, aby `SimpleProjectFactory` klasy. Wartość atrybutu jest nowa fabryka projektu identyfikatora GUID.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Teraz możesz zarejestrować szablon projektu.

### <a name="to-register-the-project-template"></a>Aby zarejestrować szablon projektu

1. W *SimpleProjectPackage.cs*, Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutu `SimpleProjectPackage` klasy w następujący sposób.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Ponownie skompiluj rozwiązanie, a następnie sprawdź, czy opiera się bez błędów.

    Ponowne tworzenie rejestruje szablonu projektu.

   Parametry `defaultProjectExtension` i `possibleProjectExtensions` są ustawione na rozszerzenia nazw plików projektu (*.myproj*). `projectTemplatesDirectory` Parametr ma wartość względną ścieżkę *szablony* folderu. Podczas kompilacji ta ścieżka zostanie przekonwertowane na pełnej kompilacji i dodany do rejestru, aby zarejestrować system projektu.

## <a name="test-the-template-registration"></a>Test rejestracji szablonu
 Szablon rejestracji informuje program Visual Studio lokalizacji folderu szablonu projektu tak, aby program Visual Studio można wyświetlić nazwę szablonu i ikony w **nowy projekt** okno dialogowe.

### <a name="to-test-the-template-registration"></a>Aby przetestować Rejestracja szablonu

1. Naciśnij klawisz **F5** można rozpocząć debugowania doświadczalne wystąpienie programu Visual Studio.

2. W doświadczalnym wystąpieniu Utwórz nowy projekt typu nowo utworzonego projektu. W **nowy projekt** okno dialogowe powinna zostać wyświetlona **SimpleProject** w obszarze **zainstalowane szablony**.

   Masz teraz fabryka projektu, który jest zarejestrowany. Jednak nie można jeszcze utworzyć projekt. Pakiet projektu i projektu fabryki współpracują ze sobą, aby utworzyć i zainicjować projektu.

## <a name="add-the-managed-package-framework-code"></a>Dodaj kod środowiska pakietu zarządzanego
 Implementuje połączenie między pakietu z projektem i fabryka projektu.

-   Zaimportuj pliki kodu źródłowego dla środowiska pakietu zarządzanego.

    1.  Cofnij ładowanie projektu SimpleProject (w **Eksploratora rozwiązań**, wybierz węzeł projektu i w menu kontekstowym kliknij **Zwolnij projekt**.), a następnie otwórz plik projektu w edytorze XML.

    2.  Dodaj poniższe bloki do pliku projektu (tuż powyżej \<Import > bloków). Ustaw `ProjectBasePath` do lokalizacji *ProjectBase.files* pliku w kodzie środowiska pakietu zarządzanego został pobrany. Być może będzie trzeba dodać ukośnik odwrotny na nazwę ścieżki. Jeśli tego nie zrobisz, projekt może się nie powieść można znaleźć środowiska pakietu zarządzanego kodu źródłowego.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        >  Nie zapomnij ukośnik odwrotny na końcu ścieżki.

    3.  Ponownie Załaduj projekt.

    4.  Dodaj odwołania do następujących zestawów:

        -   `Microsoft.VisualStudio.Designer.Interfaces` (w  *\<VSSDK instalacji > \VisualStudioIntegration\Common\Assemblies\v2.0*)

        -   `WindowsBase`

        -   `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Aby zainicjować fabryka projektu

1.  W *SimpleProjectPackage.cs* plików, Dodaj następujący kod `using` instrukcji.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2.  Pochodzi `SimpleProjectPackage` klasy z `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3.  Zarejestrować fabryki projektu. Dodaj następujący wiersz do `SimpleProjectPackage.Initialize` metody tuż za `base.Initialize`.

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4.  Implementuje właściwość abstrakcyjną `ProductUserContext`:

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5.  W *SimpleProjectFactory.cs*, Dodaj następujący kod `using` instrukcji znajdującej się po istniejącej `using` instrukcji.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6.  Pochodzi `SimpleProjectFactory` klasy z `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7.  Dodaj następującą metodę fikcyjnego do `SimpleProjectFactory` klasy. Ta metoda będzie implementowany w dalszej części tego tematu.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8.  Dodaj następujące pola i Konstruktor `SimpleProjectFactory` klasy. To `SimpleProjectPackage` odwołanie jest buforowany w pole prywatne, dzięki czemu mogą służyć podczas ustawiania witryna dostawcy usług.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Ponownie skompiluj rozwiązanie, a następnie sprawdź, czy opiera się bez błędów.

## <a name="test-the-project-factory-implementation"></a>Wdrożenie fabryki projekt testu
 Sprawdź, czy wywoływany jest konstruktor implementacji fabryka projektu.

### <a name="to-test-the-project-factory-implementation"></a>Aby przetestować wdrożenie fabryki projektu

1.  W *SimpleProjectFactory.cs* plików, ustaw punkt przerwania na następujący wiersz w `SimpleProjectFactory` konstruktora.

    ```csharp
    this.package = package;
    ```

2.  Naciśnij klawisz **F5** można uruchomić doświadczalne wystąpienie programu Visual Studio.

3.  W doświadczalnym wystąpieniu Uruchom utworzyć nowy projekt. W **nowy projekt** okno dialogowe, wybierz opcję **SimpleProject** typ projektu, a następnie kliknij przycisk **OK**. Zatrzymuje wykonywanie w punkcie przerwania.

4.  Wyczyść punkt przerwania i zatrzymać debugowanie. Ponieważ nie utworzono jeszcze węzła projektu, kod tworzenia projektu nadal zgłasza wyjątków.

## <a name="extend-the-projectnode-class"></a>Rozszerzenie klasy
 Teraz można zaimplementować `SimpleProjectNode` klasy, która jest pochodną `ProjectNode` klasy. `ProjectNode` Klasy bazowej obsługuje następujące zadania tworzenia projektu:

- Kopiuje plik szablonu projektu *SimpleProject.myproj*, do nowego folderu projektu. Kopia jest zmieniana zgodnie z nazwą wprowadzoną w **nowy projekt** okno dialogowe. `ProjectGuid` Wartość właściwości jest zastępowana przez nowy identyfikator GUID.

- Przechodzi przez elementy programu MSBuild w pliku szablonu projektu *SimpleProject.myproj*, a szuka `Compile` elementów. Dla każdego `Compile` pliku docelowego, kopiuje plik do nowego folderu projektu.

  Pochodnej `SimpleProjectNode` klasa obsługuje następujące zadania:

- Włącza ikony dla projektu i pliku węzłów w **Eksploratora rozwiązań** ma zostać utworzona lub wybrana.

- Umożliwia podstawieniach parametrów szablonu projektu dodatkowe należy określić.

### <a name="to-extend-the-projectnode-class"></a>Aby rozszerzyć klasę

1. Dodaj klasę o nazwie `SimpleProjectNode.cs`.

2. Zastąp istniejący kod następującym kodem.

   ```csharp
   using System;
   using System.Collections.Generic;
   using Microsoft.VisualStudio.Project;

   namespace SimpleProject
   {
       public class SimpleProjectNode : ProjectNode
       {
           private SimpleProjectPackage package;

           public SimpleProjectNode(SimpleProjectPackage package)
           {
               this.package = package;
           }
           public override Guid ProjectGuid
           {
               get { return SimpleProjectPackage.guidSimpleProjectFactory; }
           }
           public override string ProjectType
           {
               get { return "SimpleProjectType"; }
           }

           public override void AddFileFromTemplate(
               string source, string target)
           {
               this.FileTemplateProcessor.UntokenFile(source, target);
               this.FileTemplateProcessor.Reset();
           }
       }
   }
   ```

   To `SimpleProjectNode` Implementacja klasy ma następujące przesłonięte metody:

- `ProjectGuid`, która zwraca GUID fabryki projektu.

- `ProjectType`, która zwraca zlokalizowana nazwa typu projektu.

- `AddFileFromTemplate`, który kopiuje wybrane pliki z folderu szablonu do projektu docelowego. Ta metoda jest dalsze implementowana w dalszej części tego tematu.

  `SimpleProjectNode` Konstruktora, takiej jak `SimpleProjectFactory` konstruktora, buforuje `SimpleProjectPackage` odwołanie do pola prywatnego w celu późniejszego użycia.

  Do łączenia z `SimpleProjectFactory` klasy `SimpleProjectNode` klasy, trzeba utworzyć nową `SimpleProjectNode` w `SimpleProjectFactory.CreateProject` metody i zapisać go w pamięci podręcznej w prywatnego pola do późniejszego użycia.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Aby połączyć klasę fabryki projektu i klasa węzła

1.  W *SimpleProjectFactory.cs* plików, Dodaj następujący kod `using` instrukcji:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2.  Zastąp `SimpleProjectFactory.CreateProject` metody, używając następującego kodu.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3.  Ponownie skompiluj rozwiązanie, a następnie sprawdź, czy opiera się bez błędów.

## <a name="test-the-projectnode-class"></a>Klasa testu
 Przetestuj fabryką projektu, aby zobaczyć, czy zostaje utworzony hierarchii projektu.

### <a name="to-test-the-projectnode-class"></a>Aby przetestować klasy

1.  Naciśnij klawisz **F5** można rozpocząć debugowania. W doświadczalnym wystąpieniu należy utworzyć nowe SimpleProject.

2.  Program Visual Studio, należy wywołać fabryką projektu, aby utworzyć projekt.

3.  Zamknij wystąpienie doświadczalne programu Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Dodaj ikonę węzła niestandardowego projektu
 Ikona węzła projektu we wcześniejszej sekcji znajduje się ikona domyślna. Można go zmienić, na ikony niestandardowej.

### <a name="to-add-a-custom-project-node-icon"></a>Aby dodać ikonę węzła niestandardowego projektu

1. W **zasobów** folderu, Dodaj plik mapy bitowej o nazwie *SimpleProjectNode.bmp*.

2. W **właściwości** systemu windows, zmniejszyć mapę bitową do 16 na 16 pikseli. Mapy bitowej wprowadzić szczególne.

    ![Simple Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. W **właściwości** oknie zmiany **Akcja kompilacji** mapy bitowej do **zasób osadzony**.

4. W *SimpleProjectNode.cs*, Dodaj następujący kod `using` instrukcji:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Dodaj następujące pola statyczne i Konstruktor `SimpleProjectNode` klasy.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Dodaj następującą właściwość do stanu sprzed `SimpleProjectNode` klasy.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Zamień Konstruktor wystąpienia następujący kod.

   ```csharp
   public SimpleProjectNode(SimpleProjectPackage package)
   {
       this.package = package;

       imageIndex = this.ImageHandler.ImageList.Images.Count;

       foreach (Image img in imageList.Images)
       {
           this.ImageHandler.AddImage(img);
       }
   }
   ```

   Podczas konstruowania statyczne `SimpleProjectNode` pobiera mapy bitowej węzła projektu z zasobów manifestu zestawu i zapisuje go w pamięci podręcznej prywatnego pola do późniejszego użycia. Zwróć uwagę, składnia <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ścieżkę obrazu. Aby wyświetlić nazwy zasobów manifestu osadzonego w zestawie, należy użyć <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metody. Gdy ta metoda jest stosowany do `SimpleProject` zestawu, wyniki powinny być następujące:

- *SimpleProject.Resources.resources*

- *VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Podczas tworzenia wystąpienia `ProjectNode` ładowania klasy bazowej *Resources.imagelis.bmp*, w którym są osadzone powszechnie używane bitmap 16 x 16 z *Resources\imagelis.bmp*. Ta lista mapy bitowej ma zostać udostępnione `SimpleProjectNode` jako `ImageHandler.ImageList`. `SimpleProjectNode` dołącza mapy bitowej węzła projektu do listy. Przesunięcie mapy bitowej węzła projektu z listy obrazów jest buforowany do późniejszego użycia z wartością publicznie `ImageIndex` właściwości. Program Visual Studio używa tej właściwości, aby określić, które mapy bitowej do wyświetlenia jako ikona węzła projektu.

## <a name="test-the-custom-project-node-icon"></a>Testowanie ikony węzła niestandardowego projektu
 Przetestuj fabryką projektu, aby zobaczyć, czy zostaje utworzony hierarchii projektu ikona węzła niestandardowego projektu.

### <a name="to-test-the-custom-project-node-icon"></a>Aby przetestować niestandardowego projektu ikony węzła

1.  Rozpocznij debugowanie, a w doświadczalnym wystąpieniu tworzenie nowych SimpleProject.

2.  W nowo utworzonym projekcie, zwróć uwagę, że *SimpleProjectNode.bmp* jest używany jako ikona węzła projektu.

     ![Prosty projekt nowy węzeł projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3.  Otwórz *Program.cs* w edytorze kodu. Kod źródłowy, który przypomina poniższy kod powinien być widoczny.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;

    namespace $nameSpace$
    {
        public class $className$
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Hello VSX!!!");
                Console.ReadKey();
            }
        }
    }
    ```

     Zwróć uwagę, parametry szablonu $nameSpace$ i $className$ ma nowe wartości. Dowiesz się jak zaimplementować Podstawienie parametru szablonu w następnej sekcji.

## <a name="substitute-template-parameters"></a>Zastąp parametry szablonu
 W wcześniejszej sekcji rejestrowania szablon projektu przy użyciu programu Visual Studio przy użyciu `ProvideProjectFactory` atrybutu. Rejestrowanie ścieżkę do folderu szablonu w ten sposób pozwala włączyć Podstawienie parametru podstawowy szablon, zastępowanie i rozszerzanie `ProjectNode.AddFileFromTemplate` klasy. Aby uzyskać więcej informacji, zobacz [Generowanie nowego projektu: Za kulisami, część dwóch](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Teraz Dodaj kod zastępczy `AddFileFromTemplate` klasy.

### <a name="to-substitute-template-parameters"></a>Aby zastąpić parametry szablonu

1. W *SimpleProjectNode.cs* plików, Dodaj następujący kod `using` instrukcji.

   ```csharp
   using System.IO;
   ```

2. Zastąp `AddFileFromTemplate` metody, używając następującego kodu.

   ```csharp
   public override void AddFileFromTemplate(
       string source, string target)
   {
       string nameSpace =
           this.FileTemplateProcessor.GetFileNamespace(target, this);
       string className = Path.GetFileNameWithoutExtension(target);

       this.FileTemplateProcessor.AddReplace("$nameSpace$", nameSpace);
       this.FileTemplateProcessor.AddReplace("$className$", className);

       this.FileTemplateProcessor.UntokenFile(source, target);
       this.FileTemplateProcessor.Reset();
   }
   ```

3. Ustaw punkt przerwania w metodzie zaraz po `className` instrukcji przypisania.

   Instrukcje przypisania określa rozsądne wartości dla przestrzeni nazw i nazwy klasy. Dwa `ProjectNode.FileTemplateProcessor.AddReplace` wywołania metody Zastąp odpowiednie wartości parametrów szablonu, używając tych nowych wartości.

## <a name="test-the-template-parameter-substitution"></a>Testowanie Podstawienie parametru szablonu
 Teraz można przetestować Podstawienie parametru szablonu.

### <a name="to-test-the-template-parameter-substitution"></a>Aby przetestować Podstawienie parametru szablonu

1. Rozpocznij debugowanie, a w doświadczalnym wystąpieniu tworzenie nowych SimpleProject.

2. Wykonanie zatrzymuje się w punkcie przerwania w `AddFileFromTemplate` metody.

3. Sprawdź wartości `nameSpace` i `className` parametrów.

   -   `nameSpace` podano wartość \<RootNamespace > element *\Templates\Projects\SimpleProject\SimpleProject.myproj* pliku szablonu projektu. W tym przypadku wartość jest `MyRootNamespace`.

   -   `className` podana jest wartość nazwę klasy źródłowej pliku bez rozszerzenia nazwy pliku. W tym przypadku jest to plik był kopiowany do folderu docelowego *AssemblyInfo.cs*; w związku z tym, wartość className `AssemblyInfo`.

4. Usuń punkt przerwania, a następnie naciśnij klawisz **F5** do kontynuowania wykonywania.

    Program Visual Studio powinno zostać zakończone, tworzenia projektu.

5. Otwórz *Program.cs* w edytorze kodu. Kod źródłowy, który przypomina poniższy kod powinien być widoczny.

   ```csharp
   using System;
   using System.Collections.Generic;
   using System.Linq;
   using System.Text;

   namespace MyRootNamespace
   {
       public class Program
       {
           static void Main(string[] args)
           {
               Console.WriteLine("Hello VSX!!!");
               Console.ReadKey();
           }
       }
   }
   ```

    Należy zauważyć, że przestrzeń nazw jest teraz `MyRootNamespace` i nazwa klasy jest teraz `Program`.

6. Uruchom debugowanie projektu. Nowy projekt powinien kompilowania, uruchamiania i wyświetlić "Hello VSX!!!" w oknie konsoli.

    ![Polecenie prostego projektu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Gratulacje! Udało Ci się wdrożyć systemu podstawowego projektu zarządzanego.