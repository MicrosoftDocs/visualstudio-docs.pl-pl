---
title: Definicje elementów | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f3e450ef87733ffed88436114458d804c125fc20
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55956977"
---
# <a name="item-definitions"></a>Definicje elementów
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] w wersji 2.0 umożliwia deklarację statycznych elementów w plikach projektu za pomocą [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Jednak metadane mogą być dodawane tylko na poziomie elementu, nawet jeśli metadane są identyczne dla wszystkich elementów. Począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, element projektu o nazwie [ItemDefinitionGroup —](../msbuild/itemdefinitiongroup-element-msbuild.md) pozwala pokonać tego ograniczenia. *ItemDefinitionGroup —* umożliwiają definiowanie zestawu definicji elementu, aby dodać wartości metadanych domyślne dla wszystkich elementów w typie elementu o nazwie.

*ItemDefinitionGroup —* element pojawia się natychmiast po [projektu](../msbuild/project-element-msbuild.md) elementu w pliku projektu. Definicje elementów zapewniają następujące funkcje:

- Można zdefiniować metadane domyślnie globalne dla elementów poza obiekt docelowy. Oznacza to tych samych metadanych ma zastosowanie do wszystkich elementów określonego typu.

- Typy elementów może mieć wielu definicji. Dodanie specyfikacje dodatkowe metadane na typ specyfikację ostatni ma pierwszeństwo. \(Metadane następuje po takiej samej kolejności importu następujące właściwości czynności.\)

- Metadane mogą być dodatku. Na przykład CDefines wartości są zbierane warunkowo, w zależności od właściwości, które są ustawiane. Na przykład `MT;STD_CALL;DEBUG;UNICODE`.

- Metadane mogą zostać usunięte.

- Warunki może służyć do kontrolowania włączenia metadanych.

## <a name="item-metadata-default-values"></a>Wartości domyślne metadane elementu
Metadane elementu, który jest zdefiniowany w ItemDefinitionGroup — jest po prostu deklarację domyślnej metadanych. Metadane nie ma zastosowania, chyba że zdefiniujesz elementu, który używa ItemGroup zawiera wartości metadanych.

> [!NOTE]
> W wielu przykładach w niniejszym temacie ItemDefinitionGroup — element jest wyświetlane, ale jego odpowiedniej definicji ItemGroup została pominięta w celu przejrzystości.

Metadane jawnie zdefiniowany w ItemGroup mają pierwszeństwo przed metadanych w ItemDefinitionGroup —. Metadane w ItemDefinitionGroup — są stosowane tylko w przypadku niezdefiniowane metadanych w ItemGroup. Na przykład:

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

W tym przykładzie domyślne metadanych "m" jest stosowany do elementu "i", ponieważ metadane "m" nie jest jawnie zdefiniowany przez element "i". Jednak domyślne metadanych "n" nie ma zastosowania do elementu "i", ponieważ metadane "n" jest już zdefiniowany przez element "i".

> [!NOTE]
> Nazwy elementu XML i parametru jest uwzględniana wielkość\-poufnych. Element metadanych i elementu\/nazwy właściwości nie są przypadków\-poufnych. W związku z tym ItemDefinitionGroup — elementy, których nazwy różnią się tylko wielkością liter powinny być traktowane jako ten sam element ItemGroup.

## <a name="value-sources"></a>Wartość źródła
Wartości metadanych, który jest zdefiniowany w ItemDefinitionGroup — mogą pochodzić z różnych źródeł, w następujący sposób:

- PropertyGroup — właściwość

- ItemDefinitionGroup — element

- Przekształć element ItemDefinitionGroup — element

- Zmienna środowiskowa

- Global — właściwość (z *MSBuild.exe* wiersza polecenia)

- Właściwości zastrzeżone

- Metadane dobrze znanego z ItemDefinitionGroup — element

- Sekcja CDATA \< \! \[CDATA\[tutaj niczego nie jest analizowana\]\]\>

> [!NOTE]
> Metadane elementu z ItemGroup nie jest przydatne w deklaracji metadanych ItemDefinitionGroup —, ponieważ ItemDefinitionGroup — elementy są przetwarzane przed ItemGroup elementów.

## <a name="additive-and-multiple-definitions"></a>Dodatek i wiele definicji
Podczas dodawania definicji lub użyć wielu ItemDefinitionGroups, pamiętaj o następujących kwestiach:

- Specyfikacja dodatkowych metadanych jest dodawana do typu.

- Specyfikacja ostatni ma pierwszeństwo.

W przypadku wielu ItemDefinitionGroups każda kolejne specyfikacji dodaje jego metadane do poprzednią definicję. Na przykład:

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

W tym przykładzie zostanie dodany metadanych "o", "m" i "n".

Ponadto można również dodać wartości metadanych uprzednio zdefiniowany. Na przykład:

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

W tym przykładzie wartością uprzednio zdefiniowany dla metadanych "m" \(m1\) jest dodawana do nowej wartości \(m2\), dzięki czemu jest końcowa wartość "m1; m2".

> [!NOTE]
> To może również wystąpić w ten sam element ItemDefinitionGroup.

Podczas zastąpienia wcześniej zdefiniowane metadane specyfikację ostatni ma pierwszeństwo. W poniższym przykładzie końcowa wartość metadanych "m" przechodzi od "m1" do "m1a".

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

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>Warunki stosowania w ItemDefinitionGroup —
Warunki w ItemDefinitionGroup — służy do sterowania włączenia metadanych. Na przykład:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

W tym przypadku metadane domyślny "m1" w elemencie "i" są dołączone, tylko wtedy, gdy wartość właściwości "Konfiguracja" "Debug".

> [!NOTE]
> Tylko odwołania do metadanych lokalnego są obsługiwane w warunkach.

Odwołania do metadanych zdefiniowanych w starszych ItemDefinitionGroup — są lokalne do elementu, a nie grupy definicji. Oznacza to, że zakres odwołania są specyficzne dla elementu. Na przykład:

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

W powyższym przykładzie elementu "i" odwołuje się do elementu "test" w jego stan. Ten warunek nigdy nie będzie true, ponieważ program MSBuild interpretuje odwołania do metadanych innym elementem w ItemDefinitionGroup — jako pusty ciąg. W związku z tym "m" będzie miał ustawienie "m0."

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

W powyższym przykładzie, "m" będzie miał ustawienie na wartość "m1", jako odwołania do stanu elementu "i" w wartości metadanych dla elementu "yes".

## <a name="override-and-delete-metadata"></a>Zastąp i usuwanie metadanych
Metadane zdefiniowane w ItemDefinitionGroup — element może być zastąpiona w późniejszym ItemDefinitionGroup — element, ustawiając wartość metadanych na wartość pustą. Możesz również skutecznie usunąć element metadanych, ustawiając dla niej wartość pustą. Na przykład:

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

Element "i" nadal zawiera metadane "m", ale jej wartość jest obecnie pusta.

## <a name="scope-of-metadata"></a>Zakres metadanych
ItemDefinitionGroups mieć zakresu globalnego zdefiniowanego i globalne właściwości wszędzie tam, gdzie są zdefiniowane. Definicje metadanych domyślne w ItemDefinitionGroup — może być relacją. Na przykład następujące używa odwołania proste metadanych:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Można także odwołania kwalifikowaną metadanych:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

Jednak że jest nieprawidłowa:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

Począwszy od [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] 3.5, ItemGroups może być również relacją. Na przykład:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>Zobacz także
[Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
