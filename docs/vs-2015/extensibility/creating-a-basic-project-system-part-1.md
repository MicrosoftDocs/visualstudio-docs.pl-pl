---
title: Tworzenie systemu podstawowego projektu, część 1 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: 882a10fa-bb1c-4b01-943a-7a3c155286dd
caps.latest.revision: 48
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8304719a4b15b5f23957c99244796999d7b3f55c
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63439396"
---
# <a name="creating-a-basic-project-system-part-1"></a>Tworzenie systemu podstawowego projektu, część 1
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W programie Visual Studio projekty są kontenerami, używanych przez deweloperów do organizowania plików kodu źródłowego i inne zasoby. Projekty są traktowane jako elementy podrzędne rozwiązań w **Eksploratora rozwiązań**. Projekty umożliwiają organizowanie, tworzenie, debugowanie i wdrażanie kodu źródłowego i utworzyć odwołania do usług sieci Web, baz danych i innych zasobów.  
  
 Projekty są zdefiniowane w plikach projektu, na przykład plik csproj projektu Visual C#. Można utworzyć swój własny typ projektu, który ma własne rozszerzenia nazw plików projektu. Aby uzyskać więcej informacji na temat typów projektów, zobacz [typów projektów](../extensibility/internals/project-types.md).  
  
> [!NOTE]
> Jeśli zachodzi potrzeba Rozszerzanie programu Visual Studio przy użyciu typu niestandardowego projektu, zdecydowanie zalecamy korzystanie z [System projektu usługi Visual Studio](https://github.com/Microsoft/VSProjectSystem) która ma kilka zalet w stosunku do tworzenia projektu systemu od zera:  
> 
> - Łatwiejsze dołączanie.  Nawet systemu podstawowego projektu wymaga dziesiątki tysięcy wierszy kodu.  Wykorzystując CPS zmniejsza koszty dołączania do kilku kliknięć, zanim można przystąpić do go dostosować do swoich potrzeb.  
>   - Łatwiejsze konserwacji.  Dzięki wykorzystaniu CPS, wystarczy do obsługi własnych scenariuszy.  My zajmujemy utrzymania wszystkich infrastruktury systemu projektu.  
> 
>   Jeśli potrzebujesz do wersji docelowej programu Visual Studio starszych niż program Visual Studio 2013, nie można wykorzystać CPS w rozszerzeniu Visual Studio.  Jeśli tak jest rzeczywiście, ten przewodnik jest dobrym miejscem, aby rozpocząć pracę.  
  
 W tym instruktażu dowiesz się, jak utworzyć typ projektu, który ma .myproj rozszerzenie nazwy pliku projektu. W tym przewodniku pożycza z istniejącego systemu projektów języka Visual C#.  
  
> [!NOTE]
> System projektu języka pełną, na przykład end-to-end, można znaleźć w artykule IronPython przykładowe Deep Dive w [przykłady VSSDK](../misc/vssdk-samples.md).  
  
 Ten przewodnik omawia sposób wykonywania tych zadań:  
  
- Tworzenie typu podstawowego projektu.  
  
- Utwórz szablon podstawowy projekt.  
  
- Szablon projektu należy zarejestrować w usłudze Visual Studio.  
  
- Utwórz wystąpienie projektu, otwierając **nowy projekt** okno dialogowe, a następnie za pomocą szablonu.  
  
- Tworzenie fabryki projektu w systemie projektu.  
  
- Utwórz węzeł projektu w systemie projektu.  
  
- Dodaj niestandardowe ikony system projektu.  
  
- Implementuje podstawowy szablon Podstawienie parametru.  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 Począwszy od programu Visual Studio 2015, możesz nie należy instalować programu Visual Studio SDK z Centrum pobierania. Jest dołączony jako opcjonalna funkcja w Instalatorze programu Visual Studio. Możesz także zainstalować zestaw SDK programu VS później. Aby uzyskać więcej informacji, zobacz [instalowania programu Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
 Należy również pobrać kod źródłowy [zarządzanego środowiska pakietu dla projektów](http://mpfproj12.codeplex.com/). Wyodrębnij plik do lokalizacji, który jest dostępny do rozwiązania, które chcesz utworzyć.  
  
## <a name="creating-a-basic-project-type"></a>Tworzenie typu podstawowego projektu  
 Utwórz projekt VSIX języka C# o nazwie **SimpleProject**. (**Pliku, nowe, projekt** i następnie **pakietu Visual Studio C#, rozszerzalności,** ). Dodawanie szablonu elementu projektu pakietu Visual Studio (w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł projektu, a następnie wybierz pozycję **Add / nowy element**, a następnie przejdź do **rozszerzalność / pakiet Visual Studio**). Nadaj plikowi nazwę **SimpleProjectPackage**.  
  
## <a name="creating-a-basic-project-template"></a>Tworzenie podstawowego projektu szablonu  
 Teraz można zmodyfikować tego podstawowego pakietu VSPackage wdrożyć nowy typ projektu .myproj. Aby utworzyć projekt, który jest oparty na typie projektu .myproj, Visual Studio musi wiedzieć, które pliki, zasobów i odwołania do dodania do nowego projektu. Aby podać te informacje, należy umieścić pliki projektu w folderze szablonu projektu. Gdy użytkownik używa projektu .myproj, aby utworzyć projekt, pliki są kopiowane do nowego projektu.  
  
#### <a name="to-create-a-basic-project-template"></a>Aby utworzyć szablon podstawowy projekt  
  
1. Dodaj trzy foldery w projekcie, jeden pod innymi: **Templates\Projects\SimpleProject**. (W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **SimpleProject** węzła projektu, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy Folder**. Nazwa folderu `Templates`. W **szablony** folderu, Dodaj folder o nazwie `Projects`. W **projektów** folderu, Dodaj folder o nazwie `SimpleProject`.)  
  
2. W **Projects\SimpleProject** folderu Dodaj plik ikony o nazwie `SimpleProject.ico`. Po kliknięciu **Dodaj**, zostanie otwarty Edytor ikon.  
  
3. Ikona szczególne. Ta ikona pojawi się w **nowy projekt** okno dialogowe w dalszej części przewodnika.  
  
    ![Ikona prostego projektu](../extensibility/media/simpleprojicon.png "SimpleProjIcon")  
  
4. Ikonę Zapisz i zamknij Edytor ikon.  
  
5. W **Projects\SimpleProject** folderu, Dodaj **klasy** element o nazwie `Program.cs`.  
  
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
   > Nie jest ostatnim formularza kod pliku Program.cs; Parametry zamiany zostaną omówione w dalszej części. Może zostać wyświetlony błędy kompilacji, ale tak długo, jak plik **BuildAction** jest **zawartości**, powinno być możliwe skompilować i uruchomić projekt w zwykły sposób.  
  
7. Zapisz plik.  
  
8. Skopiuj plik AssemblyInfo.cs z **właściwości** folder **Projects\SimpleProject** folderu.  
  
9. W **Projects\SimpleProject** folderu Dodaj plik XML o nazwie `SimpleProject.myproj`.  
  
   > [!NOTE]
   > Rozszerzenie nazwy pliku dla wszystkich projektów tego typu jest .myproj. Jeśli chcesz ją zmienić, należy zmienić go wszędzie tam, gdzie jest wymieniony w instruktażu.  
  
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
  
12. W **właściwości** oknie **Build Action** AssemblyInfo.cs, plik Program.cs, SimpleProject.ico i SimpleProject.myproj do **zawartości**i ustaw ich  **Uwzględnione w VSIX** właściwości **True**.  
  
    Ten szablon projektu w tym artykule opisano podstawowe Visual C# projekt, który ma zarówno konfigurację debugowania, jak i konfiguracji wydania. Projekt zawiera dwa pliki źródłowe, AssemblyInfo.cs i plik Program.cs i kilka zestawów odwołań. Gdy projekt jest tworzony na podstawie tego szablonu, wartość ProjectGuid jest automatycznie zastępowany przez nowy identyfikator GUID.  
  
    W **Eksploratora rozwiązań**, rozwiniętym okienku **szablony** folderu powinna wyglądać następująco:  
  
    Szablony  
  
    Projekty  
  
    SimpleProject  
  
    AssemblyInfo.cs  
  
    Program.cs  
  
    SimpleProject.ico  
  
    SimpleProject.myproj  
  
## <a name="creating-a-basic-project-factory"></a>Tworzenie fabryki podstawowego projektu  
 Musisz poinformować lokalizacji folderu szablonu projektu programu Visual Studio. Aby to zrobić, należy dodać atrybut do klasy pakietu VSPackage, która implementuje fabryka projektu, dzięki czemu lokalizacja szablonu są zapisywane w rejestrze systemu podczas tworzenia pakietu VSPackage. Rozpocznij od utworzenia fabryki podstawowego projektu, która jest identyfikowana przez fabrykę projektu identyfikatora GUID. Użyj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybut klasy SimpleProjectPackage nawiązać połączenia z fabryką projektu.  
  
#### <a name="to-create-a-basic-project-factory"></a>Umożliwia ono utworzenie fabryki podstawowego projektu  
  
1. Otwórz SimpleProjectPackageGuids.cs w edytorze kodu.  
  
2. Tworzenie identyfikatorów GUID fabryki projekt (na **narzędzia** menu, kliknij przycisk **Utwórz GUID**), lub użyj w poniższym przykładzie. Dodaj identyfikatory GUID do klasy SimpleProjectPackageGuids. Identyfikatory GUID musi być zarówno w formie GUID, jak i w postaci ciągu. Po modyfikacji kod powinien wyglądać następująco.  
  
   ```  
   static class SimpleProjectPackageGuids  
   {  
       public const string guidSimpleProjectPkgString =   
           "96bf4c26-d94e-43bf-a56a-f8500b52bfad";  
       public const string guidSimpleProjectCmdSetString =   
           "72c23e1d-f389-410a-b5f1-c938303f1391";  
       public const string guidSimpleProjectFactoryString =   
           "471EC4BB-E47E-4229-A789-D1F5F83B52D4";  
  
       public static readonly Guid guidSimpleProjectCmdSet =   
           new Guid(guidSimpleProjectCmdSetString);  
       public static readonly Guid guidSimpleProjectFactory =   
           new Guid(guidSimpleProjectFactoryString);  
   }  
   ```  
  
3. Dodaj klasę do góry **SimpleProject** folder o nazwie `SimpleProjectFactory.cs`.  
  
4. Dodaj następujące instrukcje using:  
  
   ```  
   using System.Runtime.InteropServices;  
   using Microsoft.VisualStudio.Shell;  
   ```  
  
5. Dodaj atrybut Guid do klasy SimpleProjectFactory. Wartość atrybutu jest nowa fabryka projektu identyfikatora GUID.  
  
   ```  
   [Guid(SimpleProjectGuids.guidSimpleProjectFactoryString)]  
   class SimpleProjectFactory  
   {  
   }  
   ```  
  
   Teraz możesz zarejestrować szablon projektu.  
  
#### <a name="to-register-the-project-template"></a>Aby zarejestrować szablon projektu  
  
1. W SimpleProjectPackage.cs, Dodaj <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybutów do klasy SimpleProjectPackage w następujący sposób.  
  
   ```  
   [ProvideProjectFactory(    typeof(SimpleProjectFactory),     "Simple Project",   
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",   
       @"Templates\Projects\SimpleProject",     LanguageVsTemplate = "SimpleProject")]  
   [Guid(SimpleProjectGuids.guidSimpleProjectPkgString)]  
   public sealed class SimpleProjectPackage : Package  
   ```  
  
2. Ponownie skompiluj rozwiązanie, a następnie sprawdź, czy opiera się bez błędów.  
  
    Ponowne tworzenie rejestruje szablonu projektu.  
  
   Parametry `defaultProjectExtension` i `possibleProjectExtensions` są ustawione na rozszerzenia nazw plików projektu (.myproj). `projectTemplatesDirectory` Parametr jest ustawiony na ścieżkę względną w folderze szablonów. Podczas kompilacji ta ścieżka zostanie przekonwertowane na pełnej kompilacji i dodany do rejestru, aby zarejestrować system projektu.  
  
## <a name="testing-the-template-registration"></a>Testowanie Rejestracja szablonu  
 Szablon rejestracji informuje program Visual Studio lokalizacji folderu szablonu projektu tak, aby program Visual Studio można wyświetlić nazwę szablonu i ikony w **nowy projekt** okno dialogowe.  
  
#### <a name="to-test-the-template-registration"></a>Aby przetestować Rejestracja szablonu  
  
1. Naciśnij klawisz F5, aby rozpocząć debugowanie doświadczalne wystąpienie programu Visual Studio.  
  
2. W doświadczalnym wystąpieniu Utwórz nowy projekt typu nowo utworzonego projektu. W **nowy projekt** okno dialogowe powinna zostać wyświetlona **SimpleProject** w obszarze **zainstalowane szablony**.  
  
   Masz teraz fabryka projektu, który jest zarejestrowany. Jednak nie można jeszcze utworzyć projekt. Pakiet projektu i projektu fabryki współpracują ze sobą, aby utworzyć i zainicjować projektu.  
  
## <a name="add-the-managed-package-framework-code"></a>Dodaj kod środowiska pakietu zarządzanego  
 Implementuje połączenie między pakietu z projektem i fabryka projektu.  
  
- Zaimportuj pliki kodu źródłowego dla środowiska pakietu zarządzanego.  
  
    1. Cofnij ładowanie projektu SimpleProject (w **Eksploratora rozwiązań**, wybierz węzeł projektu i w menu kontekstowym kliknij **Zwolnij projekt**.), a następnie otwórz plik projektu w edytorze XML.  
  
    2. Dodaj poniższe bloki do pliku projektu (tuż powyżej \<Import > bloków). Ustaw ProjectBasePath lokalizację pliku ProjectBase.files w kodzie środowiska pakietu zarządzanego, które zostały pobrane. Być może będzie trzeba dodać ukośnik odwrotny na nazwę ścieżki. Jeśli tego nie zrobisz, projekt może się nie powieść można znaleźć kodu zarządzanego środowiska pakietu.  
  
        ```  
        <PropertyGroup>  
             <ProjectBasePath>your path here\</ProjectBasePath>  
             <RegisterWithCodebase>true</RegisterWithCodebase>  
          </PropertyGroup>  
          <Import Project="$(ProjectBasePath)\ProjectBase.Files" />  
        ```  
  
        > [!IMPORTANT]
        > Nie zapomnij ukośnik odwrotny na końcu ścieżki.  
  
    3. Ponownie Załaduj projekt.  
  
    4. Dodaj odwołania do następujących zestawów:  
  
        - Microsoft.VisualStudio.Designer.Interfaces (w \<VSSDK instalacji > \VisualStudioIntegration\Common\Assemblies\v2.0)  
  
        - WindowsBase  
  
        - Microsoft.Build.Tasks.v4.0  
  
#### <a name="to-initialize-the-project-factory"></a>Aby zainicjować fabryka projektu  
  
1. W pliku SimpleProjectPackage.cs, Dodaj następujący kod `using` instrukcji.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
2. Pochodzi `SimpleProjectPackage` klasy z `Microsoft.VisualStudio.Package.ProjectPackage`.  
  
    ```  
    public sealed class SimpleProjectPackage : ProjectPackage  
    ```  
  
3. Zarejestrować fabryki projektu. Dodaj następujący wiersz do `SimpleProjectPackage.Initialize` metody tuż za `base.Initialize`.  
  
    ```  
    base.Initialize();  
    this.RegisterProjectFactory(new SimpleProjectFactory(this));  
    ```  
  
4. Implementuje właściwość abstrakcyjną `ProductUserContext`:  
  
    ```csharp  
    public override string ProductUserContext  
        {  
            get { return ""; }  
    }  
    ```  
  
5. W SimpleProjectFactory.cs, Dodaj następujący kod `using` instrukcji znajdującej się po istniejącej `using` instrukcji.  
  
    ```  
    using Microsoft.VisualStudio.Project;  
    ```  
  
6. Pochodzi `SimpleProjectFactory` klasy z `ProjectFactory`.  
  
    ```  
    class SimpleProjectFactory : ProjectFactory  
    ```  
  
7. Dodaj następującą metodę fikcyjnego do `SimpleProjectFactory` klasy. Ta metoda będzie implementowany w dalszej części tego tematu.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        return null;  
    }  
    ```  
  
8. Dodaj następujące pola i Konstruktor `SimpleProjectFactory` klasy. To `SimpleProjectPackage` odwołanie jest buforowany w pole prywatne, dzięki czemu mogą służyć podczas ustawiania witryna dostawcy usług.  
  
    ```  
    private SimpleProjectPackage package;  
  
    public SimpleProjectFactory(SimpleProjectPackage package)  
        : base(package)  
    {  
        this.package = package;  
    }  
    ```  
  
9. Ponownie skompiluj rozwiązanie, a następnie sprawdź, czy opiera się bez błędów.  
  
## <a name="testing-the-project-factory-implementation"></a>Testowanie projektu wdrożenie fabryki  
 Sprawdź, czy wywoływany jest konstruktor implementacji fabryka projektu.  
  
#### <a name="to-test-the-project-factory-implementation"></a>Aby przetestować wdrożenie fabryki projektu  
  
1. W pliku SimpleProjectFactory.cs Ustaw punkt przerwania na następujący wiersz w `SimpleProjectFactory` konstruktora.  
  
    ```  
    this.package = package;  
    ```  
  
2. Naciśnij klawisz F5, aby uruchomić doświadczalne wystąpienie programu Visual Studio.  
  
3. W doświadczalnym wystąpieniu Uruchom utworzyć nowy projekt. W **nowy projekt** okno dialogowe, wybierz opcję SimpleProject typ projektu, a następnie kliknij przycisk **OK**. Zatrzymuje wykonywanie w punkcie przerwania.  
  
4. Wyczyść punkt przerwania i zatrzymać debugowanie. Ponieważ nie utworzono jeszcze węzła projektu, kod tworzenia projektu nadal zgłasza wyjątków.  
  
## <a name="extending-the-project-node-class"></a>Rozszerzanie klasa węzła projektu  
 Teraz można zaimplementować `SimpleProjectNode` klasy, która jest pochodną `ProjectNode` klasy. `ProjectNode` Klasy bazowej obsługuje następujące zadania tworzenia projektu:  
  
- Kopiuje plik szablonu projektu SimpleProject.myproj, do nowego folderu projektu. Kopia jest zmieniana zgodnie z nazwą wprowadzoną w **nowy projekt** okno dialogowe. `ProjectGuid` Wartość właściwości jest zastępowana przez nowy identyfikator GUID.  
  
- Przechodzi przez elementy programu MSBuild w pliku szablonu projektu SimpleProject.myproj, a szuka `Compile` elementów. Dla każdego `Compile` pliku docelowego, kopiuje plik do nowego folderu projektu.  
  
  Pochodnej `SimpleProjectNode` klasa obsługuje następujące zadania:  
  
- Włącza ikony dla projektu i pliku węzłów w **Eksploratora rozwiązań** ma zostać utworzona lub wybrana.  
  
- Umożliwia podstawieniach parametrów szablonu projektu dodatkowe należy określić.  
  
#### <a name="to-extend-the-project-node-class"></a>Aby rozszerzyć klasę węzła projektu  
  
1. 
  
2. Dodaj klasę o nazwie `SimpleProjectNode.cs`.  
  
3. Zastąp istniejący kod następującym kodem.  
  
   ```  
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
               get { return SimpleProjectGuids.guidSimpleProjectFactory; }  
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
  
#### <a name="to-connect-the-project-factory-class-and-the-node-class"></a>Aby połączyć klasę fabryki projektu i klasa węzła  
  
1. W pliku SimpleProjectFactory.cs, Dodaj następujący kod `using` instrukcji:  
  
    ```  
    using IOleServiceProvider =    Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
    ```  
  
2. Zastąp `SimpleProjectFactory.CreateProject` metody, używając następującego kodu.  
  
    ```  
    protected override ProjectNode CreateProject()  
    {  
        SimpleProjectNode project = new SimpleProjectNode(this.package);  
  
        project.SetSite((IOleServiceProvider)        ((IServiceProvider)this.package).GetService(            typeof(IOleServiceProvider)));  
        return project;  
    }  
    ```  
  
3. Ponownie skompiluj rozwiązanie, a następnie sprawdź, czy opiera się bez błędów.  
  
## <a name="testing-the-project-node-class"></a>Testowanie klasa węzła projektu  
 Przetestuj fabryką projektu, aby zobaczyć, czy zostaje utworzony hierarchii projektu.  
  
#### <a name="to-test-the-project-node-class"></a>Aby przetestować klasa węzła projektu  
  
1. Naciśnij klawisz F5, aby rozpocząć debugowanie. W doświadczalnym wystąpieniu należy utworzyć nowe SimpleProject.  
  
2. Program Visual Studio, należy wywołać fabryką projektu, aby utworzyć projekt.  
  
3. Zamknij wystąpienie doświadczalne programu Visual Studio.  
  
## <a name="adding-a-custom-project-node-icon"></a>Dodawanie ikony węzła niestandardowego projektu  
 Ikona węzła projektu we wcześniejszej sekcji znajduje się ikona domyślna. Można go zmienić, na ikony niestandardowej.  
  
#### <a name="to-add-a-custom-project-node-icon"></a>Aby dodać ikonę węzła niestandardowego projektu  
  
1. W **zasobów** folderu, Dodaj plik mapy bitowej o nazwie SimpleProjectNode.bmp.  
  
2. W **właściwości** systemu windows, zmniejszyć mapę bitową do 16 na 16 pikseli. Mapy bitowej wprowadzić szczególne.  
  
    ![Simple Project Comm](../extensibility/media/simpleprojprojectcomm.png "SimpleProjProjectComm")  
  
3. W **właściwości** oknie zmiany **Akcja kompilacji** mapy bitowej do **zasób osadzony**.  
  
4. W SimpleProjectNode.cs, Dodaj następujący kod `using` instrukcji:  
  
   ```  
   using System.Drawing;  
   using System.Windows.Forms;  
   ```  
  
5. Dodaj następujące pola statyczne i Konstruktor `SimpleProjectNode` klasy.  
  
   ```  
   private static ImageList imageList;  
  
   static SimpleProjectNode()  
   {  
       imageList =        Utilities.GetImageList(            typeof(SimpleProjectNode).Assembly.GetManifestResourceStream(                "SimpleProject.Resources.SimpleProjectNode.bmp"));  
   }  
   ```  
  
6. Dodaj następującą właściwość do stanu sprzed `SimpleProjectNode` klasy.  
  
   ```  
   internal static int imageIndex;  
      public override int ImageIndex  
      {  
          get { return imageIndex; }  
      }  
   ```  
  
7. Zamień Konstruktor wystąpienia następujący kod.  
  
   ```  
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
  
- SimpleProject.Resources.resources  
  
- VisualStudio.Project.resources  
  
- SimpleProject.VSPackage.resources  
  
- Resources.imagelis.bmp  
  
- Microsoft.VisualStudio.Project.DontShowAgainDialog.resources  
  
- Microsoft.VisualStudio.Project.SecurityWarningDialog.resources  
  
- SimpleProject.Resources.SimpleProjectNode.bmp  
  
  Podczas tworzenia wystąpienia `ProjectNode` klasy bazowej ładuje Resources.imagelis.bmp, w którym są osadzone powszechnie używane bitmapy 16 x 16 z Resources\imagelis.bmp. Ta lista mapy bitowej ma zostać udostępnione `SimpleProjectNode` jako ImageHandler.ImageList. `SimpleProjectNode` dołącza mapy bitowej węzła projektu do listy. Przesunięcie mapy bitowej węzła projektu z listy obrazów jest buforowany do późniejszego użycia z wartością publicznie `ImageIndex` właściwości. Program Visual Studio używa tej właściwości, aby określić, które mapy bitowej do wyświetlenia jako ikona węzła projektu.  
  
## <a name="testing-the-custom-project-node-icon"></a>Testowanie ikony węzła niestandardowego projektu  
 Przetestuj fabryką projektu, aby zobaczyć, czy zostaje utworzony hierarchii projektu ikona węzła niestandardowego projektu.  
  
#### <a name="to-test-the-custom-project-node-icon"></a>Aby przetestować niestandardowego projektu ikony węzła  
  
1. Rozpocznij debugowanie, a w doświadczalnym wystąpieniu tworzenie nowych SimpleProject.  
  
2. W nowo utworzonym projekcie należy zauważyć, że SimpleProjectNode.bmp jest używany jako ikona węzła projektu.  
  
     ![Prosty projekt nowy węzeł projektu](../extensibility/media/simpleprojnewprojectnode.png "SimpleProjNewProjectNode")  
  
3. Otwórz plik Program.cs w edytorze kodu. Kod źródłowy, który przypomina poniższy kod powinien być widoczny.  
  
    ```  
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
  
## <a name="substituting-template-parameters"></a>Zastępowanie parametrów szablonu  
 W wcześniejszej sekcji rejestrowania szablon projektu przy użyciu programu Visual Studio przy użyciu `ProvideProjectFactory` atrybutu. Rejestrowanie ścieżkę do folderu szablonu w ten sposób pozwala włączyć Podstawienie parametru podstawowy szablon, zastępowanie i rozszerzanie `ProjectNode.AddFileFromTemplate` klasy. Aby uzyskać więcej informacji, zobacz [Generowanie nowego projektu: Za kulisami, część dwóch](../extensibility/internals/new-project-generation-under-the-hood-part-two.md).  
  
 Teraz Dodaj kod zastępczy `AddFileFromTemplate` klasy.  
  
#### <a name="to-substitute-template-parameters"></a>Aby zastąpić parametry szablonu  
  
1. W pliku SimpleProjectNode.cs, Dodaj następujący kod `using` instrukcji.  
  
   ```  
   using System.IO;  
   ```  
  
2. Zastąp `AddFileFromTemplate` metody, używając następującego kodu.  
  
   ```  
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
  
## <a name="testing-the-template-parameter-substitution"></a>Testowanie Podstawienie parametru szablonu  
 Teraz można przetestować Podstawienie parametru szablonu.  
  
#### <a name="to-test-the-template-parameter-substitution"></a>Aby przetestować Podstawienie parametru szablonu  
  
1. Rozpocznij debugowanie, a w doświadczalnym wystąpieniu tworzenie nowych SimpleProject.  
  
2. Wykonanie zatrzymuje się w punkcie przerwania w `AddFileFromTemplate` metody.  
  
3. Sprawdź wartości `nameSpace` i `className` parametrów.  
  
   - `nameSpace` podano wartość \<RootNamespace > elementu w pliku szablonu projektu \Templates\Projects\SimpleProject\SimpleProject.myproj. W tym przypadku wartość jest "MyRootNamespace".  
  
   - `className` podana jest wartość nazwę klasy źródłowej pliku bez rozszerzenia nazwy pliku. W tym przypadku jest to plik był kopiowany do folderu docelowego AssemblyInfo.cs; Dlatego wartość className jest "AssemblyInfo".  
  
4. Usuń punkt przerwania, a następnie naciśnij klawisz F5, aby kontynuować wykonywanie.  
  
    Program Visual Studio powinno zostać zakończone, tworzenia projektu.  
  
5. Otwórz plik Program.cs w edytorze kodu. Kod źródłowy, który przypomina poniższy kod powinien być widoczny.  
  
   ```  
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
  
    Należy zauważyć, że przestrzeń nazw jest teraz "MyRootNamespace", a nazwa klasy jest teraz "Program".  
  
6. Uruchom debugowanie projektu. Nowy projekt powinien kompilowania, uruchamiania i wyświetlić "Hello VSX!!!" w oknie konsoli.  
  
    ![Polecenie prostego projektu](../extensibility/media/simpleprojcommand.png "SimpleProjCommand")  
  
   Gratulacje! Udało Ci się wdrożyć systemu podstawowego projektu zarządzanego.
