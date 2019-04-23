---
title: Definicje elementów | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
caps.latest.revision: 24
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9298f57e3b1f4a05effcb82a39e14503c9cbf74
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090762"
---
# <a name="item-definitions"></a>Definicje elementów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] w wersji 2.0 umożliwia deklarację statycznych elementów w plikach projektu za pomocą [ItemGroup](../msbuild/itemgroup-element-msbuild.md) elementu. Jednak metadane mogą być dodawane tylko na poziomie elementu, nawet jeśli metadane są identyczne dla wszystkich elementów. Począwszy od [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, element projektu o nazwie [ItemDefinitionGroup —](../msbuild/itemdefinitiongroup-element-msbuild.md) pozwala pokonać tego ograniczenia. *ItemDefinitionGroup —* umożliwiają definiowanie zestawu definicji elementu, aby dodać wartości metadanych domyślne dla wszystkich elementów w typie elementu o nazwie.  
  
 *ItemDefinitionGroup —* element pojawia się natychmiast po [projektu](../msbuild/project-element-msbuild.md) elementu w pliku projektu. Definicje elementów zapewniają następujące funkcje:  
  
- Można zdefiniować metadane domyślnie globalne dla elementów poza obiekt docelowy. Oznacza to tych samych metadanych ma zastosowanie do wszystkich elementów określonego typu.  
  
- Typy elementów może mieć wielu definicji. Dodanie specyfikacje dodatkowe metadane na typ specyfikację ostatni ma pierwszeństwo. \(Metadane następuje po takiej samej kolejności importu następujące właściwości czynności.\)  
  
- Metadane mogą być dodatku. Na przykład CDefines wartości są zbierane warunkowo, w zależności od właściwości, które są ustawiane. Na przykład `MT;STD_CALL;DEBUG;UNICODE`.  
  
- Metadane mogą zostać usunięte.  
  
- Warunki może służyć do kontrolowania włączenia metadanych.  
  
## <a name="item-metadata-default-values"></a>Element metadanych domyślne wartości  
 Metadane elementu, który jest zdefiniowany w ItemDefinitionGroup — jest po prostu deklarację domyślnej metadanych. Metadane nie ma zastosowania, chyba że zdefiniujesz elementu, który używa ItemGroup zawiera wartości metadanych.  
  
> [!NOTE]
>  W wielu przykładach w niniejszym temacie ItemDefinitionGroup — element jest wyświetlane, ale jego odpowiedniej definicji ItemGroup została pominięta w celu przejrzystości.  
  
 Metadane jawnie zdefiniowany w ItemGroup mają pierwszeństwo przed metadanych w ItemDefinitionGroup —. Metadane w ItemDefinitionGroup — są stosowane tylko w przypadku niezdefiniowane metadanych w ItemGroup. Na przykład:  
  
```  
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
>  Nazwy elementu XML i parametru jest uwzględniana wielkość\-poufnych. Element metadanych i elementu\/nazwy właściwości nie są przypadków\-poufnych. W związku z tym ItemDefinitionGroup — elementy, których nazwy różnią się tylko wielkością liter powinny być traktowane jako ten sam element ItemGroup.  
  
## <a name="value-sources"></a>Wartość źródła  
 Wartości metadanych, który jest zdefiniowany w ItemDefinitionGroup — mogą pochodzić z różnych źródeł, w następujący sposób:  
  
- PropertyGroup — właściwość  
  
- ItemDefinitionGroup — element  
  
- Przekształć element ItemDefinitionGroup — element  
  
- Zmienna środowiskowa  
  
- Global — właściwość \(z wiersza polecenia MSBuild.exe\)  
  
- Właściwości zastrzeżone  
  
- Dobrze\-znanych metadanych elementu z ItemDefinitionGroup —  
  
- Sekcja CDATA \< \! \[CDATA\[tutaj niczego nie jest analizowana\]\]\>  
  
> [!NOTE]
>  Metadane elementu z ItemGroup nie jest przydatne w deklaracji metadanych ItemDefinitionGroup —, ponieważ ItemDefinitionGroup — elementy są przetwarzane przed ItemGroup elementów.  
  
## <a name="additive-and-multiple-definitions"></a>Dodatek i wiele definicji  
 Podczas dodawania definicji lub użyć wielu ItemDefinitionGroups, pamiętaj o następujących kwestiach:  
  
- Specyfikacja dodatkowych metadanych jest dodawana do typu.  
  
- Specyfikacja ostatni ma pierwszeństwo.  
  
  W przypadku wielu ItemDefinitionGroups każda kolejne specyfikacji dodaje jego metadane do poprzednią definicję. Na przykład:  
  
```  
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
  
```  
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
>  To może również wystąpić w ten sam element ItemDefinitionGroup.  
  
 Podczas zastąpienia wcześniej zdefiniowane metadane specyfikację ostatni ma pierwszeństwo. W poniższym przykładzie końcowa wartość metadanych "m" przechodzi od "m1" do "m1a".  
  
```  
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
  
## <a name="using-conditions-in-an-itemdefinitiongroup"></a>Za pomocą warunków w ItemDefinitionGroup —  
 Warunki w ItemDefinitionGroup — służy do sterowania włączenia metadanych. Na przykład:  
  
```  
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">  
    <i>  
        <m>m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 W tym przypadku metadane domyślny "m1" w elemencie "i" są dołączone, tylko wtedy, gdy wartość właściwości "Konfiguracja" "Debug".  
  
> [!NOTE]
>  Tylko odwołania do metadanych lokalnego są obsługiwane w warunkach.  
  
 Odwołania do metadanych zdefiniowanych w starszych ItemDefinitionGroup — są lokalne do elementu, a nie grupy definicji. Oznacza to, że zakres odwołania są elementu\-określone. Na przykład:  
  
```  
<ItemDefinitionGroup>  
    <test>  
        <yes>1</yes>  
    </test>  
    <i>  
        <m Condition="'%(test.yes)'=='1'">m1</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 W tym przykładzie element "i" odwołuje się do elementu "test" w warunku.  
  
## <a name="overriding-and-deleting-metadata"></a>Zastępowanie i usuwanie metadanych  
 Metadane zdefiniowane w ItemDefinitionGroup — element może być zastąpiona w późniejszym ItemDefinitionGroup — element, ustawiając wartość metadanych na wartość pustą. Możesz również skutecznie usunąć element metadanych, ustawiając dla niej wartość pustą. Na przykład:  
  
```  
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
 ItemDefinitionGroups mieć zakresu globalnego zdefiniowanego i globalne właściwości wszędzie tam, gdzie są zdefiniowane. Definicje metadanych domyślne w ItemDefinitionGroup — może być samodzielnie\-referencyjną. Na przykład następujące używa odwołania proste metadanych:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Można także odwołania kwalifikowaną metadanych:  
  
```  
<ItemDefinitionGroup>  
    <i>  
      <m>m1</m>  
      <m>%(i.m);m2</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Jednak że jest nieprawidłowa:  
  
```  
<ItemDefinitionGroup>  
    <i>  
        <m>m1</m>  
        <m>@(x)</m>  
    </i>  
</ItemDefinitionGroup>  
```  
  
 Począwszy od [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 3.5, ItemGroups może być również samodzielnie\-referencyjną. Na przykład:  
  
```  
<ItemGroup>  
    <item Include="a">  
        <m>m1</m>  
        <m>%(m);m2</m>  
    </item>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Przetwarzanie wsadowe](../msbuild/msbuild-batching.md)
