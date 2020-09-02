---
title: Konfiguracje standardowego i niestandardowego zestawu narzędzi | Microsoft Docs
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
ms.openlocfilehash: d08a7eb20c01568b3501f16348eb19afdcaefa2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "64802644"
---
# <a name="standard-and-custom-toolset-configurations"></a>Konfiguracje standardowego i niestandardowego zestawu narzędzi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zestaw narzędzi programu MSBuild zawiera odwołania do zadań, obiektów docelowych i narzędzi, których można użyć do kompilowania projektu aplikacji. Program MSBuild zawiera standardowy zestaw narzędzi, ale można również tworzyć niestandardowe zestawy narzędzi. Aby uzyskać informacje na temat sposobu określania zestawu narzędzi, zobacz zestaw [narzędzi (ToolsVersion).](../msbuild/msbuild-toolset-toolsversion.md)  

## <a name="standard-toolset-configurations"></a>Standardowe konfiguracje zestawu narzędzi  
 Program MSBuild 12,0 zawiera następujące standardowe zestawy narzędzi:  

| ToolsVersion | Ścieżka zestawu narzędzi (zgodnie z definicją we właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath) |
|--------------|--------------------------------------------------------------------------------------|
|     2,0      |           *Ścieżka instalacji systemu Windows*\Microsoft.Net\Framework\v2.0.50727\            |
|     3,5      |              *Ścieżka instalacji systemu Windows*\Microsoft.Net\Framework\v3.5\               |
|     4,0      |           *Ścieżka instalacji systemu Windows*\Microsoft.NET\Framework\v4.0.30319\            |
|     12.0     |                          *% ProgramFiles%* \MSBuild\12.0\bin                           |

 `ToolsVersion`Wartość określa, który zestaw narzędzi jest używany przez projekt generowany przez program Visual Studio. [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]Wartość domyślna to "12,0" (niezależnie od wersji określonej w pliku projektu), ale można przesłonić ten atrybut przy użyciu przełącznika **/ToolsVersion** w wierszu polecenia. Aby uzyskać informacje o tym atrybucie i innych sposobach określania `ToolsVersion` , zobacz [przesłanianie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).  

 Jeśli `ToolsVersion` nie zostanie określony, klucz rejestru **HKEY_LOCAL_MACHINE \Software\microsoft\msbuild \\<numer wersji \> \DefaultToolsVersion** definiuje `ToolsVersion` , który jest zawsze 2,0.  

 Następujące klucze rejestru określają ścieżkę instalacji MSBuild.exe.  

|Klucz rejestru|Nazwa klucza|Wartość klucza ciągu|  
|------------------|--------------|----------------------|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\MSBuild\ToolsVersions\2.0 \| MSBuildToolsPath|Ścieżka instalacji .NET Framework 2,0|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5 \| MSBuildToolsPath|Ścieżka instalacji .NET Framework 3,5|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0 \| MSBuildToolsPath|Ścieżka instalacji .NET Framework 4|  
|\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\12.0 \| MSBuildToolsPath|Ścieżka instalacji programu MSBuild|  

### <a name="sub-toolsets"></a>Podzestawy narzędzi  
 Jeśli klucz rejestru w poprzedniej tabeli ma podklucz, program MSBuild używa go do określenia ścieżki podzestawu narzędzi może zastąpić ścieżkę w nadrzędnym zestawie narzędzi. Następujący podklucz jest przykładem:  

 \ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0  

 Jeśli wszystkie właściwości są zdefiniowane zarówno w podstawowym zestawie narzędzi, jak i w wybranym podzestawie, są używane definicje właściwości w podzestawie narzędzi. Na przykład zestaw narzędzi programu MSBuild 4,0 definiuje `SDK40ToolsPath` , aby wskazać wersję 7.0 a SDK, ale zestaw narzędzi MSBuild 4.0 \ 11.0 definiuje tę samą właściwość, aby wskazywała na 8.0 a SDK. Jeśli `VisualStudioVersion` to ustawienie ma wartość `SDK40ToolsPath` 7.0 a, ale jeśli `VisualStudioVersion` jest ustawiona na 11,0, właściwość będzie zamiast niego wskazywać 8.0 a.  

 `VisualStudioVersion`Właściwość Build wskazuje, czy podzestaw narzędzi zostanie uaktywniony. Na przykład `VisualStudioVersion` wartość "12,0" określa podrzędny zestaw narzędzi MSBuild 12,0. Aby uzyskać więcej informacji, zobacz sekcję podzestawy narzędzi zestawu [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).  

> [!NOTE]
> Zalecamy uniknięcie zmiany tych ustawień. Niemniej jednak możesz dodać własne ustawienia i zdefiniować niestandardowe definicje zestawu narzędzi dla całego komputera, jak opisano w następnej sekcji.  

## <a name="custom-toolset-definitions"></a>Niestandardowe definicje zestawu narzędzi  
 Jeśli standardowy zestaw narzędzi nie spełnia wymagań kompilacji, można utworzyć niestandardowy zestaw narzędzi. Na przykład może istnieć scenariusz laboratorium kompilacji, w którym trzeba mieć oddzielny system do kompilowania [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektów. Za pomocą niestandardowego zestawu narzędzi, można przypisać niestandardowe wartości do `ToolsVersion` atrybutu podczas tworzenia projektów lub uruchamiania MSBuild.exe. Dzięki temu można również użyć `$(MSBuildToolsPath)` właściwości do importowania plików docelowych z tego katalogu, a także do definiowania własnych niestandardowych właściwości zestawu narzędzi, które mogą być używane dla dowolnego projektu, który używa tego zestawu narzędzi.  

 Określ niestandardowy zestaw narzędzi w pliku konfiguracyjnym dla MSBuild.exe (lub niestandardowego narzędzia, które hostuje aparat MSBuild, jeśli jest to dane, które są używane). Na przykład plik konfiguracyjny MSBuild.exe może zawierać następującą definicję zestawu narzędzi, jeśli chcesz zastąpić domyślne zachowanie ToolsVersion 12,0.  

```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  

 `<msbuildToolsets>` muszą być również zdefiniowane w pliku konfiguracji w następujący sposób.  

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
> Aby można było poprawnie odczytać, `<configSections>` musi to być pierwsza podsekcja w `<configuration>` sekcji.  

 `ToolsetConfigurationSection` to sekcja konfiguracji niestandardowej, która może być używana przez dowolnego hosta programu MSBuild do konfiguracji niestandardowej. W przypadku korzystania z niestandardowego zestawu narzędzi host nie musi wykonywać żadnych czynności w celu zainicjowania aparatu kompilacji, z wyjątkiem podania wpisów w pliku konfiguracji. Definiując wpisy w rejestrze, można określić zestawy narzędzi dla całego komputera, które mają zastosowanie do MSBuild.exe, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i wszystkich hostów programu MSBuild.  

> [!NOTE]
> Jeśli plik konfiguracji definiuje ustawienia dla elementu, `ToolsVersion` który został już zdefiniowany w rejestrze, dwie definicje nie są scalane. Definicja w pliku konfiguracji ma pierwszeństwo, a ustawienia w rejestrze dla programu `ToolsVersion` są ignorowane.  

 Następujące właściwości są specyficzne dla wartości `ToolsVersion` , która jest używana w projektach:  

- **$ (MSBuildBinPath)** jest ustawiona na `ToolsPath` wartość określoną w rejestrze lub w pliku konfiguracyjnym, w którym `ToolsVersion` jest zdefiniowany. `$(MSBuildToolsPath)`Ustawienie w rejestrze lub pliku konfiguracji określa lokalizację podstawowych zadań i elementów docelowych. W pliku projektu, jest mapowany do właściwości $ (MSBuildBinPath), a także do właściwości $ (MSBuildToolsPath).  

- `$(MSBuildToolsPath)` jest właściwością zastrzeżoną, która jest dostarczana przez właściwość MSBuildToolsPath, która jest określona w pliku konfiguracji. (Ta właściwość zastępuje `$(MSBuildBinPath)` . Jednak `$(MSBuildBinPath)` jest on przenoszony pod kątem zgodności). Niestandardowy zestaw narzędzi musi definiować jeden `$(MSBuildToolsPath)` lub `$(MSBuildBinPath)` , ale nie oba, chyba że obie te wartości mają tę samą wartość.  

  Możesz również dodać niestandardowe właściwości specyficzne dla ToolsVersion do pliku konfiguracji, używając tej samej składni, która jest używana do dodawania właściwości MSBuildToolsPath. Aby udostępnić te właściwości niestandardowe dla pliku projektu, należy użyć tej samej nazwy co nazwa wartości, która jest określona w pliku konfiguracji. Można definiować zestawy narzędzi, ale nie podzestawy narzędzi w pliku konfiguracji.  

## <a name="see-also"></a>Zobacz też  
 [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
