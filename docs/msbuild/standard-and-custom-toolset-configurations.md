---
title: Standardowe i niestandardowe konfiguracje zestawu narzędzi | Dokumenty firmy Microsoft
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fef5a84285afdaa429606937f3e537863b060ec8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "77632164"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standardowe i niestandardowe konfiguracje zestawu narzędzi

Zestaw narzędzi MSBuild zawiera odwołania do zadań, obiektów docelowych i narzędzi, których można użyć do utworzenia projektu aplikacji. MSBuild zawiera standardowy zestaw narzędzi, ale można również tworzyć niestandardowe zestawy narzędzi. Aby uzyskać informacje dotyczące określania zestawu narzędzi, zobacz [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Standardowe konfiguracje zestawu narzędzi

::: moniker range=">=vs-2019"
 MSBuild 16.0 zawiera następujące standardowe zestawy narzędzi:

|Toolsversion|Ścieżka zestawu narzędzi (określona w właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath)|
|------------------| - |
|2.0|*\<Ścieżka instalacji systemu Windows>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Ścieżka instalacji systemu Windows>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Ścieżka instalacji systemu Windows>\Microsoft.NET\Framework\v4.0.30319\\*|
|Current|*\<Ścieżka instalacji programu Visual Studio>\MSBuild\Current\bin*|

 Wartość `ToolsVersion` określa, który zestaw narzędzi jest używany przez projekt, który generuje visual studio. W programie Visual Studio 2019 wartością domyślną jest "Current" (bez względu na wersję określoną w pliku projektu), ale można zastąpić ten atrybut przy użyciu **przełącznika /toolsversion** w wierszu polecenia. Aby uzyskać informacje o tym atrybucie i innych sposobach określania `ToolsVersion`opcji , zobacz Ustawienia [zastępowania narzędzi.](../msbuild/overriding-toolsversion-settings.md)

 ::: moniker-end

::: moniker range="vs-2017"
 MSBuild 15.0 zawiera następujące standardowe zestawy narzędzi:

|Toolsversion|Ścieżka zestawu narzędzi (określona w właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath)|
|------------------| - |
|2.0|*\<Ścieżka instalacji systemu Windows>\Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<Ścieżka instalacji systemu Windows>\Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Ścieżka instalacji systemu Windows>\Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Ścieżka instalacji programu Visual Studio>\MSBuild\15.0\bin*|

 Wartość `ToolsVersion` określa, który zestaw narzędzi jest używany przez projekt, który generuje visual studio. W programie Visual Studio 2017 wartość domyślna to "15.0" (bez względu na wersję określoną w pliku projektu), ale można zastąpić ten atrybut za pomocą **przełącznika /toolsversion** w wierszu polecenia. Aby uzyskać informacje o tym atrybucie i innych sposobach określania `ToolsVersion`opcji , zobacz Ustawienia [zastępowania narzędzi.](../msbuild/overriding-toolsversion-settings.md)
 ::: moniker-end

Visual Studio 2017 i nowsze wersje nie używają klucza rejestru dla ścieżki do MSBuild. W przypadku wersji programu MSBuild przed wersją 15.0 zainstalowanych w programie Visual Studio 2017 następujące klucze rejestru określają ścieżkę instalacji programu MSBuild.exe.

|Klucz rejestru|Nazwa klucza|Wartość klucza ciągu|
|------------------|--------------|----------------------|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**Msbuildtoolspath**|**Ścieżka instalacji programu .NET Framework 2.0**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**Msbuildtoolspath**|**Ścieżka instalacji programu .NET Framework 3.5**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**Msbuildtoolspath**|**Ścieżka instalacji programu .NET Framework 4**|

### <a name="sub-toolsets"></a>Zestawy narzędzi podrzędnych

 Jeśli klucz rejestru w poprzedniej tabeli ma podklucz, program MSBuild używa go do określenia ścieżki poddostawki, która zastępuje ścieżkę w nadrzędnym urzędzie narzędziowym. Przykładem jest następujący podklucz:

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Jeśli wszystkie właściwości są zdefiniowane zarówno w podstawowym zestawie narzędzi, jak i w wybranym poddobiernym, używane są definicje właściwości w poddobiernym. Na przykład zestaw narzędzi MSBuild 4.0 definiuje `SDK40ToolsPath` wskazywać zestaw SDK 7.0A, ale zestaw narzędzi MSBuild 4.0\11.0 definiuje tę samą właściwość, aby wskazać zestaw SDK 8.0A. Jeśli `VisualStudioVersion` jest unset, `SDK40ToolsPath` wskazuje 7.0A, `VisualStudioVersion` ale jeśli jest ustawiona na 11.0, właściwość zamiast wskazać 8.0A.

 Właściwość `VisualStudioVersion` build wskazuje, czy zestaw narzędzi podrzędnych staje się aktywny. Na przykład `VisualStudioVersion` wartość "12.0" określa zestaw narzędzi podrzędnych MSBuild 12.0. Aby uzyskać więcej informacji, zobacz sekcję Poddokonustawy [zestawu narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

> [!NOTE]
> Zaleca się unikanie zmiany tych ustawień. Niemniej jednak można dodać własne ustawienia i zdefiniować niestandardowe definicje zestawu narzędzi dla całego komputera, jak opisano w następnej sekcji.

## <a name="custom-toolset-definitions"></a>Niestandardowe definicje zestawu narzędzi

 Jeśli standardowy zestaw narzędzi nie spełnia wymagań kompilacji, można utworzyć niestandardowy zestaw narzędzi. Na przykład może mieć scenariusz laboratorium kompilacji, w którym musi mieć oddzielny system do tworzenia projektów C++. Za pomocą niestandardowego zestawu narzędzi można przypisać `ToolsVersion` wartości niestandardowe do atrybutu podczas tworzenia projektów lub uruchamiania programu *MSBuild.exe*. W ten sposób można również `$(MSBuildToolsPath)` użyć właściwości do importowania plików *.targets* z tego katalogu, a także definiowania własnych niestandardowych właściwości zestawu narzędzi, które mogą być używane dla dowolnego projektu, który używa tego zestawu narzędzi.

 Określ niestandardowy zestaw narzędzi w pliku konfiguracyjnym dla *programu MSBuild.exe* (lub dla niestandardowego narzędzia, które obsługuje aparat MSBuild, jeśli jest to, czego używasz). Na przykład plik konfiguracyjny dla *pliku MSBuild.exe* może zawierać następującą definicję zestawu narzędzi, jeśli chcesz zdefiniować zestaw narzędzi o nazwie *MyCustomToolset*.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 `<msbuildToolsets>`należy również zdefiniować w pliku konfiguracyjnym w następujący sposób.

```xml
<configSections>
   <section name="msbuildToolsets"
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,
       Microsoft.Build, Version=15.1.0.0, Culture=neutral,
       PublicKeyToken=b03f5f7f11d50a3a"
   </section>
</configSections>
```

> [!NOTE]
> Aby można było `<configSections>` poprawnie odczytać, musi być `<configuration>` pierwszą podsekcją w sekcji.

 `ToolsetConfigurationSection`to niestandardowa sekcja konfiguracji, która może być używana przez dowolnego hosta MSBuild dla konfiguracji niestandardowej. Jeśli używasz niestandardowego zestawu narzędzi, host nie musi nic robić, aby zainicjować aparat kompilacji, z wyjątkiem podać wpisy pliku konfiguracji. Definiując wpisy w rejestrze, można określić zestawy narzędzi dla całego komputera, które mają zastosowanie do *programu MSBuild.exe,* programu Visual Studio i wszystkich hostów programu MSBuild.

> [!NOTE]
> Jeśli plik konfiguracyjny `ToolsVersion` definiuje ustawienia dla tego, który został już zdefiniowany w rejestrze, dwie definicje nie są scalane. Definicja w pliku konfiguracyjny ma pierwszeństwo, `ToolsVersion` a ustawienia w rejestrze są ignorowane.

 Następujące właściwości są specyficzne dla `ToolsVersion` wartości, która jest używana w projektach:

- **$(MSBuildBinPath)** jest ustawiona na wartość określoną `ToolsPath` w rejestrze lub `ToolsVersion` w pliku konfiguracyjnym, w którym jest zdefiniowana. Ustawienie `$(MSBuildToolsPath)` w rejestrze lub pliku konfiguracyjnym określa lokalizację podstawowych zadań i obiektów docelowych. W pliku projektu ta jest mapowana na właściwość $(MSBuildBinPath), a także do właściwości $(MSBuildToolsPath).

- `$(MSBuildToolsPath)`jest właściwością zastrzeżoną, która jest dostarczana przez właściwość MSBuildToolsPath określoną w pliku konfiguracyjnym. (Ta właściwość `$(MSBuildBinPath)`zastępuje . Jednakże, `$(MSBuildBinPath)` jest przenoszony do zgodności.) Niestandardowy zestaw narzędzi musi `$(MSBuildToolsPath)` `$(MSBuildBinPath)` definiować oba lub oba, chyba że oba mają tę samą wartość.

  Można również dodać niestandardowe właściwości specyficzne dla ToolsVersion do pliku konfiguracyjnego przy użyciu tej samej składni, której używasz do dodania właściwości MSBuildToolsPath. Aby te właściwości niestandardowe były dostępne dla pliku projektu, należy użyć tej samej nazwy co nazwa wartości, która jest określona w pliku konfiguracji. Zestawy narzędzi można definiować, ale nie zestawy narzędzi podrzędnych w pliku konfiguracyjnym.

## <a name="see-also"></a>Zobacz też

- [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
