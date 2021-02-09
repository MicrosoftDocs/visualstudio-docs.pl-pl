---
title: Tworzenie systemu podstawowego projektu, część 1 | Microsoft Docs
description: Dowiedz się, jak utworzyć typ projektu o nazwie Extension. webproj. W programie Visual Studio projekty są kontenerami używanymi do organizowania plików kodu źródłowego i innych zasobów.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a1b21ef736e69c962db389a7bb1a3eb284ebdd0a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99887370"
---
# <a name="create-a-basic-project-system-part-1"></a>Tworzenie podstawowego systemu projektu, część 1
W programie Visual Studio projekty są kontenerami używanymi przez deweloperów do organizowania plików kodu źródłowego i innych zasobów. Projekty są wyświetlane jako elementy podrzędne rozwiązań w **Eksplorator rozwiązań**. Projekty pozwalają organizować, kompilować, debugować i wdrażać kod źródłowy oraz tworzyć odwołania do usług sieci Web, baz danych i innych zasobów.

 Projekty są zdefiniowane w plikach projektu, na przykład plik *. csproj* dla projektu Visual C#. Można utworzyć własny typ projektu, który ma własne rozszerzenie nazwy pliku projektu. Aby uzyskać więcej informacji na temat typów projektów, zobacz [typy projektów](../extensibility/internals/project-types.md).

> [!NOTE]
> Jeśli musisz rozbudować program Visual Studio z niestandardowym typem projektu, zdecydowanie zalecamy użycie [systemu projektu programu Visual Studio](https://github.com/Microsoft/VSProjectSystem) (vsps), który ma wiele zalet w porównaniu do kompilowania systemu projektu od podstaw:
>
> - Łatwiejsze dołączanie.  Nawet podstawowy system projektu wymaga dziesiątek tysięcy wierszy kodu.  Korzystanie z VSPS zmniejsza koszt dołączania do kilku kliknięć, zanim wszystko będzie gotowe do dostosowania go do Twoich potrzeb.
> - Łatwiejsza konserwacja.  Korzystając z VSPS, wystarczy zachować własne scenariusze.  Obsługujemy całą infrastrukturę systemu projektu.
>
>   Jeśli chcesz docelować wersje programu Visual Studio starsze niż Visual Studio 2013, nie będziesz w stanie korzystać z VSPS w rozszerzeniu programu Visual Studio.  W takim przypadku ten przewodnik jest dobrym miejscem, aby rozpocząć pracę.

 W tym instruktażu pokazano, jak utworzyć typ projektu, który ma rozszerzenie nazwy pliku projektu *. proj*. Ten Instruktaż jest zaciągnięty z istniejącego systemu projektu Visual C#.

> [!NOTE]
> Aby uzyskać więcej przykładów projektów rozszerzeń, zobacz [VSSDK Samples](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

 W tym instruktażu przedstawiono sposób wykonywania następujących zadań:

- Utwórz podstawowy typ projektu.

- Utwórz podstawowy szablon projektu.

- Zarejestruj szablon projektu w programie Visual Studio.

- Utwórz wystąpienie projektu, otwierając okno dialogowe **Nowy projekt** , a następnie używając szablonu.

- Utwórz fabrykę projektu dla systemu projektu.

- Utwórz węzeł projektu dla systemu projektu.

- Dodaj niestandardowe ikony dla systemu projektu.

- Zaimplementuj Podstawienie parametru podstawowego szablonu.

## <a name="prerequisites"></a>Wymagania wstępne
 Począwszy od programu Visual Studio 2015, nie należy instalować zestawu Visual Studio SDK z centrum pobierania. Jest ona dostępna jako opcjonalna funkcja w Instalatorze programu Visual Studio. Zestaw VS SDK można także zainstalować później. Aby uzyskać więcej informacji, zobacz [Instalowanie zestawu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

 Należy również pobrać kod źródłowy dla [struktury zarządzanego pakietu dla projektów](https://github.com/tunnelvisionlabs/MPFProj10). Wyodrębnij plik do lokalizacji dostępnej dla rozwiązania, które chcesz utworzyć.

## <a name="create-a-basic-project-type"></a>Tworzenie podstawowego typu projektu
 Utwórz projekt w języku C# o nazwie **SimpleProject**. (**Plik**  >  **Nowe**  >  **Projekt, a** następnie   >    >  **Projekt VSIX** rozszerzalności Visual C#). Dodaj szablon elementu projektu pakietu programu Visual Studio (na **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu i wybierz polecenie **Dodaj**  >  **nowy element**, a następnie przejdź do **rozszerzenia rozszerzalny**  >  **pakiet Visual Studio**). Nazwij plik *SimpleProjectPackage*.

## <a name="creating-a-basic-project-template"></a>Tworzenie podstawowego szablonu projektu
 Teraz możesz zmodyfikować ten podstawowy pakietu VSPackage, aby zaimplementować nowy typ projektu *. proj* . Aby utworzyć projekt oparty na typie projektu *. proj* , program Visual Studio musi wiedzieć, które pliki, zasoby i odwołania, które mają zostać dodane do nowego projektu. Aby podać te informacje, Umieść pliki projektu w folderze szablonu projektu. Gdy użytkownik używa projektu *. proj* do tworzenia projektu, pliki są kopiowane do nowego projektu.

### <a name="to-create-a-basic-project-template"></a>Aby utworzyć podstawowy szablon projektu

1. Dodaj trzy foldery do projektu, jeden pod drugim: *Templates\Projects\SimpleProject*. (W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł projektu **SimpleProject** , wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy folder**. Nazwij *Szablony* folderów. W folderze *Szablony* Dodaj folder o nazwie *projekty*. W folderze *projekty* Dodaj folder o nazwie *SimpleProject*.)

2. W folderze *Templates\Projects\SimpleProject* Dodaj plik obrazu mapy bitowej, który ma być używany jako ikona o nazwie *SimpleProject. ico*. Po kliknięciu przycisku **Dodaj** zostanie otwarty Edytor ikon.

3. Ustaw charakterystyczną ikonę. Ta ikona zostanie wyświetlona w oknie dialogowym **Nowy projekt** w dalszej części przewodnika.

    ![Ikona prostego projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon")

4. Zapisz ikonę i Zamknij Edytor ikon.

5. W folderze *Templates\Projects\SimpleProject* Dodaj element **klasy** o nazwie *program.cs*.

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
   > To nie jest końcowa postać kodu *program.cs* ; parametry zastępujące będą rozpatrywane w późniejszym kroku. Mogą pojawić się błędy kompilacji, ale o ile plik **BuildAction** ma **zawartość**, powinno być możliwe skompilowanie i uruchomienie projektu w zwykły sposób.

7. Zapisz plik.

8. Skopiuj plik *AssemblyInfo.cs* z folderu *Properties* do folderu *Projects\SimpleProject* .

9. W folderze *Projects\SimpleProject* Dodaj plik XML o nazwie *SimpleProject. webproj*.

   > [!NOTE]
   > Rozszerzenie nazwy pliku dla wszystkich projektów tego typu to *. proj*. Jeśli chcesz ją zmienić, musisz ją zmienić wszędzie tam, gdzie jest to opisane w przewodniku.

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

12. W oknie **Właściwości** Ustaw **akcję kompilacja** z *AssemblyInfo.cs*, *program.cs*, *SimpleProject. ico* i *SimpleProject. webproj* na **zawartość**, a następnie ustaw dla nich opcję **include** na **wartość true**.

    Ten szablon projektu opisuje podstawowy projekt Visual C#, który ma zarówno konfigurację debugowania, jak i konfigurację wydania. Projekt zawiera dwa pliki źródłowe, *AssemblyInfo.cs* i *program.cs* oraz kilka odwołań do zestawów. Po utworzeniu projektu na podstawie szablonu wartość ProjectGuid jest automatycznie zastępowana przez nowy identyfikator GUID.

    W **Eksplorator rozwiązań** folder rozwinięte **Szablony** powinien wyglądać następująco:

```
Templates
   Projects
      SimpleProject
         AssemblyInfo.cs
         Program.cs
         SimpleProject.ico
         SimpleProject.myproj
```

## <a name="create-a-basic-project-factory"></a>Utwórz podstawową fabrykę projektu
 Musisz poinformować program Visual Studio o lokalizacji folderu szablonów projektu. Aby to zrobić, Dodaj atrybut do klasy pakietu VSPackage, która implementuje fabrykę projektu, tak aby lokalizacja szablonu została zapisana do rejestru systemowego podczas kompilowania pakietu VSPackage. Zacznij od utworzenia podstawowej fabryki projektu, która jest identyfikowana przez identyfikator GUID fabryki projektu. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutu, aby połączyć fabrykę projektu z `SimpleProjectPackage` klasą.

### <a name="to-create-a-basic-project-factory"></a>Aby utworzyć podstawową fabrykę projektu

1. Utwórz identyfikatory GUID dla fabryki projektu (w menu **Narzędzia** kliknij polecenie **Utwórz GUID**) lub użyj jednego z nich w poniższym przykładzie. Dodaj identyfikatory GUID do klasy w `SimpleProjectPackage` sekcji już zdefiniowanej `PackageGuidString` . Identyfikatory GUID muszą znajdować się zarówno w formie identyfikatora GUID, jak i w postaci ciągu. Otrzymany kod powinien wyglądać podobnie do poniższego przykładu.

   ```csharp
       public sealed class SimpleProjectPackage : Package
       {
           ...
           public const string SimpleProjectPkgString = "96bf4c26-d94e-43bf-a56a-f8500b52bfad";
           public const string SimpleProjectFactoryString = "471EC4BB-E47E-4229-A789-D1F5F83B52D4";

           public static readonly Guid guidSimpleProjectFactory = new Guid(SimpleProjectFactoryString);
       }
   ```

2. Dodaj klasę do folderu Top *SimpleProject* o nazwie *SimpleProjectFactory.cs*.

3. Dodaj następujące dyrektywy using:

   ```csharp
   using System.Runtime.InteropServices;
   using Microsoft.VisualStudio.Shell;
   ```

4. Dodaj atrybut identyfikatora GUID do `SimpleProjectFactory` klasy. Wartość atrybutu jest nowym identyfikatorem GUID fabryki projektu.

   ```csharp
   [Guid(SimpleProjectPackage.SimpleProjectFactoryString)]
   class SimpleProjectFactory
   {
   }
   ```

   Teraz możesz zarejestrować szablon projektu.

### <a name="to-register-the-project-template"></a>Aby zarejestrować szablon projektu

1. W *SimpleProjectPackage.cs* Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybut do `SimpleProjectPackage` klasy w następujący sposób.

   ```csharp
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]
   [Guid(SimpleProjectPackage.PackageGuidString)]
   public sealed class SimpleProjectPackage : Package
   ```

2. Skompiluj ponownie rozwiązanie i sprawdź, czy jest ono kompilacje bez błędów.

    Ponowne kompilowanie rejestruje szablon projektu.

   Parametry `defaultProjectExtension` i `possibleProjectExtensions` są ustawiane jako rozszerzenie nazwy pliku projektu (*. proj*). `projectTemplatesDirectory`Parametr jest ustawiony na ścieżkę względną folderu *templates* . Podczas kompilacji Ta ścieżka zostanie przekonwertowana na pełną kompilację i dodana do rejestru w celu zarejestrowania systemu projektu.

## <a name="test-the-template-registration"></a>Testowanie rejestracji szablonu
 Rejestracja szablonu informuje program Visual Studio o lokalizacji folderu szablonu projektu, aby program Visual Studio mógł wyświetlić nazwę i ikonę szablonu w oknie dialogowym **Nowy projekt** .

### <a name="to-test-the-template-registration"></a>Aby przetestować rejestrację szablonu

1. Naciśnij klawisz **F5** , aby rozpocząć debugowanie eksperymentalnego wystąpienia programu Visual Studio.

2. W eksperymentalnym wystąpieniu Utwórz nowy projekt nowo utworzonego typu projektu. W oknie dialogowym **Nowy projekt** w obszarze **zainstalowane szablony** powinny być widoczne **SimpleProject** .

   Teraz masz zarejestrowaną fabrykę projektów. Jednak nie może jeszcze utworzyć projektu. Pakiet projektu i fabryka projektów współpracują ze sobą, aby utworzyć i zainicjować projekt.

## <a name="add-the-managed-package-framework-code"></a>Dodawanie kodu struktury zarządzanego pakietu
 Zaimplementuj połączenie między pakietem projektu a fabryką projektu.

- Zaimportuj pliki kodu źródłowego dla struktury pakietu zarządzanego.

    1. Zwolnij projekt SimpleProject (w **Eksplorator rozwiązań** wybierz węzeł projektu, a następnie w menu kontekstowym kliknij polecenie **Zwolnij projekt**.) i Otwórz plik projektu w edytorze XML.

    2. Dodaj następujące bloki do pliku projektu (tuż powyżej \<Import> bloków). Ustaw `ProjectBasePath` lokalizację pliku *ProjectBase. Files* w pobranym kodzie struktury pakietu zarządzanego. Może być konieczne dodanie ukośnika odwrotnego do nazwy ścieżki. W przeciwnym razie projekt może nie znaleźć kodu źródłowego struktury pakietu zarządzanego.

        ```
        <PropertyGroup>
             <ProjectBasePath>your path here\</ProjectBasePath>
             <RegisterWithCodebase>true</RegisterWithCodebase>
          </PropertyGroup>
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />
        ```

        > [!IMPORTANT]
        > Nie zapomnij ukośnika odwrotnego na końcu ścieżki.

    3. Załaduj ponownie projekt.

    4. Dodaj odwołania do następujących zestawów:

        - `Microsoft.VisualStudio.Designer.Interfaces`(w *\<VSSDK install> \VisualStudioIntegration\Common\Assemblies\v2.0*)

        - `WindowsBase`

        - `Microsoft.Build.Tasks.v4.0`

### <a name="to-initialize-the-project-factory"></a>Aby zainicjować fabrykę projektu

1. W pliku *SimpleProjectPackage.cs* Dodaj następującą `using` dyrektywę.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

2. Utwórz `SimpleProjectPackage` klasę z `Microsoft.VisualStudio.Package.ProjectPackage` .

    ```csharp
    public sealed class SimpleProjectPackage : ProjectPackage
    ```

3. Zarejestruj fabrykę projektu. Dodaj następujący wiersz do `SimpleProjectPackage.Initialize` metody, tuż po `base.Initialize` .

    ```csharp
    base.Initialize();
    this.RegisterProjectFactory(new SimpleProjectFactory(this));
    ```

4. Zaimplementuj Właściwość abstrakcyjną `ProductUserContext` :

    ```csharp
    public override string ProductUserContext
        {
            get { return ""; }
    }
    ```

5. W *SimpleProjectFactory.cs*, Dodaj następującą `using` dyrektywę po istniejących `using` dyrektywach.

    ```csharp
    using Microsoft.VisualStudio.Project;
    ```

6. Utwórz `SimpleProjectFactory` klasę z `ProjectFactory` .

    ```csharp
    class SimpleProjectFactory : ProjectFactory
    ```

7. Dodaj następującą metodę fikcyjną do `SimpleProjectFactory` klasy. Ta metoda zostanie zaimplementowana w dalszej części.

    ```csharp
    protected override ProjectNode CreateProject()
    {
        return null;
    }
    ```

8. Dodaj następujące pole i Konstruktor do `SimpleProjectFactory` klasy. To `SimpleProjectPackage` odwołanie jest buforowane w polu prywatnym, dzięki czemu może być używane podczas ustawiania lokacji dostawcy usług.

    ```csharp
    private SimpleProjectPackage package;

    public SimpleProjectFactory(SimpleProjectPackage package)
        : base(package)
    {
        this.package = package;
    }
    ```

9. Skompiluj ponownie rozwiązanie i sprawdź, czy jest ono kompilacje bez błędów.

## <a name="test-the-project-factory-implementation"></a>Testowanie implementacji fabryki projektu
 Sprawdź, czy Konstruktor dla implementacji fabryki projektu jest wywoływany.

### <a name="to-test-the-project-factory-implementation"></a>Aby przetestować implementację programu Project Factory

1. W pliku *SimpleProjectFactory.cs* Ustaw punkt przerwania w następującym wierszu w `SimpleProjectFactory` konstruktorze.

    ```csharp
    this.package = package;
    ```

2. Naciśnij klawisz **F5** , aby uruchomić eksperymentalne wystąpienie programu Visual Studio.

3. W eksperymentalnym wystąpieniu Rozpocznij tworzenie nowego projektu. W oknie dialogowym **Nowy projekt** wybierz typ projektu **SimpleProject** , a następnie kliknij przycisk **OK**. Wykonywanie jest zatrzymane w punkcie przerwania.

4. Wyczyść punkt przerwania i Zatrzymaj debugowanie. Ponieważ nie został jeszcze utworzony węzeł projektu, kod tworzenia projektu nadal zgłasza wyjątki.

## <a name="extend-the-projectnode-class"></a>Poszerzenie klasy ProjectNode
 Teraz można zaimplementować `SimpleProjectNode` klasę, która pochodzi od `ProjectNode` klasy. `ProjectNode`Klasa bazowa obsługuje następujące zadania tworzenia projektu:

- Kopiuje plik szablonu projektu, *SimpleProject. webproj* do nowego folderu projektu. Nazwa kopii zostanie zmieniona na podstawie nazwy wprowadzonej w oknie dialogowym **Nowy projekt** . `ProjectGuid`Wartość właściwości jest zastępowana przez nowy identyfikator GUID.

- Przechodzi elementy programu MSBuild pliku szablonu projektu, *SimpleProject. webproj* i szuka `Compile` elementów. Dla każdego `Compile` pliku docelowego Program kopiuje plik do folderu nowego projektu.

  Klasa pochodna `SimpleProjectNode` obsługuje następujące zadania:

- Włącza lub wybiera ikony dla węzłów projektu i pliku w **Eksplorator rozwiązań** .

- Zezwala na określenie dodatkowych podstawiania parametrów szablonu projektu.

### <a name="to-extend-the-projectnode-class"></a>Aby zwiększyć klasę ProjectNode

1. Dodaj klasę o nazwie `SimpleProjectNode.cs` .

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

   Ta `SimpleProjectNode` Implementacja klasy obejmuje następujące przeciążone metody:

- `ProjectGuid`, która zwraca identyfikator GUID fabryki projektu.

- `ProjectType`, która zwraca zlokalizowaną nazwę typu projektu.

- `AddFileFromTemplate`, która kopiuje wybrane pliki z folderu Template do projektu docelowego. Ta metoda jest zaimplementowana w dalszej części.

  `SimpleProjectNode`Konstruktor, taki jak `SimpleProjectFactory` Konstruktor, buforuje `SimpleProjectPackage` odwołanie w prywatnym polu do późniejszego użycia.

  Aby połączyć `SimpleProjectFactory` klasę z `SimpleProjectNode` klasą, należy utworzyć wystąpienie nowej `SimpleProjectNode` `SimpleProjectFactory.CreateProject` metody i buforować ją w prywatnym polu do późniejszego użycia.

### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Aby połączyć klasę fabryki projektu i klasę węzła

1. W pliku *SimpleProjectFactory.cs* Dodaj następującą `using` dyrektywę:

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

3. Skompiluj ponownie rozwiązanie i sprawdź, czy jest ono kompilacje bez błędów.

## <a name="test-the-projectnode-class"></a>Testowanie klasy ProjectNode
 Przetestuj fabrykę projektu, aby zobaczyć, czy tworzy hierarchię projektu.

### <a name="to-test-the-projectnode-class"></a>Aby przetestować klasę ProjectNode

1. Naciśnij klawisz **F5**, aby uruchomić debugowanie. W eksperymentalnym wystąpieniu Utwórz nowy SimpleProject.

2. Program Visual Studio powinien wywołać fabrykę projektu, aby utworzyć projekt.

3. Zamknij wystąpienie eksperymentalne programu Visual Studio.

## <a name="add-a-custom-project-node-icon"></a>Dodaj niestandardową ikonę węzła projektu
 Ikona węzła projektu w poprzedniej sekcji jest domyślną ikoną. Można ją zmienić na ikonę niestandardową.

### <a name="to-add-a-custom-project-node-icon"></a>Aby dodać niestandardową ikonę węzła projektu

1. W folderze **resources** Dodaj plik mapy bitowej o nazwie *SimpleProjectNode.bmp*.

2. W oknach **Właściwości** Zmniejsz mapę bitową do 16 pikseli. Oznacz mapę bitową.

    ![Prosta Communication Project](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")

3. W oknie **Właściwości** Zmień **akcję kompilacja** mapy bitowej na **zasób osadzony**.

4. W *SimpleProjectNode.cs* Dodaj następujące `using` dyrektywy:

   ```csharp
   using System.Drawing;
   using System.Windows.Forms;
   ```

5. Dodaj następujące statyczne pole i Konstruktor do `SimpleProjectNode` klasy.

   ```csharp
   private static ImageList imageList;

   static SimpleProjectNode()
   {
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));
   }
   ```

6. Dodaj następującą właściwość na początku `SimpleProjectNode` klasy.

   ```csharp
   internal static int imageIndex;
      public override int ImageIndex
      {
          get { return imageIndex; }
      }
   ```

7. Zastąp Konstruktor wystąpienia poniższym kodem.

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

   Podczas konstruowania statycznego program `SimpleProjectNode` Pobiera mapę bitową węzła projektu z zasobów manifestu zestawu i buforuje ją w prywatnym polu do późniejszego użycia. Zwróć uwagę na składnię <xref:System.Reflection.Assembly.GetManifestResourceStream%2A> ścieżki obrazu. Aby wyświetlić nazwy zasobów manifestu osadzone w zestawie, użyj <xref:System.Reflection.Assembly.GetManifestResourceNames%2A> metody. Po zastosowaniu tej metody do `SimpleProject` zestawu wyniki powinny być następujące:

- *SimpleProject. resources. resources*

- *VisualStudio. Project. resources*

- *SimpleProject. pakietu VSPackage. resources*

- *Resources.imagelis.bmp*

- *Microsoft. VisualStudio. Project. DontShowAgainDialog. resources*

- *Microsoft. VisualStudio. Project. SecurityWarningDialog. resources*

- *SimpleProject.Resources.SimpleProjectNode.bmp*

  Podczas konstruowania wystąpienia `ProjectNode` Klasa bazowa ładuje *Resources.imagelis.bmp*, w których są osadzone powszechnie używane 16 x 16 map bitowych z *Resources\imagelis.bmp*. Ta lista mapy bitowej jest udostępniana `SimpleProjectNode` jako `ImageHandler.ImageList` . `SimpleProjectNode` dołącza mapę bitową węzła projektu do listy. Przesunięcie mapy bitowej węzła projektu na liście obrazów jest buforowane do późniejszego użycia jako wartość `ImageIndex` Właściwości publicznej. Program Visual Studio używa tej właściwości, aby określić, która mapa bitowa ma być wyświetlana jako ikona węzła projektu.

## <a name="test-the-custom-project-node-icon"></a>Przetestuj ikonę niestandardowego węzła projektu
 Przetestuj fabrykę projektu, aby zobaczyć, czy tworzy hierarchię projektu, która ma niestandardową ikonę węzła projektu.

### <a name="to-test-the-custom-project-node-icon"></a>Aby przetestować ikonę węzła projektu niestandardowego

1. Rozpocznij debugowanie i w eksperymentalnym wystąpieniu Utwórz nowy SimpleProject.

2. W nowo utworzonym projekcie należy zauważyć, że *SimpleProjectNode.bmp* jest używany jako ikona węzła projektu.

     ![Prosty węzeł projektu nowego projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")

3. Otwórz plik *Program.cs* w edytorze kodu. Powinien zostać wyświetlony kod źródłowy podobny do następującego kodu.

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

     Zwróć uwagę, że parametry szablonu $nameSpace $ i $className $ nie mają nowych wartości. Dowiesz się, jak zaimplementować podstawienie parametrów szablonu w następnej sekcji.

## <a name="substitute-template-parameters"></a>Podstawianie parametrów szablonu
 W poprzedniej sekcji zarejestrowano szablon projektu w programie Visual Studio przy użyciu `ProvideProjectFactory` atrybutu. Zarejestrowanie ścieżki folderu szablonów w ten sposób umożliwia włączenie podstawiania parametrów podstawowego szablonu przez zastępowanie i rozszerzanie `ProjectNode.AddFileFromTemplate` klasy. Aby uzyskać więcej informacji, zobacz temat [Nowa generacja projektu: pod okapem, część druga](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).

 Teraz Dodaj kod zastępczy do `AddFileFromTemplate` klasy.

### <a name="to-substitute-template-parameters"></a>Aby zastąpić parametry szablonu

1. W pliku *SimpleProjectNode.cs* Dodaj następującą `using` dyrektywę.

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

3. Ustaw punkt przerwania w metodzie tuż po `className` instrukcji przypisania.

   Instrukcje przypisania określają odpowiednie wartości dla przestrzeni nazw i nazwę nowej klasy. Dwa `ProjectNode.FileTemplateProcessor.AddReplace` wywołania metody zastępują odpowiednie wartości parametrów szablonu przy użyciu tych nowych wartości.

## <a name="test-the-template-parameter-substitution"></a>Testowanie podstawienia parametru szablonu
 Teraz można testować Podstawienie parametrów szablonu.

### <a name="to-test-the-template-parameter-substitution"></a>Aby przetestować Podstawienie parametru szablonu

1. Rozpocznij debugowanie i w eksperymentalnym wystąpieniu Utwórz nowy SimpleProject.

2. Wykonywanie jest zatrzymane w punkcie przerwania w `AddFileFromTemplate` metodzie.

3. Przeanalizuj wartości `nameSpace` `className` parametrów i.

   - `nameSpace` otrzymuje wartość \<RootNamespace> elementu w pliku szablonu projektu *\Templates\Projects\SimpleProject\SimpleProject.myproj* . W tym przypadku wartość jest `MyRootNamespace` .

   - `className` otrzymuje wartość nazwy pliku źródłowego klasy, bez rozszerzenia nazwy pliku. W takim przypadku pierwszy plik do skopiowania do folderu docelowego to *AssemblyInfo.cs*; w związku z tym wartość className jest `AssemblyInfo` .

4. Usuń punkt przerwania i naciśnij klawisz **F5** , aby kontynuować wykonywanie.

    Program Visual Studio powinien zakończyć tworzenie projektu.

5. Otwórz plik *Program.cs* w edytorze kodu. Powinien zostać wyświetlony kod źródłowy podobny do następującego kodu.

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

    Zauważ, że przestrzeń nazw jest teraz `MyRootNamespace` , a nazwa klasy to teraz `Program` .

6. Rozpocznij debugowanie projektu. Nowy projekt powinien kompilować, uruchamiać i wyświetlać "Hello VSX!!!" w oknie konsoli.

    ![Proste polecenie projektu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")

   Gratulacje! Wdrożono podstawowy zarządzany system projektów.
