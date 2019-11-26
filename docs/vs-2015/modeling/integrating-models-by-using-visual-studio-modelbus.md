---
title: Integrowanie modeli za pomocą Modelbus | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9abb8bd82f8a00c37cb76588ded8813ec984067
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298893"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Integrowanie modeli za pomocą Visual Studio Modelbus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus zapewnia metodę tworzenia linków między modelami i z innych narzędzi do modeli. Na przykład możesz połączyć modeli języka specyficznego dla domeny (DSL) i modeli UML. Możesz utworzyć zintegrowany zestaw językami DSL.

 ModelBus umożliwia utworzenie unikatowych odwołania do modelu lub do określonego elementu w modelu. To odwołanie mogą być przechowywane poza modelem, na przykład w elemencie w innym modelem. Gdy przy późniejszej okazji, narzędzie chce, aby uzyskać dostęp do elementu, infrastruktury Model Bus odpowiedni model obciążenia i zwraca element. Jeśli chcesz, możesz wyświetlić modelu do użytkownika. Jeśli plik nie jest dostępny w poprzedniej lokalizacji, ModelBus będzie monitować użytkownika o znalezienie go. Jeśli użytkownik znajduje się plik, ModelBus naprawi wszystkie odwołania do tego pliku.

> [!NOTE]
> W bieżącej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] implementacji ModelBus połączone modele muszą być elementami w tym samym rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Aby uzyskać dodatkowe informacje i przykładowy kod zobacz:

- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Modeling SDK dla programu Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

## <a name="provide"></a>Zapewnianie dostępu do DSL
 Przed utworzeniem ModelBus odwołania do modelu lub jego elementy, należy zdefiniować element ModelBusAdapter dla języka DSL. Najprostszym sposobem jest użycie rozszerzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model bus, które dodaje polecenia do projektant DSL.

### <a name="expose"></a>Aby uwidocznić definicję DSL dla magistrali modelu

1. Pobierz i zainstaluj rozszerzenie programu Visual Studio Model Bus, chyba że użytkownik jest już zainstalowany. Aby uzyskać więcej informacji, zobacz temat [Wizualizacja i Modeling SDK](https://go.microsoft.com/fwlink/?LinkID=185579).

2. Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij pozycję **Włącz ModelBus**.

3. W oknie dialogowym wybierz opcję **Chcę uwidocznić ten DSL w ModelBus**. Można wybrać obu opcji, jeśli chcesz, aby tego języka DSL, aby uwidocznić jej modeli i korzystanie z odwołań do innych języków DSL.

4. Kliknij przycisk **OK**. Nowy projekt "Elementu ModelBusAdapter" jest dodawany do rozwiązania DSL.

5. Jeśli chcesz uzyskać dostęp do język DSL z szablonu tekstu, należy zmodyfikować AdapterManager.tt w nowym projekcie. Pomiń ten krok, jeśli chcesz uzyskać dostęp do język DSL od innego kodu, takich jak polecenia i procedury obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [używanie Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Zmień klasę bazową AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

   2. Pod koniec pliku Wstaw ten atrybut dodatkowe przed klasy element AdapterManager:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. W odniesieniu do projektu ModelBusAdapter Dodaj **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**.

      Jeśli chcesz uzyskać dostęp język DSL, zarówno z poziomu szablonów tekstu, jak i z innego kodu, należy dwóch kart: jeden zmodyfikowane, a drugi w niezmienionej postaci.

6. Kliknij kolejno pozycje **Przekształć wszystkie szablony**.

7. Ponownie skompiluj rozwiązanie.

   Teraz jest możliwa do ModelBus otworzyć wystąpień tego języka DSL.

   Folder `ModelBusAdapters\bin\*` zawiera zestawy skompilowane przez projekt `Dsl` i projekt `ModelBusAdapters`. Aby odwoływać się do tego języka DSL z innego języka DSL, należy zaimportować te zestawy.

### <a name="making-sure-that-elements-can-be-referenced"></a>Upewnij się, że elementy mogą być przywoływane
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] karty ModelBus używają identyfikatora GUID elementu, aby zidentyfikować go domyślnie. Tych identyfikatorów w związku z tym musi być utrwalone w pliku modelu.

##### <a name="to-ensure-that-element-ids-are-persisted"></a>Aby upewnić się, że element identyfikatory są zachowywane

1. Otwórz DslDefinition.dsl.

2. W Eksploratorze DSL rozwiń opcję **zachowanie serializacji XML**, a następnie **dane klasy**.

3. Dla każdej klasy, do której chcesz utworzyć Model Bus odwołuje się:

    Kliknij węzeł Klasa i w okno Właściwości upewnij się, że **Identyfikator serializacji** jest ustawiony na `true`.

   Alternatywnie, jeśli chcesz użyć nazwy elementów do identyfikowania elementów zamiast identyfikatory GUID, można zastąpić części wygenerowanego kart. Należy zastąpić następujące metody w klasie karty:

- Przesłoń `GetElementId`, aby zwrócić identyfikator, którego chcesz użyć. Ta metoda jest wywoływana podczas tworzenia odwołania.

- Przesłoń `ResolveElementReference`, aby zlokalizować prawidłowy element z odwołania do magistrali modelu.

## <a name="editRef"></a>Dostęp do DSL z innego modemu DSL
 Odwołania do modelu magistrali można przechowywać we właściwości domeny w DSL i można napisać kod niestandardowy, który korzysta z nich. Można także pozwolić użytkownikom na tworzenie odwołanie magistrali modelu, pobierania pliku modelu i elemencie.

 Aby włączyć użycie przez DSL odwołań do innego DSL, należy najpierw utworzyć *odbiorcę* odwołań do magistrali modelu.

#### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Aby włączyć DSL korzystanie z odwołań do narażonych DSL

1. Na diagramie definicji DSL kliknij prawym przyciskiem myszy główną część diagramu, a następnie kliknij pozycję **Włącz ModelBus**.

2. W oknie dialogowym wybierz opcję **Chcę włączyć ten model, aby korzystać z odwołań do magistrali modelu**.

3. W projekcie języka Dsl konsumencki DSL należy dodać następujące zestawy do odwołań projektu. Te zestawy (pliki. dll) znajdują się w katalogu ModelBusAdapter\bin\\* w udostępnionym DSL.

    - Zestaw dostępnego DSL, na przykład **fabrikam. FamilyTree. DSL. dll**

    - Zestaw udostępnionej karty magistrali modelu, na przykład **fabrikam. FamilyTree. ModelBusAdapter. dll**

4. Dodaj następujące zestawy .NET do odwołania do projektu konsumencki projektu DSL.

    1. **Microsoft. VisualStudio. Modeling. Sdk. Integration. 11.0. dll**

    2. **Microsoft. VisualStudio. Modeling. Sdk. Integration. Shell. 11.0. dll**

#### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Do przechowywania odwołania magistrali modelu we właściwości domeny

1. W definicji DSL konsumencki DSL Dodaj właściwość domeny do klasy domeny i ustaw jego nazwę.

2. W okno Właściwości z wybraną właściwością domena ustaw wartość **Typ** na `ModelBusReference`.

   Na tym etapie kod programu, można ustawić wartości właściwości, ale jest tylko do odczytu w oknie dialogowym właściwości.

   Możesz zezwalać użytkownikom można ustawić właściwości przy użyciu specjalnego edytora odwołanie ModelBus. Istnieją dwie wersje tego edytora lub *selektora:* jeden umożliwia użytkownikom wybranie pliku modelu, a drugi umożliwia użytkownikom wybranie pliku modelu i elementu w modelu.

#### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Aby zezwolić użytkownikowi na ustawianie odwołanie magistrali modelu we właściwości domeny

1. Kliknij prawym przyciskiem myszy Właściwość domena, a następnie kliknij pozycję **Edytuj właściwości specyficzne dla ModelBusReference**. Zostanie otwarte okno dialogowe. Jest to *Selektor magistrali modelu*.

2. Wybierz odpowiedni **rodzaj ModelBusReference**: do modelu lub do elementu wewnątrz modelu.

3. W polu ciąg filtru okna dialogowego plików wprowadź ciąg, taki jak `Family Tree files |*.ftree`. Subsitute rozszerzenie pliku narażonych DSL.

4. Jeśli wybrano odwoływać się do elementu w modelu, można dodać listę typów, które użytkownik może wybrać, na przykład Company.FamilyTree.Person.

5. Kliknij przycisk **OK**, a następnie kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań.

    > [!WARNING]
    > Jeśli nie wybrano prawidłowego modelu lub jednostki przycisku OK nie wpłyną, mimo że może pojawić się włączone.

6. Jeśli określono listę typów docelowych, takich jak Company.FamilyTree.Person, następnie należy dodać odwołanie do zestawu do projektu DSL odwołuje się do elementu docelowego DSL, na przykład Company.FamilyTree.Dsl.dll biblioteki DLL

#### <a name="to-test-a-model-bus-reference"></a>Aby przetestować odwołanie magistrali modelu

1. Twórz zarówno narażonych i korzystanie z nich języków DSL.

2. Uruchom jedno z języków DSL w trybie doświadczalnym, naciskając klawisz F5 lub CTRL + F5.

3. W projekcie debugowania w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Dodaj pliki, które są wystąpieniami poszczególnych DSL.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus może rozpoznać tylko odwołania do modeli, które są elementami w tym samym rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Na przykład nie można utworzyć odwołania do pliku modelu w innej części systemu plików.

4. Utwórz niektóre elementy i łącza w wystąpieniu narażonych DSL i zapisz go.

5. Otwórz wystąpienie konsumencki DSL, a następnie wybierz element modelu, który ma właściwość odwołanie magistrali modelu.

6. W oknie właściwości kliknij dwukrotnie model bus referencyjna właściwość. Zostanie otwarte okno dialogowe selektora.

7. Kliknij przycisk **Przeglądaj** i wybierz wystąpienie uwidocznionego DSL.

     Selektor również umożliwi wybranie elementu w modelu, jeśli określony rodzaj specyficzne dla elementu modelu magistrali odwołania.

## <a name="creating-references-in-program-code"></a>Tworzenie odwołań w kodzie programu
 Jeśli chcesz przechowywać odwołanie do modelu lub elementu wewnątrz modelu, tworzysz `ModelBusReference`. Istnieją dwa rodzaje `ModelBusReference`: odwołania do modelu i odwołania do elementów.

 Aby utworzyć odwołanie do modelu, potrzebna jest karta DSL, dla której model jest wystąpienie, oraz nazwa pliku lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] elementu projektu modelu.

 Aby utworzyć odwołanie do elementu, potrzebna jest karta pliku modelu i element, którego ma dotyczyć.

> [!NOTE]
> Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus można tworzyć odwołania tylko do elementów w tym samym rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

### <a name="import-the-exposed-dsl-assemblies"></a>Importowanie narażonych zestawów języka DSL
 W projekcie odbierająca komunikaty należy dodać odwołania projektu do zestawów DSL i elementu ModelBusAdapter narażonych DSL.

 Na przykład załóżmy, że chcesz przechowywać ModelBus odwołania w elementach MusicLibrary DSL. Odwołania ModelBus będzie odnosił się do elementów FamilyTree język DSL. W `Dsl` projekcie rozwiązania MusicLibrary w węźle odwołania Dodaj odwołania do następujących zestawów:

- Fabrikam.FamilyTree.Dsl.dll - narażonych DSL.

- Fabrikam.FamilyTree.ModelBusAdapters.dll - karty ModelBus narażonych DSL.

- Microsoft.VisualStudio.Modeling.Sdk.Integration.11.0

- Microsoft.VisualStudio.Modeling.Sdk.Integration.Shell.11.0

  Te zestawy mogą znajdować się w `ModelBusAdapters` projekcie uwidocznionych linii DSL w obszarze `bin\*`.

  W pliku kodu, w której tworzysz odwołania zazwyczaj trzeba będzie zaimportować te przestrzenie nazw:

```
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Można utworzyć odwołania do modelu
 Można utworzyć odwołania do modelu, dostęp element AdapterManager narażonych DSL i umożliwia utworzenie odwołania do modelu. Można określić ścieżkę pliku lub `EnvDTE.ProjectItem`.

 Z AdapterManager można uzyskać karty, która zapewnia dostęp do poszczególnych elementów w modelu.

> [!NOTE]
> Po zakończeniu z nim, musi dysponować karty. Najwygodniejszym sposobem osiągnięcia tego celu jest instrukcja `using`. Ilustruje to poniższy przykład.

```
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

 Jeśli chcesz mieć możliwość późniejszego użycia `modelReference`, możesz zapisać go we właściwości domeny z typem zewnętrznym `ModelBusReference`:

```
using Transaction t = this.Store.TransactionManager
    .BeginTransaction("keep reference"))
{
  artist.FamilyTreeReference = modelReference;
  t.Commit();
}
```

 Aby umożliwić użytkownikom edytowanie tej właściwości domeny, użyj `ModelReferenceEditor` jako parametru w atrybucie edytora. Aby uzyskać więcej informacji, zobacz [Zezwalanie użytkownikowi na edytowanie odwołania](#editRef).

### <a name="to-create-a-reference-to-an-element"></a>Aby utworzyć odwołanie do elementu
 Karty, który został utworzony w modelu może służyć do tworzenia i rozpoznawania odwołań.

```
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

 Jeśli chcesz mieć możliwość późniejszego użycia `elementReference`, możesz zapisać go we właściwości domeny z typem zewnętrznym `ModelBusReference`. Aby umożliwić użytkownikom edycję, użyj `ModelElementReferenceEditor` jako parametru w atrybucie edytora. Aby uzyskać więcej informacji, zobacz [Zezwalanie użytkownikowi na edytowanie odwołania](#editRef).

### <a name="resolving-references"></a>Rozpoznawanie odwołania
 Jeśli masz `ModelBusReference` (MBR), możesz uzyskać model lub element modelu, do którego się odwołuje. Jeśli element jest wyświetlane na diagramie lub w innym widoku, można otworzyć widoku i wybierz element.

 Można utworzyć adapter z MBR. Z karty sieciowej można uzyskać korzeń modelu. Można także rozwiązać MBRs, które odwołują się do określonych elementów w obrębie modelu.

```
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

##### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Aby rozwiązać odwołania ModelBus w szablonie tekstu

1. DSL, który chcesz uzyskać dostęp do musi mieć kartę ModelBus, który został skonfigurowany do dostępu przez Szablony tekstowe. Aby uzyskać więcej informacji, zobacz [zapewnianie dostępu do DSL](#provide).

2. Zazwyczaj można będą uzyskiwać dostęp do obiektu docelowego, który DSL za pomocą odwołania magistrali modelu (MBR) przechowywane w źródle DSL. Szablon zawiera w związku z tym dyrektywa źródła DSL, a także kod można rozpoznać MBR. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

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

   Aby uzyskać więcej informacji i przewodnik, zobacz [używanie Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md)

## <a name="serializing-a-modelbusreference"></a>Serializacja ModelBusReference
 Jeśli chcesz przechowywać `ModelBusReference` (MBR) w postaci ciągu, można serializować go:

```
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

 MBR, który jest serializowany w ten sposób nie zależy od kontekstu. Jeśli używasz proste karty magistrali opartych na plikach modelu główny rekord rozruchowy zawiera bezwzględną ścieżkę do pliku. Jest to wystarczające, jeśli pliki modelu wystąpienia nigdy nie jest przenoszony. Jednak pliki modelu zwykle będą elementami w projekcie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Użytkownicy będą należy oczekiwać, że może być konieczne przeniesienie całego projektu do różnych części systemu plików. Zostanie również oczekuje, że można zachować projektu objętego kontrolą źródła, a następnie otwórz go na różnych komputerach. Nazwy ścieżek w związku z tym powinien zostać Zserializowany względem lokalizacji pliku projektu, który zawiera pliki.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serializacja względem określonej ścieżki pliku
 `ModelBusReference` zawiera `ReferenceContext`, który jest słownikiem, w którym można przechowywać informacje, takie jak ścieżka do pliku, względem której powinna być serializowana.

 Do serializacji względem ścieżki:

```
elementReference.ReferenceContext.Add(
   ModelBusReferencePropertySerializer.FilePathSaveContextKey,
   currentProjectFilePath);
string serialized = modelBus.SerializeReference(elementReference);
```

 Aby pobrać odwołanie z ciągu:

```
ReferenceContext context = new ReferenceContext();
context.Add(ModelBusReferencePropertySerializer.FilePathLoadContextKey,
    currentProjectFilePath);
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, context);
```

### <a name="modelbusreferences-created-by-other-adapters"></a>ModelBusReferences utworzone przez innych kart
 Następujące informacje są przydatne, jeśli chcesz tworzyć własne karty.

 `ModelBusReference` (MBR) składa się z dwóch części: nagłówka MBR, który jest deserializowany przez magistralę modelu i specyficzne dla adaptera, który jest obsługiwany przez określonego Menedżera adapterów. Dzięki temu możesz podać własne format serializacji karty. Na przykład można odwoływać się bazy danych, a nie plikiem lub uzyskać dodatkowe informacje można przechowywać w odwołaniu do karty. Twoja własna karta może umieścić dodatkowe informacje w `ReferenceContext`.

 Podczas deserializacji MBR, musisz podać ReferenceContext, który następnie jest przechowywany w obiekcie MBR. Serializujesz MBR przechowywanych ReferenceContext jest używany przez kartę ułatwiający Generowanie ciągu. Zdeserializowany ciąg nie zawiera wszystkie informacje w ReferenceContext. Na przykład prosty adapter opartych na plikach, ReferenceContext zawiera główny ścieżki pliku, która nie znajduje się w ciągu MBR serializacji.

 Główny rekord rozruchowy jest przeprowadzona w dwóch etapach:

- `ModelBusReferencePropertySerializer` to standardowy Serializator, który zajmuje się nagłówkiem MBR. Używa standardowego zbioru właściwości `SerializationContext` DSL, który jest przechowywany w `ReferenceContext` przy użyciu `ModelBusReferencePropertySerializer.ModelBusLoadContextKey`klucza. W szczególności `SerializationContext` powinien zawierać wystąpienie `ModelBus`.

- Karta ModelBus zajmuje się częścią kart MBR. Może używać dodatkowych informacji przechowywanych w ReferenceContext z MBR. Prosta karta oparta na plikach zachowuje ścieżki plików głównych przy użyciu kluczy `FilePathLoadContextKey` i `FilePathSaveContextKey`.

     Odwołanie karty w pliku modelu jest przeprowadzona tylko wtedy, gdy jest używany.

## <a name="to-create-a-model"></a>Aby utworzyć Model

### <a name="creating-opening-and-editing-a-model"></a>Tworzenie, otwieranie i edytowanie modelu
 Poniższy fragment jest pobierana z przykładu automatu stanów w witrynie sieci Web VMSDK. Przykład ilustruje użycie ModelBusReferences, aby utworzyć i otworzyć modelu oraz w celu uzyskania diagram skojarzonego z tym modelem.

 W tym przykładzie nazwa obiektu docelowego DSL jest automat stanów. Kilka nazw są uzyskiwane z nich, takie jak nazwa klasy modelu i nazwę elementu ModelBusAdapter.

```
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

## <a name="validating-references"></a>Sprawdzanie poprawności odwołania
 BrokenReferenceDetector sprawdza wszystkie właściwości domeny w Store, który może pomieścić ModelBusReferences. Wywołuje akcję, podaj, gdzie znajduje się żadnych działań. Jest to szczególnie przydatne w przypadku metody sprawdzania poprawności. Następujące metody sprawdzania poprawności testów magazynu na podjęto próbę zapisania modelu, a następnie raportuje uszkodzenie odwołań w oknie błędów:

```
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
 Poniższe informacje nie jest istotne, ale mogą być przydatne, jeśli wprowadzisz zwiększone użycie ModelBus.

 Rozszerzenie ModelBus wprowadza następujące zmiany w rozwiązaniu języka DSL.

 Po kliknięciu prawym przyciskiem myszy diagramu definicji DSL kliknij pozycję **Włącz ModelBus**, a następnie wybierz opcję **Włącz tę funkcję DSL, aby korzystać z ModelBus**:

- W projekcie DSL odwołanie jest dodawane do **Microsoft. VisualStudio. Modeling. Sdk. Integration. 11.0. dll**

- W definicji DSL dodawane jest odwołanie do typu zewnętrznego: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Odwołanie można zobaczyć w **Eksploratorze DSL**, w obszarze **typy domen**. Aby ręcznie dodać odwołania do typu zewnętrznego, kliknij prawym przyciskiem myszy węzeł główny.

- Dodawany jest nowy plik szablonu, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

  Po ustawieniu typu właściwości domeny na ModelBusReference, a następnie kliknięciu prawym przyciskiem myszy właściwości i kliknięciu opcji **Włącz określone właściwości ModelBusReference**:

- Kilka atrybutów CLR są dodawane do właściwości domeny. Można je wyświetlić w polu atrybutów niestandardowych, w oknie dialogowym właściwości. W **Dsl\GeneratedCode\DomainClasses.cs**można zobaczyć atrybuty deklaracji właściwości:

  ```
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

  Po kliknięciu prawym przyciskiem myszy diagramu definicji DSL kliknij pozycję **Włącz ModelBus**i wybierz opcję **Uwidocznij ten DSL w ModelBus**:

- Do rozwiązania zostanie dodany nowy `ModelBusAdapter` projektu.

- Odwołanie do `ModelBusAdapter` jest dodawane do projektu `DslPackage`. `ModelBusAdapter` ma odwołanie do projektu `Dsl`.

- W **DslPackage\source.extention.tt**`|ModelBusAdapter|` jest dodawany jako składnik MEF.

## <a name="see-also"></a>Zobacz też
 [Instrukcje: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md) [integrowanie modeli UML z innymi modelami i narzędzia](../modeling/integrate-uml-models-with-other-models-and-tools.md) [: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md) [przy użyciu Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md)
