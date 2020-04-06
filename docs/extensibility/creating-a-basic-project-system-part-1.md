---
title: Tworzenie podstawowego systemu projektów, część 1 | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4ff969a905d48ef16b3cb036fa897bf0307b929d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739724"
---
# <a name="create-a-basic-project-system-part-1"></a>Tworzenie podstawowego systemu projektów, część 1
W programie Visual Studio projekty są kontenerami używanymi przez deweloperów do organizowania plików kodu źródłowego i innych zasobów. Projekty są wyświetlane jako dzieci rozwiązań w **Eksploratorze rozwiązań**. Projekty umożliwiają organizowanie, tworzenie, debugowanie i wdrażanie kodu źródłowego oraz tworzenie odwołań do usług sieci Web, baz danych i innych zasobów.

 Projekty są definiowane w plikach projektu, na przykład pliku *csproj* dla projektu Visual C#. Można utworzyć własny typ projektu, który ma własne rozszerzenie nazwy pliku projektu. Aby uzyskać więcej informacji na temat typów projektów, zobacz [Typy projektów](../extensibility/internals/project-types.md).

> [!NOTE]
> Jeśli chcesz rozszerzyć program Visual Studio o niestandardowy typ projektu, zdecydowanie zalecamy wykorzystanie [systemu projektu programu Visual Studio](https://github.com/Microsoft/VSProjectSystem) (VSPS), który ma szereg zalet w porównaniu z tworzeniem systemu projektu od podstaw:
>
> - Łatwiejsze dołączanie.  Nawet podstawowy system projektu wymaga dziesiątek tysięcy wierszy kodu.  Wykorzystanie vsps zmniejsza koszt dołączania do kilku kliknięć, zanim będziesz gotowy, aby dostosować go do swoich potrzeb.
> - Łatwiejsza konserwacja.  Korzystając z usługi VSPS, wystarczy tylko zachować własne scenariusze.  Zajmujemy się utrzymaniem całej infrastruktury systemu projektowego.
>
>   Jeśli chcesz kierować wersje programu Visual Studio starsze niż Visual Studio 2013, nie będzie można wykorzystać VSPS w rozszerzeniu programu Visual Studio.  Jeśli tak jest, ten przewodnik jest dobrym miejscem, aby rozpocząć.

 W tym przewodniku pokazano, jak utworzyć typ projektu z rozszerzeniem nazwy pliku projektu *.myproj*. W tym instruktażu zapożycza się z istniejącego systemu projektu języka Visual C#.

> [!NOTE]
> Aby uzyskać więcej przykładów projektów rozszerzenia, zobacz [przykłady VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 W tym przewodniku uczy się, jak wykonać następujące zadania:

- Utwórz podstawowy typ projektu.

- Utwórz podstawowy szablon projektu.

- Zarejestruj szablon projektu w programie Visual Studio.

- Utwórz wystąpienie projektu, otwierając okno dialogowe **Nowy projekt,** a następnie używając szablonu.

- Utwórz fabrykę projektów dla systemu projektu.

- Utwórz węzeł projektu dla systemu projektu.

- Dodaj niestandardowe ikony dla systemu projektu.

- Zaimplementuj podstawianie parametrów szablonu podstawowego.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować visual studio SDK z centrum pobierania. Jest on dołączony jako opcjonalna funkcja w konfiguracji programu Visual Studio. Można również zainstalować vs SDK później. Aby uzyskać więcej informacji, zobacz [Instalowanie pakietu SDK programu Visual Studio](../extensibility/installing-the-visual-studio-sdk.md).

 Należy również pobrać kod źródłowy dla [struktury pakietu zarządzanego dla projektów](https://github.com/tunnelvisionlabs/MPFProj10). Wyodrębnij plik do lokalizacji, która jest dostępna dla rozwiązania, które zamierzasz utworzyć.

## <a name="create-a-basic-project-type"></a>Tworzenie podstawowego typu projektu
 Utwórz projekt VSIX w języku C o nazwie **SimpleProject**. (Plik**File** > **nowy** > **projekt,** a następnie **Visual C#** > **Rozszerzalność** > **PROJEKTU VSIX**). Dodaj szablon elementu projektu pakietu programu Visual Studio (w **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj** > **nowy element**, a następnie przejdź do pakietu Programu Visual**Studio** **rozszerzalność).** >  Nazwij plik *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Tworzenie podstawowego szablonu projektu
 Teraz można zmodyfikować ten podstawowy vspackage do zaimplementowania nowego typu projektu *.myproj.* Aby utworzyć projekt, który jest oparty na typie projektu *.myproj,* visual studio musi wiedzieć, które pliki, zasoby i odwołania, aby dodać do nowego projektu. Aby podać te informacje, umieść pliki projektu w folderze szablonów projektu. Gdy użytkownik używa projektu *.myproj* do utworzenia projektu, pliki są kopiowane do nowego projektu.

### <a name="to-create-a-basic-project-template"></a>Aby utworzyć podstawowy szablon projektu

1. Dodaj trzy foldery do projektu, jeden pod drugim: *Templates\Projects\SimpleProject*. (W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **SimpleProject,** wskaż polecenie **Dodaj**, a następnie kliknij polecenie **Nowy folder**. Nazwij folder *Szablony*. W folderze *Szablony* dodaj folder o nazwie *Projekty*. W folderze *Projekty* dodaj folder o nazwie *SimpleProject*.)

2. W folderze *Templates\Projects\SimpleProject* dodaj plik obrazu bitmapy, który będzie używany jako ikona o nazwie *SimpleProject.ico*. Po kliknięciu **przycisku Dodaj**zostanie otwarty edytor ikon.

3. Nadaj ikonę charakterystyczną. Ta ikona pojawi się w oknie dialogowym **Nowy projekt** w dalszej części przewodnika.

    ![Ikona prostego projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon (SimpleProjIcon)")

4. Zapisz ikonę i zamknij edytor ikon.

5. W folderze *Szablony\Projekty\Prostyproject* dodaj element **klasy** o nazwie *Program.cs*.

6. Zastąp istniejący kod następującymi wierszami.

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
   > Nie jest to ostateczna forma *kodu Program.cs;* parametry zastępcze zostaną omówione w późniejszym etapie. Mogą być widoczne błędy kompilacji, ale tak długo, jak plik **BuildAction** jest **zawartość**, powinieneś być w stanie skompilować i uruchomić projekt jak zwykle.

7. Zapisz plik.

8. Skopiuj plik *AssemblyInfo.cs* z folderu *Właściwości* do folderu *Projekty\SimpleProject.*

9. W folderze *Projekty\SimpleProject* dodaj plik XML o nazwie *SimpleProject.myproj*.

   > [!NOTE]
   > Rozszerzenie nazwy pliku dla wszystkich projektów tego typu to *.myproj*. Jeśli chcesz go zmienić, należy zmienić go wszędzie tam, gdzie jest wymieniony w instruktażu.

10. Zastąp istniejącą zawartość następującymi wierszami.

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

12. W oknie Właściwości ustaw **akcję** **kompilacji** *AssemblyInfo.cs* *, Program.cs*, *SimpleProject.ico*i *SimpleProject.myproj* na **Content**i ustaw ich uwzględnij we właściwościach **VSIX** na **True**.

    Ten szablon projektu opisuje podstawowy projekt języka Visual C#, który ma zarówno konfigurację debugowania, jak i konfigurację wydania. Projekt zawiera dwa pliki źródłowe, *AssemblyInfo.cs* i *Program.cs*oraz kilka odniesień do zestawu. Gdy projekt jest tworzony na podstawie szablonu, ProjectGuid wartość jest automatycznie zastępowany przez nowy identyfikator GUID.

    W **Eksploratorze rozwiązań**rozwinięty folder **Szablony** powinien być wyświetlany w następujący sposób:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Tworzenie podstawowej fabryki projektów
 Należy poinformować program Visual Studio o lokalizacji folderu szablonów projektu. Aby to zrobić, należy dodać atrybut do klasy VSPackage, która implementuje fabrykę projektu, tak aby lokalizacja szablonu jest zapisywana w rejestrze systemowym podczas budowy programu VSPackage. Zacznij od utworzenia podstawowej fabryki projektów, która jest identyfikowana przez identyfikator GUID fabryki projektu. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutu, aby połączyć `SimpleProjectPackage` fabrykę projektu z klasą.

### <a name="to-create-a-basic-project-factory"></a>Aby utworzyć podstawową fabrykę projektów

1. Utwórz identyfikatory GUID dla fabryki projektów (w menu **Narzędzia** kliknij polecenie **Utwórz identyfikator GUID)** lub użyj identyfikatora w poniższym przykładzie. Dodaj identyfikatory GUID `SimpleProjectPackage` do klasy w pobliżu `PackageGuidString`sekcji z już zdefiniowanym . Identyfikatory GUID muszą być zarówno w formie GUID, jak i w formie ciągu. Wynikowy kod powinien przypominać poniższy przykład.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Dodaj klasę do górnego folderu *SimpleProject* o nazwie *SimpleProjectFactory.cs*.

3. Dodaj następujące za pomocą dyrektyw:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Dodaj atrybut GUID do `SimpleProjectFactory` klasy. Wartość atrybutu jest nowy identyfikator GUID fabryki projektu.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Teraz możesz zarejestrować szablon projektu.

### <a name="to-register-the-project-template"></a>Aby zarejestrować szablon projektu

1. W *SimpleProjectPackage.cs*, dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybut do `SimpleProjectPackage` klasy, w następujący sposób.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Odbuduj rozwiązanie i sprawdź, czy tworzy bez błędów.

    Przebudowa rejestruje szablon projektu.

   Parametry `defaultProjectExtension` i `possibleProjectExtensions` są ustawione na rozszerzenie nazwy pliku projektu (*.myproj*). Parametr `projectTemplatesDirectory` jest ustawiony na ścieżkę względną folderu *Szablony.* Podczas kompilacji ta ścieżka zostanie przekonwertowana na pełną kompilację i dodana do rejestru w celu zarejestrowania systemu projektu.

## <a name="test-the-template-registration"></a>Testowanie rejestracji szablonu
 Rejestracja szablonu informuje program Visual Studio o lokalizacji folderu szablonu projektu, dzięki czemu program Visual Studio może wyświetlać nazwę szablonu i ikonę w oknie dialogowym **Nowy projekt.**

### <a name="to-test-the-template-registration"></a>Aby przetestować rejestrację szablonu

1. Naciśnij **klawisz F5,** aby rozpocząć debugowanie eksperymentalnego wystąpienia programu Visual Studio.

2. W wystąpieniu eksperymentalnym utwórz nowy projekt nowo utworzonego typu projektu. W oknie dialogowym **Nowy projekt** powinien zostać wyświetlony komunikat **SimpleProject** w obszarze **Zainstalowane szablony**.

   Teraz masz fabrykę projektów, która jest zarejestrowana. Jednak nie można jeszcze utworzyć projektu. Pakiet projektu i fabryka projektu współpracują ze sobą w celu utworzenia i zainicjowania projektu.

## <a name="add-the-managed-package-framework-code"></a>Dodawanie kodu struktury pakietu zarządzanego
 Zaimplementuj połączenie między pakietem projektu a fabryką projektu.

- Importowanie plików kodu źródłowego dla struktury pakietu zarządzanego.

    1. Zwolnij projekt SimpleProject (w **Eksploratorze rozwiązań**wybierz węzeł projektu i w menu kontekstowym kliknij polecenie **Zwolnij projekt**.) i otwórz plik projektu w edytorze XML.

    2. Dodaj następujące bloki do pliku projektu \<(tuż nad blokami Importuj>). Ustaw `ProjectBasePath` lokalizację pliku *ProjectBase.files* w kodzie struktury pakietu zarządzanego, który właśnie pobrano. Może być trzeba dodać ukośnik odwrotny do nazwy ścieżki. Jeśli nie, projekt może nie znaleźć kodu źródłowego struktury pakietu zarządzanego.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Nie zapomnij o ukośnik odwrotny na końcu ścieżki.

    3. Przeładuj ponownie projekt.

    4. Dodaj odwołania do następujących zestawów:

        - `Microsoft.VisualStudio.Designer.Interfaces`(w * \<programie VSSDK zainstalować>\VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Aby zainicjować fabrykę projektu

1. W pliku *SimpleProjectPackage.cs* dodaj następującą `using` dyrektywę.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Wykierowuj `SimpleProjectPackage` klasę z `Microsoft.VisualStudio.Package.ProjectPackage`.

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Zarejestruj fabrykę projektu. Dodaj następujący wiersz `SimpleProjectPackage.Initialize` do metody, `base.Initialize`zaraz po .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Zaimplementuj abstrakcyjną właściwość: `ProductUserContext`

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. W *SimpleProjectFactory.cs*, dodać następującą `using` dyrektywę `using` po istniejących dyrektyw.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Wykierowuj `SimpleProjectFactory` klasę z `ProjectFactory`.

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Dodaj następującą metodę manekina `SimpleProjectFactory` do klasy. Zaimplementujesz tę metodę w dalszej sekcji.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Dodaj następujące pole i konstruktora `SimpleProjectFactory` do klasy. To `SimpleProjectPackage` odwołanie jest buforowane w polu prywatnym, dzięki czemu może być używane do ustawiania lokacji dostawcy usług.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Odbuduj rozwiązanie i sprawdź, czy tworzy bez błędów.

## <a name="test-the-project-factory-implementation"></a>Testowanie wdrożenia fabryki projektu
 Sprawdź, czy konstruktor implementacji fabryki projektu jest wywoływana.

### <a name="to-test-the-project-factory-implementation"></a>Aby przetestować implementację fabryki projektu

1. W pliku *SimpleProjectFactory.cs* ustaw punkt przerwania w następującym `SimpleProjectFactory` wierszu w konstruktorze.

    ```csharp
    this.package = package;
    ```

2. Naciśnij **klawisz F5,** aby uruchomić eksperymentalne wystąpienie programu Visual Studio.

3. W wystąpieniu eksperymentalnym rozpocznij tworzenie nowego projektu. W oknie dialogowym **Nowy projekt** wybierz typ projektu **SimpleProject,** a następnie kliknij przycisk **OK**. Wykonanie zatrzymuje się w punkcie przerwania.

4. Wyczyść punkt przerwania i zatrzymaj debugowanie. Ponieważ nie utworzyliśmy jeszcze węzła projektu, kod tworzenia projektu nadal zgłasza wyjątki.

## <a name="extend-the-projectnode-class"></a>Rozszerzanie klasy ProjectNode
 Teraz można zaimplementować `SimpleProjectNode` klasę, `ProjectNode` która pochodzi z klasy. Klasa `ProjectNode` podstawowa obsługuje następujące zadania tworzenia projektu:

- Kopiuje plik szablonu projektu *SimpleProject.myproj*do nowego folderu projektu. Nazwa kopii została zmieniona zgodnie z nazwą wprowadzona w oknie dialogowym **Nowy projekt.** Wartość `ProjectGuid` właściwości zostanie zastąpiona nowym identyfikatorem GUID.

- Przechodzi przez MSBuild elementów pliku szablonu projektu, *SimpleProject.myproj*, i szuka `Compile` elementów. Dla `Compile` każdego pliku docelowego kopiuje plik do nowego folderu projektu.

  Klasa pochodna `SimpleProjectNode` obsługuje następujące zadania:

- Umożliwia utworzenie lub wybranie ikon węzłów projektu i plików w **Eksploratorze rozwiązań.**

- Umożliwia określenie dodatkowych podstawienia parametrów szablonu projektu.

### <a name="to-extend-the-projectnode-class"></a>Aby rozszerzyć klasę ProjectNode

1. Dodaj klasę `SimpleProjectNode.cs`o nazwie .

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

   Ta `SimpleProjectNode` implementacja klasy ma te zastąpione metody:

- `ProjectGuid`, który zwraca identyfikator GUID fabryki projektu.

- `ProjectType`, który zwraca zlokalizowane nazwy typu projektu.

- `AddFileFromTemplate`, która kopiuje wybrane pliki z folderu szablonu do projektu docelowego. Ta metoda jest dalej implementowana w dalszej sekcji.

  Konstruktor, `SimpleProjectNode` podobnie `SimpleProjectFactory` jak konstruktor, buforuje `SimpleProjectPackage` odwołanie w polu prywatnym do późniejszego użycia.

  Aby `SimpleProjectFactory` połączyć klasę `SimpleProjectNode` z klasą, należy `SimpleProjectNode` utworzyć `SimpleProjectFactory.CreateProject` wystąpienie nowego w metodzie i buforować ją w polu prywatnym do późniejszego użycia.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Aby połączyć klasę fabryki projektu i klasę węzła

1. W pliku *SimpleProjectFactory.cs* dodaj następującą `using` dyrektywę:

    ```csharp
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;
    ```

2. Zastąp `SimpleProjectFactory.CreateProject` metodę przy użyciu następującego kodu.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        SimpleProjectNode project = new SimpleProjectNode(this.package);

        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));
        return project;
    }
    ```

3. Odbuduj rozwiązanie i sprawdź, czy tworzy bez błędów.

## <a name="test-the-projectnode-class"></a>Testowanie klasy ProjectNode
 Przetestuj fabrykę projektu, aby zobaczyć, czy tworzy hierarchię projektów.

### <a name="to-test-the-projectnode-class"></a>Aby przetestować klasę ProjectNode

1. Naciśnij klawisz **F5**, aby uruchomić debugowanie. W eksperymentalnym wystąpieniu utwórz nowy SimpleProject.

2. Visual Studio należy wywołać fabryki projektu, aby utworzyć projekt.

3. Zamknij eksperymentalne wystąpienie programu Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Dodawanie niestandardowej ikony węzła projektu
 Ikona węzła projektu we wcześniejszej sekcji jest ikoną domyślną. Można go zmienić na niestandardową ikonę.

### <a name="to-add-a-custom-project-node-icon"></a>Aby dodać niestandardową ikonę węzła projektu

1. W folderze **Zasoby** dodaj plik mapy bitowej o nazwie *SimpleProjectNode.bmp*.

2. W **oknach Właściwości** zmniejsz bitmapę do 16 na 16 pikseli. Uaszli, aby mapa bitowa była charakterystyczna.

    ![Prosty projekt Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm (ProstyprojProjectComm)")

3. W oknie Właściwości zmień **akcję Kompilacja** mapy bitowej na **Osadzony zasób**. **Properties**

4. W *SimpleProjectNode.cs*dodaj następujące `using` dyrektywy:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Dodaj następujące pole statyczne i `SimpleProjectNode` konstruktora do klasy.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Dodaj następującą właściwość na `SimpleProjectNode` początku klasy.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Zastąp konstruktora wystąpienia następującym kodem.

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

   Podczas budowy statycznej `SimpleProjectNode` pobiera mapę bitową węzła projektu z zasobów manifestu zestawu i buforuje go w polu prywatnym do późniejszego użycia. Zwróć uwagę na składnię <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ścieżki obrazu. Aby wyświetlić nazwy zasobów manifestu osadzonych w <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> zestawie, należy użyć metody. Gdy ta metoda jest `SimpleProject` stosowana do złożenia, wyniki powinny być następujące:

- *SimpleProject.Resources.resources*

- *Zasoby programu VisualStudio.Project.resources*

- *SimpleProject.VSPackage.resources*

- *Resources.imagelis.bmp*

- *Microsoft.VisualStudio.Project.DontShowAgainDialog.resources*

- *Microsoft.VisualStudio.Project.SecurityWarningDialog.resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Podczas budowy wystąpienia `ProjectNode` klasa podstawowa ładuje *plik Resources.imagelis.bmp,* w którym są osadzone powszechnie używane 16 x 16 bitmap z *pliku Resources\imagelis.bmp*. Ta lista bitmap jest `SimpleProjectNode` `ImageHandler.ImageList`udostępniana jako . `SimpleProjectNode`dołącza mapę bitową węzła projektu do listy. Przesunięcie mapy bitowej węzła projektu na liście obrazów jest buforowane do `ImageIndex` późniejszego użycia jako wartość właściwości publicznej. Visual Studio używa tej właściwości, aby określić, która mapa bitowa ma być wyświetlana jako ikona węzła projektu.

## <a name="test-the-custom-project-node-icon"></a>Testowanie niestandardowej ikony węzła projektu
 Przetestuj fabrykę projektu, aby zobaczyć, czy tworzy hierarchię projektu, która ma niestandardową ikonę węzła projektu.

### <a name="to-test-the-custom-project-node-icon"></a>Aby przetestować niestandardową ikonę węzła projektu

1. Rozpocznij debugowanie, a w wystąpieniu eksperymentalnym utwórz nowy SimpleProject.

2. W nowo utworzonym projekcie należy zauważyć, że *SimpleProjectNode.bmp* jest używany jako ikona węzła projektu.

     ![Prosty węzeł nowego projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Otwórz plik *Program.cs* w edytorze kodu. Powinien zostać wyświetlony kod źródłowy, który przypomina następujący kod.

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

     Należy zauważyć, że parametry szablonu $nameSpace$ i $className$ nie mają nowych wartości. Dowiesz się, jak zaimplementować podstawienie parametrów szablonu w następnej sekcji.

## <a name="substitute-template-parameters"></a>Zastępcze parametry szablonu
 We wcześniejszej sekcji szablon projektu został zarejestrowany w `ProvideProjectFactory` programie Visual Studio przy użyciu atrybutu. Rejestrowanie ścieżki folderu szablonu w ten sposób umożliwia włączenie podstawiania parametrów `ProjectNode.AddFileFromTemplate` szablonu podstawowego przez zastąpienie i rozszerzenie klasy. Aby uzyskać więcej informacji, zobacz [Nowa generacja projektu: Pod maską, część druga](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Teraz dodaj kod `AddFileFromTemplate` zastępczy do klasy.

### <a name="to-substitute-template-parameters"></a>Aby zastąpić parametry szablonu

1. W pliku *SimpleProjectNode.cs* dodaj następującą `using` dyrektywę.

   ```csharp
   using System.IO;
   ```

2. Zastąp `AddFileFromTemplate` metodę przy użyciu następującego kodu.

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

3. Ustaw punkt przerwania w metodzie, zaraz po `className` instrukcji przypisania.

   Instrukcje przypisania określają rozsądne wartości dla obszaru nazw i nowej nazwy klasy. Wywołanie `ProjectNode.FileTemplateProcessor.AddReplace` dwóch metod zastępuje odpowiednie wartości parametrów szablonu przy użyciu tych nowych wartości.

## <a name="test-the-template-parameter-substitution"></a>Testowanie podstawiania parametrów szablonu
 Teraz możesz przetestować podstawienie parametrów szablonu.

### <a name="to-test-the-template-parameter-substitution"></a>Aby przetestować podstawienie parametrów szablonu

1. Rozpocznij debugowanie, a w wystąpieniu eksperymentalnym utwórz nowy SimpleProject.

2. Wykonanie zatrzymuje się w `AddFileFromTemplate` punkcie przerwania w metodzie.

3. Sprawdź wartości `nameSpace` i `className` parametry.

   - `nameSpace`otrzymuje wartość elementu \<> RootNamespace w pliku *szablonów\projektów\SimpleProject\SimpleProject.myproj.* W takim przypadku wartość `MyRootNamespace`jest .

   - `className`otrzymuje wartość nazwy pliku źródłowego klasy, bez rozszerzenia nazwy pliku. W takim przypadku pierwszy plik skopiowany do folderu docelowego jest *AssemblyInfo.cs*; w związku z tym wartość `AssemblyInfo`className jest .

4. Usuń punkt przerwania i naciśnij **klawisz F5,** aby kontynuować wykonywanie.

    Visual Studio należy zakończyć tworzenie projektu.

5. Otwórz plik *Program.cs* w edytorze kodu. Powinien zostać wyświetlony kod źródłowy, który przypomina następujący kod.

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

    Należy zauważyć, że `MyRootNamespace` obszar nazw jest `Program`teraz i nazwa klasy jest teraz .

6. Rozpocznij debugowanie projektu. Nowy projekt powinien skompilować, uruchomić i wyświetlić "Hello VSX!!!" w oknie konsoli.

    ![Proste polecenie projektu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand (SimpleProjCommand)")

   Gratulacje! Zaimplementowano podstawowy system zarządzanych projektów.
