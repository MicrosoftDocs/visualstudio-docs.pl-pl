---
title: Definicje towarów | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633710"
---
# <a name="item-definitions"></a>Definicje elementów

MSBuild 2.0 włącza statyczną deklarację elementów w plikach projektu przy użyciu [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Jednak metadane mogą być dodawane tylko na poziomie elementu, nawet jeśli metadane są identyczne dla wszystkich elementów. Począwszy od MSBuild 3.5, element projektu o nazwie [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md) pokonuje to ograniczenie. *ItemDefinitionGroup* umożliwia zdefiniowanie zestawu definicji elementów, które dodają domyślne wartości metadanych do wszystkich elementów w typie nazwanego elementu.

*Element ItemDefinitionGroup* pojawia się natychmiast po [projekcie](../msbuild/project-element-msbuild.md) element pliku projektu. Definicje elementów zapewniają następujące funkcje:

- Można zdefiniować globalne domyślne metadane dla elementów poza obiektem docelowym. Oznacza to, że te same metadane ma zastosowanie do wszystkich elementów określonego typu.

- Typy elementów mogą mieć wiele definicji. Po dodaniu dodatkowych specyfikacji metadanych do typu, ostatnia specyfikacja ma pierwszeństwo. \(Metadane są zgodne z tym samym zamówieniem importu, co właściwości.\)

- Metadane mogą być addytywne. Na przykład CDefines wartości są kumulowane warunkowo, w zależności od właściwości, które są ustawione. Na przykład `MT;STD_CALL;DEBUG;UNICODE`.

- Metadane można usunąć.

- Warunki mogą służyć do kontrolowania dołączania metadanych.

## <a name="item-metadata-default-values"></a>Wartości domyślne metadanych elementu

Metadane elementu, który jest zdefiniowany w ItemDefinitionGroup jest tylko deklaracja domyślnych metadanych. Metadane nie ma zastosowania, chyba że zdefiniowano element, który używa ItemGroup zawierać wartości metadanych.

> [!NOTE]
> W wielu przykładach w tym temacie element ItemDefinitionGroup jest wyświetlany, ale jego odpowiednia definicja ItemGroup jest pomijana dla przejrzystości.

Metadane jawnie zdefiniowane w itemgroup ma pierwszeństwo przed metadanymi w ItemDefinitionGroup. Metadane w ItemDefinitionGroup są stosowane tylko dla niezdefiniowanych metadanych w grupie elementów. Przykład:

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

W tym przykładzie domyślne metadane "m" jest stosowany do elementu "i", ponieważ metadane "m" nie jest jawnie zdefiniowane przez element "i". Jednak domyślne metadane "n" nie są stosowane do elementu "i", ponieważ metadane "n" są już zdefiniowane przez element "i".

> [!NOTE]
> W nazwach XML\-i Parameter są rozróżniane wielkość liter. W przypadku metadanych elementu i nazw właściwości elementu\/nie jest rozróżniana wielkość liter.\- W związku z tym ItemDefinitionGroup elementy, które mają nazwy, które różnią się tylko w zależności od przypadku powinny być traktowane jako tej samej ItemGroup.

## <a name="value-sources"></a>Źródła wartości

Wartości metadanych zdefiniowanych w ItemDefinitionGroup mogą pochodzić z wielu różnych źródeł, w następujący sposób:

- Właściwość PropertyGroup

- Element z grupy elementówDefiniowanie elementów

- Przekształcanie elementu w elemencie ItemDefinitionGroup

- Zmienna środowiskowa

- Właściwość globalna (z wiersza polecenia *MSBuild.exe)*

- Nieruchomość zarezerwowana

- Dobrze znane metadane elementu z grupy elementów

- \< \!Sekcja \[CDATA\[CDATA nic tutaj nie jest analizowana\]\]\>

> [!NOTE]
> Metadane elementu z grupy elementów nie są przydatne w deklaracji metadanych ItemDefinitionGroup, ponieważ elementy ItemDefinitionGroup są przetwarzane przed elementami ItemGroup.

## <a name="additive-and-multiple-definitions"></a>Definicje dodatków i wielu definicji

Podczas dodawania definicji lub używania wielu grup elementów, należy pamiętać o następujących czynnościach:

- Dodatkowa specyfikacja metadanych jest dodawana do typu.

- Pierwszeństwo ma ostatnia specyfikacja.

Jeśli masz wiele ItemDefinitionGroups, każda kolejna specyfikacja dodaje swoje metadane do poprzedniej definicji. Przykład:

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

Ponadto można również dodać wcześniej zdefiniowane wartości metadanych. Przykład:

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

W tym przykładzie poprzednio zdefiniowana wartość \(metadanych "m1" m1\) jest dodawana do nowej wartości \(m2\), tak aby wartość końcowa to "m1;m2".

> [!NOTE]
> Może to również wystąpić w tej samej itemDefinitionGroup.

Po zastąpieniu wcześniej zdefiniowanych metadanych ostatnia specyfikacja ma pierwszeństwo. W poniższym przykładzie ostateczna wartość metadanych "m" przechodzi od "m1" do "m1a".

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

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Używanie warunków w grupie itemdefinitionGroup

Można użyć warunków w ItemDefinitionGroup kontrolować dołączanie metadanych. Przykład:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

W takim przypadku domyślne metadane "m1" w elemencie "i" są uwzględniane tylko wtedy, gdy wartość właściwości "Konfiguracja" to "Debug".

> [!NOTE]
> Tylko lokalne odwołania do metadanych są obsługiwane w warunkach.

Odwołania do metadanych zdefiniowane we wcześniejszej ItemDefinitionGroup są lokalne dla elementu, a nie grupy definicji. Oznacza to, że zakres odwołań są specyficzne dla towaru. Przykład:

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

W powyższym przykładzie element "i" odwołuje się do elementu "test" w jego condition. Ten warunek nigdy nie będzie true, ponieważ MSBuild interpretuje odwołanie do metadanych innego elementu w ItemDefinitionGroup jako pusty ciąg. W związku z tym "m" zostanie ustawiona na "m0".

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

W powyższym przykładzie "m" zostanie ustawiona na wartość "m1" jako element Odzrzeniania odwołuje się do elementu "i" wartość metadanych dla elementu "tak".

## <a name="override-and-delete-metadata"></a>Zastępowanie i usuwanie metadanych

Metadane zdefiniowane w elemencie ItemDefinitionGroup można zastąpić w późniejszym elemencie ItemDefinitionGroup, ustawiając wartość metadanych na inną wartość. Można również skutecznie usunąć element metadanych, ustawiając go na pustą wartość. Przykład:

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

Element "i" nadal zawiera metadane "m", ale jego wartość jest teraz pusta.

## <a name="scope-of-metadata"></a>Zakres metadanych

ItemDefinitionGroups mają zakres globalny na zdefiniowane i właściwości globalne, gdziekolwiek są zdefiniowane. Domyślne definicje metadanych w ItemDefinitionGroup mogą być samoreferencyjne. Na przykład następujące używa prostego odwołania do metadanych:

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

Jednak następujące są nieprawidłowe:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

Począwszy od MSBuild 3.5 ItemGroups może być również self-referential. Przykład:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz też

- [Tworzenie partii](../msbuild/msbuild-batching.md)
