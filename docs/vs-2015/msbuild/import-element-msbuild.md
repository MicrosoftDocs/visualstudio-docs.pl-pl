---
title: Import — element (MSBuild) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64833530"
---
# <a name="import-element-msbuild"></a>Import — Element (MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Importuje zawartość jednego pliku projektu do innego pliku projektu.  
  
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
|`Project`|Atrybut wymagany.<br /><br /> Ścieżka pliku projektu do zaimportowania. Ścieżka może zawierać symbole wieloznaczne. Pasujące pliki są importowane w kolejności sortowania. Korzystając z tej funkcji, można dodać kod do projektu tylko przez dodanie pliku kodu do katalogu.|  
|`Condition`|Atrybut opcjonalny.<br /><br /> Warunek do obliczenia. Aby uzyskać więcej informacji, zobacz [warunki](../msbuild/msbuild-conditions.md).|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[Project](../msbuild/project-element-msbuild.md)|Wymagany element główny [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] pliku projektu.|  
|[Element importgroup](../msbuild/importgroup-element.md)|Zawiera kolekcję `Import` elementów zgrupowanych w warunku opcjonalnym.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą `Import` elementu można ponownie użyć kodu, który jest wspólny dla wielu plików projektu. Ułatwia to zachowanie kodu, ponieważ wszelkie aktualizacje wprowadzone w kodzie udostępnionym są propagowane do wszystkich projektów, które go zaimportują.  
  
 Zgodnie z Konwencją udostępnione pliki zaimportowanych projektów są zapisywane jako pliki. targets, ale są [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] plikami projektu standardowego. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] nie uniemożliwia importowania projektu o innym rozszerzeniu nazwy pliku, ale zalecamy użycie rozszerzenia. targets w celu zapewnienia spójności.  
  
 Ścieżki względne w zaimportowanych projektach są interpretowane względem katalogu projektu importowania. W związku z tym, jeśli plik projektu zostanie zaimportowany do kilku plików projektu w różnych lokalizacjach, ścieżki względne w zaimportowanym pliku projektu będą interpretowane inaczej dla każdego zaimportowanego projektu.  
  
 Wszystkie [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] zastrzeżone właściwości, które odnoszą się do pliku projektu, na przykład, `MSBuildProjectDirectory` i `MSBuildProjectFile` , które są przywoływane w zaimportowanym projekcie, są przypisywane wartości na podstawie pliku projektu importowania.  
  
 Jeśli zaimportowany projekt nie ma `DefaultTargets` atrybutu, importowane projekty są sprawdzane w kolejności, w której zostały zaimportowane, a wartość pierwszego wykrytego `DefaultTargets` atrybutu jest używana. Na przykład jeśli w przypadku projektów Importy ProjectB i ProjectC (w tej kolejności) i ProjectB Importy są planowane, [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] najpierw szuka `DefaultTargets` określonych w projekcie, a następnie ProjectB, następnie jest rzutowane i na końcu ProjectC.  
  
 Schemat zaimportowanego projektu jest taki sam jak w projekcie standardowym. Mimo że [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] może być możliwe skompilowanie zaimportowanego projektu, jest mało prawdopodobne, ponieważ importowany projekt zwykle nie zawiera informacji o właściwościach, które należy ustawić, lub kolejności, w której mają zostać uruchomione obiekty docelowe. Zaimportowany projekt zależy od projektu, w którym został zaimportowany, aby zapewnić te informacje.  
  
> [!NOTE]
> Chociaż warunkowe instrukcje importowe działają w programie MSBuild w wierszu polecenia, nie działają w programie MSBuild w [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] zintegrowanym środowisku programistycznym (IDE). Importy warunkowe są oceniane przy użyciu wartości konfiguracji i platformy ustawionych podczas ładowania projektu. Jeśli następnie wprowadzono zmiany, które wymagają ponownej oceny warunku w pliku projektu, na przykład zmiany platformy, program [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] obliczy warunki dotyczące właściwości i elementów, ale nie do importowania. Ponieważ warunkowe Importowanie nie jest ponownie oceniane, importowanie jest pomijane.  
>   
> W celu obejścia tego problemu należy umieścić Importy warunkowe w plikach. targets lub umieścić kod w bloku warunkowym, takim jak blok [Wybierz element (MSBuild)](../msbuild/choose-element-msbuild.md) .  
  
## <a name="wildcards"></a>Symbole wieloznaczne  
 W .NET Framework 4, MSBuild zezwala na symbole wieloznaczne w atrybucie projektu. W przypadku symboli wieloznacznych wszystkie znalezione dopasowania są sortowane (na potrzeby odtwarzalności), a następnie są importowane w takiej kolejności, jak w przypadku, gdy zamówienie zostało jawnie ustawione.  
  
 Jest to przydatne, jeśli chcesz zaoferować punkt rozszerzalności, aby ktoś inny mógł zaimportować plik, bez konieczności jawnego dodawania nazwy pliku do pliku importu. W tym celu Microsoft. Common. targets zawiera poniższy wiersz w górnej części pliku.  
  
```  
<Import Project="$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore\*" Condition="'$(ImportByWildcardBeforeMicrosoftCommonTargets)' == 'true' and exists('$(MSBuildExtensionsPath)\$(MSBuildToolsVersion)\$(MSBuildThisFile)\ImportBefore')"/>  
```  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono projekt, który ma kilka elementów i właściwości, i importuje ogólny plik projektu.  
  
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
 [Instrukcje: Użycie tej samej wartości docelowej w wielu plikach projektów](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)
