---
title: projektant XAML migracji rozszerzalności
ms.date: 07/09/2019
ms.topic: conceptual
author: lutzroeder
ms.author: lutzr
manager: jillfra
dev_langs:
- csharp
- vb
monikerRange: vs-2019
ms.openlocfilehash: 9f5085c7a655f186c3c8a4a6eecada8b440650cd
ms.sourcegitcommit: 528178a304e66c0cb7ab98b493fe3c409f87493a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71273216"
---
# <a name="xaml-designer-extensibility-migration"></a>Migracja rozszerzalności projektanta XAML

W programie Visual Studio 2019 Projektant XAML obsługuje dwie różne architektury: architekturę izolacji projektanta i nowszą architekturę izolacji powierzchni. To przejście architektury jest wymagane do obsługi docelowych środowisk uruchomieniowych, które nie mogą być hostowane w procesie .NET Framework. Przejście do architektury izolacji powierzchni wprowadza istotne zmiany w modelu rozszerzalności innych firm. W tym artykule opisano te zmiany, które są dostępne w programie Visual Studio 2019, począwszy od wersji 16,3.

**Izolacja projektanta** jest używana przez projektanta WPF dla projektów, które są przeznaczone dla .NET Framework i obsługuje rozszerzenia *. Design. dll* . Kod użytkownika, biblioteki formantów i rozszerzenia innych firm są ładowane w procesie zewnętrznym (*XDesProc. exe*) wraz z rzeczywistym kodem projektanta i panelami projektanta.

**Izolacja powierzchni** jest używana przez projektanta platformy UWP. Jest on również używany przez projektanta WPF dla projektów przeznaczonych dla platformy .NET Core. W przypadku izolacji powierzchni są ładowane tylko biblioteki kodu użytkownika i kontroli w osobnym procesie, podczas gdy projektant i jego panele są załadowane w procesie programu Visual Studio (*DevEnv. exe*). Środowisko uruchomieniowe używane do wykonywania kodu użytkownika i bibliotek formantów jest inne niż używane przez .NET Framework dla bieżącego projektanta i kodu rozszerzalności innych firm.

![Rozszerzalność — migracja — architektura](media/xaml-designer-extensibility-migration-architecture.png)

Ze względu na to przejście do architektury rozszerzenia innych firm nie są już ładowane do tego samego procesu co biblioteki formantów innych firm. Rozszerzenia nie mogą już mieć bezpośrednich zależności od bibliotek formantów ani bezpośredniego dostępu do obiektów w czasie wykonywania. Rozszerzenia, które zostały wcześniej napisano dla architektury izolacji projektanta przy użyciu interfejsu API *Microsoft. Windows. rozszerzalność. dll* , muszą zostać zmigrowane do nowego podejścia do pracy z architekturą izolacji powierzchni. W tym przypadku istniejące rozszerzenie będzie musiało zostać skompilowane pod kątem nowych zestawów interfejsów API rozszerzalności. Dostęp do typów kontroli czasu wykonywania za pośrednictwem [typeof](/dotnet/csharp/language-reference/keywords/typeof) lub wystąpień czasu wykonywania musi zostać zamieniony lub usunięty, ponieważ biblioteki formantów są teraz ładowane w innym procesie.

## <a name="new-extensibility-api-assemblies"></a>Nowe zestawy interfejsów API rozszerzalności

Nowe zestawy interfejsów API rozszerzalności są podobne do istniejących zestawów interfejsów API rozszerzalności, ale używają różnych schematów nazewnictwa, aby je odróżnić. Podobnie nazwy przestrzeni nazw zostały zmienione w celu odzwierciedlenia nowych nazw zestawów.

| Zestaw interfejsów API izolacji projektanta            | Zestaw interfejsu API izolacji powierzchni                       |
|:------------------------------------------ |:---------------------------------------------------- |
| Microsoft.Windows.Design.Extensibility.dll | Microsoft.VisualStudio.DesignTools.Extensibility.dll |
| Microsoft.Windows.Design.Interaction.dll   | Microsoft.VisualStudio.DesignTools.Interaction.dll   |

## <a name="new-file-extension-and-discovery"></a>Nowe rozszerzenie i odnajdowanie plików

Zamiast używać rozszerzenia pliku *. Design. dll* , nowe rozszerzenia powierzchni będą odnajdywane przy użyciu rozszerzenia pliku *. DesignTools. dll* . rozszerzenia *. Design. dll* i *. DesignTools. dll* mogą znajdować się w tym samym podfolderze *projektu* .

Chociaż biblioteki formantów innych firm są kompilowane dla rzeczywistego docelowego środowiska uruchomieniowego (.NET Core lub platformy UWP), rozszerzenie *. DesignTools. dll* powinno być zawsze kompilowane jako zestaw .NET Framework.

## <a name="decouple-attribute-tables-from-run-time-types"></a>Oddziel Tabele atrybutów od typów czasu wykonywania

Model rozszerzalności izolacji powierzchni nie zezwala na używanie rozszerzeń w przypadku rzeczywistych bibliotek kontroli i dlatego rozszerzenia nie mogą odwoływać się do typów z biblioteki formantów. Na przykład biblioteka. *DesignTools. dll* nie powinna być zależna od *biblioteki. dll*.

Takie zależności były najczęściej używane podczas rejestrowania metadanych dla typów za pośrednictwem tabel atrybutów. Kod rozszerzenia, który odwołuje się do typów bibliotek kontroli bezpośrednio za pośrednictwem [typeof](/dotnet/csharp/language-reference/keywords/typeof) lub [GetType](/dotnet/visual-basic/language-reference/operators/gettype-operator) , jest zastępowany w nowych interfejsach API przy użyciu nazw typów opartych na ciągach:

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
      var builder = new AttributeTableBuilder();
      builder.AddCustomAttributes("MyLibrary.MyControl", new DescriptionAttribute(Strings.MyControlDescription);
      builder.AddCustomAttributes("MyLibrary.MyControl", new FeatureAttribute(typeof(MyControlDefaultInitializer));
      return builder.CreateTable();
    }
  }
}
```

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Metadata
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

<Assembly: ProvideMetadata(GetType(AttributeTableProvider))>

Public Class AttributeTableProvider
    Implements IProvideAttributeTable

    Public ReadOnly Property AttributeTable As AttributeTable Implements IProvideAttributeTable.AttributeTable
        Get
            Dim builder As New AttributeTableBuilder
            builder.AddCustomAttributes("MyLibrary.MyControl", New DescriptionAttribute(Strings.MyControlDescription))
            builder.AddCustomAttributes("MyLibrary.MyControl", New FeatureAttribute(GetType(MyControlDefaultInitializer)))
            Return builder.CreateTable()
        End Get
    End Property
End Class
```

## <a name="feature-providers-and-model-api"></a>Dostawcy funkcji i interfejs API modelu

Dostawcy funkcji są zaimplementowani w zestawach rozszerzeń i załadowane w procesie programu Visual Studio. `FeatureAttribute`Program będzie nadal odwoływać się do typów dostawców funkcji bezpośrednio przy użyciu [typeof](/dotnet/csharp/language-reference/keywords/typeof).

Obecnie obsługiwane są następujące dostawcy funkcji:

* `DefaultInitializer`
* `AdornerProvider`
* `ContextMenuProvider`
* `ParentAdapter`
* `PlacementAdapter`
* `DesignModeValueProvider`jest obsługiwane z ograniczeniem, `TranslatePropertyValue` które zostanie wywołane `InvalidateProperty` za pośrednictwem lub podczas modyfikacji projektanta. Nie zostanie wywołana w przypadku zmodyfikowania w kodzie czasu wykonywania.

Ponieważ dostawcy funkcji są obecnie załadowane w procesie innym niż rzeczywisty kod w czasie wykonywania i biblioteki kontroli, nie mogą oni już bezpośrednio uzyskiwać dostępu do obiektów w czasie wykonywania. Zamiast tego wszystkie takie interakcje muszą zostać przekonwertowane, aby można było korzystać z odpowiednich interfejsów API opartych na modelu. Interfejs API modelu został <xref:System.Type> zaktualizowany i dostęp do <xref:System.Object> niego lub nie jest już dostępny lub został zastąpiony programem `TypeIdentifier` i `TypeDefinition`.

`TypeIdentifier`reprezentuje ciąg bez nazwy zestawu identyfikującego typ. Można rozpoznać do zapytania, aby uzyskać dodatkowe informacje o typie. `TypeDefinition` `TypeIdenfifier` `TypeDefinition`wystąpienia nie mogą być buforowane w kodzie rozszerzenia.

```csharp
TypeDefinition type = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("MyLibrary.MyControl"));
TypeDefinition buttonType = ModelFactory.ResolveType(
    item.Context, new TypeIdentifier("System.Windows.Controls.Button"));
if (type?.IsSubclassOf(buttonType) == true)
{
}
```

```vb
Dim type As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("MyLibrary.MyControl"))
Dim buttonType As TypeDefinition = ModelFactory.ResolveType(
    item.Context, New TypeIdentifier("System.Windows.Controls.Button"))
If type?.IsSubclassOf(buttonType) Then

End If
```

Interfejsy API usunięte z zestawu interfejsów API rozszerzalności izolacji powierzchni:

* `ModelFactory.CreateItem(EditingContext context, object item)`
* `ViewItem.PlatformObject`
* `ModelProperty.DefaultValue`
* `AssemblyReferences.GetTypes(Type baseType)`

Interfejsy API używane `TypeIdentifier` <xref:System.Type>zamiast:

* `ModelFactory.CreateItem(EditingContext context, Type itemType, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, Type itemType, CreateOptions options, params object[] arguments)`
* `ModelFactory.CreateStaticMemberItem(EditingContext context, Type type, string memberName)`
* `ModelFactory.ResolveType(EditingContext context, Type)`zmieniono na`MetadataFactory.ResolveType(EditingContext context, TypeIdentifier typeIdentifier)`
* `ModelService.ResolveType(TypeIdentifier typeIdentifier)`zmieniono na`MetadataService.ResolveType(TypeIdentifier typeIdentifier)`
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

Interfejsy API, `TypeIdentifier` które używają <xref:System.Type> zamiast i nie obsługują już argumentów konstruktora:

* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, params object[] arguments)`
* `ModelFactory.CreateItem(EditingContext context, TypeIdentifier typeIdentifier, CreateOptions options, params object[] arguments)`

Interfejsy API używane `TypeDefinition` <xref:System.Type>zamiast:

* `ValueTranslationService.GetProperties(Type itemType)`
* `ValueTranslationService.HasValueTranslation(Type itemType, PropertyIdentifier identifier)`
* `ValueTranslationService.TranslatePropertyValue(Type itemType, ModelItem item, PropertyIdentifier identifier, object value)`
* `ModelService.Find(ModelItem startingItem, Type type)`
* `ModelService.Find(ModelItem startingItem, Predicate<Type> match)`
* `ModelItem.ItemType`
* `ModelProperty.AttachedOwnerType`
* `ModelProperty.PropertyType`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type)`
* `FeatureManager.CreateFeatureProviders(Type featureProviderType, Type type, Predicate<Type> match)`
* `FeatureManager.InitializeFeatures(Type type)`
* `FeatureManager.GetCustomAttributes(Type type, Type attributeType)`
* `AdapterService.GetAdapter<TAdapterType>(Type itemType)`
* `AdapterService.GetAdapter(Type adapterType, Type itemType)`
* `PropertyEntry.PropertyType`

Interfejsy API używane `AssemblyIdentifier` `<xref:System.Reflection.AssemblyName?displayProperty=fullName>`zamiast:

* `AssemblyReferences.ReferencedAssemblies`
* `AssemblyReferences.LocalAssemblyName`zmieniono na`AssemblyReferences.LocalAssemblyIdentifier`

Ponadto interfejsy `ModelItem` API, `SetValue` takie jak, obsługują tylko wystąpienia typów pierwotnych lub wbudowanych typów .NET Framework, które można przekonwertować dla docelowego środowiska uruchomieniowego. Obsługiwane są obecnie następujące typy:

* Typy pierwotne .NET Framework `Boolean`: `Byte`, `Char`, `DateTime` ,,`Guid` ,`SByte` ,, ,,`Int64`, ,`Nullable` `Int16` `Double` `Enum` `Int32` , `Single`, `String`, `Type`, `UInt16`, `UInt32`, `UInt64`,`Uri`
* Znane typy .NET Framework WPF (i typy pochodne): `Brush`, `Color`, `CompositeTransform` `EllipseGeometry` `EasingFunctionBase` `Duration` `CornerRadius`,,,, `EasingMode`, `FontFamily` ,,`Geometry` , `GeneralTransform` , `GradientStopCollection`, `GradientStop`, `GridLength`, `ImageSource`, `InlineCollection`, `Inline`, `KeySpline`, `Material`, `Matrix`, `PathFigureCollection`, `PathFigure`, `PathSegmentCollection`, `PathSegment`, `Path`, `PointCollection`, `Point`, `PropertyPath`, `Rect`, `RepeatBehavior`, `Setter`, `Size`, `StaticResource`, `TextAlignment`, `TextDecorationCollection`, `ThemeResourceExtension`, `Thickness`, `TimeSpan`, `Transform3D`,`TransformCollection`

Na przykład:

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

```vb
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Features
Imports Microsoft.VisualStudio.DesignTools.Extensibility.Model

Public Class MyControlDefaultInitializer
    Inherits DefaultInitializer

    Public Overrides Sub InitializeDefaults(item As ModelItem)
        item.Properties!Width.SetValue(800.0)
        MyBase.InitializeDefaults(item)
    End Sub
End Class
```

Więcej przykładów kodu jest dostępnych w repozytorium [XAML-Designer-rozszerzalności-Samples](https://github.com/microsoft/xaml-designer-extensibility-samples) .

## <a name="limited-support-for-designdll-extensions"></a>Ograniczona obsługa rozszerzeń. Design. dll

Jeśli jakieś rozszerzenie *. DesignTools. dll* zostało odnalezione dla biblioteki formantów, zostanie ono najpierw załadowane i odnajdywanie dla rozszerzeń *. Design. dll* jest pomijane.

Jeśli nie ma rozszerzenia. *DesignTools. dll* , ale znaleziono rozszerzenie *. Design. dll* , usługa języka XAML próbuje załadować ten zestaw w celu wyodrębnienia informacji z tabeli atrybutów do obsługi podstawowych scenariuszy edytora i Inspektora właściwości. Ten mechanizm jest ograniczony do zakresu. Nie zezwala na ładowanie rozszerzeń izolacji projektanta w celu wykonywania dostawców funkcji, ale może zapewnić podstawową pomoc techniczną dla istniejących bibliotek formantów WPF.
