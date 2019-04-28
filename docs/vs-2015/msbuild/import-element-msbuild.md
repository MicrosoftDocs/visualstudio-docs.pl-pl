---
title: Import — Element (MSBuild) | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#Import
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- Import element [MSBuild]
- <Import> element [MSBuild]
ms.assetid: 3bfecaf1-69fd-4008-b651-c9dafd4389d9
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9f8edefc8e097f7ada67041b807231f594774548
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433558"
---
# <a name="import-element-msbuild"></a>Import — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Importuje zawartość pliku jednego projektu do innego pliku projektu.  
  
 \<Project>  
 \<Import>  
  
## <a name="syntax"></a>Składnia  
  
```  
<Import Project="ProjectPath"  
    Condition="'String A'=='String B'" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|`Project`|Atrybut wymagany.<br /><br /> Ścieżka pliku projektu do zaimportowania. Ścieżka może zawierać symboli wieloznacznych. Pasujące pliki są importowane w kolejności posortowanej. Za pomocą tej funkcji, można dodać kod do projektu podczas dodawania pliku kodu do katalogu.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do sprawdzenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Element główny wymagany [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.|  
|[Importgroup —](../msbuild/importgroup-element.md)|Zawiera kolekcję `Import` elementy są pogrupowane w obszarze opcjonalny warunek.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą `Import` elementu, można użyć ponownie kod, który jest wspólne dla wielu plików projektu. Ułatwia utrzymanie kodu, ponieważ wszelkie aktualizacje wprowadzone współużytkowanym kodem Pobierz propagowane do wszystkich projektów, które go zaimportować.  
  
 Zgodnie z Konwencją projektu udostępnionego zaimportowane pliki są zapisywane jako pliki .targets, ale są one standardowego [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliki projektu. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] uniemożliwia importowania projektu, który ma rozszerzenie nazwy pliku różnych, ale zalecane jest użycie rozszerzenia .targets w celu zachowania spójności.  
  
 Ścieżki względne w projektach zaimportowane, są interpretowane względem katalogu projektu importowania. W związku z tym jeśli plik projektu jest importowany do niektóre pliki projektu w różnych lokalizacjach, ścieżek względnych w pliku importowanych projektu będą interpretowane inaczej dla każdego zaimportowanego projektu.  
  
 Wszystkie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zastrzeżone właściwości, które odnoszą się do pliku projektu, na przykład `MSBuildProjectDirectory` i `MSBuildProjectFile`, do których istnieje odwołanie w importowanym projekcie są przypisane wartości na podstawie importowania pliku projektu.  
  
 Jeśli importowany projekt nie ma `DefaultTargets` atrybutu, zaimportowane projekty są kontrolowane w kolejności, są one importowane, a wartość pierwszego odnalezione `DefaultTargets` atrybut jest używany. Na przykład, jeśli ProjectA importuje ProjectB i ProjectC (w tej kolejności) i ProjectB importuje ProjectD [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] szuka najpierw `DefaultTargets` określone w ProjectA, a następnie ProjectB, a następnie ProjectD, a na koniec ProjectC.  
  
 Schemat importowanym projekcie jest identyczna jak standardowy projekt. Mimo że [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] może być zdolny do skompilowania importowanym projekcie, jest mało prawdopodobne, ponieważ importowanym projekcie zwykle nie zawiera informacji na temat właściwości, które z zestawem lub kolejność, w którym ma być uruchamiany elementów docelowych. Zaimportowanego projektu zależy od projektu, do którego jest importowany, aby podać te informacje.  
  
> [!NOTE]
> Instrukcje warunkowe importu współdziałanie w MSBuilds wiersza polecenia, nie działają z użyciem MSBuild w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanego środowiska programistycznego (IDE). Importy warunkowego są oceniane przy użyciu wartości konfiguracji i platformy, które są ustawione, gdy projekt jest ładowany. Jeśli następnie wprowadzono zmiany wymagające ponownej oceny instrukcje warunkowe w pliku projektu, na przykład zmiana platformę [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] reevaluates warunki na właściwości i elementów, ale nie w przypadku importów. Ponieważ nie jest ponownie szacowane warunkowe importu, importowania zostanie pominięta.  
>   
> Aby obejść ten problem, umieść warunkowego Importy w plikach .targets lub umieść kod w bloku warunkowego, takich jak [wybierz Element (MSBuild)](../msbuild/choose-element-msbuild.md) bloku.  
  
## <a name="wildcards"></a>Symboli wieloznacznych  
 W programie .NET Framework 4 program MSBuild umożliwia symboli wieloznacznych w atrybucie projektu. W przypadku symboli wieloznacznych znalezione wszystkie dopasowania są sortowane (w przypadku odtwarzaniem), a następnie są importowane w tej kolejności tak, jakby kolejność ma jawnie ustawione.  
  
 Jest to przydatne, jeśli chcesz zaoferować punkt rozszerzeń, aby ktoś można zaimportować plik bez konieczności jawnie dodać nazwę pliku do importowania pliku. W tym celu Microsoft.Common.Targets zawiera następujący wiersz u góry pliku.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia projekt, który ma kilka elementów i właściwości, a następnie importuje plik ogólnego projektu.  
  
```  
<Project DefaultTargets="Compile"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <PropertyGroup>  
        <resourcefile>Strings.resx</resourcefile>  
  
        <compiledresources>  
            $(O)\$(MSBuildProjectName).Strings.resources  
        </compiledresources>  
    </PropertyGroup>  
  
    <ItemGroup>  
        <CSFile Include="*.cs" />  
  
        <Reference Include="System" />  
        <Reference Include="System.Data" />  
    </ItemGroup>  
  
    <Import Project="$(CommonLocation)\General.targets" />  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do schematu pliku projektu](../msbuild/msbuild-project-file-schema-reference.md)   
 [Instrukcje: użycie tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
