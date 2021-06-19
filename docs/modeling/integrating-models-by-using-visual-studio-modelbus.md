---
title: Integrowanie modeli przy użyciu modelubus
description: Dowiedz się, Visual Studio ModelBus metody tworzenia połączeń między modelami i z innych narzędzi do modeli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 350398d91d73a722956d195b300311f313ff34db
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391065"
---
# <a name="integrate-models-by-using-visual-studio-modelbus"></a>Integrowanie modeli przy użyciu Visual Studio Modelbus

Visual Studio ModelBus udostępnia metodę tworzenia połączeń między modelami i z innych narzędzi do modeli. Można na przykład połączyć modele języka specyficznego dla domeny (DSL) i modele UML. Możesz utworzyć zintegrowany zestaw plików DSL.

ModelBus umożliwia utworzenie unikatowego odwołania do modelu lub do określonego elementu wewnątrz modelu. To odwołanie może być przechowywane poza modelem, na przykład w elemencie w innym modelu. Gdy w późniejszym czasie narzędzie chce uzyskać dostęp do elementu, infrastruktura magistrali modelu załaduje odpowiedni model i zwróci element . Jeśli chcesz, możesz wyświetlić model użytkownikowi. Jeśli nie można uzyskać dostępu do pliku w poprzedniej lokalizacji, modelBus poprosi użytkownika o jego znalezienie. Jeśli użytkownik znajdzie plik, modelBus naprawi wszystkie odwołania do tego pliku.

> [!NOTE]
> W bieżącej Visual Studio ModelBus połączone modele muszą być elementami w tym samym Visual Studio rozwiązania.

Aby uzyskać dodatkowe informacje i przykładowy kod, zobacz:

- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Modeling SDK for Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="providing-access-to-a-dsl"></a><a name="provide"></a> Zapewnianie dostępu do DSL
 Przed utworzeniem odwołania ModelBus do modelu lub jego elementów, należy zdefiniować ModelBusAdapter dla DSL. Najprostszym sposobem na to jest użycie rozszerzenia Visual Studio Model Bus, które dodaje polecenia do projektant DSL.

### <a name="to-expose-a-dsl-definition-to-model-bus"></a><a name="expose"></a> Aby uwidocznić definicję DSL dla magistrali modelu

1. Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektową, a następnie kliknij **pozycję Włącz modelbus.**

2. W oknie dialogowym wybierz pozycję Chcę uwidocznić ten **DSL dla modeluBus.** Możesz wybrać obie opcje, jeśli chcesz, aby ten DSL uwidocznił swoje modele i używać odwołań do innych plików DSL.

3. Kliknij przycisk **OK**. Nowy projekt "ModelBusAdapter" jest dodawany do rozwiązania DSL.

4. Jeśli chcesz uzyskać dostęp do DSL z szablonu tekstowego, musisz zmodyfikować AdapterManager.tt w nowym projekcie. Pomiń ten krok, jeśli chcesz uzyskać dostęp do DSL z innego kodu, takiego jak polecenia i programy obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz Using Visual Studio ModelBus in a Text Template (Używanie Visual Studio ModelBus [w szablonie tekstowym).](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

   1. Zmień klasę bazową adapterManagerBase na [VsTextTemplatingModelingAdapterManager.](/previous-versions/ee844317(v=vs.140))

   2. Pod koniec pliku wstaw ten dodatkowy atrybut przed klasy AdapterManager:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. W projekcie References of ModelBusAdapter dodaj plik **Microsoft.VisualStudio.TextTemplating.Modeling.11.0.**

      Aby uzyskać dostęp do DSL zarówno z szablonów tekstowych, jak i z innego kodu, potrzebne są dwie karty, jedna zmodyfikowana i niezmodyfikowana.

5. Kliknij **pozycję Przekształć wszystkie szablony.**

6. Ponownie skompiluj rozwiązanie.

   Teraz jest możliwe, aby ModelBus otworzyć wystąpienia tego DSL.

   Folder zawiera `ModelBusAdapters\bin\*` zestawy sbudowaną przez `Dsl` projekt i `ModelBusAdapters` projekt. Aby odwołać się do tego DSL z innego DSL, należy zaimportować te zestawy.

### <a name="ensure-that-elements-can-be-referenced"></a>Upewnij się, że można odwoływać się do elementów

Visual Studio ModelBus karty domyślnie używają identyfikatora GUID elementu do jego identyfikacji. W związku z tym te identyfikatory muszą być utrwalane w pliku modelu.

Aby upewnić się, że identyfikatory elementów są utrwalane:

1. Otwórz dslDefinition.dsl.

2. W eksploratorze DSL rozwiń pozycję **Zachowanie serializacji XML**, a następnie **pozycję Dane klasy**.

3. Dla każdej klasy, do której chcesz utworzyć odwołania do magistrali modelu:

    Kliknij węzeł klasy i w okno Właściwości upewnij się, że dla właściwości **Serialize ID ustawiono** wartość `true` .

   Alternatywnie, jeśli chcesz używać nazw elementów do identyfikowania elementów zamiast identyfikatorów GUID, możesz przesłonić części wygenerowanych kart. Zastąp następujące metody w klasie adaptera:

- Zastąp `GetElementId` , aby zwrócić identyfikator, którego chcesz użyć. Ta metoda jest wywoływana podczas tworzenia odwołań.

- Zastąp `ResolveElementReference` element w celu zlokalizowania poprawnego elementu w odwołaniu do magistrali modelu.

## <a name="accessing-a-dsl-from-another-dsl"></a><a name="editRef"></a> Uzyskiwanie dostępu do DSL z innego DSL

Odwołania do magistrali modelu można przechowywać we właściwości domeny w dsl i można napisać kod niestandardowy, który z nich korzysta. Możesz również pozwolić użytkownikowi na utworzenie odwołania do magistrali modelu przez wybranie pliku modelu i jego elementu.

Aby umożliwić DSL do używania odwołań do innego DSL, należy najpierw uczynić go *konsumentem* odwołań magistrali modelu.

### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Aby włączyć DSL do obsługi odwołań do ujawnionego DSL

1. W diagramie definicji DSL kliknij prawym przyciskiem myszy główną część diagramu, a następnie kliknij pozycję **Włącz modelbus.**

2. W oknie dialogowym wybierz pozycję **I want to enable this model to consume model bus references (Chcę włączyć** w tym modelu odwołania do magistrali modelu).

3. W projekcie Dsl konsumowania DSL dodaj następujące zestawy do odwołań do projektu. Te zestawy (pliki .dll) można znaleźć w katalogu ModelBusAdapter\bin \\ * widocznego DSL.

    - Ujawniony zestaw DSL, na **przykładFabrikam.FamilyTree.Dsl.dll**

    - Ujawniony zestaw adaptera magistrali modelu, na **przykładFabrikam.FamilyTree.ModelBusAdapter.dll**

4. Dodaj następujące zestawy .NET do odwołań do projektu DSL zużywającego go projektu.

    1. **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

    2. **Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0.dll**

### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Aby zapisać odwołanie do magistrali modelu we właściwości domeny

1. W definicji DSL konsumowania DSL dodaj właściwość domeny do klasy domeny i ustaw jej nazwę.

2. W okno Właściwości z wybraną właściwością domeny ustaw **typ** na `ModelBusReference` .

   Na tym etapie kod programu może ustawić wartość właściwości, ale jest tylko do odczytu w okno Właściwości.

   Możesz zezwolić użytkownikom na ustawianie właściwości za pomocą wyspecjalizowanego edytora odwołania ModelBus. Istnieją dwie wersje tego edytora lub s *wyboru:* jedna umożliwia użytkownikom wybranie pliku modelu, a druga umożliwia użytkownikom wybranie pliku modelu i elementu w modelu.

### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Aby umożliwić użytkownikowi ustawienie odwołania do magistrali modelu we właściwości domeny

1. Kliknij prawym przyciskiem myszy właściwość domeny, a następnie kliknij pozycję **Edytuj modelBusReference określonych właściwości**. Zostanie otwarte okno dialogowe. Jest to s *wyboru magistrali modelu*.

2. Wybierz odpowiedni **rodzaj elementu ModelBusReference**: dla modelu lub elementu wewnątrz modelu.

3. W ciągu filtru okna dialogowego pliku wprowadź ciąg, taki jak `Family Tree files |*.ftree` . Zastąp rozszerzenie pliku widocznego DSL.

4. Jeśli wybierzesz odwołanie do elementu w modelu, możesz dodać listę typów, które użytkownik może wybrać, na przykład Company.FamilyTree.Person.

5. Kliknij **przycisk OK**, a następnie kliknij pozycję **Przekształć wszystkie** szablony na pasku **Eksplorator rozwiązań** narzędzi.

    > [!WARNING]
    > Jeśli nie wybrano prawidłowego modelu lub jednostki, przycisk OK nie będzie mieć żadnego efektu, mimo że może być wyświetlany jako włączony.

6. Jeśli określono listę typów docelowych, takich jak Company.FamilyTree.Person, następnie należy dodać odwołanie do zestawu do projektu DSL, odwołując się do biblioteki DLL docelowego DSL, na przykład Company.FamilyTree.Dsl.dll

### <a name="to-test-a-model-bus-reference"></a>Aby przetestować odwołanie do magistrali modelu

1. Tworzenie zarówno ujawnionych, jak i zużywających plików DSL.

2. Uruchom jeden z plików DSL w trybie eksperymentalnym, naciskając klawisze F5 lub CTRL+F5.

3. W projekcie Debugowanie w eksperymentalnym wystąpieniu Visual Studio dodaj pliki, które są wystąpieniami każdego DSL.

    > [!NOTE]
    > Visual Studio ModelBus rozpoznać odwołania tylko do modeli, które są elementami w tym samym Visual Studio rozwiązania. Na przykład nie można utworzyć odwołania do pliku modelu w innej części systemu plików.

4. Utwórz niektóre elementy i linki w wystąpieniu ujawnionego DSL i zapisz go.

5. Otwórz wystąpienie konsumuje DSL i wybierz element modelu, który ma właściwość odwołania magistrali modelu.

6. W okno Właściwości kliknij dwukrotnie właściwość odwołania magistrali modelu. Zostanie otwarte okno dialogowe s wyboru.

7. Kliknij **przycisk Przeglądaj** i wybierz wystąpienie widocznego DSL.

     S picker umożliwia również wybranie elementu w modelu, jeśli określono rodzaj odwołania magistrali modelu specyficzny dla elementu.

## <a name="creating-references-in-program-code"></a>Tworzenie odwołań w kodzie programu

Jeśli chcesz przechowywać odwołanie do modelu lub elementu wewnątrz modelu, tworzysz element `ModelBusReference` . Istnieją dwa `ModelBusReference` rodzaje: odwołania do modelu i odwołania do elementów.

Aby utworzyć odwołanie do modelu, potrzebujesz elementu AdapterManager DSL, którego model jest wystąpieniem, oraz nazwy pliku lub Visual Studio elementu projektu modelu.

Aby utworzyć odwołanie do elementu, potrzebujesz adaptera dla pliku modelu i elementu, do którego chcesz się odwoływać.

> [!NOTE]
> Za pomocą Visual Studio ModelBus można tworzyć odwołania tylko do elementów w tym samym Visual Studio rozwiązania.

### <a name="import-the-exposed-dsl-assemblies"></a>Importowanie ujawnionych zestawów DSL

W projekcie konsumowania dodaj odwołania do projektu do zestawów DSL i ModelBusAdapter widocznego DSL.

Załóżmy na przykład, że chcesz przechowywać odwołania ModelBus w elementach DSL MusicLibrary. Odwołania ModelBus będą odwoływać się do elementów FamilyTree DSL. W `Dsl` projekcie rozwiązania MusicLibrary w węźle Odwołania dodaj odwołania do następujących zestawów:

- Fabrikam.FamilyTree.Dsl.dll — ujawniony DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll — adapter ModelBus widocznego DSL.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Te zestawy można znaleźć w `ModelBusAdapters` projekcie widocznego DSL, w obszarze `bin\*` .

  W pliku kodu, w którym będą tworzyć odwołania, zazwyczaj trzeba będzie zaimportować następujące przestrzenie nazw:

```csharp
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Aby utworzyć odwołanie do modelu

Aby utworzyć odwołanie do modelu, należy uzyskać dostęp do adapterManager dla widocznego DSL i użyć go do utworzenia odwołania do modelu. Można określić ścieżkę pliku lub `EnvDTE.ProjectItem` .

Z adapterManager można uzyskać adapter, który zapewnia dostęp do poszczególnych elementów w modelu.

> [!NOTE]
> Po zakończeniu pracy z kartą należy usunąć kartę. Najbardziej wygodnym sposobem osiągnięcia tego celu jest instrukcja `using` . Ilustruje to poniższy przykład.

```csharp
// The file path of a model instance of the FamilyTree DSL:
string targetModelFile = "TudorFamilyTree.ftree";
// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Get an adapterManager for the target DSL:
FamilyTreeAdapterManager manager =
    (modelbus.GetAdapterManager(FamilyTreeAdapter.AdapterId)
     as FamilyTreeAdapterManager;
// or: (modelBus.FindAdapterManagers(targetModelFile).First())
// or could provide an EnvDTE.ProjectItem

// Create a reference to the target model:
// NOTE: the target model must be a file in this project.
ModelBusReference modelReference =
     manager.CreateReference(targetModelFile);
// or can use an EnvDTE.ProjectItem instead of the filename

// Get the root element of this model:
using (FamilyTreeAdapter adapter =
     modelBus.CreateAdapter(modelReference) as FamilyTreeAdapter)
{
  FamilyTree modelRoot = adapter.ModelRoot;
  // Access elements under the root in the usual way:
  foreach (Person p in modelRoot.Persons) {...}
  // You can create adapters for individual elements:
  ModelBusReference elementReference =
     adapter.GetElementReference(person);
  ...
} // Dispose adapter
```

Jeśli chcesz mieć możliwość późniejszego użycia, możesz zapisać go we właściwości `modelReference` domeny, która ma typ zewnętrzny `ModelBusReference` :

```csharp
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

Aby umożliwić użytkownikom edytowanie tej właściwości domeny, użyj `ModelReferenceEditor` parametru w atrybutze Edytor. Aby uzyskać więcej informacji, zobacz [Zezwalaj użytkownikowi na edytowanie odwołania](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Aby utworzyć odwołanie do elementu

Adapter utworzony dla modelu może służyć do tworzenia i rozpoznawania odwołań.

```csharp
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

Jeśli chcesz mieć możliwość późniejszego użycia, możesz zapisać go we właściwości `elementReference` domeny, która ma typ zewnętrzny `ModelBusReference` . Aby zezwolić użytkownikom na jego edycję, użyj `ModelElementReferenceEditor` parametru w atrybutze Edytor. Aby uzyskać więcej informacji, zobacz [Zezwalaj użytkownikowi na edytowanie odwołania](#editRef).

### <a name="resolving-references"></a>Rozpoznawanie odwołań

Jeśli masz element `ModelBusReference` (MBR), możesz uzyskać model lub element modelu, do którego się odwołuje. Jeśli element jest przedstawiony na diagramie lub w innym widoku, możesz otworzyć widok i wybrać element.

Można utworzyć kartę z MBR. Z karty można uzyskać katalog główny modelu. Można również rozpoznać mbr, które odnoszą się do określonych elementów w modelu.

```csharp
using Microsoft.VisualStudio.Modeling.Integration; ...
ModelBusReference elementReference = ...;

// Get the ModelBus service:
IModelBus modelBus =
    this.Store.GetService(typeof(SModelBus)) as IModelBus;
// Use a model reference or an element reference
// to obtain an adapter for the target model:
using (FamilyTreeAdapter adapter =
   modelBus.CreateAdapter(elementReference) as FamilyTreeAdapter)
   // or CreateAdapter(modelReference)
{
  // Get the root of the model:
  FamilyTree tree = adapter.ModelRoot;

  // Get a model element:
  MyDomainClass mel =
    adapter.ResolveElementReference<MyDomainClass>(elementReference);
  if (mel != null) {...}

  // Get the diagram or other view, if there is one:
  ModelBusView view = adapter.GetDefaultView();
  if (view != null)
  {
   view.Open();
   // Display the diagram:
   view.Show();
   // Attempt to select the shape that presents the element:
   view.SetSelection(elementReference);
  }
} // Dispose the adapter.
```

#### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Aby rozwiązać problem z odwołaniami ModelBus w szablonie tekstowym

1. Dsl, do którego chcesz uzyskać dostęp, musi mieć kartę ModelBus, która została skonfigurowana do uzyskiwania dostępu za pomocą szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [Zapewnianie dostępu do DSL](#provide).

2. Zazwyczaj uzyskujesz dostęp do docelowego DSL przy użyciu odwołania do magistrali modelu (MBR) przechowywanego w źródłowym DSL. W związku z tym szablon zawiera dyrektywę źródłowego DSL oraz kod do rozpoznawania MBR. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz Generowanie kodu [z Domain-Specific języku](../modeling/generating-code-from-a-domain-specific-language.md).

   ```
   <#@ template debug="true" hostspecific="true"
   inherits="Microsoft.VisualStudio.TextTemplating.Modeling.ModelBusEnabledTextTransformation" #>
   <#@ SourceDsl processor="SourceDslDirectiveProcessor" requires="fileName='Sample.source'" #>
   <#@ output extension=".txt" #>
   <#@ assembly name = "Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0" #>
   <#@ assembly name = "System.Core" #>
   <#@ assembly name = "Company.CompartmentDragDrop.Dsl.dll" #>
   <#@ assembly name = "Company.CompartmentDragDrop.ModelBusAdapter.dll" #>
   <#@ import namespace="Microsoft.VisualStudio.Modeling.Integration" #>
   <#@ import namespace="System.Linq" #>
   <#@ import namespace="Company.CompartmentDragDrop" #>
   <#@ import namespace="Company.CompartmentDragDrop.ModelBusAdapters" #>
   <# // Get source root from directive processor:
     ExampleModel source = this.ExampleModel;
     // This DSL has a MBR in its root:
   using (ModelBusAdapter adapter = this.ModelBus.CreateAdapter(source.ModelReference) as ModelBusAdapter)
     {
     ModelBusAdapterManager manager = this.ModelBus.FindAdapterManagers(this.Host.ResolvePath("Sample.compDD1")).FirstOrDefault();
     ModelBusReference modelReference =
       manager.CreateReference(this.Host.ResolvePath("Sample.compDD1"));

     // Get the root element of this model:
     using (CompartmentDragDropAdapter adapter =
        this.ModelBus.CreateAdapter(modelReference) as CompartmentDragDropAdapter)
     {
       ModelRoot root = adapter.ModelRoot;
   #>
   [[<#= root.Name #>]]
   <#
     }
   #>
   ```

   Aby uzyskać więcej informacji i przewodnik, zobacz [Using Visual Studio ModelBus in a Text Template (Używanie Visual Studio ModelBus w szablonie tekstowym)](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Serializowanie modeluBusReference

Jeśli chcesz przechowywać `ModelBusReference` (MBR) w postaci ciągu, można serializować go:

```csharp
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

MbR, który jest serializowany w ten sposób jest niezależny od kontekstu. Jeśli używasz prostej karty magistrali modelu opartej na plikach, mbr zawiera ścieżkę bezwzględną pliku. Jest to wystarczające, jeśli pliki modelu wystąpienia nigdy nie zostaną przeniesiene. Jednak pliki modelu zazwyczaj będą elementami w Visual Studio projektu. Użytkownicy będą mogli przenieść cały projekt do różnych części systemu plików. Będą oni również mogli zachować kontrolę źródła projektu i otworzyć go na różnych komputerach. W związku z tym nazwy ścieżek powinny być serializowane względem lokalizacji projektu, który zawiera pliki.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serializowanie względem określonej ścieżki pliku

Zawiera , który jest słownikiem, w którym można przechowywać informacje, takie jak ścieżka pliku względna, do której `ModelBusReference` `ReferenceContext` ma być serializowana.

Aby serializować względem ścieżki:

```csharp
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

Aby pobrać odwołanie z ciągu:

```csharp
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>ModelBusReferences utworzone przez inne karty
 Poniższe informacje są przydatne, jeśli chcesz utworzyć własną kartę sieciową.

 Element (MBR) składa się z dwóch części: nagłówka MBR, który jest deserializowany przez magistralę modelu, oraz specyficznego dla adaptera, który jest obsługiwany przez `ModelBusReference` określonego menedżera adaptera. Dzięki temu można podać własny format serializacji karty. Na przykład można odwoływać się do bazy danych, a nie do pliku, lub można przechowywać dodatkowe informacje w odwołani do adaptera. Twoja własna karta może umieścić dodatkowe informacje w `ReferenceContext` .

 Podczas deserializować MBR, należy podać ReferenceContext, który jest następnie przechowywany w obiekcie MBR. Podczas serializacji MBR przechowywane ReferenceContext jest używany przez adapter do generowania ciągu. Zdeserializowany ciąg nie zawiera wszystkich informacji w referenceContext. Na przykład w przypadku prostej karty opartej na plikach referenceContext zawiera ścieżkę pliku głównego, która nie jest przechowywana w serializowanym ciągu MBR.

 MbR jest deserializowany w dwóch etapach:

- `ModelBusReferencePropertySerializer` to standardowy serializator, który zajmuje się nagłówkiem MBR. Używa ona standardowego zestawu właściwości `SerializationContext` DSL, który jest przechowywany w `ReferenceContext` obiekcie przy użyciu klucza `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` . W szczególności element `SerializationContext` powinien zawierać wystąpienie klasy `ModelBus` .

- Karta ModelBus obsługuje część MBR specyficzną dla karty. Może używać dodatkowych informacji przechowywanych w referenceContext MBR. Prosta karta oparta na plikach przechowuje ścieżki plików głównych przy użyciu kluczy `FilePathLoadContextKey` i `FilePathSaveContextKey` .

     Odwołanie do adaptera w pliku modelu jest deserializowane tylko wtedy, gdy jest używane.

## <a name="to-create-a-model"></a>Aby utworzyć model

### <a name="creating-opening-and-editing-a-model"></a>Tworzenie, otwieranie i edytowanie modelu
 Poniższy fragment pochodzi z przykładu State Machine w witrynie sieci Web VMSDK. Ilustruje on użycie klasy ModelBusReferences do utworzenia i otwarcia modelu oraz uzyskania diagramu skojarzonego z modelem.

 W tym przykładzie nazwa docelowego DSL jest StateMachine. Pochodzi z niego kilka nazw, takich jak nazwa klasy modelu i nazwa klasy ModelBusAdapter.

```csharp
using Fabrikam.StateMachine.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
using Microsoft.VisualStudio.Modeling.Integration;
using Microsoft.VisualStudio.Modeling.Integration.Shell;
using Microsoft.VisualStudio.Modeling.Shell;
...
// Create a new model.
ModelBusReference modelReference =
   StateMachineAdapterManager    .CreateStateMachineModel(modelName, fileName);
//Keep reference of new model in this model.
using (Transaction t = ...)
{
  myModelElement.ReferenceProperty = modelReference;
  t.Commit();
}
// Get the ModelBus service from Visual Studio.
IModelBus modelBus = Microsoft.VisualStudio.Shell.Package.
    GetGlobalService(typeof(SModelBus)) as IModelBus;
// Get a modelbus adapter on the new model.
ModelBusAdapter modelBusAdapter;
modelBus.TryCreateAdapter(modelReference,
    this.ServiceProvider, out modelBusAdapter);
using (StateMachineAdapter adapter =
      modelBusAdapter as StateMachineAdapter)
{
    if (adapter != null)
    {
        // Obtain a Diagram from the adapter.
        Diagram targetDiagram =
           ((StandardVsModelingDiagramView)
                 adapter.GetDefaultView()
            ).Diagram;

        using (Transaction t =
             targetDiagram.Store.TransactionManager
                .BeginTransaction("Update diagram"))
        {
            DoUpdates(targetDiagram);
            t.Commit();
        }

        // Display the new diagram.
        adapter.GetDefaultView().Show();
    }
}
```

## <a name="validating-references"></a>Sprawdzania poprawności odwołań
 BrokenReferenceDetector testuje wszystkie właściwości domeny w magazynie, który może przechowywać modelBusReferences. Wywołuje ona akcję, która umożliwia podanie miejsca, w którym zostanie znaleziona dowolna akcja. Jest to szczególnie przydatne w przypadku metod walidacji. Następująca metoda walidacji testuje magazyn na próbie zapisania modelu i zgłasza uszkodzone odwołania w oknie błędów:

```csharp
[ValidationMethod(ValidationCategories.Save)]
public void ValidateModelBusReferences(ValidationContext context)
{
  BrokenReferenceDetector.DetectBrokenReferences(this.Store,
    delegate(ModelElement element, // parent of property
             DomainPropertyInfo property, // identifies property
             ModelBusReference reference) // invalid reference
    {
      context.LogError(string.Format(INVALID_REF_FORMAT,
             property.Name,
             referenceState.Name,
             new ModelBusReferenceTypeConverter().
                 ConvertToInvariantString(reference)),
         "Reference",
         element);
      });
}}
private const string INVALID_REF_FORMAT =
    "The '{0}' domain property of ths ReferenceState instance "
  + "named '{1}' contains reference value '{2}' which is invalid";
```

## <a name="actions-performed-by-the-modelbus-extension"></a>Akcje wykonywane przez rozszerzenie ModelBus

Poniższe informacje nie są niezbędne, ale mogą być przydatne w przypadku intensywnego korzystania z magistrali modelu.

Rozszerzenie ModelBus wprowadza następujące zmiany w rozwiązaniu DSL.

Po kliknięciu prawym przyciskiem myszy diagramu definicji DSL kliknij pozycję Włącz **modelbus,** a następnie wybierz pozycję Włącz ten DSL, aby **korzystać z modeluBus:**

- W projekcie DSL dodano odwołanie do **Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0.dll**

- W definicji DSL dodawane jest odwołanie do typu zewnętrznego: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference` .

   Odwołanie można znaleźć w Eksploratorze **DSL** w obszarze **Typy domen**. Aby ręcznie dodać odwołania do typu zewnętrznego, kliknij prawym przyciskiem myszy węzeł główny.

- Zostanie dodany nowy plik szablonu **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

Po ustawieniu typu właściwości domeny na ModelBusReference, a następnie kliknij prawym przyciskiem myszy właściwość i kliknij polecenie **Włącz modelBusReference określonych właściwości:**

- Kilka atrybutów CLR są dodawane do właściwości domeny. Możesz je wyświetlić w polu Atrybuty niestandardowe w okno Właściwości. W **pliku Dsl\GeneratedCode\DomainClasses.cs** można zobaczyć atrybuty w deklaracji właściwości:

  ```csharp
  [System.ComponentModel.TypeConverter(typeof(
  Microsoft.VisualStudio.Modeling.Integration.ModelBusReferenceTypeConverter))]
  [System.ComponentModel.Editor(typeof(
    Microsoft.VisualStudio.Modeling.Integration.Picker
    .ModelReferenceEditor // or ModelElementReferenceEditor
    ), typeof(System.Drawing.Design.UITypeEditor))]
  [Microsoft.VisualStudio.Modeling.Integration.Picker
    .SupplyFileBasedBrowserConfiguration
    ("Choose a model file", "Target model|*.target")]
  ```

Po kliknięciu prawym przyciskiem myszy diagram definicji DSL, kliknij przycisk **Włącz modelBus,** a następnie wybierz **uwidocznić ten DSL do ModelBus:**

- Do rozwiązania `ModelBusAdapter` zostanie dodany nowy projekt.

- Odwołanie do `ModelBusAdapter` jest dodawane do `DslPackage` projektu. `ModelBusAdapter` ma odwołanie do `Dsl` projektu.

- W **dslPackage\source.extention.tt**, `|ModelBusAdapter|` jest dodawany jako składnik MEF.

## <a name="see-also"></a>Zobacz też

- [Porady: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)
- [Użycie programu Visual Studio ModelBus w szablonie tekstu](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
