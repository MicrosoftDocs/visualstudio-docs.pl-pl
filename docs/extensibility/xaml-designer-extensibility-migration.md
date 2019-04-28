---
title: Migracja rozszerzalności projektanta XAML
ms.date: 04/17/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
monikerRange: vs-2019
ms.openlocfilehash: f83c40a67dc36301816b2384242d790a9f776044
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63447338"
---
# <a name="xaml-designer-extensibility-migration"></a>Migracja rozszerzalności projektanta XAML

Począwszy od programu Visual Studio 2019 wersji 16.1 w publicznej wersji zapoznawczej, Projektant XAML obsługuje dwie różne architektury służące: Architektura projektanta izolacji i nowszą architektury powierzchni izolacji. Ten proces przejścia architektury jest wymagany do obsługi środowisk uruchomieniowych docelowych, które nie mogą być hostowane w procesie .NET Framework. Przejście do architektury powierzchni izolacji wprowadza zmiany powodujące niezgodność w modelu rozszerzeń innych firm. W tym artykule opisano zmiany.

**Izolacja projektanta** jest używany przez projektanta WPF dla projektów przeznaczonych dla platformy .NET Framework i obsługuje *. design.dll* rozszerzenia. Kod użytkownika, bibliotek kontrolek i rozszerzeń innych firm, które zostały załadowane w procesie zewnętrznym (*XDesProc.exe*) oraz rzeczywisty kod projektanta i panele projektanta.

**Urządzenia Surface izolacji** jest używany przez projektanta platformy uniwersalnej systemu Windows. Jest on również używany przez projektanta WPF dla projektów przeznaczonych dla platformy .NET Core. W przypadku izolacji powierzchni jedynym użytkownikiem biblioteki kodu i kontroli są ładowane w oddzielnym procesie, podczas projektanta i jej zespoły są ładowane w procesie programu Visual Studio (*DevEnv.exe*). Środowisko uruchomieniowe używane do wykonywania bibliotek kodu i kontroli użytkownika różni się od używanej przez program .NET Framework dla rzeczywistego projektanta i kodu rozszerzeń innych firm.

![rozszerzalność migracji architektury](media/xaml-designer-extensibility-migration-architecture.png)

Ta modyfikacja Architektura rozszerzenia innych firm nie były ładowane w tym samym procesie co bibliotek kontrolek innych firm. Rozszerzenia można już nie ma bezpośredniej zależności na bibliotek kontrolek lub uzyskać bezpośredni dostęp do środowiska wykonawczego obiektów. Rozszerzenia, które wcześniej zostały napisane dla przy użyciu architektury projektanta izolacji *Microsoft.Windows.Extensibility.dll* interfejsu API muszą być migrowane do nowego podejścia do pracy z architekturą powierzchni izolacji. W praktyce musisz być skompilowany nowych zestawów API rozszerzalności istniejące rozszerzenie. Dostęp do środowiska uruchomieniowego kontroli typów za pośrednictwem [typeof](/dotnet/csharp/language-reference/keywords/typeof) lub wystąpienia środowiska uruchomieniowego musi zostać zastąpione lub usunięty, ponieważ kontrolka biblioteki są obecnie ładowane w ramach innego procesu.

## <a name="new-extensibility-api-assemblies"></a>Nowych zestawów rozszerzeń interfejsu API

Nowe zestawy API rozszerzalności są podobne do istniejących zestawów API rozszerzalności, ale wykonać inny schemat nazewnictwa, aby odróżnić je. Podobnie aby odzwierciedlały nowe nazwy zestawu zmieniły się nazwy przestrzeni nazw.

| Projektanta izolacji zestawu interfejsów API            | Izolacja powierzchni interfejsu API zestawu                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Nowe rozszerzenie pliku i odnajdywania

Zamiast używania *. design.dll* rozszerzenie, nowe powierzchni rozszerzenia zostanie odnaleziona przy użyciu pliku *. designtools.dll* rozszerzenie pliku. *. design.dll* i *. designtools.dll* rozszerzenia może istnieć w tym samym *projektowania* podfolderu.

Gdy bibliotek kontrolek innych firm są kompilowane dla rzeczywistego docelowe środowisko uruchomieniowe (.NET Core i platformy uniwersalnej systemu Windows), *. designtools.dll* rozszerzenia zawsze powinna być skompilowana jako zestawu .NET Framework.

## <a name="decouple-attribute-tables-from-runtime-types"></a>Rozdzielenie atrybut tabel z typami środowiska wykonawczego

Model rozszerzalności powierzchni izolacji nie pozwala na rozszerzenia są zależne od rzeczywistego formantu biblioteki, a w związku z tym, rozszerzenia nie może odwoływać się do typów z biblioteki kontroli. Na przykład *MyLibrary.designtools.dll* nie powinny mieć zależność *MyLibrary.dll*.

Takie zależności zostały najczęściej, gdy rejestrowanie metadanych dla typów za pomocą atrybutu tabel. Kod rozszerzenia, który odwołuje się do biblioteki formantów typy bezpośrednio za pośrednictwem [typeof](/dotnet/csharp/language-reference/keywords/typeof) zostanie zastąpiony w nowych interfejsów API za pomocą nazw opartej na ciągach typu:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Metadata;
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

[assembly: ProvideMetadata(typeof(AttributeTableProvider))]

public class AttributeTableProvider : IProvideAttributeTable
{
  public AttributeTable AttributeTable
  {
    get
    {
      AttributeTableBuilder builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

## <a name="feature-providers-and-model-api"></a>Dostawców funkcji i interfejs API modelu

Dostawców funkcji są implementowane w zestawach, rozszerzenia i załadowany w procesie programu Visual Studio. `FeatureAttribute` będą nadal odwoływać się bezpośrednio przy użyciu typów dostawców funkcji [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Ponieważ dostawców funkcji zostaną załadowane w procesie różni się od rzeczywistej środowiska uruchomieniowego bibliotek kodu i kontroli, nie są już możliwość bezpośredniego dostępu do obiektów w czasie wykonywania. Zamiast tego należy przekonwertować takie interakcje przy użyciu odpowiednich interfejsów API opartych na modelu. Interfejs API modelu została zaktualizowana, a dostęp do <xref:System.Type> lub <xref:System.Object> jest albo nie będą już dostępne lub został zastąpiony `TypeIdentifier` i `TypeDefinition`.

`TypeIdentifier` Określa ciąg bez identyfikowania typu nazwy zestawu. A `TypeIdenfifier` mógł zostać rozpoznany `TypeDefinition` do zapytania dodatkowych informacji o typie. `TypeDefinition` Nie można buforować wystąpień w kodzie rozszerzenia.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type != null && buttonType != type.IsSubclassOf(buttonType))
{
}
```

Interfejsy API są usuwane z zestawu rozszerzeń interfejsu API powierzchni izolacji:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`

Interfejsy API, używanego przez `TypeIdentifier` zamiast <xref:System.Type>:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ViewItem.ItemType`
* `ModelEvent.EventType`
* `ModelEvent.IsEventOfType(Type type)`
* `ModeItem.IsItemOfType(Type type)`
* `ModelParent.CanParent(EditingContext context, ModelItem parent, Type childType)`
* `ModelParent.FindParent(EditingContext context, Type childType, ModelItem startingItem)`
* `ModelParent.FindParent(Type childType, GestureData gestureData)`
* `ModelProperty.IsPropertyOfType(Type type)`
* `ParentAdpater.CanParent(ModelItem parent, Type childType)`
* `ParentAdapter.RedirectParent(ModelItem parent, Type childType)`

Interfejsy API, używanego przez `TypeIdentifier` zamiast <xref:System.Type> i nie obsługują już argumenty konstruktora:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

Interfejsy API, używanego przez `TypeDefinition` zamiast <xref:System.Type>:

* `ModelFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`

Interfejsy API, używanego przez `ModelItem` zamiast <xref:System.Object>:

* `ModelItemCollection.Insert(int index, object value)`
* `ModelItemCollection.Remove(object value)`
* `ModelItemDictionary.Add(object key, object value)`
* `ModelItemDictionary.ContainsKey(object key)`
* `ModelItemDictionary.Remove(object key)`
* `ModelItemDictionary.TryGetValue(object key, out ModelItem value)`

Znane typy pierwotne, takie jak `int`, `string`, lub `Thickness` mogą być przekazywane do interfejsu API modelu w postaci wystąpień w .NET Framework i zostanie przekonwertowana na odpowiadający mu obiekt środowiska uruchomieniowego procesu docelowego. Na przykład:

```csharp
using Microsoft.VisualStudio.DesignTools.Extensibility.Features;
using Microsoft.VisualStudio.DesignTools.Extensibility.Model;

public class MyControlDefaultInitializer : DefaultInitializer
{
  public override void InitializeDefaults(ModelItem item)
  {
    item.Properties["Width"].SetValue(800d);
    base.InitializeDefaults(item);
  }
}
```

## <a name="limited-support-for-designdll-extensions"></a>Ograniczona obsługa. design.dll rozszerzenia

Ewentualne *. designtools.dll* rozszerzenia został odnaleziony w bibliotece kontrolki, jest ładowany, pierwsze i odnajdywanie *. design.dll* rozszerzenia jest pomijany.

Jeśli nie *. designtools.dll* rozszerzenia są obecne, ale *. design.dll* rozszerzenie zostanie znaleziony, próbuje załadować tego zestawu można wyodrębnić informacji o tabeli atrybutu do obsługi usługi języka XAML Edytor języka Basic i scenariuszy Inspektora właściwości. Ten mechanizm jest ograniczona w zakresie. Nie zezwala na ładowanie rozszerzeń projektanta izolacji wykonywanie dostawców funkcji, ale może zapewnić podstawowa pomoc techniczna dla istniejących bibliotek kontrolek WPF.
