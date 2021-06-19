---
title: Używanie modelu ModelBus w szablonie tekstowym
description: Dowiedz się, jak rozwiązując odwołania w celu uzyskania dostępu do modeli docelowych, jeśli piszesz szablony tekstowe, które odczytują model zawierający Visual Studio ModelBus odwołania.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2afe8de66b109793a4e15e8320c3f498a08b25ec
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388389"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Użycie programu Visual Studio ModelBus w szablonie tekstu

W przypadku pisania szablonów tekstowych, które odczytują model zawierający Visual Studio ModelBus odwołania, warto rozpoznać odwołania w celu uzyskania dostępu do modeli docelowych. W takim przypadku należy dostosować szablony tekstowe i przywołyne języki specyficzne dla domeny (DSL):

- DSL, który jest obiektem docelowym odwołań, musi mieć adapter ModelBus, który jest skonfigurowany do uzyskiwania dostępu z szablonów tekstowych. Jeśli uzyskujesz również dostęp do DSL z innego kodu, wymagana jest ponownie skonfigurowana karta oprócz standardowej karty ModelBus.

     Menedżer adapterów musi dziedziczyć z [klasy VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) i musi mieć atrybut `[HostSpecific(HostName)]` .

- Szablon musi dziedziczyć z [właściwości ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Jeśli chcesz odczytywać modele DSL, które nie zawierają odwołań ModelBus, możesz użyć procesorów dyrektyw generowanych w projektach DSL. Aby uzyskać więcej informacji, zobacz [Accessing Models from Text Templates (Uzyskiwanie dostępu do modeli z szablonów tekstowych).](../modeling/accessing-models-from-text-templates.md)

Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz Design-Time Code Generation by using T4 Text Templates (Generowanie kodu [w czasie projektowania przy użyciu szablonów tekstowych T4).](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Tworzenie adaptera magistrali modelu w celu uzyskania dostępu z szablonów tekstowych

Aby rozpoznać odwołanie ModelBus w szablonie tekstowym, docelowy DSL musi mieć zgodną kartę. Szablony tekstowe są wykonywane w oddzielnej domenie AppDomain Visual Studio edytorach dokumentów, dlatego karta musi załadować model zamiast uzyskać do niego dostęp za pośrednictwem dte.

1. Jeśli docelowe rozwiązanie DSL nie ma projektu **ModelBusAdapter,** utwórz go za pomocą kreatora rozszerzenia Modelbus:

    1. Pobierz i zainstaluj rozszerzenie Visual Studio ModelBus, jeśli jeszcze tego nie zrobiono. Aby uzyskać więcej informacji, zobacz [Visualization and Modeling SDK (Zestaw SDK wizualizacji i modelowania).](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/)

    2. Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektową, a następnie kliknij pozycję **Włącz modelbus.**

    3. W oknie dialogowym wybierz pozycję **Chcę uwidocznić ten DSL dla modeluBus.** Możesz wybrać obie opcje, jeśli chcesz, aby ten DSL uwidocznił swoje modele i używać odwołań do innych plików DSL.

    4. Kliknij przycisk **OK**. Nowy projekt "ModelBusAdapter" jest dodawany do rozwiązania DSL.

    5. Kliknij **pozycję Przekształć wszystkie szablony.**

    6. Ponownie skompiluj rozwiązanie.

2. Jeśli chcesz uzyskać dostęp do DSL zarówno z szablonu tekstowego, jak i z innego kodu, takiego jak polecenie, zduplikuj **projekt ModelBusAdapter:**

    1. W Eksplorator Windows skopiuj i wklej folder zawierający **plik ModelBusAdapter.csproj.**

    2. Zmień nazwę pliku projektu (na przykład **na T4ModelBusAdapter.csproj).**

    3. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Istniejący projekt**. Znajdź nowy projekt adaptera **T4ModelBusAdapter.csproj.**

    4. W każdym `*.tt` pliku nowego projektu zmień przestrzeń nazw.

    5. Kliknij prawym przyciskiem myszy nowy projekt w **Eksplorator rozwiązań** a następnie kliknij pozycję **Właściwości.** W edytorze właściwości zmień nazwy wygenerowanego zestawu i domyślną przestrzeń nazw.

    6. W projekcie DslPackage dodaj odwołanie do nowego projektu adaptera, aby zawierało odwołania do obu kart.

    7. W folderze DslPackage\source.extension.tt dodaj wiersz, który odwołuje się do nowego projektu adaptera.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Przekształć wszystkie** szablony i ponownie skompilować rozwiązanie. Nie powinny występować żadne błędy kompilacji.

3. W nowym projekcie adaptera dodaj odwołania do następujących zestawów:

    - Microsoft.VisualStudio.TextTemplating.11.0
    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

4. W AdapterManager.tt:

    - Zmień deklarację klasy AdapterManagerBase tak, aby dziedziczyła z [klasy VsTextTemplatingModelingAdapterManager.](/previous-versions/ee844317(v=vs.140))

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Pod koniec pliku zastąp atrybut HostSpecific przed klasą AdapterManager. Usuń następujący wiersz:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Wstaw następujący wiersz:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Ten atrybut filtruje zestaw kart dostępnych, gdy konsument modelubus wyszukuje kartę.

5. **Przekształć wszystkie** szablony i ponownie skompilować rozwiązanie. Nie powinny występować żadne błędy kompilacji.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Pisanie szablonu tekstowego, który może rozpoznać odwołania ModelBus

Zazwyczaj rozpoczynasz od szablonu, który odczytuje i generuje pliki z "źródłowego" DSL. Ten szablon używa dyrektywy wygenerowanej w źródłowym projekcie DSL do odczytywania plików modelu źródłowego w sposób opisany w tece Uzyskiwanie dostępu do modeli z [szablonów tekstowych.](../modeling/accessing-models-from-text-templates.md) Jednak źródłowy DSL zawiera ModelBus odwołania do "docelowy" DSL. W związku z tym należy włączyć kod szablonu, aby rozpoznać odwołania i uzyskać dostęp do docelowego DSL. W związku z tym należy dostosować szablon, wykonać następujące kroki:

- Zmień klasę bazową szablonu na [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Uwzględnij `hostspecific="true"` w dyrektywie szablonu.

- Dodaj odwołania do zestawu do docelowego DSL i jego karty i włączyć ModelBus.

- Nie potrzebujesz dyrektywy, która jest generowana jako część docelowego DSL.

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

 Podczas wykonywania tego szablonu tekstowego dyrektywa `SourceDsl` ładuje plik `Sample.source` . Szablon może uzyskać dostęp do elementów tego modelu, począwszy od `this.ModelRoot` . Kod może używać klas domeny i właściwości tego DSL.

 Ponadto szablon może rozpoznać odwołania ModelBus. Gdzie odwołania wskazują model docelowy, dyrektywy zestawu umożliwiają kodowi używanie klas domeny i właściwości DSL tego modelu.

- Jeśli nie używasz dyrektywy, która jest generowana przez projekt DSL, należy również uwzględnić następujące.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Użyj `this.ModelBus` , aby uzyskać dostęp do modeluBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Przewodnik: testowanie szablonu tekstowego, który używa modeluBus
 W tym przewodniku wykonaj następujące kroki:

1. Skonstruuj dwa pliki DSL. Jeden DSL, *konsument*, ma właściwość , która może odwoływać się do innego `ModelBusReference` DSL, *dostawcy*.

2. Utwórz dwie karty ModelBus w dostawcy: jedną dla dostępu za pomocą szablonów tekstowych, drugą dla zwykłego kodu.

3. Tworzenie modeli wystąpień plików DSL w jednym projekcie eksperymentalnym.

4. Ustaw właściwość domeny w jednym modelu, aby wskazać drugi model.

5. Napisz program obsługi dwukrotnego kliknięcia, który otwiera wskazywany model.

6. Napisz szablon tekstowy, który może załadować pierwszy model, postępuj zgodnie z odwołaniem do innego modelu i odczytaj drugi model.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Konstruowanie DSL, który jest dostępny dla ModelBus

1. Utwórz nowe rozwiązanie DSL. W tym przykładzie wybierz szablon rozwiązania Przepływ zadań. Ustaw nazwę języka na , `MBProvider` a rozszerzenie nazwy pliku na ".provide".

2. Na diagramie definicji DSL kliknij prawym przyciskiem myszy pustą część diagramu, która nie znajduje się u góry, a następnie kliknij pozycję **Włącz modelbus.**

   Jeśli nie widzisz przycisku **Włącz modelbus,** pobierz i zainstaluj rozszerzenie VMSDK ModelBus.

3. W **oknie dialogowym Włączanie magistrali** modeli wybierz pozycję **Uwidocznij ten DSL dla modeluBus,** a następnie kliknij przycisk **OK.**

    Do rozwiązania dodawany `ModelBusAdapter` jest nowy projekt.

Masz teraz DSL, do którego można uzyskać dostęp za pomocą szablonów tekstowych za pośrednictwem modeluBus. Odwołania do niego można rozpoznać w kodzie poleceń, programów obsługi zdarzeń lub reguł, które działają w domenie Aplikacji edytora plików modelu. Szablony tekstowe są jednak uruchamiane w oddzielnej domenie AppDomain i nie mogą uzyskać dostępu do modelu podczas jego edytowania. Aby uzyskać dostęp do odwołań ModelBus do tego DSL z szablonu tekstowego, musisz mieć oddzielny modelBusAdapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Tworzenie adaptera ModelBus skonfigurowanego dla szablonów tekstowych

1. W Eksplorator plików skopiuj i wklej folder zawierający *plik ModelBusAdapter.csproj.*

    Nadaj **folderowi nazwę T4ModelBusAdapter.**

    Zmień nazwę pliku projektu *T4ModelBusAdapter.csproj.*

2. W Eksplorator rozwiązań dodaj T4ModelBusAdapter do rozwiązania MBProvider. Kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Istniejący projekt**.

3. Kliknij prawym przyciskiem myszy węzeł projektu T4ModelBusAdapter, a następnie kliknij polecenie Właściwości. W oknie właściwości projektu zmień wartości w polach **Nazwa zestawu** i **Domyślna przestrzeń nazw** na `Company.MBProvider.T4ModelBusAdapters` .

4. W każdym pliku *.tt w folderze T4ModelBusAdapter wstaw tekst "T4" do ostatniej części przestrzeni nazw, tak aby wiersz był podobny do poniższego.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. W `DslPackage` projekcie dodaj odwołanie do projektu do . `T4ModelBusAdapter`

6. W obszarze DslPackage\source.extension.tt dodaj następujący wiersz w obszarze `<Content>` .

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. W `T4ModelBusAdapter` projekcie dodaj odwołanie do: **Microsoft.VisualStudio.TextTemplating.Modeling.11.0**

8. Otwórz folder T4ModelBusAdapter\AdapterManager.tt:

   1. Zmień klasę bazową adapterManagerBase na [VsTextTemplatingModelingAdapterManager.](/previous-versions/ee844317(v=vs.140)) Ta część pliku jest teraz podobna do poniższej.

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

   2. Pod koniec pliku wstaw następujący dodatkowy atrybut przed klasą AdapterManager.

        `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

        Wynik jest podobny do poniższego.

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

9. Kliknij **pozycję Przekształć** wszystkie szablony na pasku tytułu Eksplorator rozwiązań.

10. Naciśnij klawisz **F5**.

11. Sprawdź, czy DSL działa. W projekcie eksperymentalnym otwórz `Sample.provider` . Zamknij eksperymentalne wystąpienie Visual Studio.

    Odwołania ModelBus do tego DSL można teraz rozpoznać w szablonach tekstowych, a także w zwykłym kodzie.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Konstruowanie DSL z właściwością domeny odwołania ModelBus

1. Utwórz nowy język DSL przy użyciu szablonu rozwiązania w języku minimalnym. Nadaj językowi nazwę MBConsumer i ustaw rozszerzenie nazwy pliku na ".consume".

2. W projekcie DSL dodaj odwołanie do zestawu DSL MBProvider. Kliknij prawym przyciskiem  `MBConsumer\Dsl\References` myszy, a następnie kliknij polecenie **Dodaj odwołanie**. Na karcie **Przeglądaj** znajdź pozycję `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Dzięki temu można utworzyć kod, który używa innego DSL. Jeśli chcesz utworzyć odwołania do kilku plików DSL, dodaj je również.

3. Na diagramie definicji DSL kliknij prawym przyciskiem myszy diagram, a następnie kliknij pozycję **Włącz modelBus.** W oknie dialogowym wybierz pozycję **Włącz dla tego DSL, aby korzystać z modeluBus.**

4. W klasie `ExampleElement` dodaj nową właściwość domeny , a `MBR` w okno Właściwości ustaw jej typ na `ModelBusReference` .

5. Kliknij prawym przyciskiem myszy właściwość domeny na diagramie, a następnie kliknij pozycję **Edytuj modelBusReference określonych właściwości**. W oknie dialogowym wybierz **element modelu**.

    Ustaw filtr okna dialogowego pliku na następujący.

    `Provider File|*.provide`

    Podciąg po "&#124;" jest filtrem okna dialogowego wyboru pliku. Można ją ustawić tak, aby zezwalała na wszystkie pliki przy użyciu *.\*

    Na **liście Typ elementu** modelu wprowadź nazwy co najmniej jednej klasy domeny w dsl dostawcy (na przykład Company.MBProvider.Task). Mogą być klasami abstrakcyjnymi. Jeśli pozostawisz listę pustą, użytkownik może ustawić odwołanie do dowolnego elementu.

6. Zamknij okno dialogowe i **przekształć wszystkie szablony.**

   Utworzono DSL, który może zawierać odwołania do elementów w innym DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Tworzenie odwołania ModelBus do innego pliku w rozwiązaniu

1. W rozwiązaniu MBConsumer naciśnij klawisze CTRL+F5. Eksperymentalne wystąpienie Visual Studio zostanie otwarte w projekcie **MBConsumer\Debugging.**

2. Dodaj kopię pliku Sample.provide do **projektu MBConsumer\Debugging.** Jest to konieczne, ponieważ odwołanie ModelBus musi odwoływać się do pliku w tym samym rozwiązaniu.

   1. Kliknij prawym przyciskiem myszy projekt Debugowanie, wskaż **polecenie Dodaj**, a następnie kliknij pozycję **Istniejący element**.

   2. W **oknie dialogowym Dodawanie** elementu ustaw filtr na **wartość Wszystkie pliki ( . \* \* )**.

   3. Przejdź do , `MBProvider\Debugging\Sample.provide` a następnie kliknij pozycję **Dodaj.**

3. Otwórz plik `Sample.consume`.

4. Kliknij jeden przykładowy kształt, a następnie w okno Właściwości kliknij **przycisk [...]** we właściwości MBR. W oknie dialogowym kliknij przycisk **Przeglądaj i** wybierz pozycję `Sample.provide` . W oknie elementów rozwiń typ Zadanie i wybierz jeden z elementów.

5. Zapisz plik. (Nie zamykaj jeszcze eksperymentalnego wystąpienia Visual Studio).

   Utworzono model, który zawiera odwołanie ModelBus do elementu w innym modelu.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Rozwiązywanie odwołania ModelBus w szablonie tekstowym

1. W eksperymentalnym wystąpieniu Visual Studio otwórz przykładowy plik szablonu tekstowego. Ustaw jego zawartość w następujący sposób.

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

     Zwróć uwagę na następujące kwestie:

    - Należy ustawić atrybuty i `hostSpecific` `inherits` dyrektywy `template` .

    - Dostęp do modelu konsumenta jest uzyskiwany w zwykły sposób za pośrednictwem procesora dyrektywy, który został wygenerowany w tym DSL.

    - Dyrektywy zestawu i importu muszą mieć dostęp do modeluBus i typów DSL dostawcy.

    - Jeśli wiesz, że wiele MBR jest połączonych z tym samym modelem, lepiej jest wywołać createadapter tylko raz.

2. Zapisz szablon. Sprawdź, czy wynikowy plik tekstowy jest podobny do poniższego.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Rozwiązywanie odwołania ModelBus w obsłudze gestów

1. Zamknij eksperymentalne wystąpienie Visual Studio, jeśli jest uruchomione.

2. Dodaj plik o *nazwie MBConsumer\Dsl\Custom.cs* i ustaw jego zawartość na następującą:

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

3. Naciśnij **klawisze Ctrl** + **F5.**

4. W eksperymentalnym wystąpieniu Visual Studio `Debugging\Sample.consume` otwórz .

5. Kliknij dwukrotnie jeden kształt.

    Jeśli ustawiono MBR dla tego elementu, model, do których istnieje odwołanie, zostanie otwarty i zostanie wybrany przywołyny element.

## <a name="see-also"></a>Zobacz też

- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
