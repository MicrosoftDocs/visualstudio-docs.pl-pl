---
title: Użyj ModelBus w szablonie tekstu
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9324c33e383029fa6f98a9b890309cc0a11eb95d
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226271"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Użycie programu Visual Studio ModelBus w szablonie tekstu

Jeśli piszesz szablony tekstowe, które odczytują modelu, który zawiera odwołania Visual Studio ModelBus, możesz chcieć rozpoznawania odwołań, aby uzyskiwać dostęp do modeli docelowego. W takim przypadku konieczne będzie dostosowywać szablony tekstowe i odwołania języków specyficznych dla domeny (językami DSL):

- Język DSL, który jest elementem docelowym odwołania musi mieć kartę ModelBus, który jest skonfigurowany dla dostępu z poziomu szablonów tekstu. Jeśli język DSL jest również dostęp z innego kodu, ponownie skonfigurowane jest wymagana karta oprócz standardowej karty ModelBus.

     Menedżera adapterów musi dziedziczyć <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager> i muszą mieć atrybut `[HostSpecific(HostName)]`.

- Szablon musi dziedziczyć <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

> [!NOTE]
> Jeśli chcesz odczytać DSL modeli, które nie zawierają odwołań ModelBus, można użyć procesorów dyrektyw, które są generowane w projektach języka DSL. Aby uzyskać więcej informacji, zobacz [uzyskiwania dostępu do modeli z poziomu szablonów tekstu](../modeling/accessing-models-from-text-templates.md).

Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Tworzenie karty magistrali modelu dla dostępu z poziomu szablonów tekstu

Aby rozwiązać odwołanie ModelBus w szablonie tekstu, docelowy DSL musi mieć kartę zgodne. Szablonów tekstowych wykonywania w oddzielnym elemencie AppDomain z edytorów dokumentu programu Visual Studio i w związku z tym karta ma można załadować modelu zamiast uzyskiwanie do niej dostępu za pośrednictwem obiektu DTE.

1. Jeśli nie ma docelowej rozwiązania DSL **elementu ModelBusAdapter** projektu, należy go utworzyć za pomocą Kreatora Modelbus rozszerzenia:

    1. Pobierz i zainstaluj rozszerzenia programu Visual Studio ModelBus, jeśli użytkownik jeszcze nie zostało to zrobione. Aby uzyskać więcej informacji, zobacz [wizualizacji i modelowania SDK](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij przycisk **Włącz Modelbus**.

    3. W oknie dialogowym wybierz **chcę, aby udostępnić tego języka DSL do ModelBus**. Można wybrać obu opcji, jeśli chcesz, aby tego języka DSL, aby uwidocznić jej modeli i korzystanie z odwołań do innych języków DSL.

    4. Kliknij przycisk **OK**. Nowy projekt "Elementu ModelBusAdapter" jest dodawany do rozwiązania DSL.

    5. Kliknij przycisk **Transformuj wszystkie szablony**.

    6. Ponownie skompiluj rozwiązanie.

2. Jeśli chcesz uzyskać dostęp do język DSL, zarówno z szablonu tekstu i innego kodu, takich jak polecenia zduplikowane **elementu ModelBusAdapter** projektu:

    1. W Eksploratorze Windows skopiuj i Wklej folder, który zawiera **ModelBusAdapter.csproj**.

    2. Zmień nazwę pliku projektu (na przykład, aby **T4ModelBusAdapter.csproj**).

    3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż **Dodaj**, a następnie kliknij przycisk **istniejący projekt**. Zlokalizuj nowy projekt karty **T4ModelBusAdapter.csproj**.

    4. W każdym `*.tt` pliku nowego projektu Zmienianie przestrzeni nazw.

    5. Kliknij prawym przyciskiem myszy nowy projekt w **Eksploratora rozwiązań** a następnie kliknij przycisk **właściwości**. W edytorze właściwości można zmienić nazwy wygenerowanego zestawu i domyślny obszar nazw.

    6. W projekcie DslPackage Dodaj odwołanie do nowego projektu karty, tak, że ma odwołania do obu kart.

    7. W DslPackage\source.extension.tt Dodaj wiersz, który odwołuje się do nowego projektu karty.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Transformuj wszystkie szablony** i ponownie skompiluj rozwiązanie. Powinien wystąpić żadne błędy kompilacji.

3. W nowym projekcie adaptera należy dodać odwołania do następujących zestawów:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. W AdapterManager.tt:

    - Zmień deklarację elementu AdapterManagerBase, tak aby dziedziczył z <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>.

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Pod koniec pliku Zastąp atrybut HostSpecific przed klasy adaptermanager obsługującego element. Usuń następujący wiersz:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Wstaw następujący wiersz:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Ten atrybut służy do przefiltrowania zestaw kart sieciowych, który jest dostępny, gdy konsument modelbus wyszukuje karty.

5. **Transformuj wszystkie szablony** i ponownie skompiluj rozwiązanie. Powinien wystąpić żadne błędy kompilacji.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Pisanie szablonu tekstu, który może rozpoznać odwołania ModelBus

Zazwyczaj Rozpocznij od szablonu, który odczytuje i generuje pliki z "źródło" DSL. Ten szablon używa dyrektywy, który jest generowany w projekcie języka DSL źródło do odczytu źródła plików modelu w sposób opisany w [uzyskiwania dostępu do modeli z poziomu szablonów tekstu](../modeling/accessing-models-from-text-templates.md). Jednak źródło DSL zawiera ModelBus odwołania do "target" DSL. W związku z tym chcesz włączyć kod szablonu do rozpoznawania odwołań i dostępu do docelowych DSL. W związku z tym należy dostosować szablon, wykonaj następujące czynności:

- Zmień klasę bazową szablonu do <xref:Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation>.

- Obejmują `hostspecific="true"` w dyrektywie szablonu.

- Dodaj odwołania do zestawów docelowych DSL i jego karty i włączyć ModelBus.

- Dyrektywę, który zostanie wygenerowany jako część DSL element docelowy nie jest konieczne.

```
<#@ template debug="true" hostspecific="true" language="C#"
inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
<#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
<#@ output extension=".txt" #>
<#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
<#@ assembly name = "Company.TargetDsl.Dsl.dll" #>
<#@ assembly name = "Company.TargetDsl.T4ModelBusAdapter.dll" #>
<#@ assembly name = "System.Core" #>
<#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
<#@ import namespace="Company.TargetDsl" #>
<#@ import namespace="Company.TargetDsl.T4ModelBusAdapters" #>
<#@ import namespace="System.Linq" #>
<#
  SourceModelRoot source = this.ModelRoot; // Usual access to source model.
  // In the source DSL Definition, the root element has a model reference:
  using (TargetAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as TargetAdapter)
  {if (adapter != null)
   {
      // Get the root of the target model:
      TargetRoot target = adapter.ModelRoot;
    // The source DSL Definition has a class "SourceElement" embedded under the root.
    // (Let's assume they're all in the same model file):
    foreach (SourceElement sourceElement in source.Elements)
    {
      // In the source DSL Definition, each SourceElement has a MBR property:
      ModelBusReference elementReference = sourceElement.ReferenceToTarget;
      // Resolve the target model element:
      TargetElement element = adapter.ResolveElementReference<TargetElement>(elementReference);
#>
     The source <#= sourceElement.Name #> is linked to: <#= element.Name #> in target model: <#= target.Name #>.
<#
    }
  }}
  // Other useful code: this.Host.ResolvePath(filename) gets an absolute filename
  // from a path that is relative to the text template.
#>
```

 Po wykonaniu tego szablonu tekstowego `SourceDsl` dyrektywy ładuje plik `Sample.source`. Szablon można uzyskać dostęp do elementów modelu, zaczynając od `this.ModelRoot`. Kod można użyć klasy domeny i właściwości działania tego języka DSL.

 Ponadto szablon może rozpoznać odwołania ModelBus. W przypadku, gdy punkt odwołania do modelu docelowego, dyrektyw zestawu umożliwiają kodu klasami domeny i właściwości tego modelu DSL.

- Jeśli nie używasz dyrektywy, który jest generowany przez projektu DSL, powinny również obejmować następujące czynności.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Użyj `this.ModelBus` do uzyskania dostępu do ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Przewodnik: Testowanie szablonu tekstu, który używa ModelBus
 W tym przewodniku należy wykonać następujące kroki:

1. Skonstruuj dwóch języków DSL. Jednym języku DSL *konsumenta*, ma `ModelBusReference` właściwość, która może odwoływać się do innych DSL *dostawcy*.

2. Utwórz dwie karty ModelBus w dostawcy: jeden dla dostępu przez Szablony tekstowe, inne zwykłego kodu.

3. Utwórz wystąpienie modeli języków DSL w jednym projekcie eksperymentalne.

4. Ustawianie właściwości domeny w jednym modelu, aby wskazywał inny model.

5. Napisz program obsługi dwukrotnego kliknięcia otwartym modelu, który jest wskazywany.

6. Napisz szablon tekstowy, który jest pierwszy model obciążenia, należy wykonać odwołanie do innego modelu i przeczytaj innego modelu.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Konstrukcja DSL, który jest dostępny dla ModelBus

1. Utwórz nowe rozwiązanie języka DSL. W tym przykładzie wybierz szablon przepływu zadań rozwiązania. Ustaw nazwę języka `MBProvider` i rozszerzenie nazwy pliku ".provide".

2. W definicji DSL diagramu, kliknij prawym przyciskiem myszy pustą część diagramu, który nie jest u góry, a następnie kliknij **Włącz Modelbus**.

   Jeśli nie widzisz **Włącz Modelbus**, Pobierz i zainstaluj rozszerzenie VMSDK ModelBus.

3. W **Włącz Modelbus** okno dialogowe, wybierz opcję **udostępnienia tego języka DSL do ModelBus**, a następnie kliknij przycisk **OK**.

    Nowy projekt `ModelBusAdapter`, jest dodawany do rozwiązania.

Masz teraz DSL, który może zostać oceniony przez szablonów tekstowych przy użyciu ModelBus. Można rozwiązać odwołania do niego w kodzie poleceń, programy obsługi zdarzeń lub reguły, które działają w elemencie AppDomain edytora pliku modelu. Jednak szablony tekstowe uruchamiane w oddzielnej domenie aplikacji i nie można uzyskać dostępu modelu, gdy jest edytowany. Jeśli chcesz uzyskać dostęp ModelBus odwołania do tego języka DSL, z szablonu tekstu, konieczne jest posiadanie oddzielnych elementu ModelBusAdapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Utwórz kartę ModelBus, który jest skonfigurowany dla szablonów tekstowych

1. W Eksploratorze plików, kopiowanie i wklejanie folderu, który zawiera *ModelBusAdapter.csproj*.

    Nazwa folderu **T4ModelBusAdapter**.

    Zmień nazwę pliku projektu *T4ModelBusAdapter.csproj*.

2. W Eksploratorze rozwiązań należy dodać do rozwiązania MBProvider T4ModelBusAdapter. Kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż opcję **Dodaj**, a następnie kliknij przycisk **istniejący projekt**.

3. Kliknij prawym przyciskiem myszy węzeł projektu T4ModelBusAdapter, a następnie kliknij polecenie Właściwości. W oknie dialogowym właściwości projektu, należy zmienić **nazwy zestawu** i **domyślne Namespace** do `Company.MBProvider.T4ModelBusAdapters`.

4. W każdym pliku *.tt w T4ModelBusAdapter Wstawianie "T4" ostatniej części przestrzeni nazw, dzięki czemu wiersz podobny do następującego.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. W `DslPackage` projektu, należy dodać odwołanie projektu do `T4ModelBusAdapter`.

6. W DslPackage\source.extension.tt, Dodaj następujący wiersz w obszarze `<Content>`.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. W `T4ModelBusAdapter` projektu, Dodaj odwołanie do: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Open T4ModelBusAdapter\AdapterManager.tt:

   1. Zmień klasę bazową AdapterManagerBase do <xref:Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager>. Teraz ta część pliku podobny do następującego.

       ```
       namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters
       {
           /// <summary>
           /// Adapter manager base class (double derived pattern) for the <#= dslName #> Designer
           /// </summary>
           public partial class <#= dslName #>AdapterManagerBase
           : Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager
           {
       ```

   2. Pod koniec pliku Wstaw następujący atrybut dodatkowe przed klasy adaptermanager obsługującego element.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Wynik podobny do następującego.

       ```
       /// <summary>
       /// ModelBus modeling adapter manager for a <#= dslName #>Adapter model adapter
       /// </summary>
       [Mef::Export(typeof(DslIntegration::ModelBusAdapterManager))]
       [Mef::ExportMetadata(DslIntegration::CompositionAttributes.AdapterIdKey,<#= dslName #>Adapter.AdapterId)]
       [DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]
       [Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]
       public partial class <#= dslName #>AdapterManager : <#= dslName #>AdapterManagerBase
       {
       }
       ```

9. Kliknij przycisk **Przekształć wszystkie szablony** w tytuł paska z Eksploratora rozwiązań.

10. Naciśnij klawisz **F5**.

11. Sprawdź, czy działa język DSL. W projekcie eksperymentalne Otwórz `Sample.provider`. Zamknij wystąpienie doświadczalne programu Visual Studio.

    Teraz można rozwiązać ModelBus odwołania do tego języka DSL w szablonach tekstowych, a także w zwykłych kodu.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Konstrukcja DSL z właściwością domeny odwołanie ModelBus

1. Utwórz nowy język DSL za pomocą szablonu rozwiązania dotyczącego języka minimalny. Nazwa języka MBConsumer i ustawić rozszerzenie nazwy pliku ".consume".

2. W projekcie języka DSL Dodaj odwołanie do zestawu MBProvider DSL. Kliknij prawym przyciskiem myszy `MBConsumer\Dsl\References` a następnie kliknij przycisk **Dodaj odwołanie**. W **Przeglądaj** kartę, Znajdź `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Pozwala na tworzenie kodu, który używa innego języka DSL. Jeśli chcesz utworzyć odwołania do kilku języków DSL, dodaj je również.

3. W definicji DSL diagramu, kliknij prawym przyciskiem myszy diagram, a następnie kliknij przycisk **Włącz ModelBus**. W oknie dialogowym wybierz **Włącz tego języka DSL zużyje ModelBus**.

4. W klasie `ExampleElement`, Dodaj nową właściwość domeny `MBR`i w oknie właściwości ustaw typ `ModelBusReference`.

5. Kliknij prawym przyciskiem myszy właściwość domeny na diagramie, a następnie kliknij przycisk **ModelBusReference edytować właściwości określonych**. W oknie dialogowym wybierz **elementu modelu**.

    Ustaw filtr okna dialogowego plików do następujących.

    `Provider File|*.provide`

    Podciąg po "&#124;" jest filtr dla okna dialogowego wyboru pliku. Możesz ustawić ją, aby zezwolić na wszystkie pliki przy użyciu *.\*

    W **typu elementu modelu** listy, należy wprowadzić nazwy jedną lub więcej domen klasy dostawcy DSL (na przykład Company.MBProvider.Task). Mogą być abstrakcyjne klasy. Jeśli lista jest puste, użytkownik może ustawić odwołanie do dowolnego elementu.

6. Zamknij okno dialogowe i **Przekształć wszystkie szablony**.

   Utworzono DSL, który może zawierać odwołania do elementów w innym DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Utwórz odwołanie ModelBus do innego pliku w rozwiązaniu

1. W rozwiązaniu MBConsumer naciśnij kombinację klawiszy CTRL + F5. Otwiera doświadczalne wystąpienie programu Visual Studio, w **MBConsumer\Debugging** projektu.

2. Dodaj kopię Sample.provide do **MBConsumer\Debugging** projektu. Jest to konieczne, ponieważ odwołanie ModelBus musi odwoływać się do pliku w tym samym rozwiązaniu.

   1. Kliknij prawym przyciskiem myszy projekt debugowania, wskaż opcję **Dodaj**, a następnie kliknij przycisk **istniejący element**.

   2. W **elementu Dodawanie** okna dialogowego, ustaw filtr na **wszystkie pliki (\*.\*)** .

   3. Przejdź do `MBProvider\Debugging\Sample.provide` a następnie kliknij przycisk **Dodaj**.

3. Otwórz `Sample.consume`.

4. Kliknij jeden kształt przykładu, a w oknie dialogowym właściwości kliknij **[...]**  we właściwości MBR. W oknie dialogowym kliknij **Przeglądaj** i wybierz `Sample.provide`. W oknie elementy rozwiń węzeł typu zadania, a następnie wybierz jeden z elementów.

5. Zapisz plik. (Nie należy jeszcze zamykać doświadczalnym wystąpieniu programu Visual Studio.)

   Utworzono model, który zawiera odwołanie do elementu w innym modelem ModelBus.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Rozwiąż odwołanie ModelBus w szablonie tekstu

1. W doświadczalnym wystąpieniu programu Visual Studio Otwórz przykładowy plik szablonu tekstu. Ustaw jego zawartość w następujący sposób.

    ```
    <#@ template debug="true" hostspecific="true" language="C#"
    inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
    <#@ MBConsumer processor="MBConsumerDirectiveProcessor" requires="fileName='Sample.consume'" #>
    <#@ output extension=".txt" #>
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
    <#@ assembly name = "Company.MBProvider.Dsl.dll" #>
    <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
    <#@ import namespace="Company.MBProvider" #>
    <#
      // Property provided by the Consumer directive processor:
      ExampleModel consumerModel = this.ExampleModel;
      // Iterate through Consumer model, listing the elements:
      foreach (ExampleElement element in consumerModel.Elements)
      {
    #>
       <#= element.Name #>
    <#
        if (element.MBR != null)
      using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(element.MBR))
      {
              // If we allowed multiple types or DSLs in the MBR, discover type here.
        Task task = adapter.ResolveElementReference<Task>(element.MBR);
    #>
            <#= element.Name #> is linked to Task: <#= task==null ? "(null)" : task.Name #>
    <#
          }
      }
    #>

    ```

     Zwróć uwagę następujące kwestie:

    - `hostSpecific` i `inherits` atrybuty `template` dyrektywa musi być ustawiona.

    - Modelu odbiorców jest dostępny w zwykły sposób przy użyciu procesora dyrektywy, który został wygenerowany w tym DSL.

    - W dyrektywach zestawu i importu musi mieć możliwość dostępu ModelBus i typy dostawcy DSL.

    - Jeśli wiesz, że wiele MBRs są połączone z tego samego modelu, lepiej jest wywołać CreateAdapter tylko jeden raz.

2. Zapisz szablon. Upewnij się, że wynikowy plik tekstowy jest podobny do następującego.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Rozwiąż odwołanie ModelBus w obsługi gestu

1. Zamknij wystąpienie doświadczalne programu Visual Studio, jeśli jest uruchomiony.

2. Dodaj plik o nazwie *MBConsumer\Dsl\Custom.cs* i ustawi jego zawartość do następującego:

    ```csharp
    namespace Company.MB2Consume
    {
      using Microsoft.VisualStudio.Modeling.Integration;
      using Company.MB3Provider;

      public partial class ExampleShape
      {
        public override void OnDoubleClick(Microsoft.VisualStudio.Modeling.Diagrams.DiagramPointEventArgs e)
        {
          base.OnDoubleClick(e);
          ExampleElement element = this.ModelElement as ExampleElement;
          if (element.MBR != null)
          {
            IModelBus modelbus = this.Store.GetService(typeof(SModelBus)) as IModelBus;
            using (ModelBusAdapter adapter = modelbus.CreateAdapter(element.MBR))
            {
              Task task = adapter.ResolveElementReference<Task>(element.MBR);
              // Open a window on this model:
              ModelBusView view = adapter.GetDefaultView();
              view.Show();
              view.SetSelection(element.MBR);
            }
          }
        }
      }
    }
    ```

3. Naciśnij klawisz **Ctrl**+**F5**.

4. W doświadczalnym wystąpieniu programu Visual Studio, otwórz `Debugging\Sample.consume`.

5. Kliknij dwukrotnie jeden kształt.

    Jeśli ustawisz MBR na ten element, otwiera przywoływanym modelem i odnośny element jest wybrany.

## <a name="see-also"></a>Zobacz także

- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
