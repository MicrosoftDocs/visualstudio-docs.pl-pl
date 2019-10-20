---
title: Używanie ModelBus w szablonie tekstowym
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2d6e34793f36da2bf9c5ee8a2cd9d410c9f692ea
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663753"
---
# <a name="using-visual-studio-modelbus-in-a-text-template"></a>Użycie programu Visual Studio ModelBus w szablonie tekstu

W przypadku pisania szablonów tekstowych, które odczytują model, który zawiera Visual Studio ModelBus odwołania, możesz chcieć rozwiązać odwołania w celu uzyskania dostępu do modeli docelowych. W takim przypadku konieczne jest dostosowanie szablonów tekstowych i odwołań do języków specyficznych dla domeny (językami DSL):

- DSL, który jest obiektem docelowym odwołań, musi mieć adapter ModelBus skonfigurowany do dostępu z szablonów tekstowych. W przypadku uzyskania dostępu do modemu DSL z innego kodu, oprócz standardowej karty ModelBus, wymagana jest ponownie skonfigurowana karta.

     Menedżer adapterów musi dziedziczyć z [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)) i musi mieć atrybut `[HostSpecific(HostName)]`.

- Szablon musi dziedziczyć po elemencie [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

> [!NOTE]
> Jeśli chcesz odczytywać modele DSL, które nie zawierają odwołań ModelBus, możesz użyć procesorów dyrektywy, które są generowane w projektach DSL. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md).

Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu w czasie projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

## <a name="create-a-model-bus-adapter-for-access-from-text-templates"></a>Tworzenie karty magistrali modelu na potrzeby dostępu z szablonów tekstowych

Aby można było rozpoznać odwołanie ModelBus w szablonie tekstowym, docelowy DSL musi mieć zgodną kartę. Szablony tekstowe są wykonywane w oddzielnym elemencie AppDomain z edytorów dokumentów programu Visual Studio, dlatego Adapter musi ładować model zamiast uzyskiwać do niego dostęp za pośrednictwem DTE.

1. Jeśli docelowe rozwiązanie DSL nie ma projektu **ModelBusAdapter** , utwórz je za pomocą Kreatora rozszerzenia ModelBus:

    1. Pobierz i zainstaluj rozszerzenie Visual Studio ModelBus, jeśli jeszcze tego nie zrobiono. Aby uzyskać więcej informacji, zobacz temat [Wizualizacja i Modeling SDK](https://devblogs.microsoft.com/devops/the-visual-studio-modeling-sdk-is-now-available-with-visual-studio-2017/).

    2. Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij pozycję **Włącz ModelBus**.

    3. W oknie dialogowym wybierz opcję **Chcę uwidocznić ten DSL w ModelBus**. Możesz wybrać obie opcje, jeśli chcesz, aby ta linia DSL mogła uwidocznić swoje modele i wykorzystać odwołania do innych językami DSL.

    4. Kliknij przycisk **OK**. Do rozwiązania DSL zostanie dodany nowy projekt "ModelBusAdapter".

    5. Kliknij kolejno pozycje **Przekształć wszystkie szablony**.

    6. Ponownie skompiluj rozwiązanie.

2. Jeśli chcesz uzyskać dostęp do linii DSL zarówno z szablonu tekstu, jak i z innego kodu, takiego jak polecenie, Duplikuj projekt **ModelBusAdapter** :

    1. W Eksploratorze Windows skopiuj i wklej folder zawierający **ModelBusAdapter. csproj**.

    2. Zmień nazwę pliku projektu (na przykład na **T4ModelBusAdapter. csproj**).

    3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł rozwiązanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący projekt**. Znajdź nowy projekt karty, **T4ModelBusAdapter. csproj**.

    4. W każdym pliku `*.tt` nowego projektu Zmień przestrzeń nazw.

    5. Kliknij prawym przyciskiem myszy nowy projekt w **Eksplorator rozwiązań** a następnie kliknij polecenie **Właściwości**. W edytorze właściwości Zmień nazwy wygenerowanego zestawu i domyślnego obszaru nazw.

    6. W projekcie DslPackage Dodaj odwołanie do projektu nowej karty, aby odwoływać się do obu kart.

    7. W DslPackage\source.extension.tt Dodaj wiersz odwołujący się do nowego projektu karty.

        ```
        <MefComponent>|T4ModelBusAdapter|</MefComponent>
        ```

    8. **Przekształć wszystkie szablony** i Skompiluj ponownie rozwiązanie. Nie powinny wystąpić błędy kompilacji.

3. W projekcie nowej karty Dodaj odwołania do następujących zestawów:

    - Microsoft. VisualStudio. TextTemplating. 11.0
    - Microsoft. VisualStudio. TextTemplating. Modeling. 11.0

4. W AdapterManager.tt:

    - Zmień deklarację elementu AdapterManagerBase tak, aby dziedziczył po [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

         `public partial class <#= dslName =>AdapterManagerBase :`

         `Microsoft.VisualStudio.TextTemplating.Modeling.VsTextTemplatingModelingAdapterManager { ...`

    - Przed końcem pliku Zastąp atrybut HostSpecific przed klasą adaptera. Usuń następujący wiersz:

         `[DslIntegration::HostSpecific(DslIntegrationShell::VsModelingAdapterManager.HostName)]`

         Wstaw następujący wiersz:

         `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

         Ten atrybut filtruje zestaw kart, które są dostępne, gdy odbiorca ModelBus wyszukuje adapter.

5. **Przekształć wszystkie szablony** i Skompiluj ponownie rozwiązanie. Nie powinny wystąpić błędy kompilacji.

## <a name="write-a-text-template-that-can-resolve-modelbus-references"></a>Napisz szablon tekstowy, który może rozwiązać odwołania ModelBus

Zwykle zaczynasz od szablonu, który odczytuje i generuje pliki z "source". Ten szablon używa dyrektywy, która jest generowana w źródłowym projekcie DSL do odczytywania plików modeli źródłowych w sposób opisany w temacie [Uzyskiwanie dostępu do modeli z szablonów tekstowych](../modeling/accessing-models-from-text-templates.md). Jednak Źródło DSL zawiera odwołania ModelBus do elementu "target" DSL. W związku z tym należy włączyć kod szablonu, aby rozpoznać odwołania i uzyskać dostęp do docelowego języka DSL. W związku z tym należy dostosować szablon, wykonując następujące czynności:

- Zmień klasę bazową szablonu na [ModelBusEnabledTextTransformation](/previous-versions/ee844263(v=vs.140)).

- Uwzględnij `hostspecific="true"` w dyrektywie Template.

- Dodaj odwołania do zestawu do docelowego DSL i jego karty, a następnie Włącz ModelBus.

- Nie potrzebujesz dyrektywy, która jest generowana w ramach docelowego DSL.

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

 Po wykonaniu tego szablonu tekstu dyrektywa `SourceDsl` ładuje plik `Sample.source`. Szablon może uzyskać dostęp do elementów tego modelu, rozpoczynając od `this.ModelRoot`. Kod może używać klas domen i właściwości tego języka DSL.

 Ponadto szablon może rozpoznać odwołania ModelBus. Gdy odwołania wskazują na model docelowy, dyrektywy zestawu pozwalają kodowi używać klas domeny i właściwości tego modelu.

- Jeśli nie używasz dyrektywy, która jest generowana przez projekt DSL, należy również uwzględnić następujące elementy.

    ```
    <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.11.0" #>
    <#@ assembly name = "Microsoft.VisualStudio.TextTemplating.Modeling.11.0" #>
    ```

- Użyj `this.ModelBus`, aby uzyskać dostęp do ModelBus.

## <a name="walkthrough-testing-a-text-template-that-uses-modelbus"></a>Przewodnik: testowanie szablonu tekstu korzystającego z ModelBus
 W tym instruktażu wykonaj następujące czynności:

1. Utwórz dwa językami DSL. Jeden DSL, *konsument*, ma właściwość `ModelBusReference`, która może odwoływać się do innych dostawców DSL, *dostawcy*.

2. Utwórz dwie karty ModelBus w dostawcy: jeden dla dostępu według szablonów tekstowych, drugi dla zwykłego kodu.

3. Utwórz modele wystąpień językami DSL w jednym projekcie eksperymentalnym.

4. Ustaw właściwość domeny w jednym modelu, aby wskazywała na inny model.

5. Napisz procedurę obsługi dwukrotnego kliknięcia otwierającą model, który jest wskazywany przez.

6. Napisz szablon tekstowy, który może ładować pierwszy model, postępuj zgodnie z odwołaniem do drugiego modelu i odczytaj inny model.

### <a name="construct-a-dsl-that-is-accessible-to-modelbus"></a>Konstruowanie języka DSL dostępnego dla ModelBus

1. Utwórz nowe rozwiązanie DSL. Na potrzeby tego przykładu wybierz szablon rozwiązania przepływu zadań. Ustaw nazwę języka na `MBProvider` i rozszerzenie nazwy pliku na ". Podaj".

2. Na diagramie definicji DSL kliknij prawym przyciskiem myszy pustą część diagramu, która nie znajduje się blisko góry, a następnie kliknij pozycję **Włącz ModelBus**.

   Jeśli nie widzisz **ModelBus Enable**, Pobierz i zainstaluj rozszerzenie VMSDK ModelBus.

3. W oknie dialogowym **Włączanie ModelBus** wybierz opcję **Uwidocznij ten DSL do ModelBus**, a następnie kliknij przycisk **OK**.

    Nowy projekt, `ModelBusAdapter`, zostanie dodany do rozwiązania.

Masz teraz dostęp do języka DSL, który można uzyskać za pomocą szablonów tekstowych w ModelBus. Odwołania do niego można rozwiązać w kodzie poleceń, obsługi zdarzeń lub regułach, które działają w domenie aplikacji edytora plików modelu. Jednak szablony tekstowe są uruchamiane w oddzielnym elemencie AppDomain i nie mogą uzyskać dostępu do modelu podczas jego edytowania. Jeśli chcesz uzyskać dostęp do ModelBus odwołań do tego języka DSL z szablonu tekstu, musisz mieć osobne ModelBusAdapter.

### <a name="create-a-modelbus-adapter-that-is-configured-for-text-templates"></a>Tworzenie adaptera ModelBus, który jest skonfigurowany do szablonów tekstowych

1. W Eksploratorze plików skopiuj i wklej folder zawierający *ModelBusAdapter. csproj*.

    Nazwij folder **T4ModelBusAdapter**.

    Zmień nazwę pliku projektu *T4ModelBusAdapter. csproj*.

2. W Eksplorator rozwiązań Dodaj T4ModelBusAdapter do rozwiązania MBProvider. Kliknij prawym przyciskiem myszy węzeł rozwiązanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący projekt**.

3. Kliknij prawym przyciskiem myszy węzeł projektu T4ModelBusAdapter, a następnie kliknij polecenie Właściwości. W oknie właściwości projektu Zmień **nazwę zestawu** i **domyślną przestrzeń nazw** na `Company.MBProvider.T4ModelBusAdapters`.

4. W każdym pliku *. tt w T4ModelBusAdapter, Wstaw "T4" do ostatniej części przestrzeni nazw, aby linia była podobna do poniższego.

    `namespace <#= CodeGenerationUtilities.GetPackageNamespace(this.Dsl) #>.T4ModelBusAdapters`

5. W projekcie `DslPackage` Dodaj odwołanie do projektu do `T4ModelBusAdapter`.

6. W DslPackage\source.extension.tt Dodaj następujący wiersz w obszarze `<Content>`.

    `<MefComponent>|T4ModelBusAdapter|</MefComponent>`

7. W projekcie `T4ModelBusAdapter` Dodaj odwołanie do: **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**

8. Otwórz T4ModelBusAdapter\AdapterManager.tt:

   1. Zmień klasę bazową AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)). Ta część pliku jest teraz podobna do następującej.

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

   2. Obok końca pliku Wstaw poniższy dodatkowy atrybut przed klasą AdapterManager.

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

9. Kliknij pozycję **Przekształć wszystkie szablony** na pasku tytułu Eksplorator rozwiązań.

10. Naciśnij klawisz **F5**.

11. Sprawdź, czy DSL działa. W projekcie eksperymentalnym Otwórz `Sample.provider`. Zamknij wystąpienie eksperymentalne programu Visual Studio.

    Odwołania ModelBus do tego języka DSL można teraz rozpoznać w szablonach tekstowych, a także w zwykłym kodzie.

### <a name="construct-a-dsl-with-a-modelbus-reference-domain-property"></a>Konstruowanie języka DSL z właściwością domeny odwołania ModelBus

1. Utwórz nowy DSL przy użyciu szablonu rozwiązania minimalnego języka. Nazwij język MBConsumer i ustaw rozszerzenie nazwy pliku na ". Wykorzystaj".

2. W projekcie DSL Dodaj odwołanie do zestawu MBProvider DSL. Kliknij prawym przyciskiem myszy `MBConsumer\Dsl\References` a następnie kliknij pozycję **Dodaj odwołanie**. Na karcie **Przeglądaj** Znajdź `MBProvider\Dsl\bin\Debug\Company.MBProvider.Dsl.dll`

    Dzięki temu można utworzyć kod, który używa innego DSL. Jeśli chcesz utworzyć odwołania do kilku językami DSL, Dodaj je również.

3. Na diagramie definicji DSL, kliknij prawym przyciskiem myszy diagram, a następnie kliknij pozycję **Włącz ModelBus**. W oknie dialogowym wybierz opcję **Włącz tę funkcję DSL, aby korzystać z ModelBus**.

4. W `ExampleElement` klasy Dodaj nową właściwość domeny `MBR` i w okno Właściwości ustaw jej typ na `ModelBusReference`.

5. Kliknij prawym przyciskiem myszy właściwość domeny na diagramie, a następnie kliknij pozycję **Edytuj właściwości specyficzne dla ModelBusReference**. W oknie dialogowym wybierz **element modelu**.

    Ustaw filtr okna dialogowego plików na następujący.

    `Provider File|*.provide`

    Podciąg po "&#124;" to filtr dla okna dialogowego Wybór pliku. Można ustawić, aby zezwalać na dowolnych plików przy użyciu *. \*

    Na liście **Typ elementu modelu** wprowadź nazwy kilku trudniejszych klas domen w dostawcy DSL (na przykład Company. MBProvider. Task). Mogą to być klasy abstrakcyjne. Jeśli pozostawisz pustą listę, użytkownik może ustawić odwołanie do dowolnego elementu.

6. Zamknij okno dialogowe i **Przekształć wszystkie szablony**.

   Utworzono DSL, które może zawierać odwołania do elementów w innym DSL.

### <a name="create-a-modelbus-reference-to-another-file-in-the-solution"></a>Utwórz odwołanie ModelBus do innego pliku w rozwiązaniu

1. W rozwiązaniu MBConsumer naciśnij klawisze CTRL + F5. Eksperymentalne wystąpienie programu Visual Studio otwiera się w projekcie **MBConsumer\Debugging** .

2. Dodaj kopię przykładu. Podaj do projektu **MBConsumer\Debugging** . Jest to konieczne, ponieważ odwołanie ModelBus musi odwoływać się do pliku w tym samym rozwiązaniu.

   1. Kliknij prawym przyciskiem myszy projekt debugowanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący element**.

   2. W oknie dialogowym **Dodaj element** Ustaw filtr na **wszystkie pliki (\*. \*)** .

   3. Przejdź do `MBProvider\Debugging\Sample.provide` a następnie kliknij przycisk **Dodaj**.

3. Otwórz `Sample.consume`.

4. Kliknij jeden przykład kształtu, a następnie w okno właściwości kliknij pozycję **[...]** we właściwości MBR. W oknie dialogowym kliknij przycisk **Przeglądaj** i wybierz pozycję `Sample.provide`. W oknie elementy rozwiń zadanie typ i wybierz jeden z elementów.

5. Zapisz plik. (Nie zamykaj jeszcze eksperymentalnego wystąpienia programu Visual Studio).

   Utworzono model, który zawiera odwołanie ModelBus do elementu w innym modelu.

### <a name="resolve-a-modelbus-reference-in-a-text-template"></a>Rozwiązywanie odwołania ModelBus w szablonie tekstowym

1. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz przykładowy plik szablonu tekstowego. Ustaw jej zawartość w następujący sposób.

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

    - Należy ustawić atrybuty `hostSpecific` i `inherits` dyrektywy `template`.

    - Model konsumenta jest dostępny w zwykły sposób przez procesor dyrektywy, który został wygenerowany w ramach tego języka DSL.

    - Dyrektywy Assembly i import muszą mieć możliwość dostępu do ModelBus i typów dostawcy DSL.

    - Jeśli wiesz, że wiele MBRs jest połączonych z tym samym modelem, lepszym rozwiązaniem jest wywołanie metody tylko jeden raz.

2. Zapisz szablon. Sprawdź, czy plik tekstowy z wynikiem jest podobny do poniższego.

    ```
    ExampleElement1
    ExampleElement2
         ExampleElement2 is linked to Task: Task2
    ```

### <a name="resolve-a-modelbus-reference-in-a-gesture-handler"></a>Rozwiązywanie odwołania ModelBus w procedurze obsługi gestu

1. Zamknij wystąpienie eksperymentalne programu Visual Studio, jeśli jest uruchomione.

2. Dodaj plik o nazwie *MBConsumer\Dsl\Custom.cs* i ustaw jego zawartość na następujące elementy:

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

3. Naciśnij klawisz **Ctrl** +**F5**.

4. W eksperymentalnym wystąpieniu programu Visual Studio Otwórz `Debugging\Sample.consume`.

5. Kliknij dwukrotnie jeden kształt.

    Po ustawieniu dla tego elementu rekordu MBR, przywoływany model zostanie otwarty i zostanie wybrany element, do którego się odwoływano.

## <a name="see-also"></a>Zobacz także

- [Integrowanie modeli za pomocą Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)
- [Generowanie kodu i szablony tekstowe T4](../modeling/code-generation-and-t4-text-templates.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
