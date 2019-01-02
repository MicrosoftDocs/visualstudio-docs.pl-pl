---
title: 'Instrukcje: Użyj tej samej wartości docelowej w wielu plikach projektów | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, importing
- MSBuild, using the same target in multiple project files
ms.assetid: 163734bd-1bfd-4093-a730-7741fc21742d
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ace0e86a5c65afa2c8c5fb12364b9dba66c093e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53905468"
---
# <a name="how-to-use-the-same-target-in-multiple-project-files"></a>Instrukcje: Użyj tej samej wartości docelowej w wielu plikach projektów
Jeśli jesteś autorem kilku [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliki projektu może znasz muszą używać tych samych zadań i obiekty docelowe w plikach inny projekt. Zamiast w każdym pliku projektu w tym pełny opis tych zadań lub miejsc docelowych, można zapisać elementu docelowego w oddzielny plik projektu i następnie zaimportować ten projekt do innego projektu, który musi używać obiektu docelowego.  
  
## <a name="use-the-import-element"></a>Użyj elementu importu  
 `Import` Element jest używany, aby wstawić jeden plik projektu do innego pliku projektu. Plik projektu, który jest importowany musi być prawidłowym [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] pliku projektu i zawierać poprawnie sformułowany dokument XML. `Project` Atrybut określa ścieżkę do plików importowany projektów. Aby uzyskać więcej informacji na temat `Import` elementu, zobacz [Import — element (MSBuild)](../msbuild/import-element-msbuild.md).  
  
#### <a name="to-import-a-project"></a>Aby zaimportować projekt  
  
1.  Zdefiniuj w importowania pliku projektu, wszystkie właściwości i elementy, które są używane jako parametry dla właściwości i elementy w projekcie zaimportowane.  
  
2.  Użyj `Import` element Importowanie projektu. Na przykład:  
  
     `<Import Project="MyCommon.targets"/>`  
  
3.  Następujące `Import` elementu zdefiniować wszystkie właściwości i elementy, które musisz przesłonić domyślny definicji właściwości i elementy w projekcie zaimportowane.  
  
## <a name="order-of-evaluation"></a>Kolejność obliczeń  
 Gdy [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] osiągnie `Import` elementu zaimportowanego projektu skutecznie są wstawiane do importowania projektu w lokalizacji `Import` elementu. W związku z tym, lokalizacja `Import` element może mieć wpływ na wartości właściwości i elementów. Należy zapoznać się z właściwości i elementy, które są skonfigurowane przy importowany projekt i właściwości i elementy, których używa zaimportowanego projektu.  
  
 Gdy projekt zostanie skompilowany, wszystkie właściwości są obliczane jako pierwsze, a następnie elementy. Na przykład, następujący kod XML definiuje plik importowany projektów *MyCommon.targets*:  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyCommon</Name>  
    </PropertyGroup>  
  
    <Target Name="Go">  
        <Message Text="Name=$(Name)"/>  
    </Target>  
</Project>  
```  
  
 Definiuje następujący kod XML *MyApp.proj*, który importuje *MyCommon.targets*:  
  
```xml  
<Project  
    DefaultTargets="Go"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Name>MyApp</Name>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
 Gdy projekt zostanie skompilowany, zostanie wyświetlony następujący komunikat:  
  
 `Name="MyCommon"`  
  
 Ponieważ projekt jest importowany po właściwość `Name` został zdefiniowany w *MyApp.proj*, definicja `Name` w *MyCommon.targets* zastępuje definicję w *MyApp.proj*. Jeśli projekt jest importowany przed właściwość, której nazwa jest zdefiniowana, kompilacja zostanie wyświetlony następujący komunikat:  
  
 `Name="MyApp"`  
  
#### <a name="use-the-following-approach-when-importing-projects"></a>Podczas importowania projektów, zastosuj następujące podejście  
  
1.  Zdefiniuj w pliku projektu, wszystkie właściwości i elementy, które są używane jako parametry dla właściwości i elementy w projekcie zaimportowane.  
  
2.  Importowanie projektu.  
  
3.  Wszystkie właściwości i elementów, które musisz przesłonić domyślny definicji właściwości i elementów w zaimportowanego projektu, należy zdefiniować w pliku projektu.  
  
## <a name="example"></a>Przykład  
 Poniższy kod przedstawia przykład *MyCommon.targets* pliku, który importuje drugi przykład kodu. *.Targets* pliku ocenia właściwości z importowania projektu do konfigurowania kompilacji.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor Condition="'$(Flavor)'==''">DEBUG</Flavor>  
        <Optimize Condition="'$(Flavor)'=='RETAIL'">yes</Optimize>  
        <appname>$(MSBuildProjectName)</appname>  
    <PropertyGroup>  
    <Target Name="Build">  
        <Csc Sources="hello.cs"  
            Optimize="$(Optimize)"  
            OutputAssembly="$(appname).exe"/>  
    </Target>  
</Project>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy kod importuje przykład *MyCommon.targets* pliku.  
  
```xml  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
    <PropertyGroup>  
        <Flavor>RETAIL</Flavor>  
    </PropertyGroup>  
    <Import Project="MyCommon.targets"/>  
</Project>  
```  
  
## <a name="see-also"></a>Zobacz także  
 [Import — element (MSBuild)](../msbuild/import-element-msbuild.md)   
 [Docelowe elementy](../msbuild/msbuild-targets.md)