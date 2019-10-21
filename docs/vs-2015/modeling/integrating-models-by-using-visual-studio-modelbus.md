---
title: Integrowanie modeli za pomocą ModelBus | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ff722f3-21d6-44e2-9efd-f6694aee9987
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bbb22dd65b806672c7ec2b4888ed8142764f908e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646160"
---
# <a name="integrating-models-by-using-visual-studio-modelbus"></a>Integrowanie modeli za pomocą Visual Studio Modelbus
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus zapewnia metodę tworzenia linków między modelami i z innych narzędzi do modeli. Można na przykład połączyć modele języka (DSL) specyficzne dla domeny i modele UML. Można utworzyć zintegrowany zestaw językami DSL.

 ModelBus umożliwia utworzenie unikatowego odwołania do modelu lub do określonego elementu wewnątrz modelu. To odwołanie może być przechowywane poza modelem, na przykład w elemencie w innym modelu. Gdy w późniejszym czasie, narzędzie chce uzyskać dostęp do elementu, infrastruktura magistrali modelu będzie ładować odpowiedni model i zwrócić element. Jeśli chcesz, możesz wyświetlić model dla użytkownika. Jeśli w poprzedniej lokalizacji nie można uzyskać dostępu do pliku, program ModelBus wyświetli monit o jego znalezienie. Jeśli użytkownik odnajdzie plik, ModelBus naprawi wszystkie odwołania do tego pliku.

> [!NOTE]
> W bieżącej [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] implementacji ModelBus połączone modele muszą być elementami w tym samym rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

 Aby uzyskać dodatkowe informacje i przykładowy kod, zobacz:

- [Instrukcje: Dodawanie obsługi przeciągania i upuszczania](../modeling/how-to-add-a-drag-and-drop-handler.md)

- [Modeling SDK dla programu Visual Studio](https://www.microsoft.com/download/details.aspx?id=48148)

## <a name="provide"></a>Zapewnianie dostępu do DSL
 Aby można było utworzyć odwołania ModelBus do modelu lub jego elementów, należy zdefiniować ModelBusAdapter dla DSL. Najprostszym sposobem jest użycie rozszerzenia [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] model bus, które dodaje polecenia do projektant DSL.

### <a name="expose"></a>Aby uwidocznić definicję DSL dla magistrali modelu

1. Pobierz i zainstaluj rozszerzenie magistrali modelu programu Visual Studio, chyba że zostało już zainstalowane. Aby uzyskać więcej informacji, zobacz temat [Wizualizacja i Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=185579).

2. Otwórz plik definicji DSL. Kliknij prawym przyciskiem myszy powierzchnię projektu, a następnie kliknij pozycję **Włącz ModelBus**.

3. W oknie dialogowym wybierz opcję **Chcę uwidocznić ten DSL w ModelBus**. Możesz wybrać obie opcje, jeśli chcesz, aby ta linia DSL mogła uwidocznić swoje modele i wykorzystać odwołania do innych językami DSL.

4. Kliknij przycisk **OK**. Do rozwiązania DSL zostanie dodany nowy projekt "ModelBusAdapter".

5. Jeśli chcesz uzyskać dostęp do modemu DSL z szablonu tekstu, musisz zmodyfikować AdapterManager.tt w nowym projekcie. Pomiń ten krok, jeśli chcesz uzyskać dostęp do DSL z innego kodu, takiego jak polecenia i programy obsługi zdarzeń. Aby uzyskać więcej informacji, zobacz [używanie Visual Studio ModelBus w szablonie tekstowym](../modeling/using-visual-studio-modelbus-in-a-text-template.md).

   1. Zmień klasę bazową AdapterManagerBase na [VsTextTemplatingModelingAdapterManager](/previous-versions/ee844317(v=vs.140)).

   2. Po zakończeniu ostatniego pliku Wstaw ten dodatkowy atrybut przed klasą AdapterManager:

       `[Microsoft.VisualStudio.Modeling.Integration.HostSpecific(HostName)]`

   3. W odniesieniu do projektu ModelBusAdapter Dodaj **Microsoft. VisualStudio. TextTemplating. Modeling. 11.0**.

      Jeśli chcesz uzyskać dostęp do linii DSL zarówno z szablonów tekstu, jak i z innego kodu, musisz mieć dwie karty, jeden modyfikowany i jeden niemodyfikowany.

6. Kliknij kolejno pozycje **Przekształć wszystkie szablony**.

7. Ponownie skompiluj rozwiązanie.

   Możliwe jest teraz, aby ModelBus otwarte wystąpienia tego języka DSL.

   Folder `ModelBusAdapters\bin\*` zawiera zestawy skompilowane przez projekt `Dsl` i projekt `ModelBusAdapters`. Aby odwołać się do tego języka DSL z innego modemu DSL, należy zaimportować te zestawy.

### <a name="making-sure-that-elements-can-be-referenced"></a>Upewnienie się, że elementy mogą być przywoływane
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] karty ModelBus używają identyfikatora GUID elementu, aby zidentyfikować go domyślnie. W związku z tym te identyfikatory muszą być utrwalane w pliku modelu.

##### <a name="to-ensure-that-element-ids-are-persisted"></a>Aby upewnić się, że identyfikatory elementów są utrwalane

1. Otwórz DslDefinition. DSL.

2. W Eksploratorze DSL rozwiń opcję **zachowanie serializacji XML**, a następnie **dane klasy**.

3. Dla każdej klasy, do której chcesz utworzyć odwołania do magistrali modelu:

    Kliknij węzeł Klasa i w okno Właściwości upewnij się, że **Identyfikator serializacji** jest ustawiony na `true`.

   Alternatywnie, jeśli chcesz użyć nazw elementów do identyfikacji elementów zamiast identyfikatorów GUID, można zastąpić części wygenerowanych kart. Zastąp następujące metody w klasie adapter:

- Przesłoń `GetElementId`, aby zwrócić identyfikator, którego chcesz użyć. Ta metoda jest wywoływana podczas tworzenia odwołań.

- Przesłoń `ResolveElementReference`, aby zlokalizować prawidłowy element z odwołania do magistrali modelu.

## <a name="editRef"></a>Dostęp do DSL z innego modemu DSL
 Odwołania do magistrali modelu można przechowywać we właściwości domeny w DSL i można napisać kod niestandardowy, który z nich korzysta. Możesz również pozwolić użytkownikowi na tworzenie odwołania do magistrali modelu przez pobranie pliku modelu i elementu w nim.

 Aby włączyć użycie przez DSL odwołań do innego DSL, należy najpierw utworzyć *odbiorcę* odwołań do magistrali modelu.

#### <a name="to-enable-a-dsl-to-consume-references-to-an-exposed-dsl"></a>Aby umożliwić DSL korzystanie z odwołań do uwidocznionych linii DSL

1. Na diagramie definicji DSL kliknij prawym przyciskiem myszy główną część diagramu, a następnie kliknij pozycję **Włącz ModelBus**.

2. W oknie dialogowym wybierz opcję **Chcę włączyć ten model, aby korzystać z odwołań do magistrali modelu**.

3. W projekcie DSL zużywanej przez DSL, Dodaj następujące zestawy do odwołań projektu. Te zestawy (pliki. dll) znajdują się w katalogu ModelBusAdapter\bin \\ * w udostępnionym DSL.

    - Zestaw dostępnego DSL, na przykład **fabrikam. FamilyTree. DSL. dll**

    - Zestaw udostępnionej karty magistrali modelu, na przykład **fabrikam. FamilyTree. ModelBusAdapter. dll**

4. Dodaj następujące zestawy .NET do odwołań do projektu, które są projektem języka DSL.

    1. **Microsoft. VisualStudio. Modeling. Sdk. Integration. 11.0. dll**

    2. **Microsoft. VisualStudio. Modeling. Sdk. Integration. Shell. 11.0. dll**

#### <a name="to-store-a-model-bus-reference-in-a-domain-property"></a>Aby zapisać odwołanie magistrali modelu w właściwości domeny

1. W definicji DSL dla konsumowanego języka DSL Dodaj właściwość domeny do klasy domeny i ustaw jej nazwę.

2. W okno Właściwości z wybraną właściwością domena ustaw wartość **Typ** na `ModelBusReference`.

   Na tym etapie kod programu może ustawić wartość właściwości, ale jest ona tylko do odczytu w okno Właściwości.

   Możesz zezwolić użytkownikom na ustawienie właściwości przy użyciu wyspecjalizowanego edytora odwołań ModelBus. Istnieją dwie wersje tego edytora lub *selektora:* jeden umożliwia użytkownikom wybranie pliku modelu, a drugi umożliwia użytkownikom wybranie pliku modelu i elementu w modelu.

#### <a name="to-allow-the-user-to-set-a-model-bus-reference-in-a-domain-property"></a>Aby zezwolić użytkownikowi na ustawienie odwołania magistrali modelu we właściwości domeny

1. Kliknij prawym przyciskiem myszy Właściwość domena, a następnie kliknij pozycję **Edytuj właściwości specyficzne dla ModelBusReference**. Zostanie otwarte okno dialogowe. Jest to *Selektor magistrali modelu*.

2. Wybierz odpowiedni **rodzaj ModelBusReference**: do modelu lub do elementu wewnątrz modelu.

3. W polu ciąg filtru okna dialogowego plików wprowadź ciąg, taki jak `Family Tree files |*.ftree`. Subsitute rozszerzenie pliku dla dostępnego DSL.

4. Jeśli wybrano odwołanie do elementu w modelu, można dodać listę typów, które użytkownik może wybrać, na przykład Company. FamilyTree. Person.

5. Kliknij przycisk **OK**, a następnie kliknij pozycję **Przekształć wszystkie szablony** na pasku narzędzi Eksploratora rozwiązań.

    > [!WARNING]
    > Jeśli nie wybrano prawidłowego modelu lub jednostki, przycisk OK nie będzie miał żadnego efektu, mimo że może on zostać włączony.

6. Jeśli określono listę typów docelowych, takich jak Company. FamilyTree. Person, należy dodać odwołanie do zestawu do projektu DSL, odwołując się do biblioteki DLL docelowego języka DSL, na przykład Company. FamilyTree. DSL. dll

#### <a name="to-test-a-model-bus-reference"></a>Aby przetestować odwołanie do magistrali modelu

1. Kompiluj zarówno uwidocznione, jak i zużywające językami DSL.

2. Uruchom jeden z językami DSL w trybie eksperymentalnym, naciskając klawisz F5 lub CTRL + F5.

3. W projekcie debugowania w eksperymentalnym wystąpieniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Dodaj pliki, które są wystąpieniami poszczególnych DSL.

    > [!NOTE]
    > [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus może rozpoznać tylko odwołania do modeli, które są elementami w tym samym rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Nie można na przykład utworzyć odwołania do pliku modelu w innej części systemu plików.

4. Utwórz niektóre elementy i linki w wystąpieniu uwidocznionego DSL i Zapisz je.

5. Otwórz wystąpienie zużywanego języka DSL i wybierz element modelu, który ma właściwość odwołania magistrali modelu.

6. W okno Właściwości kliknij dwukrotnie Właściwość odwołania magistrali modelu. Zostanie otwarte okno dialogowe selektora.

7. Kliknij przycisk **Przeglądaj** i wybierz wystąpienie uwidocznionego DSL.

     Selektor zezwoli również na wybranie elementu w modelu, jeśli określono rodzaj specyficzny dla elementu odniesienia magistrali modelu.

## <a name="creating-references-in-program-code"></a>Tworzenie odwołań w kodzie programu
 Jeśli chcesz przechowywać odwołanie do modelu lub elementu wewnątrz modelu, tworzysz `ModelBusReference`. Istnieją dwa rodzaje `ModelBusReference`: odwołania do modelu i odwołania do elementów.

 Aby utworzyć odwołanie do modelu, potrzebna jest karta DSL, dla której model jest wystąpienie, oraz nazwa pliku lub [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] elementu projektu modelu.

 Aby utworzyć odwołanie do elementu, potrzebna jest karta dla pliku modelu oraz element, do którego chcesz się odwołać.

> [!NOTE]
> Za pomocą [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ModelBus można tworzyć odwołania tylko do elementów w tym samym rozwiązaniu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

### <a name="import-the-exposed-dsl-assemblies"></a>Zaimportuj uwidocznione zestawy DSL
 W projekcie zużywanym Dodaj odwołania do projektu do zestawów DSL i ModelBusAdapter dla widocznego DSL.

 Załóżmy na przykład, że chcesz przechowywać odwołania ModelBus w elementach MusicLibrary DSL. Odwołania ModelBus odnoszą się do elementów FamilyTree DSL. W `Dsl` projekcie rozwiązania MusicLibrary w węźle odwołania Dodaj odwołania do następujących zestawów:

- Fabrikam. FamilyTree. DSL. dll — uwidoczniony DSL.

- Fabrikam. FamilyTree. ModelBusAdapters. dll — karta ModelBus dla uwidocznionych linii DSL.

- Microsoft. VisualStudio. Modeling. Sdk. Integration. 11.0

- Microsoft. VisualStudio. Modeling. Sdk. Integration. Shell. 11.0

  Te zestawy mogą znajdować się w `ModelBusAdapters` projekcie uwidocznionych linii DSL w obszarze `bin\*`.

  W pliku kodu, w którym zostaną utworzone odwołania, zazwyczaj trzeba będzie zaimportować te przestrzenie nazw:

```
// The namespace of the DSL you want to reference:
using Fabrikam.FamilyTree;  // Exposed DSL
using Fabrikam.FamilyTree.ModelBusAdapters;
using Microsoft.VisualStudio.Modeling.Integration;
using System.Linq;
...
```

### <a name="to-create-a-reference-to-a-model"></a>Aby utworzyć odwołanie do modelu
 Aby utworzyć odwołanie do modelu, można uzyskać dostęp do adaptera dla uwidocznionych linii DSL i użyć go do utworzenia odwołania do modelu. Można określić ścieżkę pliku lub `EnvDTE.ProjectItem`.

 Z poziomu adaptera można uzyskać kartę, która zapewnia dostęp do poszczególnych elementów w modelu.

> [!NOTE]
> Po zakończeniu pracy z usługą należy usunąć kartę. Najwygodniejszym sposobem osiągnięcia tego celu jest instrukcja `using`. Ilustruje to poniższy przykład.

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
 Karta utworzona dla modelu może służyć do tworzenia i rozwiązywania odwołań.

```
// person is an element in the FamilyTree model:
ModelBusReference personReference =
  adapter.GetElementReference(person);
```

 Jeśli chcesz mieć możliwość późniejszego użycia `elementReference`, możesz zapisać go we właściwości domeny z typem zewnętrznym `ModelBusReference`. Aby umożliwić użytkownikom edycję, użyj `ModelElementReferenceEditor` jako parametru w atrybucie edytora. Aby uzyskać więcej informacji, zobacz [Zezwalanie użytkownikowi na edytowanie odwołania](#editRef).

### <a name="resolving-references"></a>Rozpoznawanie odwołań
 Jeśli masz `ModelBusReference` (MBR), możesz uzyskać model lub element modelu, do którego się odwołuje. Jeśli element jest prezentowany na diagramie lub w innym widoku, można otworzyć widok i wybrać element.

 Kartę można utworzyć na podstawie rekordu MBR. Z poziomu karty można uzyskać katalog główny modelu. Można również rozwiązać MBRs odwołujące się do określonych elementów w modelu.

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

##### <a name="to-resolve-modelbus-references-in-a-text-template"></a>Aby rozwiązać odwołania ModelBus w szablonie tekstowym

1. DSL, do którego chcesz uzyskać dostęp, musi mieć adapter ModelBus, który został skonfigurowany do dostępu za pomocą szablonów tekstowych. Aby uzyskać więcej informacji, zobacz [zapewnianie dostępu do DSL](#provide).

2. Zwykle uzyskujesz dostęp do docelowego języka DSL przy użyciu odwołania do magistrali modelu (MBR) przechowywanego w źródłowym DSL. W związku z tym szablon zawiera dyrektywę źródłowego DSL oraz kod, który umożliwia rozpoznanie rekordu MBR. Aby uzyskać więcej informacji na temat szablonów tekstowych, zobacz [generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md).

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

## <a name="serializing-a-modelbusreference"></a>Serializowanie ModelBusReference
 Jeśli chcesz przechowywać `ModelBusReference` (MBR) w postaci ciągu, można serializować go:

```
string serialized = modelBus.SerializeReference(elementReference);
// Store it anywhere, then get it back again:
ModelBusReference elementReferenceRestored =
    modelBus.DeserializeReference(serialized, null);
```

 Rekord MBR, który jest serializowany w ten sposób, jest niezależny od kontekstu. Jeśli używasz prostej karty magistrali modelu opartej na plikach, rekord MBR zawiera bezwzględną ścieżkę do pliku. Jest to wystarczające, jeśli pliki modelu wystąpienia nigdy nie będą przenoszone. Jednak pliki modelu zwykle będą elementami w projekcie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Użytkownicy będą mogli przenieść cały projekt do różnych części systemu plików. Będą również oczekiwać, że będzie można zachować projekt pod kontrolą źródła i otworzyć go na różnych komputerach. W związku z tym nazwy ścieżek powinny być serializowane względem lokalizacji projektu, który zawiera pliki.

### <a name="serializing-relative-to-a-specified-file-path"></a>Serializacja względem określonej ścieżki pliku
 @No__t_0 zawiera `ReferenceContext`, który jest słownikiem, w którym można przechowywać informacje, takie jak ścieżka do pliku, względem której powinna być serializowana.

 Aby serializować względem ścieżki względnej:

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

### <a name="modelbusreferences-created-by-other-adapters"></a>ModelBusReferences utworzone przez inne karty
 Poniższe informacje są przydatne, jeśli chcesz utworzyć własną kartę.

 @No__t_0 (MBR) składa się z dwóch części: nagłówka MBR, który jest deserializowany przez magistralę modelu i specyficzne dla adaptera, który jest obsługiwany przez określonego Menedżera adapterów. Pozwala to zapewnić własny format serializacji karty. Na przykład można odwołać się do bazy danych, a nie pliku, lub zapisać dodatkowe informacje w dokumentacji karty. Twoja własna karta może umieścić dodatkowe informacje w `ReferenceContext`.

 Podczas deserializacji rekordu MBR należy podać ReferenceContext, który jest następnie przechowywany w obiekcie MBR. Podczas serializacji rekordu MBR przechowywane ReferenceContext jest używane przez kartę do wygenerowania ciągu. Ciąg deserializowany nie zawiera wszystkich informacji w ReferenceContext. Na przykład w prostej karcie opartej na plikach ReferenceContext zawiera ścieżkę pliku głównego, która nie jest przechowywana w serializowanym ciągu MBR.

 Rekord MBR jest deserializowany w dwóch etapach:

- `ModelBusReferencePropertySerializer` to standardowy Serializator, który zajmuje się nagłówkiem MBR. Używa standardowego zbioru właściwości `SerializationContext` DSL, który jest przechowywany w `ReferenceContext` przy użyciu `ModelBusReferencePropertySerializer.ModelBusLoadContextKey` klucza. W szczególności `SerializationContext` powinien zawierać wystąpienie `ModelBus`.

- Karta ModelBus zajmuje się częścią MBR. Może on używać dodatkowych informacji przechowywanych w ReferenceContext MBR. Prosta karta oparta na plikach zachowuje ścieżki plików głównych przy użyciu kluczy `FilePathLoadContextKey` i `FilePathSaveContextKey`.

     Odwołanie do karty w pliku modelu jest deszeregowane tylko wtedy, gdy jest używany.

## <a name="to-create-a-model"></a>Aby utworzyć model

### <a name="creating-opening-and-editing-a-model"></a>Tworzenie, otwieranie i edytowanie modelu
 Poniższy fragment jest pobierany z przykładu automatu stanów w witrynie sieci Web VMSDK. Ilustruje on użycie ModelBusReferences do tworzenia i otwierania modelu oraz do uzyskiwania diagramu skojarzonego z modelem.

 W tym przykładzie nazwa docelowego DSL to StateMachine. Są od niego pochodzące różne nazwy, takie jak nazwa klasy modelu i nazwa ModelBusAdapter.

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

## <a name="validating-references"></a>Sprawdzanie poprawności odwołań
 BrokenReferenceDetector sprawdza wszystkie właściwości domeny w magazynie, który może zawierać ModelBusReferences. Wywołuje akcję, która zapewnia, gdzie można znaleźć jakąkolwiek akcję. Jest to szczególnie przydatne w przypadku metod walidacji. Następująca metoda walidacji testuje magazyn przy próbie zapisu modelu i zgłasza przerwane odwołania w oknie błędy:

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
 Poniższe informacje nie są niezbędne, ale mogą być przydatne w przypadku intensywnego korzystania z ModelBus.

 Rozszerzenie ModelBus wprowadza następujące zmiany w rozwiązaniu DSL.

 Po kliknięciu prawym przyciskiem myszy diagramu definicji DSL kliknij pozycję **Włącz ModelBus**, a następnie wybierz opcję **Włącz tę funkcję DSL, aby korzystać z ModelBus**:

- W projekcie DSL odwołanie jest dodawane do **Microsoft. VisualStudio. Modeling. Sdk. Integration. 11.0. dll**

- W definicji DSL dodawane jest odwołanie do typu zewnętrznego: `Microsoft.VisualStudio.Modeling.Integration.ModelBusReference`.

   Odwołanie można zobaczyć w **Eksploratorze DSL**, w obszarze **typy domen**. Aby ręcznie dodać odwołania do typu zewnętrznego, kliknij prawym przyciskiem myszy węzeł główny.

- Dodawany jest nowy plik szablonu, **Dsl\GeneratedCode\ModelBusReferencesSerialization.tt**.

  Po ustawieniu typu właściwości domeny na ModelBusReference, a następnie kliknięciu prawym przyciskiem myszy właściwości i kliknięciu opcji **Włącz określone właściwości ModelBusReference**:

- Do właściwości domeny dodawane są kilka atrybutów CLR. Można je wyświetlić w polu atrybuty niestandardowe w okno Właściwości. W **Dsl\GeneratedCode\DomainClasses.cs**można zobaczyć atrybuty deklaracji właściwości:

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
