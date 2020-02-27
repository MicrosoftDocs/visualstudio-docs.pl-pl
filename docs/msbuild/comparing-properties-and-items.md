---
title: Porównywanie właściwości i elementów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a86365ffe839b45fcd09862040fb88f0d4148bc
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634412"
---
# <a name="compare-properties-and-items"></a>Porównanie właściwości i elementów

Właściwości i elementy programu MSBuild służą do przekazywania informacji do zadań, oceniania warunków i przechowywania wartości, do których można się odwoływać w całym pliku projektu.

- Właściwości to pary nazwa-wartość. Aby uzyskać więcej informacji, zobacz [Właściwości programu MSBuild](../msbuild/msbuild-properties.md).

- Elementy to obiekty, które zwykle reprezentują pliki. Obiekty elementów mogą mieć skojarzone kolekcje metadanych. Metadane to pary nazwa-wartość. Aby uzyskać więcej informacji, zobacz [Items](../msbuild/msbuild-items.md).

## <a name="scalars-and-vectors"></a>Wartości skalarne i wektory

Ponieważ właściwości programu MSBuild to pary nazwa-wartość, które mają tylko jedną wartość ciągu, są one często opisane jako *skalarne*. Ponieważ typy elementów programu MSBuild to listy, często są one opisane jako *wektor*. Jednakże w przypadku właściwości mogą reprezentować wiele wartości, a typy elementów mogą mieć zero lub jeden element.

### <a name="target-dependency-injection"></a>Docelowa iniekcja zależności

Aby zobaczyć, jak właściwości mogą reprezentować wiele wartości, należy wziąć pod uwagę typowy wzorzec użycia w celu dodania celu do listy obiektów docelowych do skompilowania. Ta lista jest zazwyczaj reprezentowana przez wartość właściwości, z nazwami docelowymi oddzielonymi średnikami.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

Właściwość `BuildDependsOn` jest zwykle używana jako argument docelowego atrybutu `DependsOnTargets`, efektywnie konwertując go na listę elementów. Ta właściwość może zostać zastąpiona w celu dodania celu lub zmiany docelowej kolejności wykonania. Na przykład:

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

dodaje element docelowy CustomBuild do listy target, dając `BuildDependsOn` wartość `BeforeBuild;CoreBuild;AfterBuild;CustomBuild`.

Począwszy od programu MSBuild 4,0, docelowa iniekcja zależności jest przestarzała. Zamiast tego użyj atrybutów `AfterTargets` i `BeforeTargets`. Aby uzyskać więcej informacji, zobacz [Target Order Build](../msbuild/target-build-order.md).

### <a name="conversions-between-strings-and-item-lists"></a>Konwersje między ciągami i listami elementów

MSBuild wykonuje konwersje do i z typów elementów oraz wartości ciągów zgodnie z wymaganiami. Aby zobaczyć, jak lista elementów może być wartością ciągu, należy wziąć pod uwagę, co się dzieje, gdy typ elementu jest używany jako wartość właściwości programu MSBuild:

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

Typ elementu OutputDir ma atrybut `Include` o wartości "\\plików";\\certyfikatów ". Program MSBuild analizuje ten ciąg w dwóch elementach: plikach z certyfikatami \ i Certificates\\. Gdy typ elementu OutputDir jest używany jako wartość właściwości OutputDirList, MSBuild konwertuje lub "spłaszcza" typu elementu do postaci ciągów rozdzielanych średnikami "\\plików".\\certyfikatów ".

## <a name="properties-and-items-in-tasks"></a>Właściwości i elementy w zadaniach

Właściwości i elementy są używane jako dane wejściowe i wyjściowe do zadań programu MSBuild. Aby uzyskać więcej informacji, zobacz [zadania](../msbuild/msbuild-tasks.md).

Właściwości są przesyłane do zadań jako atrybuty. W ramach zadania Właściwość programu MSBuild jest reprezentowana przez typ właściwości, którego wartość może zostać przekonwertowana na i z ciągu. Obsługiwane typy właściwości obejmują `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string`i dowolnego typu, który <xref:System.Convert.ChangeType%2A> może obsłużyć.

Elementy są przesyłane do zadań jako obiekty <xref:Microsoft.Build.Framework.ITaskItem>. W ramach zadania <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A> reprezentuje wartość elementu, a <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A> pobiera jego metadane.

Listę elementów typu elementu można przesłać jako tablicę obiektów `ITaskItem`. Począwszy od .NET Framework 3,5, elementy można usunąć z listy elementów w obiekcie docelowym przy użyciu atrybutu `Remove`. Ponieważ elementy można usunąć z listy elementów, istnieje możliwość, aby typ elementu miał zero elementów. Jeśli lista elementów jest przenoszona do zadania, kod w zadaniu powinien sprawdzać tę możliwość.

## <a name="property-and-item-evaluation-order"></a>Kolejność szacowania właściwości i elementów

W fazie oceny kompilacji importowane pliki są włączane do kompilacji w kolejności, w jakiej są wyświetlane. Właściwości i elementy są zdefiniowane w trzech przebiegach w następującej kolejności:

- Właściwości są definiowane i modyfikowane w kolejności, w jakiej są wyświetlane.

- Definicje elementów są zdefiniowane i modyfikowane w kolejności, w jakiej są wyświetlane.

- Elementy są definiowane i modyfikowane w kolejności, w jakiej są wyświetlane.

Podczas fazy wykonywania kompilacji, właściwości i elementy, które są zdefiniowane w obiektach docelowych, są oceniane razem w jednej fazie w kolejności, w jakiej są wyświetlane.

Nie jest to jednak Kompletna historia. Gdy właściwość, definicja elementu lub element jest zdefiniowany, jego wartość jest szacowana. Ewaluatora wyrażeń rozszerza ciąg, który określa wartość. Rozszerzenie ciągu jest zależne od fazy kompilacji. Poniżej znajduje się bardziej szczegółowa Właściwość i kolejność oceny elementów:

- W fazie oceny kompilacji:

  - Właściwości są definiowane i modyfikowane w kolejności, w jakiej są wyświetlane. Funkcje właściwości są wykonywane. Wartości właściwości w formularzu $ (PropertyName) są rozwinięte w wyrażeniach. Wartość właściwości jest ustawiona na rozwinięte wyrażenie.

  - Definicje elementów są zdefiniowane i modyfikowane w kolejności, w jakiej są wyświetlane. Funkcje właściwości zostały już rozwinięte w wyrażeniach. Wartości metadanych są ustawiane na rozszerzone wyrażenia.

  - Typy elementów są zdefiniowane i modyfikowane w kolejności, w jakiej są wyświetlane. Wartości elementów w postaci @ (ItemType) są rozwinięte. Przekształcenia elementów są również rozwinięte. Funkcje i wartości właściwości zostały już rozwinięte w wyrażeniach. Lista elementów i wartości metadanych są ustawiane na rozszerzone wyrażenia.

- Podczas fazy wykonywania kompilacji:

  - Właściwości i elementy, które są zdefiniowane w obiektach docelowych, są oceniane razem w kolejności, w jakiej są wyświetlane. Funkcje właściwości są wykonywane, a wartości właściwości są rozwijane w wyrażeniach. Wartości elementów i przekształcenia elementów są również rozwinięte. Wartości właściwości, wartości typu elementu i wartości metadanych są ustawiane na rozszerzone wyrażenia.

### <a name="subtle-effects-of-the-evaluation-order"></a>Delikatne efekty kolejności oceny

W fazie oceny kompilacji właściwość Ocena poprzedza element oceny elementu. Niemniej jednak właściwości mogą mieć wartości, które są zależne od wartości elementów. Rozważmy następujący skrypt.

```xml
<ItemGroup>
    <KeyFile Include="KeyFile.cs">
        <Version>1.0.0.3</Version>
    </KeyFile>
</ItemGroup>
<PropertyGroup>
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
</PropertyGroup>
<Target Name="AfterBuild">
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Wykonanie zadania komunikatu wyświetla następujący komunikat:

```
KeyFileVersion: 1.0.0.3
```

Wynika to z faktu, że wartość `KeyFileVersion` jest w rzeczywistości ciągiem "\@(KeyFile->"% (wersja) ")". Przekształcenia elementów i elementów nie zostały rozwinięte, gdy właściwość została najpierw zdefiniowana, więc Właściwość `KeyFileVersion` ma przypisaną wartość nierozwiniętego ciągu.

Podczas fazy wykonywania kompilacji, gdy przetwarza zadanie komunikatu, MSBuild rozszerza ciąg "\@(KeyFile->"% (wersja) ")", aby dać "1.0.0.3".

Zauważ, że ten sam komunikat będzie wyświetlany nawet wtedy, gdy właściwości i grupy elementów zostały odtworzone w odpowiedniej kolejności.

W drugim przykładzie należy rozważyć, co się dzieje, gdy właściwości i grupy elementów znajdują się w elemencie targets:

```xml
<Target Name="AfterBuild">
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Komunikat zadania wyświetla następujący komunikat:

```
KeyFileVersion:
```

Wynika to z faktu, że podczas fazy wykonywania kompilacji, właściwości i elementów w obszarze elementy docelowe są oceniane z góry na dół w tym samym czasie. Gdy `KeyFileVersion` jest zdefiniowany, `KeyFile` jest nieznany. W związku z tym transformacja elementu rozwija się do pustego ciągu.

W takim przypadku odwracanie kolejności właściwości i grup elementów przywraca oryginalny komunikat:

```xml
<Target Name="AfterBuild">
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

Wartość `KeyFileVersion` jest ustawiona na "1.0.0.3", a nie "\@(KeyFile->"% (wersja) ")". Komunikat zadania wyświetla następujący komunikat:

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>Zobacz też

- [Pojęcia zaawansowane](../msbuild/msbuild-advanced-concepts.md)
