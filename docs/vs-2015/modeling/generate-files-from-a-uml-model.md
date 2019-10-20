---
title: Generowanie plików z modelu UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, generating files
ms.assetid: 4e28b0e6-ce8f-45ee-9e3a-e4d600a0ad81
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 832dc3f7fea959ff4d2834aba921cd16f1117b5c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666149"
---
# <a name="generate-files-from-a-uml-model"></a>Generowanie plików na podstawie modelu UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Z modelu UML można generować kod programu, schematy, dokumenty, zasoby i inne artefakty dowolnego rodzaju. Jedną wygodną metodą generowania plików tekstowych z modelu UML jest użycie [szablonów tekstowych](../modeling/code-generation-and-t4-text-templates.md). Umożliwiają one osadzenie kodu programu wewnątrz tekstu, który ma zostać wygenerowany.

 Istnieją trzy główne scenariusze:

- [Generowanie plików za pomocą polecenia menu](#Command) lub gestu. Zdefiniuj [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] polecenie, które jest dostępne w modelach UML.

- [Generowanie plików z aplikacji](#Application). Napiszesz aplikację, która odczytuje modele UML i generuje pliki.

- [Generowanie w czasie projektowania](#Design). Model służy do definiowania niektórych funkcji aplikacji oraz generowania kodu, zasobów i tak dalej w ramach rozwiązania [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]owego.

  Ten temat zostaje zakończony z omówieniem [sposobu korzystania z generowania tekstu](#What). Aby uzyskać więcej informacji, zobacz sekcję [generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md).

## <a name="Command"></a>Generowanie plików za pomocą polecenia menu
 Możesz użyć wstępnie przetworzonych szablonów tekstowych w menu UML polecenia. W kodzie szablonu tekstu lub w oddzielnej klasie częściowej można odczytać model, który jest wyświetlany na diagramie.

 Aby uzyskać więcej informacji o tych funkcjach, przeczytaj następujące tematy:

- [Definiowanie polecenia menu w diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md)

- [Generowanie tekstu czasu wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md)

- [Nawigowanie po modelu UML](../modeling/navigate-the-uml-model.md)

  Podejście przedstawione w poniższym przykładzie jest odpowiednie do generowania tekstu z jednego modelu, po zainicjowaniu operacji z jednego z diagramów modelu. Aby przetworzyć model w osobnym kontekście, należy rozważyć użycie [programu Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md) , aby uzyskać dostęp do modelu i jego elementów.

### <a name="example"></a>Przykład
 Aby uruchomić ten przykład, należy utworzyć projekt rozszerzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (VSIX). Nazwa projektu użyta w tym przykładzie jest `VdmGenerator`. W pliku **source. Extension. vsixmanifest** kliknij pozycję **Dodaj zawartość** i Ustaw pole Typ na **MEF składnik** i ścieżkę źródłową odwołującą się do bieżącego projektu. Aby uzyskać więcej informacji na temat sposobu konfigurowania tego typu projektu, zobacz [Definiowanie polecenia menu na diagramie modelowania](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

 Dodaj do projektu C# plik zawierający poniższy kod. Ta klasa definiuje polecenie menu, które będzie wyświetlane na diagramie klas UML.

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

 Następujący plik jest szablonem tekstowym. Generuje wiersz tekstu dla każdej klasy UML w modelu i wiersz dla każdego atrybutu w każdej klasie. Kod służący do odczytywania modelu jest osadzony w tekście rozdzielonym przez `<# ... #>`.

 Aby utworzyć ten plik, kliknij prawym przyciskiem myszy projekt w Eksplorator rozwiązań, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**. Wybierz **Szablon wstępnie przetworzonych tekstu**. Nazwa pliku dla tego przykładu powinna być **VdmGen.tt**. Właściwość **niestandardowego narzędzia** pliku powinna być **TextTemplatingFilePreprocessor**. Aby uzyskać więcej informacji na temat wstępnie przetworzonych szablonów tekstowych, zobacz [Generowanie tekstu w czasie wykonywania przy użyciu szablonów tekstowych T4](../modeling/run-time-text-generation-with-t4-text-templates.md).

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

 Szablon tekstu generuje klasę C# częściową, która wchodzi w skład projektu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W osobnym pliku Dodaj kolejną deklarację częściową tej samej klasy. Ten kod zawiera szablon z dostępem do magazynu modeli UML:

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

 Aby przetestować projekt, naciśnij klawisz **F5**. Zostanie uruchomione nowe wystąpienie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. W tym przypadku Otwórz lub Utwórz model UML, który zawiera Diagram klas. Dodaj kilka klas do diagramu i Dodaj atrybuty do każdej klasy. Kliknij prawym przyciskiem myszy na diagramie, a następnie kliknij przykładowe polecenie `Generate VDM`. Polecenie tworzy plik `C:\Generated.txt`. Sprawdź ten plik. Jego zawartość powinna wyglądać podobnie do poniższego tekstu, ale zostanie wystawiona lista własnych klas i atrybutów:

```
Type Class1 ::
          Attribute1 : int
          Attribute2 : string
Type Class2 ::
          Attribute3 : string
```

## <a name="Application"></a>Generowanie plików z aplikacji
 Można generować pliki z aplikacji, która odczytuje model UML. W tym celu najbardziej elastyczną i niezawodną metodą uzyskiwania dostępu do modelu i jego elementów jest [Visual Studio ModelBus](../modeling/integrate-uml-models-with-other-models-and-tools.md).

 Możesz również użyć podstawowego interfejsu API do załadowania modelu i przekazać model do szablonów tekstowych przy użyciu tych samych technik jak w poprzedniej sekcji. Aby uzyskać więcej informacji na temat ładowania modelu, zobacz [Odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).

## <a name="Design"></a>Generowanie plików w czasie projektowania
 Jeśli projekt ma standardową metodę interpretacji UML jako kod, można utworzyć szablony tekstowe, które umożliwiają generowanie kodu w projekcie z modelu UML. Zwykle istnieje rozwiązanie, które zawiera projekt modelu UML, oraz jeden lub więcej projektów dla kodu aplikacji. Każdy projekt kodu może zawierać kilka szablonów, które generują kod programu, zasoby i pliki konfiguracji na podstawie zawartości modelu. Deweloper może uruchomić wszystkie szablony, klikając przycisk **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań. Kod programu jest zazwyczaj generowany w formie klas częściowych, aby ułatwić integrację części pisanych ręcznie.

 Projekt [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] tego rodzaju może być dystrybuowany w formie szablonu, dzięki czemu każdy członek zespołu może tworzyć projekty, które generują kod na podstawie modelu w ten sam sposób. Zazwyczaj szablon jest częścią pakietu rozszerzenia, który obejmuje ograniczenia walidacji w modelu, aby upewnić się, że spełniono warunki wstępne kodu generacji.

### <a name="outline-procedure-for-generating-files"></a>Procedura tworzenia konspektu dla generowania plików

- Aby dodać szablon do projektu, wybierz opcję **szablon tekstowy** w oknie dialogowym Dodaj nowy plik. Szablon można dodać do większości typów projektu, ale nie do projektów modelowania.

- Właściwość narzędzi niestandardowych pliku szablonu powinna mieć wartość **TextTemplatingFileGenerator**, a rozszerzenie nazwy pliku powinno być TT.

- Szablon powinien mieć co najmniej dyrektywę wyjściową:

     `<#@ output extension=".cs" #>`

     Ustaw pole rozszerzenia zgodnie z językiem projektu.

- Aby zezwolić na generowanie kodu w szablonie w celu uzyskania dostępu do modelu, należy napisać `<#@ assembly #>` dyrektywy dla zestawów wymaganych do odczytania modelu UML. Użyj `ModelingProject.LoadReadOnly()`, aby otworzyć model. Aby uzyskać więcej informacji, zobacz [Odczytywanie modelu UML w kodzie programu](../modeling/read-a-uml-model-in-program-code.md).

- Szablon jest wykonywany po jego zapisaniu i kliknięciu przycisku **Przekształć wszystkie szablony** na pasku narzędzi Eksplorator rozwiązań.

- Aby uzyskać więcej informacji na temat tego typu szablonu, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

- W typowym projekcie będziesz mieć kilka szablonów, które generują różne pliki z tego samego modelu. Pierwsza część każdego szablonu będzie taka sama. Aby zmniejszyć to duplikowanie, Przenieś typowe części do oddzielnego pliku tekstowego, a następnie Wywołaj je za pomocą dyrektywy `<#@include file="common.txt"#>` we wszystkich szablonach.

- Można również zdefiniować wyspecjalizowany procesor dyrektywy, który umożliwia podanie parametrów dla procesu generowania tekstu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie transformacji tekstu T4](../modeling/customizing-t4-text-transformation.md).

### <a name="example"></a>Przykład
 Ten przykład generuje C# klasę dla każdej klasy UML w modelu źródłowym.

##### <a name="to-set-up-a-visual-studio-solution-for-this-example"></a>Aby skonfigurować rozwiązanie Visual Studio na potrzeby tego przykładu

1. Utwórz Diagram klas UML w projekcie modelowania w nowym rozwiązaniu.

   1. W menu **Architektura** kliknij pozycję **Nowy diagram**.

   2. Wybierz **Diagram klas UML**.

   3. Postępuj zgodnie z monitami, aby utworzyć nowe rozwiązanie i projekt modelowania.

   4. Dodaj kilka klas do diagramu, przeciągając narzędzie klasy UML z przybornika.

   5. Zapisz plik.

2. Utwórz projekt C# lub Visual Basic w tym samym rozwiązaniu.

   - W Eksplorator rozwiązań kliknij prawym przyciskiem myszy rozwiązanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Nowy projekt**. W obszarze **zainstalowane szablony**kliknij pozycję **Visual Basic** lub  **C#Wizualizacja,** a następnie wybierz typ projektu, na przykład **Aplikacja konsolowa**.

3. Dodaj zwykły plik tekstowy do projektu C# lub Visual Basic. Ten plik będzie zawierać kod, który jest współużytkowany, jeśli chcesz napisać kilka szablonów tekstowych.

   - W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**. Wybierz pozycję **plik tekstowy**.

     Wstaw tekst, który jest wyświetlany w poniższej sekcji.

4. Dodaj plik szablonu tekstu do projektu C# lub Visual Basic.

   - W Eksplorator rozwiązań kliknij prawym przyciskiem myszy projekt, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **nowy element**. Wybierz pozycję **szablon tekstowy**.

     Wstaw kod, który następuje po pliku szablonu tekstu.

5. Zapisz plik szablonu tekstu.

6. Sprawdź kod w pliku pomocniczym. Powinna zawierać klasę dla każdej klasy UML w modelu.

   1. W projekcie Visual Basic kliknij pozycję **Pokaż wszystkie pliki** na Eksplorator rozwiązań pasku narzędzi.

   2. Rozwiń węzeł plik szablonu w Eksplorator rozwiązań.

#### <a name="content-of-the-shared-text-file"></a>Zawartość udostępnionego pliku tekstowego
 W tym przykładzie plik ma nazwę SharedTemplateCode. txt i znajduje się w tym samym folderze co szablony tekstowe.

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
 Następujący tekst jest umieszczany w pliku **TT** . Ten przykład generuje klasy w C# pliku z klas UML w modelu. Można jednak generować pliki dowolnego typu. Język wygenerowanego pliku nie jest powiązany z językiem, w którym napisano kod szablonu tekstu.

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

## <a name="What"></a>Jak używać generowania tekstu
 Rzeczywista moc modelowania jest uzyskiwana w przypadku używania modeli do projektowania na poziomie wymagań lub architektury. Za pomocą szablonów tekstowych można wykonać kilka zadań związanych z konwertowaniem pomysłów wysokiego poziomu na kod. W wielu przypadkach nie prowadzi to do relacji jeden-do-jednego między elementami w modelach i klasach UML lub innymi częściami kodu programu.

 Ponadto transformacja zależy od domeny problemu. nie istnieje uniwersalne mapowanie między modelami i kodem.

 Oto kilka przykładów generowania kodu z modeli:

- **Linie produktów**. Firma Fabrikam, Inc. kompiluje i instaluje systemy obsługi bagażu na lotnisku. Większość oprogramowania jest bardzo podobna między jedną instalacją i następnym, ale konfiguracja oprogramowania zależy od tego, w jaki sposób zainstalowano maszyny obsługujące torby oraz jak te części są połączone przez pasy taśmowe. Na początku kontraktu analityków firmy Fabrikam omawiają wymagania związane z zarządzaniem lotniskami oraz przechwytują plan sprzętu przy użyciu diagramu aktywności UML. Z tego modelu zespół programistyczny generuje pliki konfiguracji, kod programu, plany i dokumenty użytkownika. Ukończą pracę dzięki ręcznym dodatkom i korektom kodu. Gdy uzyskują one doświadczenie z jednego zadania, zwiększają zakres wygenerowanego materiału.

- **Wzorce**. Deweloperzy w contoso, Ltd często kompilują witryny sieci Web i projektują schemat nawigacyjny za pomocą diagramów klas UML. Każda Strona sieci Web jest reprezentowana przez klasę, a skojarzenia reprezentują linki nawigacji. Deweloperzy generują wiele kodów witryny sieci Web z modelu. Każda Strona sieci Web odpowiada kilku klasom i wpisom plików zasobów.  Ta metoda ma zalety, aby konstrukcja każdej strony była zgodna z pojedynczym wzorcem, co sprawia, że jest bardziej niezawodna i elastyczna niż kod pisany ręcznie. Wzorzec znajduje się w szablonach generowania, natomiast model jest używany do przechwytywania aspektów zmiennych.

- **Schematy**. Ubezpieczenie Humongous ma tysiące systemów na całym świecie. Te systemy używają różnych baz danych, języków i interfejsów. Zespół architektury centralnej publikuje wewnętrznie modele koncepcji i procesów firmy. W tych modelach zespoły lokalne generują części bazy danych i schematów wymiany, deklaracje w kodzie programu i tak dalej. Graficzna Prezentacja modeli pomaga zespołom omawiać propozycje. Zespoły tworzą wiele diagramów, które pokazują podzbiory modelu, które mają zastosowanie do różnych obszarów działalności. Używają one również koloru do wyróżniania obszarów podlegających zmianom.

## <a name="important-techniques-for-generating-artifacts"></a>Ważne techniki generowania artefaktów
 W poprzednich przykładach modele są używane w różnych celach zależnych od firmy, a interpretacja elementów modelowania, takich jak klasy i działania, różni się od jednej aplikacji do innej. Poniższe techniki są przydatne podczas generowania artefaktów z modeli.

- **Profile**. Nawet w ramach jednego obszaru biznesowego interpretacja typu elementu może się różnić. Na przykład na diagramie witryny sieci Web niektóre klasy mogą reprezentować strony sieci Web, a inne reprezentują bloki zawartości. Aby ułatwić użytkownikom rejestrowanie tych rozróżnień, zdefiniuj stereotypy. Stereotypy umożliwiają również dołączanie dodatkowych właściwości, które mają zastosowanie do elementów tego rodzaju. Stereotypy są spakowane w obrębie profilów. Aby uzyskać więcej informacji, zobacz [Definiowanie profilu do rozszerania UML](../modeling/define-a-profile-to-extend-uml.md).

     W kodzie szablonu można łatwo uzyskać dostęp do stereotypów, które są zdefiniowane dla obiektu. Na przykład:

    ```
    public bool HasStereotype(IClass c, string profile, string stereo)
    { return c.AppliedStereotypes.Any
       (s => s.Profile == profile && s.Name == stereo ); }
    ```

- **Modele ograniczone**. Nie wszystkie modele, które można utworzyć, są prawidłowe dla każdego celu. Na przykład w modelach bagażu lotniskowego firmy Fabrikam może być on niewłaściwy do zaewidencjonowania bez przenośnika wychodzącego. Można zdefiniować funkcje sprawdzania poprawności, które ułatwiają użytkownikom przestrzeganie tych ograniczeń. Aby uzyskać więcej informacji, zobacz [Definiowanie ograniczeń walidacji dla modeli UML](../modeling/define-validation-constraints-for-uml-models.md).

- **Zachowaj zmiany ręcznie**. Z modelu można generować tylko niektóre pliki rozwiązań. W większości przypadków musisz mieć możliwość ręcznego dodawania lub dostosowywania wygenerowanej zawartości. Należy jednak pamiętać, że te zmiany ręczne należy zachować, gdy przekształcenie szablonu zostanie uruchomione ponownie.

     Gdzie szablony generują kod w [!INCLUDE[TLA2#tla_net](../includes/tla2sharptla-net-md.md)] językach, powinny generować klasy częściowe, aby deweloperzy mogli dodawać metody i kod. Przydatne jest również generowanie każdej klasy jako pary: abstrakcyjnej klasy bazowej zawierającej metody i klasy dziedziczenia, która zawiera tylko Konstruktor. Dzięki temu deweloperzy mogą zastępować metody. Aby zezwolić na zastąpienie inicjalizacji, należy wykonać w osobnej metodzie, a nie w konstruktorach.

     Gdzie szablon generuje XML i inne typy danych wyjściowych, może być trudniejsze, aby zachować ręczną zawartość niezależnie od wygenerowanej zawartości. Jedną z metod jest utworzenie zadania w procesie kompilacji, który łączy dwa pliki. Inna metoda polega na tym, aby deweloperzy mogli dostosować lokalną kopię generowanego szablonu.

- **Przenieś kod do oddzielnych zestawów**. Nie zalecamy pisania dużych treści kodu w szablonach. Zalecane jest zachowywanie wygenerowanej zawartości niezależnie od obliczeń, a szablony tekstowe nie są dobrze obsługiwane do edycji kodu.

     Zamiast tego, jeśli konieczne jest wykonanie znaczących obliczeń w celu wygenerowania tekstu, skompiluj te funkcje w osobnym zestawie i wywołaj metody z szablonu.
