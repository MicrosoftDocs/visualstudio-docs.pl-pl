---
title: Tworzenie systemu podstawowego projektu, część 2 | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- writing a project system
- project system
- tutorial
ms.assetid: aee48fc6-a15f-4fd5-8420-7f18824de220
caps.latest.revision: 24
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b6d44e99b584ec347abd407753f965170658969b
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65685409"
---
# <a name="creating-a-basic-project-system-part-2"></a>Tworzenie systemu podstawowego projektu, część 2
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Pierwszy instrukcje przedstawione w tej serii [Tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md), pokazuje, jak tworzenie systemu podstawowego projektu. W tym przewodniku opiera się na systemu podstawowego projektu, dodając szablonu programu Visual Studio, strony właściwości i inne funkcje. Pierwszym przewodniku należy wykonać przed rozpoczęciem korzystania z niej.  
  
 Ten przewodnik pokazuje sposób tworzenia typ projektu, który ma .myproj rozszerzenie nazwy pliku projektu. Aby ukończyć Instruktaż, nie masz do tworzenia własnego języka, ponieważ przewodnik pożycza z istniejącego systemu projektów języka Visual C#.  
  
 Ten przewodnik omawia sposób wykonywania tych zadań:  
  
- Tworzenie szablonu programu Visual Studio.  
  
- Wdróż szablon programu Visual Studio.  
  
- Tworzenie projektu typu węzeł podrzędny **nowy projekt** okno dialogowe.  
  
- Włączyć Podstawienie parametru w szablonie programu Visual Studio.  
  
- Tworzenie strony właściwości projektu.  
  
> [!NOTE]
> Kroki opisane w tym przewodniku są oparte na projekcie języka C#. Jednak z wyjątkiem określonych kryteriów, takich jak rozszerzeń nazw plików i kodu, te same czynności można użyć w projekcie języka Visual Basic.  
  
## <a name="creating-a-visual-studio-template"></a>Tworzenie szablonu programu Visual Studio  
 [Tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md) pokazuje, jak utworzyć szablon podstawowy projekt i dodać go do systemu projektu. Pokazano również, jak zarejestrować ten szablon przy użyciu programu Visual Studio przy użyciu <xref:Microsoft.VisualStudio.Shell.ProvideProjectFactoryAttribute> atrybut, który zapisuje pełną ścieżkę folderu \Templates\Projects\SimpleProject\ w rejestrze systemowym.  
  
 Za pomocą szablonu programu Visual Studio (plik .vstemplate) zamiast szablonu podstawowego projektu, można kontrolować, jak szablon jest wyświetlany w **nowy projekt** okno dialogowe i jak parametry szablonu są zastępowane.  Plik .vstemplate jest plikiem XML, w tym artykule opisano, jak mają być włączone, gdy projekt jest tworzony przy użyciu szablonu projektu systemu plików źródłowych. Sam system projektu utworzonego przez zbieranie plików .vstemplate i plików źródłowych w formie pliku .zip i wdrażane przez skopiowanie pliku .zip do lokalizacji, który jest znany w programie Visual Studio. Ten proces opisano szczegółowo w dalszej części tego przewodnika.  
  
1. W [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], otwórz rozwiązanie SimpleProject, który został utworzony, postępując zgodnie z [Tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md).  
  
2. W pliku SimpleProjectPackage.cs odnaleźć atrybutu ProvideProjectFactory. Zamień na drugi parametr (nazwa projektu) z wartością null, a czwarty parametr (ścieżka do folderu szablonu projektu) ". \\\NullPath ", wykonując następujące czynności.  
  
   ```  
   [ProvideProjectFactory(typeof(SimpleProjectFactory), null,  
       "Simple Project Files (*.myproj);*.myproj", "myproj", "myproj",  
       ".\\NullPath",  
   LanguageVsTemplate = "SimpleProject")]  
   ```  
  
3. Dodaj plik XML o nazwie SimpleProject.vstemplate do folderu \Templates\Projects\SimpleProject\.  
  
4. Zastąp zawartość SimpleProject.vstemplate następującym kodem.  
  
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
  
5. W **właściwości** okna, wybierz wszystkie pięć plików w folderze \Templates\Projects\SimpleProject\ i zestaw **Build Action** do **ZipProject**.  
  
   ![](../extensibility/media/simpproj2.png "SimpProj2")  
  
   \<TemplateData > sekcja określa lokalizację i wygląd SimpleProject typ projektu w **nowy projekt** okno dialogowe, w następujący sposób:  
  
- \<Name > szablon projektu, który ma być aplikacji SimpleProject nazwy elementu.  
  
- \<Opis > element zawiera opis wyświetlany w **nowy projekt** okno dialogowe, gdy zaznaczony jest szablon projektu.  
  
- \<Ikonę > element Określa ikonę, która jest wyświetlana wraz z SimpleProject typu projektu.  
  
- \<ProjectType > typ projektu w nazwy elementu **nowy projekt** okno dialogowe. Ta nazwa zastępuje atrybutu ProvideProjectFactory parametr nazwy projektu.  
  
  > [!NOTE]
  > \<ProjectType > element musi być zgodna `LanguageVsTemplate` argument `ProvideProjectFactory` atrybut w pliku SimpleProjectPackage.cs.  
  
  \<TemplateContent > sekcji opisano te pliki, które są generowane podczas tworzenia nowego projektu:  
  
- SimpleProject.myproj  
  
- Program.cs  
  
- AssemblyInfo.cs  
  
  Wszystkie trzy pliki mają `ReplaceParameters` ustawiona na wartość true, co umożliwia Podstawienie parametru.  Plik Program.cs ma `OpenInEditor` ustawiona na wartość true, co powoduje, że plik ma zostać otwarty w edytorze kodu, gdy projekt jest tworzony.  
  
  Aby uzyskać więcej informacji na temat elementów w schemacie szablon programu Visual Studio, zobacz [odwołanie do schematu szablonu Visual Studio](../extensibility/visual-studio-template-schema-reference.md).  
  
> [!NOTE]
> Jeśli projekt zawiera więcej niż jeden szablon programu Visual Studio, każdy szablon jest w oddzielnym folderze. Każdy plik w tym folderze muszą mieć **Build Action** równa **ZipProject**.  
  
## <a name="adding-a-minimal-vsct-file"></a>Dodawanie pliku vsct minimalny  
 Program Visual Studio musi działać w trybie instalacji, rozpoznawał nowych lub zmodyfikowanych szablonu programu Visual Studio. Tryb instalacji wymaga pliku vsct być obecne. W związku z tym należy dodać plik minimalny vsct do projektu.  
  
1. Dodaj plik XML o nazwie SimpleProject.vsct do projektu SimpleProject.  
  
2. Zastąp zawartość pliku SimpleProject.vsct następującym kodem.  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <CommandTable  
      xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable">  
    </CommandTable>  
    ```  
  
3. Ustaw **Build Action** tego pliku do **VSCTCompile**. Możesz to zrobić tylko w pliku csproj, nie w **właściwości** okna. Upewnij się, że **Build Action** tego pliku jest równa **Brak** w tym momencie.  
  
    1. Kliknij prawym przyciskiem myszy węzeł SimpleProject, a następnie kliknij przycisk **Edytuj SimpleProject.csproj**.  
  
    2. W pliku .csproj Znajdź element SimpleProject.vsct.  
  
        ```  
        <None Include="SimpleProject.vsct" />  
        ```  
  
    3. Zmienić akcję kompilacji na **VSCTCompile**.  
  
        ```  
        <VSCTCompile Include="SimpleProject.vsct" />  
        ```  
  
    4. plik projektu i zamknij Edytor.  
  
    5. Zapisz węzła SimpleProject, a następnie w **Eksploratora rozwiązań** kliknij **Załaduj ponownie projekt**.  
  
## <a name="examining-the-visual-studio-template-build-steps"></a>Badanie kroków kompilacji szablonu programu Visual Studio  
 System kompilacji projektu pakietu VSPackage jest zazwyczaj uruchamiany program Visual Studio w trybie instalacji po zmodyfikowaniu pliku .vstemplate lub projektu, który zawiera plik .vstemplate zostanie ponownie skompilowany. Możesz kontynuować pracę przez ustawienie poziomu szczegółowości MSBuild do normalnego lub nowszej.  
  
1. Na **narzędzia** menu, kliknij przycisk **opcje**.  
  
2. Rozwiń **projekty i rozwiązania** węzeł, a następnie wybierz **kompilowanie i uruchamianie**.  
  
3. Ustaw **poziom szczegółowości danych wyjściowych kompilacji projektu programu MSBuild** do **normalny**. Kliknij przycisk **OK**.  
  
4. Ponownie skompiluj projekt SimpleProject.  
  
   Krok kompilacji, aby utworzyć plik zip projektu powinna wyglądać następująco.  
  
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
  
## <a name="deploying-a-visual-studio-template"></a>Wdrażanie szablonu programu Visual Studio  
 Szablony programu Visual Studio nie zawierają informacji o ścieżce. W związku z tym plik zip szablonu należy wdrożyć do lokalizacji, który jest znany w programie Visual Studio. Lokalizacja folderu ProjectTemplates jest zazwyczaj  **\<% LOCALAPPDATA % > \Microsoft\VisualStudio\14.0Exp\ProjectTemplates**.  
  
 Aby wdrożyć fabryką projektu, program instalacyjny musi mieć uprawnienia administratora. Wdrażania szablonów w węźle instalacji programu Visual Studio: **14.0\Common7\IDE\ProjectTemplates programu Visual Studio ...\Microsoft**.  
  
## <a name="testing-a-visual-studio-template"></a>Testowanie szablonu programu Visual Studio  
 Przetestuj fabryką projektu, aby zobaczyć, czy tworzy hierarchii projektu przy użyciu szablonu programu Visual Studio.  
  
1. Zresetuj wystąpienie eksperymentalne programu Visual Studio SDK.  
  
    Na [!INCLUDE[win7](../includes/win7-md.md)]: W Start menu Znajdź **Microsoft Visual Studio/Microsoft Visual Studio SDK/Tools** folder, a następnie wybierz **Zresetuj wystąpienie eksperymentalne programu Visual Studio Microsoft**.  
  
    W nowszych wersjach systemu Windows: Na ekranie startowym wpisz **zresetować programu Microsoft Visual Studio \<wersji > eksperymentalne wystąpienie**.  
  
2. Zostanie wyświetlone okno wiersza polecenia. Po wyświetleniu wyrazy `Press any key to continue`, naciśnij klawisz ENTER. Po zamknięciu okna, Otwórz program Visual Studio.  
  
3. Ponownie skompiluj projekt SimpleProject, a następnie rozpocząć debugowanie. Zostanie wyświetlone wystąpienie eksperymentalne.  
  
4. W doświadczalnym wystąpieniu Utwórz projekt SimpleProject. W **nowy projekt** okno dialogowe, wybierz opcję **SimpleProject**.  
  
5. Nowe wystąpienie klasy SimpleProject powinny być widoczne.  
  
   ![](../extensibility/media/simpproj2-newproj.png "SimpProj2_NewProj")  
  
   ![](../extensibility/media/simpproj2-myproj.png "SimpProj2_MyProj")  
  
## <a name="creating-a-project-type-child-node"></a>Tworzenie węzła podrzędnego typu projektu  
 Można dodać węzła podrzędnego do węzła typu projektu w **nowy projekt** okno dialogowe.  Na przykład dla typu projektu SimpleProject, może mieć węzłów podrzędnych dla aplikacji konsoli, okna aplikacji, aplikacje sieci web i tak dalej.  
  
 Węzły podrzędne są tworzone przez zmianę w pliku projektu i dodawanie \<OutputSubPath > dzieci \<ZipProject > elementy. Szablon jest kopiowany podczas kompilacji lub wdrożenia, każdy węzeł podrzędny staje się podfolder folderu szablonów projektu.  
  
 W tej sekcji pokazano, jak utworzyć węzeł podrzędny konsoli SimpleProject typu projektu.  
  
1. Zmień nazwę folderu \Templates\Projects\SimpleProject\ na \Templates\Projects\ConsoleApp\\.  
  
2. W **właściwości** okno, wybierz wszystkie pięć plików w folderze \Templates\Projects\ConsoleApp\ i upewnij się, że **Build Action** ustawiono **ZipProject**.  
  
3. W pliku SimpleProject.vstemplate, Dodaj następujący wiersz na końcu \<TemplateData > sekcji, tuż przed tagiem zamykającym.  
  
    ```  
    <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
    ```  
  
     Powoduje to szablon Aplikacja konsoli się zarówno w konsoli węzeł podrzędny i SimpleProject węzła nadrzędnego, który jest jeden poziom wyżej węzeł podrzędny.  
  
4. Zapisz plik SimpleProject.vstemplate.  
  
5. W pliku .csproj Dodaj \<OutputSubPath > do każdego z elementów ZipProject. Cofnij ładowanie projektu, jak poprzednio i wyedytuj plik projektu.  
  
6. Znajdź \<ZipProject > elementy. Do każdego \<ZipProject > elementu Dodawanie \<OutputSubPath > element i nadaj mu wartość konsoli. The ZipProject  
  
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
  
7. Dodaj tę \<PropertyGroup > do pliku projektu:  
  
    ```  
    <PropertyGroup>  
      <VsTemplateLanguage>SimpleProject</VsTemplateLanguage>  
    </PropertyGroup>  
    ```  
  
8. Zapisz plik projektu i ponownie Załaduj projekt.  
  
## <a name="testing-the-project-type-child-node"></a>Testowanie węzeł podrzędny typu projektu  
 Testowanie zmodyfikowany plik projektu aby zobaczyć, czy **konsoli** węzeł podrzędny pojawia się w **nowy projekt** okno dialogowe.  
  
1. Uruchom **Zresetuj Microsoft Visual Studio wystąpienie eksperymentalne programu** narzędzia.  
  
2. Ponownie skompiluj projekt SimpleProject, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.  
  
3. W **nowy projekt** okno dialogowe, kliknij przycisk **SimpleProject** węzła. **Aplikację Konsolową** szablon powinien pojawić się w **szablony** okienka.  
  
4. Rozwiń **SimpleProject** węzła. **Konsoli** węzeł podrzędny powinna zostać wyświetlona. **Aplikacji SimpleProject** szablon będzie wyświetlany w **szablony** okienka.  
  
5. . Kliknij przycisk **anulować** i Zatrzymaj debugowanie  
  
   ![](../extensibility/media/simpproj2-rollup.png "SimpProj2_Rollup")  
  
   ![](../extensibility/media/simpproj2-subfolder.png "SimpProj2_Subfolder")  
  
## <a name="substituting-project-template-parameters"></a>Zastępowanie parametrów szablonu projektu  
 [Tworzenie podstawowego systemu projektu, część 1](../extensibility/creating-a-basic-project-system-part-1.md) pokazano, jak zastąpić `ProjectNode.AddFileFromTemplate` metodę, aby wykonać podstawowe rodzaj Podstawienie parametru szablonu. W tej sekcji omawia sposób używania bardziej zaawansowanych parametrów szablonu programu Visual Studio.  
  
 Po utworzeniu projektu przy użyciu szablonu programu Visual Studio w **nowy projekt** ciągi szablonu, parametry są zastępowane okno dialogowe, aby dostosować projekt. Parametr szablonu ma specjalne token, który rozpoczyna się i kończy znak dolara, na przykład $time$. Następujące dwa parametry są szczególnie przydatne w przypadku włączania dostosowania w projektach, które są oparte na szablonie:  
  
- $ $GUID [1 – 10] jest zastępowana przez nowy identyfikator Guid. Można określić maksymalnie 10 unikatowych identyfikatorów GUID, na przykład $guid1$.  
  
- $safeprojectname$ to nazwa podana przez użytkownika w **nowy projekt** dialogowym zmodyfikowane w celu usunięcia wszystkich niebezpiecznych znaków i spacji.  
  
  Aby uzyskać pełną listę parametrów szablonu, zobacz [parametry szablonu](../ide/template-parameters.md).  Jeśli chcesz utworzyć własny parametr szablonu niestandardowego, zobacz [NIB: Instrukcje: Niestandardowe parametry są przekazywane do szablonów](https://msdn.microsoft.com/5bc2ad11-84c7-4683-a276-e5e00d85d8fb).  
  
#### <a name="to-substitute-project-template-parameters"></a>Aby zastąpić parametry szablonu projektu  
  
1. W pliku SimpleProjectNode.cs Usuń `AddFileFromTemplate` metody.  
  
2. W pliku \Templates\Projects\ConsoleApp\SimpleProject.myproj zlokalizuj \<RootNamespace > właściwości i zmień jej wartość $safeprojectname $.  
  
    ```  
    <RootNamespace>$safeprojectname$</RootNamespace>  
    ```  
  
3. W pliku \Templates\Projects\SimpleProject\Program.cs Zastąp zawartość pliku następującym kodem:  
  
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
  
4. Ponownie skompiluj projekt SimpleProject, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.  
  
5. Utwórz nową aplikację Konsolową SimpleProject. (W **typów projektów** okienku wybierz **SimpleProject**. W obszarze **zainstalowane szablony programu Visual Studio**, wybierz opcję **aplikację Konsolową**.)  
  
6. W nowo utworzonym projekcie Otwórz plik Program.cs. Powinien on wyglądać podobnie do następującej (wartości identyfikatora GUID w pliku będą się różnić.):  
  
    ```  
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
  
## <a name="creating-a-project-property-page"></a>Tworzenie strony właściwości projektu  
 Można utworzyć strony właściwości dla danego typu projektu, tak aby użytkownicy mogli wyświetlić i zmienić właściwości w projektach, które są oparte na szablonie. W tej sekcji dowiesz się, jak utworzyć stronę właściwości niezależne od konfiguracji. Tej strony właściwości podstawowych użyto siatki właściwości, aby wyświetlić właściwości publiczne, które uwidaczniają w klasie strony właściwości.  
  
 Pochodzi z klasy strony właściwości `SettingsPage` klasy bazowej. Siatki właściwości udostępniane przez `SettingsPage` klasy zna najbardziej pierwotne typy danych i wie, jak można je wyświetlić.  Ponadto `SettingsPage` klasy wie, jak zachować wartości właściwości do pliku projektu.  
  
 Na stronie właściwości, który zostanie utworzony w tej sekcji pozwala zmienić i zapisać te właściwości projektu:  
  
- AssemblyName  
  
- Atrybut OutputType  
  
- RootNamespace.  
  
1. W pliku SimpleProjectPackage.cs Dodaj `ProvideObject` atrybutu `SimpleProjectPackage` klasy:  
  
   ```  
   [ProvideObject(typeof(GeneralPropertyPage))]  
   public sealed class SimpleProjectPackage : ProjectPackage  
   ```  
  
    Rejestruje to klasy strony właściwości `GeneralPropertyPage` w modelu COM.  
  
2. W pliku SimpleProjectNode.cs, Dodaj te dwie metody zgodnym z przesłoniętą `SimpleProjectNode` klasy:  
  
   ```  
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
  
    Obie te metody zwracają tablicę identyfikatorów GUID strony właściwości.  Identyfikator GUID GeneralPropertyPage jest jedynym elementem w tablicy, więc **stron właściwości** zostanie wyświetlone okno dialogowe tylko jedną stronę.  
  
3. Dodaj plik klasy do projektu SimpleProject o nazwie GeneralPropertyPage.cs.  
  
4. Zastąp zawartość tego pliku przy użyciu następującego kodu:  
  
   ```  
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
               this.assemblyName = this.ProjectMgr.GetProjectProperty(  
   "AssemblyName", true);  
               this.defaultNamespace = this.ProjectMgr.GetProjectProperty(  
   "RootNamespace", false);  
  
               string outputType = this.ProjectMgr.GetProjectProperty(  
   "OutputType", false);  
               this.outputType =   
   (OutputType)Enum.Parse(typeof(OutputType), outputType);  
           }  
  
           protected override int ApplyChanges()  
           {  
               this.ProjectMgr.SetProjectProperty(  
   "AssemblyName", this.assemblyName);  
               this.ProjectMgr.SetProjectProperty(  
   "OutputType", this.outputType.ToString());  
               this.ProjectMgr.SetProjectProperty(  
   "RootNamespace", this.defaultNamespace);  
               this.IsDirty = false;  
  
               return VSConstants.S_OK;  
           }  
       }  
   }  
   ```  
  
    `GeneralPropertyPage` Klasa udostępnia trzy właściwości publiczne AssemblyName, atrybut OutputType i RootNamespace. AssemblyName jest brak metody set, dlatego jest ona wyświetlana jako właściwość tylko do odczytu. Atrybut OutputType jest stała wyliczeniowa, dzięki czemu będzie ono wyświetlane jako lista rozwijana.  
  
    `SettingsPage` Udostępnia klasę bazową `ProjectMgr` można utrwalić właściwości. `BindProperties` Metoda używa `ProjectMgr` do pobierania wartości właściwości utrwalonych i ustaw odpowiednie właściwości.  `ApplyChanges` Metoda używa `ProjectMgr` pobrać wartości właściwości do utrwalenia ich w pliku projektu. Właściwością metody ustawia `IsDirty` na wartość true, aby wskazać, że właściwości musi być utrwalone.  Trwałość występuje, gdy zapisujesz projekt lub rozwiązanie.  
  
5. Ponownie skompiluj rozwiązanie SimpleProject, a następnie rozpocząć debugowanie. Wystąpienie eksperymentalne powinna zostać wyświetlona.  
  
6. W doświadczalnym wystąpieniu należy utworzyć nową aplikację SimpleProject.  
  
7. Program Visual Studio wywołuje fabryką projektu, aby utworzyć projekt przy użyciu szablonu programu Visual Studio. Nowy plik Program.cs jest otwarty w edytorze kodu.  
  
8. Kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratora rozwiązań**, a następnie kliknij przycisk **właściwości**. **Stron właściwości** zostanie wyświetlone okno dialogowe.  
  
   ![](../extensibility/media/simpproj2-proppage.png "SimpProj2_PropPage")  
  
## <a name="testing-the-project-property-page"></a>Testowanie na stronie właściwości projektu  
 Teraz możesz sprawdzić, czy można zmodyfikować, a zmiany wartości właściwości.  
  
1. W **stron właściwości MyConsoleApplication** okno dialogowe, zmiana **DefaultNamespace** do **MyApplication**.  
  
2. Wybierz **OutputType** właściwości, a następnie wybierz **biblioteki klas**.  
  
3. Kliknij przycisk **Zastosuj**, a następnie kliknij przycisk **OK**.  
  
4. Otwórz ponownie **stron właściwości** okna dialogowego pole i sprawdź, czy zmiany zostały utrwalone.  
  
5. Zamknij wystąpienie doświadczalne programu Visual Studio.  
  
6. Otwórz ponownie wystąpienie eksperymentalne.  
  
7. Otwórz ponownie **stron właściwości** okna dialogowego pole i sprawdź, czy zmiany zostały utrwalone.  
  
8. Zamknij wystąpienie doświadczalne programu Visual Studio.  
  
   ![](../extensibility/media/simpproj2-proppage2.png "SimpProj2_PropPage2")
