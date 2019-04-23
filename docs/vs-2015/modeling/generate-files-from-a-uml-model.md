---
title: Generowanie plików z modelu UML | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0d58a8b98cb27527f3d4c464119fb5543f88e8ed
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60088980"
---
# <a name="generate-files-from-a-uml-model"></a>Generowanie plików na podstawie modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z modelu UML można wygenerować kodu programu, schematów, dokumenty, zasobów i innych artefaktów wszelkiego rodzaju. Wygodna metoda Generowanie plików tekstowych na podstawie modelu UML jest użycie [szablonów tekstowych](../modeling/code-generation-and-t4-text-templates.md). Pozwalają one na program kod wewnątrz tekst, który chcesz wygenerować osadzania.  
  
 Istnieją trzy główne scenariusze:  
  
- [Generowanie plików z polecenia menu](#Command) lub gestu. Należy zdefiniować [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] polecenia, które są dostępne w modelach UML.  
  
- [Generowanie plików z aplikacji](#Application). Piszesz aplikację, która odczytuje modeli UML i generuje pliki.  
  
- [Generowanie w czasie projektowania](#Design). Korzystają z modelu do zdefiniowania, niektóre funkcje aplikacji i generowania kodu, zasoby, i tak dalej w ramach Twojej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania.  
  
  W tym temacie kończy się wraz z omówieniem [sposób używania Generowanie tekstu](#What). Aby uzyskać więcej informacji, zobacz [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).  
  
## <a name="Command"></a> Generowanie plików z polecenia menu  
 Możesz użyć wstępnie Przetwórz szablony tekstowe w ramach polecenia menu UML. W ramach kodu szablonu tekstu lub w osobnej klasy częściowej może odczytywać modelu, które są wyświetlane przez diagram.  
  
 Aby uzyskać więcej informacji o tych funkcjach przeczytaj następujące tematy:  
  
- [Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)  
  
- [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)  
  
- [Nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md)  
  
  To podejście pokazano w poniższym przykładzie jest odpowiednia do generowania tekstu z jednym modelu, po zainicjowaniu operacji z jednego na diagramach modelu. Do przetwarzania modelu w kontekście oddzielne, należy wziąć pod uwagę przy użyciu [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md) dostęp do modelu i jego elementów.  
  
### <a name="example"></a>Przykład  
 Aby uruchomić ten przykład, utworzyć [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu rozszerzenia (VSIX). Nazwa projektu, który jest używany w tym przykładzie jest `VdmGenerator`. W **source.extension.vsixmanifest** plików, kliknij **Dodaj zawartość** i ustawić pole typu **składnik MEF** i ścieżki źródłowej, które odwołuje się do bieżącego projektu. Aby uzyskać więcej informacji na temat sposobu konfigurowania tego typu projektu, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).  
  
 Dodaj do projektu plik C#, która zawiera następujący kod. Ta klasa definiuje polecenie menu, które będą wyświetlane na diagramie klas UML.  
  
```  
using System;  
using System.ComponentModel.Composition;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Presentation;  
using Microsoft.VisualStudio.Modeling.ExtensionEnablement;  
  
namespace VdmGenerator  
{  
  [Export(typeof(ICommandExtension))]  
  [ClassDesignerExtension]  
  public class GenerateVdmFromClasses : ICommandExtension  
  {  
    [Import] public IDiagramContext DiagramContext { get; set; }  
    public void Execute(IMenuCommand command)  
    {  
      // Initialize the template with the Model Store.  
      VdmGen generator = new VdmGen(  
             DiagramContext.CurrentDiagram.ModelStore);  
      // Generate the text and write it.  
      System.IO.File.WriteAllText  
        (System.IO.Path.Combine(  
            Environment.GetFolderPath(  
                Environment.SpecialFolder.Desktop),  
            "Generated.txt")   
         , generator.TransformText());  
    }  
    public void QueryStatus(IMenuCommand command)  
    {  
      command.Enabled = command.Visible = true;  
    }  
    public string Text  
    { get { return "Generate VDM"; } }  
  }  
}  
```  
  
 Następujący plik jest szablonu tekstu. Generuje wiersza tekstu dla każdej klasy UML w modelu i jeden wiersz dla każdego atrybutu w każdej klasie. Kod do odczytu, model jest osadzony w tekście, rozdzielone `<# ... #>`.  
  
 Aby utworzyć ten plik, kliknij prawym przyciskiem myszy projekt w Eksploratorze rozwiązań, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy element**. Wybierz **wstępnie przetworzony szablon tekstu**. Nazwa pliku, w tym przykładzie powinna być **VdmGen.tt**. **Narzędzie niestandardowe** właściwość pliku powinna być **TextTemplatingFilePreprocessor**. Aby uzyskać więcej informacji na temat szablonów tekstu wstępnie przetworzony zobacz [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).  
  
```  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#   
   foreach (IClass classElement in store.AllInstances<IClass>())   {  
#>  
Type <#= classElement.Name #> ::  
<#  
     foreach (IProperty attribute in classElement.OwnedAttributes)     {  
#>  
       <#= attribute.Name #> : <#=   
           attribute.Type == null ? ""  
                                  : attribute.Type.Name #>   
<#  
     }   }  
#>  
```  
  
 Szablon tekstowy generuje C# częściowe klasy, która staje się częścią z Twojej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. W oddzielnym pliku należy dodać inna częściowa deklaracja tego samego rodzaju. Ten kod zawiera szablon z dostępem do magazyn modeli UML:  
  
```  
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;  
namespace VdmGenerator  
{  
    public partial class VdmGen  
    {  
        private IModelStore store;  
        public VdmGen(IModelStore s)  
        { store = s; }  
    }  
}  
```  
  
 Aby przetestować projekt, naciśnij klawisz **F5**. Nowe wystąpienie klasy [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zostanie uruchomiona. W tym wypadku Otwórz lub Utwórz model UML, który zawiera diagram klas. Dodaj kilka klas do diagramu, a następnie dodać niektóre atrybuty do każdej klasy. Kliknij prawym przyciskiem myszy na diagramie, a następnie kliknij przycisk przykładowe polecenie `Generate VDM`. Polecenie tworzy plik `C:\Generated.txt`. Sprawdź, czy ten plik. Jego zawartość powinna przypominać następujący tekst, ale spowoduje wyświetlenie listy własnych klas i atrybutów:  
  
```  
Type Class1 ::  
          Attribute1 : int   
          Attribute2 : string   
Type Class2 ::   
          Attribute3 : string   
```  
  
## <a name="Application"></a> Generowanie plików z aplikacji  
 Można wygenerować plików z aplikacji, która odczytuje modelu UML. W tym celu jest najbardziej elastyczna i niezawodna metoda uzyskiwania dostępu do modelu i jego elementy [Visual Studio Modelbus](../modeling/integrate-uml-models-with-other-models-and-tools.md).  
  
 Można również użyć podstawowa interfejsu API można załadować modelu i przekazać model do szablonów tekstowych przy użyciu tych samych technik, tak jak w poprzedniej sekcji. Aby uzyskać więcej informacji na temat ładowania modelu, zobacz [odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).  
  
## <a name="Design"></a> Generowanie plików w czasie projektowania  
 Jeśli projekt ma standardową metodę interpretowanie UML w kodzie, można utworzyć szablony tekstowe, które umożliwiają generowanie kodu w obrębie projektu na podstawie modelu UML. Zazwyczaj trzeba rozwiązania zawierającego projekt modelu UML i jeden lub więcej projektów dla kodu aplikacji. Każdy projekt kodu może zawierać kilka szablonów, które generują pliki kodu, zasoby i konfiguracji programu, na podstawie zawartości modelu. Deweloper może uruchomić wszystkie szablony, klikając **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań. W formularzu klas częściowych, ułatwia integrowanie zapisywane ręczne części zwykle generowania kodu programu.  
  
 A [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu tego typu mogą być dystrybuowane w postaci szablonu, tak, aby każdy członek zespołu mógł tworzyć projekty, które generują kod z modelu w taki sam sposób. Zazwyczaj szablonu jest częścią pakietu rozszerzenia, obejmującą ograniczenia sprawdzania poprawności na modelu w celu zapewnienia, że zostały spełnione warunki wstępne generowania kodu.  
  
### <a name="outline-procedure-for-generating-files"></a>Konspekt procedury generowania plików  
  
- Aby dodać szablon do projektu, wybierz pozycję **szablonu tekstu** w oknie dialogowym Dodaj nowy plik. Można dodać szablon do większości typów projektu, ale nie do modelowania projektów.  
  
- Właściwości niestandardowe narzędzia plik szablonu powinien być **TextTemplatingFileGenerator**, i rozszerzenie nazwy pliku powinno być .tt.  
  
- Szablon powinien zawierać co najmniej dyrektywa wyjściowa:  
  
     `<#@ output extension=".cs" #>`  
  
     Ustaw pole rozszerzenia zgodnie z językiem Twojego projektu.  
  
- Aby umożliwić generowanie kodu w szablonie dostępu do modelu, należy napisać `<#@ assembly #>` dyrektywy dla zestawów wymaganych do odczytania modelu UML. Użyj `ModelingProject.LoadReadOnly()` można otworzyć modelu. Aby uzyskać więcej informacji, zobacz [odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).  
  
- Szablon jest wykonywany, gdy zapisujesz go, a po kliknięciu **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań.  
  
- Aby uzyskać więcej informacji na temat tego typu szablonu, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).  
  
- W typowym projekcie masz kilka szablonów, które generują różne pliki z tego samego modelu. Pierwsza część każdy szablon będą takie same. Aby zmniejszyć takie duplikowanie, Przenieś części wspólnej do oddzielnego pliku tekstowego, a następnie wywołaj ją przy użyciu dyrektywy `<#@include file="common.txt"#>` w każdym szablonie.  
  
- Można również zdefiniować specjalne procesor dyrektywy, która umożliwia dostarczanie parametry, aby proces generowania tekstu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie przekształcenia tekstu T4](../modeling/customizing-t4-text-transformation.md).  
  
### <a name="example"></a>Przykład  
 Ten przykład generuje klasy C# dla każdej klasy UML w modelu źródłowym.  
  
##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Aby skonfigurować rozwiązania programu Visual Studio, w tym przykładzie  
  
1. Utwórz diagram klas UML w projekcie modelowania w nowym rozwiązaniu.  
  
   1. W **architektury** menu, kliknij przycisk **nowy Diagram**.  
  
   2. Wybierz **Diagram klas UML**.  
  
   3. Postępuj zgodnie z monitami, aby utworzyć nowy projekt rozwiązania i modelowanie.  
  
   4. Dodaj niektórych klas do diagramu, przeciągając narzędzie klasy UML z przybornika.  
  
   5. Zapisz plik.  
  
2. Utwórz projekt C# lub Visual Basic, w tym samym rozwiązaniu.  
  
   - W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy projekt**. W obszarze **zainstalowane szablony**, kliknij przycisk **języka Visual Basic** lub **Visual C#,** a następnie wybierz typ projektu, takich jak **aplikację Konsolową**.  
  
3. Dodaj plik zwykłego tekstu, C# lub projekcie Visual Basic. Ten plik będzie zawierać kod, który jest udostępniany, jeśli chcesz napisać kilka szablonów tekstu.  
  
   - W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy element**. Wybierz **plik tekstowy**.  
  
     Wstaw tekst, który jest wyświetlany w poniższej sekcji.  
  
4. Dodaj plik szablonu tekstu, C# lub projekcie Visual Basic.  
  
   - W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż opcję **Dodaj**, a następnie kliknij przycisk **nowy element**. Wybierz **szablonu tekstu**.  
  
     Wstaw kod, znajdujący się w pliku szablonu tekstu.  
  
5. Zapisz plik szablonu tekstu.  
  
6. Sprawdź, czy kod w pliku zależnego. Powinien zawierać klasę dla każdej klasy UML w modelu.  
  
   1. W projekcie języka Visual Basic, kliknij przycisk **Pokaż wszystkie pliki** na pasku narzędzi Eksploratora rozwiązań.  
  
   2. Rozwiń węzeł pliku szablonu w Eksploratorze rozwiązań.  
  
#### <a name="content-of-the-shared-text-file"></a>Zawartość pliku tekstowego udostępnionego  
 W tym przykładzie plik nosi nazwę SharedTemplateCode.txt, a w tym samym folderze, co szablonów tekstowych.  
  
```  
<# /* Common material for inclusion in my model templates */ #>  
<# /* hostspecific allows access to the Visual Studio API */ #>  
<#@ template debug="false" hostspecific="true" language="C#" #>  
<#@ assembly name="Microsoft.VisualStudio.Uml.Interfaces.dll"#>  
<#@ assembly name="Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll"#>  
<#@ assembly name="EnvDTE" #>  
<#@ import namespace="Microsoft.VisualStudio.Uml.Classes" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility" #>  
<#@ import namespace="Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml" #>  
<#+  // Note this is a Class Feature Block  
///<summary>  
/// Text templates are run in a common AppDomain, so   
/// we can cache the model store that we find.  
///</summary>  
private IModelStore StoreCache  
{  
  get { return AppDomain.CurrentDomain.GetData("ModelStore") as IModelStore; }  
  set { AppDomain.CurrentDomain.SetData("ModelStore", value); }   
}  
private bool CacheIsOld()  
{  
    DateTime? dt = AppDomain.CurrentDomain  
           .GetData("latestAccessTime") as DateTime?;  
    DateTime t = dt.HasValue ? dt.Value : new DateTime();   
    DateTime now = DateTime.Now;  
    AppDomain.CurrentDomain.SetData("latestAccessTime", now);  
    return now.Subtract(t).Seconds > 3;  
}  
  
///<summary>  
/// Find the UML modeling project in this solution,  
/// and load the model.  
///</summary>  
private IModelStore ModelStore  
{  
  get   
  {  
    // Avoid loading the model for every template:  
    if (StoreCache == null || CacheIsOld())  
    {  
      // Use Visual Studio API to find modeling project:  
      EnvDTE.DTE dte = (EnvDTE.DTE) ((IServiceProvider) this.Host)  
                       .GetService(typeof(EnvDTE.DTE));  
      EnvDTE.Project project = null;  
      foreach (EnvDTE.Project p in dte.Solution.Projects)  
      {  
        if (p.FullName.EndsWith(".modelproj"))  
        {  
          project = p;  
          break;  
        }              
      }  
      if (project == null) return null;  
  
      // Load UML model into this AppDomain  
      // and access model store:  
      IModelingProjectReader reader =   
           ModelingProject.LoadReadOnly(project.FullName);  
      StoreCache = reader.Store;  
    }  
    return StoreCache;  
  }  
}  
#>  
```  
  
#### <a name="content-of-the-text-template-file"></a>Zawartość pliku szablonu tekstu  
 Poniższy tekst znajduje się w **.tt** pliku. Ten przykład generuje klasy w pliku C# z klas UML w modelu. Jednakże można wygenerować pliki dowolnego typu. Język wygenerowany plik nie jest powiązany dla języka, w którym napisano kod szablonu tekstu.  
  
```  
<#@include file="SharedTemplateCode.txt"#>  
<#@ output extension=".cs" #>  
namespace Test{  
<#  
      foreach (IClass c in ModelStore.AllInstances<IClass>())  
      {  
#>  
   public partial class <#=c.Name#>  
   {   }  
<#  
      }  
#>  
}  
```  
  
## <a name="What"></a> Jak używać Generowanie tekstu  
 Rzeczywista siła modelowania są uzyskiwane podczas używać modeli do projektowania na poziomie wymagania lub architektury. Do wykonania niektórych prac przekształcania wysokiego poziomu pomysłów w kod, można użyć szablonów tekstowych. W wielu przypadkach to nie prowadzi do relację między elementami w modelach UML i klas lub inne części kodu programu.  
  
 Ponadto transformacja jest zależna od domeny problem; nie istnieje uniwersalne mapowania między modelami i kodu.  
  
 Poniżej przedstawiono kilka przykładów generowanie kodu z modeli:  
  
- **Linie produktów**. Fabrikam, Inc. tworzy i instaluje bagażu Kuwejcie obsługi systemów. Większość oprogramowania jest bardzo podobne w elemencie jednej instalacji, a następnie, ale konfiguracja oprogramowania zależy od zainstalowano pakiet, jakie obsługi maszyn i jak te elementy są ze sobą połączone przez poziome. Na początku umowy analityków firmy Fabrikam omówienia ich wymagań za pomocą funkcji zarządzania lotniska i przechwytywania plan sprzętu przy użyciu diagram aktywności UML. Z tego modelu zespół opracowujący generuje pliki konfiguracji, kod programu, plany i dokumenty użytkownika. Wykonywania pracy przez ręczne dodatki i zmiany w kodzie. Zgodnie z ich zdobycia doświadczenia z jednego zadania do następnego, mogą rozszerzyć zakres wygenerowanego materiału.  
  
- **Wzorce**. Często deweloperzy firmy Contoso, Ltd tworzenie witryn sieci Web i projektowanie schematu nawigacji za pomocą diagramów klas UML. Każda strona sieci Web jest reprezentowane przez klasę, a asocjacje reprezentują łącza nawigacji. Deweloperzy Generowanie większość kodu witryny sieci Web z modelu. Każda strona sieci Web odpowiada różne klasy i we wpisach w plikach zasobów.  Ta metoda zapewnia korzyści, które konstrukcji każdej strony jest zgodny z jednym wzorcu bardziej niezawodne i elastyczne niż ręcznie napisany kod, dzięki czemu. Wzorzec jest generowanie szablonów, podczas gdy model jest używany do przechwytywania zmiennej aspektów.  
  
- **Schematy**. Agencji ubezpieczeniowej ma tysięcy systemów na całym świecie. Te systemy używają różnych baz danych, języków i interfejsy. Zespół centralnej architektury wewnętrznie publikuje modele biznesowe pojęć i procesów. Z tych modeli lokalnych zespoły Generowanie części swoje schematy bazy danych i wymiany, deklaracji w kodzie programu i tak dalej. Graficzną reprezentację modele pomaga zespołom omówić propozycję. Zespoły tworzą wiele diagramów przedstawiających podzestawy modelu, które są stosowane do poszczególnych obszarów działalności. Również używają kolor Wyróżnianie obszarów, które mogą ulec zmianie.  
  
## <a name="important-techniques-for-generating-artifacts"></a>Ważne technik do generowania artefaktów  
 W poprzednich przykładach modele są używane do różnych celów biznesowych — zależnych od ustawień lokalnych i interpretację modelowania elementów, takich jak klas i działań różni się w jednej aplikacji do innej. Następujące techniki są przydatne podczas generowania artefaktów z modeli.  
  
- **Profile**. Nawet w ramach obszar działalności jeden interpretacja typu elementu może się różnić. Na przykład na diagramie witryny sieci Web niektóre klasy może reprezentować stron sieci Web, a inne reprezentują bloki zawartości. Aby ułatwić użytkownikom zarejestrować te różnice zdefiniować stereotypy. Stereotypy również umożliwiać można dołączyć dodatkowe właściwości, które mają zastosowanie do elementów tego typu. Stereotypy są spakowane w obrębie profilów. Aby uzyskać więcej informacji, zobacz [Definiowanie profilu w celu rozszerzenia UML](../modeling/define-a-profile-to-extend-uml.md).  
  
     W kodzie szablonu jest łatwy dostęp stereotypów, które są zdefiniowane dla obiektu do. Na przykład:  
  
    ```  
    public bool HasStereotype(IClass c, string profile, string stereo)  
    { return c.AppliedStereotypes.Any  
       (s => s.Profile == profile && s.Name == stereo ); }  
    ```  
  
- **Ograniczone modeli**. Nie wszystkie modele, które można utworzyć są prawidłowe dla każdego celu. Na przykład w modelach bagażu Kuwejcie Fabrikam, byłoby niepoprawne mieć technicznej ewidencjonowania bez wychodzących taśmy. Można zdefiniować funkcje sprawdzania poprawności, które pomagają użytkownikom do przestrzegania tych warunków ograniczających. Aby uzyskać więcej informacji, zobacz [definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).  
  
- **Zachowaj ręczne zmiany**. Tylko niektóre pliki rozwiązania mogą być generowane z modelu. W większości przypadków musisz być w stanie dodać lub dostosować zawartość jest generowana ręcznie. Jest ważne, że te zmiany ręcznej powinny zostać zachowane podczas przekształcania szablonu po ponownym uruchomieniu.  
  
     Gdzie szablonów generowania kodu w [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] języków, powinien wygenerować klas częściowych, tak aby deweloperzy mogą dodawać metody i kodu. Jest to również przydatne do generowania każdej klasy jako para: abstrakcyjną klasę bazową, która zawiera metody i klasy dziedziczącej, która zawiera tylko Konstruktor. Dzięki temu deweloperzy zastąpienia metody. Aby zezwolić na inicjowanie do zastąpienia, jego odbywa się w oddzielnych metodach zamiast w konstruktorach.  
  
     W przypadku, gdy szablon generuje XML i innych typów danych wyjściowych, może być trudniejsze być oddzielone od zawartość jest generowana ręczne zawartości. Jedną z metod jest tworzenie zadania w procesie kompilacji, który łączy dwa pliki. Inną metodą jest dla deweloperów dopasować lokalną kopię generowania szablonu.  
  
- **Przenieś kod do oddzielnych zestawów**. Nie zaleca się zapisywania duże jednostki kodu w szablonach. Zaleca się zachować zawartość jest generowana oddzielnie od obliczania i szablony tekstowe nie są również obsługiwane edycji kodu.  
  
     Zamiast tego w przypadku wykonywania obliczeń istotne, aby wygenerować tekst tworzyć te funkcje w osobny zestaw i wywołać jego metody z szablonu.
