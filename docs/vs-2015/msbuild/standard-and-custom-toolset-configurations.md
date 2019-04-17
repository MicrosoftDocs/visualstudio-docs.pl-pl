---
title: Konfiguracje standardowego i niestandardowego zestawu narzędzi | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 34
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c629d82d208f45433564c1b36bb5aa889e402915
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668333"
---
# <a name="standard-and-custom-toolset-configurations"></a>Konfiguracje standardowego i niestandardowego zestawu narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw narzędzi MSBuild zawiera odwołania do zadania, celów i narzędzi, które służą do tworzenia projektu aplikacji. Program MSBuild zawiera standardowy zestaw narzędzi, ale można również tworzyć niestandardowe zestawy narzędzi. Aby uzyskać informacje o sposobie określania zestaw narzędzi, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)  

## <a name="standard-toolset-configurations"></a>Konfiguracje standardowego zestawu narzędzi  
 Program MSBuild 12.0 obejmuje następujące standardowe zestawy narzędzi:  

| ToolsVersion | Ścieżka zestawu narzędzi (określoną we właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath) |
|--------------|--------------------------------------------------------------------------------------|
|     2.0      |           *Ścieżka instalacji Windows*\Microsoft.Net\Framework\v2.0.50727\            |
|     3.5      |              *Ścieżka instalacji Windows*\Microsoft.NET\Framework\v3.5\               |
|     4.0      |           *Ścieżka instalacji Windows*\Microsoft.NET\Framework\v4.0.30319\            |
|     12.0     |                          *%ProgramFiles%* \MSBuild\12.0\bin                           |

 `ToolsVersion` Wartość określa, który zestaw narzędzi jest używany przez projekt, który generuje programie Visual Studio. W [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] wartość domyślna to "12,0" (niezależnie od tego, jakie wersja określona w pliku projektu), ale ten atrybut można zastąpić za pomocą **/toolsversion** Przejdź w wierszu polecenia. Informacje o tego atrybutu i inne sposoby określania `ToolsVersion`, zobacz [zastępowanie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  

 Jeśli `ToolsVersion` nie został określony w kluczu rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\\< numer wersji\>\DefaultToolsVersion** definiuje `ToolsVersion`, czyli zawsze w wersji 2.0.  

 Następujące klucze rejestru wpisz ścieżkę instalacji programu MSBuild.exe.  

|Klucz rejestru|Nazwa klucza|Wartość klucza ciągu|  
|------------------|--------------|----------------------|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0\|MSBuildToolsPath|Ścieżka instalacji programu .NET framework w wersji 2.0|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\|MSBuildToolsPath|Ścieżka instalacji programu .NET framework 3.5|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\|MSBuildToolsPath|Ścieżka instalacji programu .NET framework 4|  
|\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0\|MSBuildToolsPath|Ścieżka instalacji programu MSBuild|  

### <a name="sub-toolsets"></a>Sub — zestawy narzędzi  
 Jeśli klucz rejestru w poprzedniej tabeli ma podklucza, program MSBuild używa można określić ścieżkę do podzestawu narzędzi mogą zastąpić ścieżkę w zestawie narzędzi nadrzędnej. Następujący podklucz znajduje się przykład:  

 \HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  

 Jeśli dowolne właściwości są zdefiniowane w wybranej podzestawu narzędzi i podstawowego zestawu narzędzi, definicje właściwości w podzestawu narzędzi są używane. Na przykład definiuje zestaw narzędzi MSBuild 4.0 `SDK40ToolsPath` wskaż 7.0a zestawu SDK, ale MSBuild 4.0\11.0 narzędzi definiuje tę samą właściwość, aby wskazywał 8.0a zestawu SDK. Jeśli `VisualStudioVersion` ustawiono, `SDK40ToolsPath` mogą wskazywać na 7.0a, ale jeśli `VisualStudioVersion` jest równa 11.0, właściwość zamiast tego mogą wskazywać na 8.0a.  

 `VisualStudioVersion` Właściwość kompilacji wskazuje, czy podzestawu narzędzi stanie się aktywny. Na przykład `VisualStudioVersion` wartość "12.0" Określa podzestawu narzędzi MSBuild 12.0. Aby uzyskać więcej informacji, zobacz sekcję zestawy narzędzi Sub [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  

> [!NOTE]
>  Zaleca się unikać zmiany tych ustawień. Można jednak dodać własne ustawienia i zdefiniuj definicje niestandardowego zestawu narzędzi całego komputera, zgodnie z opisem w następnej sekcji.  

## <a name="custom-toolset-definitions"></a>Definicje niestandardowego zestawu narzędzi  
 Podczas standardowych narzędzi nie spełnia wymagań dotyczących kompilacji, można utworzyć niestandardowego zestawu narzędzi. Na przykład masz scenariusza laboratorium kompilacji, w którym konieczne jest posiadanie oddzielnego systemu do kompilowania [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektów. Za pomocą niestandardowego zestawu narzędzi, można przypisać wartości niestandardowych w celu `ToolsVersion` atrybutu podczas tworzenia projektów lub uruchamiania MSBuild.exe. Dzięki temu można również użyć `$(MSBuildToolsPath)` właściwości, aby zaimportować pliki .targets z tego katalogu, jak również Definiowanie własnych właściwości niestandardowego zestawu narzędzi, których można użyć dla każdego projektu, który używa tego zestawu narzędzi.  

 Określanie niestandardowego zestawu narzędzi w pliku konfiguracji, MSBuild.exe (lub narzędzia niestandardowego, który jest hostem aparat MSBuild, jeśli jest to, czego używasz). Może to obejmować na przykład plik konfiguracji MSBuild.exe następującą definicję zestawu narzędzi, chciałby zastąpić domyślne zachowanie narzędzi w wersji 12.0.  

```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  

 `<msbuildToolsets>` musi również być zdefiniowany w pliku konfiguracji w następujący sposób.  

```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  

> [!NOTE]
>  Można odczytać poprawnie, `<configSections>` musi być pierwszym podsekcję w `<configuration>` sekcji.  

 `ToolsetConfigurationSection` jest sekcji niestandardowej konfiguracji, który może służyć przez dowolnego hosta MSBuild konfiguracji niestandardowej. Jeśli używasz niestandardowego zestawu narzędzi, host nie ma nic robić, aby zainicjować aparatu kompilacji, z wyjątkiem zapewniają konfigurację we wpisach w plikach. Definiując wpisy w rejestrze, można określić zestawy narzędzi całego komputera, które są stosowane do MSBuild.exe, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]i na wszystkich hostach MSBuild.  

> [!NOTE]
>  Jeśli plik konfiguracji definiuje ustawienia `ToolsVersion` została już zdefiniowana w rejestrze, dwie definicje nie są scalane. Definicja w pliku konfiguracyjnym ma pierwszeństwo i ustawienia rejestru dla tego `ToolsVersion` są ignorowane.  

 Następujące właściwości są specyficzne dla wartości `ToolsVersion` oznacza to używane w projektach:  

- **$(MSBuildBinPath)** ustawiono `ToolsPath` wartość, która jest określona w rejestrze lub w pliku konfiguracyjnym gdzie `ToolsVersion` jest zdefiniowana. `$(MSBuildToolsPath)` Ustawienie w rejestrze lub plik konfiguracyjny określa lokalizację podstawowych zadaniach i cele. W pliku projektu mapuje właściwość $(MSBuildBinPath), a także właściwości $(MSBuildToolsPath).  

- `$(MSBuildToolsPath)` jest zastrzeżony właściwość, która jest dostarczana przez właściwość MSBuildToolsPath, która została określona w pliku konfiguracji. (Ta właściwość zastępuje `$(MSBuildBinPath)`. Jednak `$(MSBuildBinPath)` jest przenoszone w celu zachowania zgodności.) Zdefiniuj niestandardowego zestawu narzędzi, albo `$(MSBuildToolsPath)` lub `$(MSBuildBinPath)` , ale nie oba, chyba że mają taką samą wartość.  

  Właściwości niestandardowe, specyficzne dla danego ToolsVersion można również dodać do pliku konfiguracji, za pomocą tej samej składni, która umożliwia dodawanie właściwości MSBuildToolsPath. Aby udostępnić te właściwości niestandardowe do pliku projektu, należy użyć takiej samej nazwie jak nazwa wartość, która jest określona w pliku konfiguracji. W pliku konfiguracji mogą definiować zestawy narzędzi, ale nie sub-zestawy narzędzi.  

## <a name="see-also"></a>Zobacz też  
 [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
