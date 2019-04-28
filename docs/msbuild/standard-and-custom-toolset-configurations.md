---
title: Konfiguracje standardowego i niestandardowego zestawu narzędzi | Dokumentacja firmy Microsoft
ms.date: 01/31/2018
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, custom toolset configurations
- MSBuild, msbuild.exe.config
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a8d3e78e4bd49c36174280c62ca8f24cdbd7f648
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440040"
---
# <a name="standard-and-custom-toolset-configurations"></a>Standardowe i niestandardowe konfiguracje zestawu narzędzi
Zestaw narzędzi MSBuild zawiera odwołania do zadania, celów i narzędzi, które służą do tworzenia projektu aplikacji. Program MSBuild zawiera standardowy zestaw narzędzi, ale można również tworzyć niestandardowe zestawy narzędzi. Aby uzyskać informacje o sposobie określania zestaw narzędzi, zobacz [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Konfiguracje standardowego zestawu narzędzi

::: moniker range=">=vs-2019"
 Program MSBuild 16.0 obejmuje następujące standardowe zestawy narzędzi:

|ToolsVersion|Ścieżka zestawu narzędzi (określoną we właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath)|
|------------------| - |
|2.0|*\<Ścieżka instalacji Windows > \Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<Ścieżka instalacji Windows > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Ścieżka instalacji Windows > \Microsoft.NET\Framework\v4.0.30319\\*|
|bieżący|*\<Ścieżka instalacji usługi Visual Studio > \MSBuild\Current\bin*|

 `ToolsVersion` Wartość określa, który zestaw narzędzi jest używany przez projekt, który generuje programie Visual Studio. W programie Visual Studio 2019 r, wartością domyślną jest "Current" (niezależnie od tego, jakie wersja określona w pliku projektu), ale ten atrybut można zastąpić za pomocą **/toolsversion** Przejdź w wierszu polecenia. Informacje o tego atrybutu i inne sposoby określania `ToolsVersion`, zobacz [ustawienia ToolsVersion zastępowanie](../msbuild/overriding-toolsversion-settings.md).

 ::: moniker-end

::: moniker range="vs-2017"
 Program MSBuild 15.0 obejmuje następujące standardowe zestawy narzędzi:

|ToolsVersion|Ścieżka zestawu narzędzi (określoną we właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath)|
|------------------| - |
|2.0|*\<Ścieżka instalacji Windows > \Microsoft.Net\Framework\v2.0.50727\\*|
|3.5|*\<Ścieżka instalacji Windows > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<Ścieżka instalacji Windows > \Microsoft.NET\Framework\v4.0.30319\\*|
|15.0|*\<Ścieżka instalacji usługi Visual Studio > \MSBuild\15.0\bin*|

 `ToolsVersion` Wartość określa, który zestaw narzędzi jest używany przez projekt, który generuje programie Visual Studio. W programie Visual Studio 2017, wartością domyślną jest "15.0" (niezależnie od tego, jakie wersja określona w pliku projektu), ale ten atrybut można zastąpić za pomocą **/toolsversion** Przejdź w wierszu polecenia. Informacje o tego atrybutu i inne sposoby określania `ToolsVersion`, zobacz [ustawienia ToolsVersion zastępowanie](../msbuild/overriding-toolsversion-settings.md).
 ::: moniker-end

Program Visual Studio 2017 i nowsze wersje nie należy używać klucza rejestru dla ścieżki do programu MSBuild. W przypadku wersji MSBuild przed 15.0, które są instalowane z Visual Studio 2017 następujące klucze rejestru wpisz ścieżkę instalacji MSBuild.exe.

|Klucz rejestru|Nazwa klucza|Wartość klucza ciągu|
|------------------|--------------|----------------------|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**Ścieżka instalacji programu .NET framework w wersji 2.0**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**Ścieżka instalacji programu .NET framework 3.5**|
|**\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**Ścieżka instalacji programu .NET framework 4**|

### <a name="sub-toolsets"></a>Sub — zestawy narzędzi
 Jeśli klucz rejestru w poprzedniej tabeli ma podklucza, program MSBuild używa można ustalić ścieżki podzestawu narzędzi zastępujący ścieżki w obiekcie nadrzędnym zestawu narzędzi. Następujący podklucz znajduje się przykład:

 **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Jeśli dowolne właściwości są zdefiniowane w wybranej podzestawu narzędzi i podstawowego zestawu narzędzi, definicje właściwości w podzestawu narzędzi są używane. Na przykład definiuje zestaw narzędzi MSBuild 4.0 `SDK40ToolsPath` wskaż 7.0a zestawu SDK, ale MSBuild 4.0\11.0 narzędzi definiuje tę samą właściwość, aby wskazywał 8.0a zestawu SDK. Jeśli `VisualStudioVersion` ustawiono, `SDK40ToolsPath` mogą wskazywać na 7.0a, ale jeśli `VisualStudioVersion` jest równa 11.0, właściwość zamiast tego mogą wskazywać na 8.0a.

 `VisualStudioVersion` Właściwość kompilacji wskazuje, czy podzestawu narzędzi stanie się aktywny. Na przykład `VisualStudioVersion` wartość "12.0" Określa podzestawu narzędzi MSBuild 12.0. Aby uzyskać więcej informacji, zobacz sekcję zestawy narzędzi Sub [zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

> [!NOTE]
> Zaleca się unikać zmiany tych ustawień. Można jednak dodać własne ustawienia i Zdefiniuj niestandardowe definicje zestawu narzędzi całego komputera, zgodnie z opisem w następnej sekcji.

## <a name="custom-toolset-definitions"></a>Niestandardowe definicje zestawu narzędzi
 Podczas standardowych narzędzi nie spełnia wymagań dotyczących kompilacji, można utworzyć niestandardowego zestawu narzędzi. Na przykład masz scenariusza laboratorium kompilacji, w którym konieczne jest posiadanie oddzielnego systemu do kompilowania [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektów. Za pomocą niestandardowego zestawu narzędzi, można przypisać wartości niestandardowych w celu `ToolsVersion` atrybutu podczas tworzenia projektów lub uruchamiania *MSBuild.exe*. Dzięki temu można również użyć `$(MSBuildToolsPath)` właściwość do zaimportowania *.targets* pliki z tego katalogu, jak również Definiowanie własnych właściwości zestawu narzędzi niestandardowych, które mogą być używane dla każdego projektu, który używa tego zestawu narzędzi.

 Określanie niestandardowego zestawu narzędzi w pliku konfiguracji dla *MSBuild.exe* (lub narzędzia niestandardowego, który hostuje MSBuild aparatu, jeśli jest to, czego używasz). Na przykład plik konfiguracji *MSBuild.exe* mogą obejmować następujące definicje zestawu narzędzi, jeśli zamierza do definiowania zestawu narzędzi o nazwie *MyCustomToolset*.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 `<msbuildToolsets>` musi również być zdefiniowany w pliku konfiguracji w następujący sposób.

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
> Można odczytać poprawnie, `<configSections>` musi być pierwszym podsekcję w `<configuration>` sekcji.

 `ToolsetConfigurationSection` jest sekcji niestandardowej konfiguracji, który może służyć przez dowolnego hosta MSBuild konfiguracji niestandardowej. Jeśli używasz niestandardowego zestawu narzędzi, host nie ma nic robić, aby zainicjować aparatu kompilacji, z wyjątkiem zapewniają konfigurację we wpisach w plikach. Definiując wpisy w rejestrze, można określić zestawy narzędzi całego komputera, które są stosowane do *MSBuild.exe*, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]i na wszystkich hostach MSBuild.

> [!NOTE]
> Jeśli plik konfiguracji definiuje ustawienia `ToolsVersion` została już zdefiniowana w rejestrze, dwie definicje nie są scalane. Definicja w pliku konfiguracyjnym ma pierwszeństwo i ustawienia rejestru dla tego `ToolsVersion` są ignorowane.

 Następujące właściwości są specyficzne dla wartości `ToolsVersion` oznacza to używane w projektach:

- **$(MSBuildBinPath)** ustawiono `ToolsPath` wartość, która jest określona w rejestrze lub w pliku konfiguracyjnym gdzie `ToolsVersion` jest zdefiniowana. `$(MSBuildToolsPath)` Ustawienie w rejestrze lub plik konfiguracyjny określa lokalizację podstawowych zadaniach i cele. W pliku projektu mapuje właściwość $(MSBuildBinPath), a także właściwości $(MSBuildToolsPath).

- `$(MSBuildToolsPath)` jest zastrzeżony właściwość, która jest dostarczana przez właściwość MSBuildToolsPath, która została określona w pliku konfiguracji. (Ta właściwość zastępuje `$(MSBuildBinPath)`. Jednak `$(MSBuildBinPath)` jest przenoszone w celu zachowania zgodności.) Zdefiniuj niestandardowego zestawu narzędzi, albo `$(MSBuildToolsPath)` lub `$(MSBuildBinPath)` , ale nie oba, chyba że mają taką samą wartość.

  Właściwości niestandardowe, specyficzne dla danego ToolsVersion można również dodać do pliku konfiguracji, za pomocą tej samej składni, która umożliwia dodawanie właściwości MSBuildToolsPath. Aby udostępnić te właściwości niestandardowe do pliku projektu, należy użyć takiej samej nazwie jak nazwa wartość, która jest określona w pliku konfiguracji. W pliku konfiguracji mogą definiować zestawy narzędzi, ale nie sub-zestawy narzędzi.

## <a name="see-also"></a>Zobacz także
- [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)