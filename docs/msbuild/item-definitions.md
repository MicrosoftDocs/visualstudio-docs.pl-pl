---
title: Definicje elementów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18d6a2a30af4fb29a8d9e924c44c1570ff1efe29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633710"
---
# <a name="item-definitions"></a>Definicje elementów

MSBuild 2,0 włącza statyczną deklarację elementów w plikach projektu przy użyciu elementu [Item](../msbuild/itemgroup-element-msbuild.md) . Metadane mogą jednak być dodawane tylko na poziomie elementu, nawet jeśli metadane są identyczne dla wszystkich elementów. Począwszy od programu MSBuild 3,5, element projektu o nazwie [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) przejdzie do tego ograniczenia. *ItemDefinitionGroup* umożliwia zdefiniowanie zestawu definicji elementów, który dodaje domyślne wartości metadanych do wszystkich elementów w nazwanym typie elementu.

Element *ItemDefinitionGroup* pojawia się bezpośrednio po elemencie [projektu](../msbuild/project-element-msbuild.md) pliku projektu. Definicje elementów zapewniają następujące funkcje:

- Można zdefiniować globalne metadane dla elementów poza obiektem docelowym. Oznacza to, że te same metadane odnoszą się do wszystkich elementów określonego typu.

- Typy elementów mogą mieć wiele definicji. Gdy do typu są dodawane dodatkowe specyfikacje metadanych, Ostatnia Specyfikacja ma pierwszeństwo. \(Metadane są zgodne z tą samą kolejnością importu, co właściwości.\)

- Metadane mogą być dodatkiem. Na przykład wartości CDefines są wykonywane warunkowo, w zależności od właściwości, które są ustawiane. Na przykład `MT;STD_CALL;DEBUG;UNICODE`.

- Metadane można usunąć.

- Warunki mogą służyć do kontrolowania dołączania metadanych.

## <a name="item-metadata-default-values"></a>Wartości domyślne metadanych elementu

Metadane elementu, które są zdefiniowane w ItemDefinitionGroup, to tylko deklaracja metadanych domyślnych. Metadane nie są stosowane, chyba że zdefiniujesz element, który używa elementu element, aby zawierał wartości metadanych.

> [!NOTE]
> W wielu przykładach w tym temacie jest pokazywany element ItemDefinitionGroup, ale jego definicja elementów Item została pominięta w celu przejrzystości.

Metadane jawnie zdefiniowane w elemencie Itemmanager mają pierwszeństwo przed metadanymi w ItemDefinitionGroup. Metadane w ItemDefinitionGroup są stosowane tylko dla niezdefiniowanych metadanych w elemencie Items. Na przykład:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemGroup>
    <i Include="a">
        <o>o1</o>
        <n>n2</n>
    </i>
</ItemGroup>
```

W tym przykładzie domyślne metadane "m" są stosowane do elementu "i", ponieważ metadane "m" nie są jawnie zdefiniowane przez element "i". Jednak domyślne metadane "n" nie są stosowane do elementu "i", ponieważ metadane "n" są już zdefiniowane przez element "i".

> [!NOTE]
> W nazwach elementów i parametrów XML jest \- uwzględniana wielkość liter. W przypadku metadanych elementów i \/ nazw właściwości elementów nie jest \- rozróżniana wielkość liter. W związku z tym elementy ItemDefinitionGroup o nazwach, które różnią się tylko wielkością liter, powinny być traktowane jako te same elementy.

## <a name="value-sources"></a>Źródła wartości

Wartości metadanych zdefiniowane w ItemDefinitionGroup mogą pochodzić z wielu różnych źródeł w następujący sposób:

- Właściwość właściwości

- Element z ItemDefinitionGroup

- Przekształcanie elementu na element ItemDefinitionGroup

- Zmienna środowiskowa

- Właściwość globalna (z wiersza polecenia *MSBuild.exe* )

- Właściwość zastrzeżona

- Dobrze znane metadane elementu z ItemDefinitionGroup

- Sekcja CDATA \<\!\[CDATA\[anything here is not parsed\]\]\>

> [!NOTE]
> Metadane elementu z elementu Itemobject nie są przydatne w deklaracji metadanych ItemDefinitionGroup, ponieważ elementy ItemDefinitionGroup są przetwarzane przed elementami elementów Item.

## <a name="additive-and-multiple-definitions"></a>Dodatek i wiele definicji

Podczas dodawania definicji lub używania wielu ItemDefinitionGroups należy pamiętać o następujących kwestiach:

- Dodatkowa Specyfikacja metadanych jest dodawana do typu.

- Ostatnia Specyfikacja ma pierwszeństwo.

W przypadku wielu ItemDefinitionGroups każda kolejna Specyfikacja dodaje swoje metadane do poprzedniej definicji. Na przykład:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <o>o1</o>
    </i>
</ItemDefinitionGroup>
```

W tym przykładzie metadane "o" są dodawane do "m" i "n".

Dodatkowo można również dodać poprzednio zdefiniowane wartości metadanych. Na przykład:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

W tym przykładzie wcześniej zdefiniowana wartość dla metadanych "m" \( M1 \) jest dodawana do nowej wartości \( m2 \) , więc końcowa wartość to "M1; M2".

> [!NOTE]
> Może to również wystąpić w tym samym ItemDefinitionGroup.

Gdy zastąpisz poprzednio zdefiniowane metadane, Ostatnia Specyfikacja ma pierwszeństwo. W poniższym przykładzie końcowa wartość metadanych "m" przechodzi z "M1" do "M1A".

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>m1a</m>
    </i>
</ItemDefinitionGroup>
```

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Używanie warunków w ItemDefinitionGroup

Możesz użyć warunków w ItemDefinitionGroup, aby kontrolować dodawanie metadanych. Na przykład:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

W takim przypadku domyślne metadane "M1" w elemencie "i" są uwzględniane tylko wtedy, gdy wartość właściwości "Configuration" to "debug".

> [!NOTE]
> W warunkach są obsługiwane tylko odwołania do metadanych lokalnych.

Odwołania do metadanych zdefiniowanych we wcześniejszych ItemDefinitionGroup są lokalne dla elementu, a nie do grupy definicji. Oznacza to, że zakres odwołań jest specyficzny dla elementu. Na przykład:

```xml
<ItemDefinitionGroup>
    <test>
        <yes>1</yes>
    </test>
    <i>
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>
    </i>
</ItemDefinitionGroup>

```

W powyższym przykładzie element "i" odwołuje się do elementu "test" w swoim stanie. Ten stan nigdy nie będzie prawdziwy, ponieważ MSBuild interpretuje odwołanie do metadanych innego elementu w ItemDefinitionGroup jako pusty ciąg. W związku z tym "m" byłby ustawiony na "M0".

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

W powyższym przykładzie "m" zostanie ustawiona na wartość "M1", ponieważ warunek odwołuje się do wartości metadanych elementu "i" elementu "yes".

## <a name="override-and-delete-metadata"></a>Zastępowanie i usuwanie metadanych

Metadane zdefiniowane w elemencie ItemDefinitionGroup można zastąpić w późniejszym elemencie ItemDefinitionGroup, ustawiając wartość metadanych na inną wartość. Możesz również skutecznie usunąć element metadanych, ustawiając go na wartość pustą. Na przykład:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m></m>
    </i>
</ItemDefinitionGroup>
```

Element "i" nadal zawiera metadane "m", ale jego wartość jest pusta.

## <a name="scope-of-metadata"></a>Zakres metadanych

ItemDefinitionGroups mają zakres globalny dla zdefiniowanych i globalnych właściwości wszędzie tam, gdzie są zdefiniowane. Domyślne definicje metadanych w ItemDefinitionGroup mogą być odwołujące się do siebie. Na przykład następujące użycie prostego odwołania do metadanych:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Można również użyć kwalifikowanego odwołania do metadanych:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Jednak następujące elementy są nieprawidłowe:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

Począwszy od programu MSBuild 3,5, ItemGroups może być również odwołujący się do samego siebie. Na przykład:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz też

- [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
