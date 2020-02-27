---
title: Konfiguracje standardowego i niestandardowego zestawu narzędzi | Microsoft Docs
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
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632164"
---
# <a name="standard-and-custom-toolset-configurations"></a>Konfiguracje standardowego i niestandardowego zestawu narzędzi

Zestaw narzędzi programu MSBuild zawiera odwołania do zadań, obiektów docelowych i narzędzi, których można użyć do kompilowania projektu aplikacji. Program MSBuild zawiera standardowy zestaw narzędzi, ale można również tworzyć niestandardowe zestawy narzędzi. Aby uzyskać informacje na temat sposobu określania zestawu narzędzi, zobacz zestaw [narzędzi (ToolsVersion).](../msbuild/msbuild-toolset-toolsversion.md)

## <a name="standard-toolset-configurations"></a>Standardowe konfiguracje zestawu narzędzi

::: moniker range=">=vs-2019"
 Program MSBuild 16,0 zawiera następujące standardowe zestawy narzędzi:

|ToolsVersion|Ścieżka zestawu narzędzi (zgodnie z definicją we właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath)|
|------------------| - |
|2.0|*\<ścieżka instalacji systemu Windows > \Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<ścieżka instalacji systemu Windows > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<ścieżka instalacji systemu Windows > \Microsoft.NET\Framework\v4.0.30319\\*|
|Obecne|*\<ścieżka instalacji programu Visual Studio > \MSBuild\Current\bin*|

 Wartość `ToolsVersion` określa, który zestaw narzędzi jest używany przez projekt, który generuje program Visual Studio. W programie Visual Studio 2019 wartość domyślna to "Current" (niezależnie od wersji określonej w pliku projektu), ale można przesłonić ten atrybut przy użyciu przełącznika **/ToolsVersion** w wierszu polecenia. Aby uzyskać informacje o tym atrybucie i innych sposobach określania `ToolsVersion`, zobacz [przesłanianie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).

 ::: moniker-end

::: moniker range="vs-2017"
 Program MSBuild 15,0 zawiera następujące standardowe zestawy narzędzi:

|ToolsVersion|Ścieżka zestawu narzędzi (zgodnie z definicją we właściwości kompilacji MSBuildToolsPath lub MSBuildBinPath)|
|------------------| - |
|2.0|*\<ścieżka instalacji systemu Windows > \Microsoft.Net\Framework\v2.0.50727\\*|
|3,5|*\<ścieżka instalacji systemu Windows > \Microsoft.NET\Framework\v3.5\\*|
|4.0|*\<ścieżka instalacji systemu Windows > \Microsoft.NET\Framework\v4.0.30319\\*|
|15,0|*\<ścieżka instalacji programu Visual Studio > katalogu \msbuild\15.0\bin*|

 Wartość `ToolsVersion` określa, który zestaw narzędzi jest używany przez projekt, który generuje program Visual Studio. W programie Visual Studio 2017 wartość domyślna to "15,0" (niezależnie od wersji określonej w pliku projektu), ale można przesłonić ten atrybut przy użyciu przełącznika **/ToolsVersion** w wierszu polecenia. Aby uzyskać informacje o tym atrybucie i innych sposobach określania `ToolsVersion`, zobacz [przesłanianie ustawień ToolsVersion](../msbuild/overriding-toolsversion-settings.md).
 ::: moniker-end

Program Visual Studio 2017 i jego nowsze wersje nie używają klucza rejestru dla ścieżki do programu MSBuild. W przypadku wersji programu MSBuild wcześniejszych niż 15,0 zainstalowanych z programem Visual Studio 2017 następujące klucze rejestru określają ścieżkę instalacji programu MSBuild. exe.

|Klucz rejestru|Nazwa klucza|Wartość klucza ciągu|
|------------------|--------------|----------------------|
|**\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\2.0\\** |**MSBuildToolsPath**|**Ścieżka instalacji .NET Framework 2,0**|
|**\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\3.5\\** |**MSBuildToolsPath**|**Ścieżka instalacji .NET Framework 3,5**|
|**\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\ MSBuild\ToolsVersions\4.0\\** |**MSBuildToolsPath**|**Ścieżka instalacji .NET Framework 4**|

### <a name="sub-toolsets"></a>Podzestawy narzędzi

 Jeśli klucz rejestru w poprzedniej tabeli ma podklucz, program MSBuild używa go do określenia ścieżki podzestawu narzędzi, który zastępuje ścieżkę w nadrzędnym zestawie narzędzi. Następujący podklucz jest przykładem:

 **\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\MSBuild\ToolsVersions\12.0\12.0**

 Jeśli wszystkie właściwości są zdefiniowane zarówno w podstawowym zestawie narzędzi, jak i w wybranym podzestawie, są używane definicje właściwości w podzestawie narzędzi. Na przykład zestaw narzędzi programu MSBuild 4,0 definiuje `SDK40ToolsPath` tak, aby wskazywał w wersji 7.0 zestawu SDK, ale zestaw narzędzi MSBuild 4.0 \ 11.0 definiuje tę samą właściwość, aby wskazywała na 8.0 A SDK. Jeśli `VisualStudioVersion` nie zostanie ustawiona, `SDK40ToolsPath` będzie wskazywał w wersji 7.0 A, ale jeśli `VisualStudioVersion` jest ustawiony na 11,0, właściwość zamiast tego będzie wskazywała na 8.0 A.

 Właściwość kompilacja `VisualStudioVersion` wskazuje, czy podzestaw narzędzi zostanie uaktywniony. Na przykład `VisualStudioVersion` wartość "12,0" określa podrzędny zestaw narzędzi MSBuild 12,0. Aby uzyskać więcej informacji, zobacz sekcję podzestawy narzędzi zestawu [narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md).

> [!NOTE]
> Zalecamy uniknięcie zmiany tych ustawień. Niemniej jednak możesz dodać własne ustawienia i zdefiniować niestandardowe definicje zestawu narzędzi dla całego komputera, jak opisano w następnej sekcji.

## <a name="custom-toolset-definitions"></a>Niestandardowe definicje zestawu narzędzi

 Jeśli standardowy zestaw narzędzi nie spełnia wymagań kompilacji, można utworzyć niestandardowy zestaw narzędzi. Na przykład może istnieć scenariusz laboratorium kompilacji, w którym trzeba mieć oddzielny system do kompilowania C++ projektów. Przy użyciu niestandardowego zestawu narzędzi można przypisać niestandardowe wartości do atrybutu `ToolsVersion` podczas tworzenia projektów lub uruchamiania programu *MSBuild. exe*. W tym celu można również użyć właściwości `$(MSBuildToolsPath)` do zaimportowania plików *targets* z tego katalogu, a także zdefiniowania własnych niestandardowych właściwości zestawu narzędzi, które mogą być używane dla dowolnego projektu, który używa tego zestawu narzędzi.

 Określ niestandardowy zestaw narzędzi w pliku konfiguracji dla programu *MSBuild. exe* (lub niestandardowego narzędzia, które hostuje aparat MSBuild, jeśli jest to dane, które są używane). Na przykład plik konfiguracji programu *MSBuild. exe* może zawierać następującą definicję zestawu narzędzi, jeśli chcesz zdefiniować zestaw narzędzi o nazwie *MyCustomToolset*.

```xml
<msbuildToolsets default="MyCustomToolset">
   <toolset toolsVersion="MyCustomToolset">
      <property name="MSBuildToolsPath"
        value="C:\SpecialPath" />
   </toolset>
</msbuildToolsets>
```

 `<msbuildToolsets>` muszą być również zdefiniowane w pliku konfiguracji w następujący sposób.

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
> Aby można było poprawnie odczytać, `<configSections>` musi być pierwszą podsekcją w sekcji `<configuration>`.

 `ToolsetConfigurationSection` to niestandardowa sekcja konfiguracji, która może być używana przez dowolnego hosta programu MSBuild do konfiguracji niestandardowej. W przypadku korzystania z niestandardowego zestawu narzędzi host nie musi wykonywać żadnych czynności w celu zainicjowania aparatu kompilacji, z wyjątkiem podania wpisów w pliku konfiguracji. Definiując wpisy w rejestrze, można określić zestawy narzędzi dla całego komputera, które mają zastosowanie do programu *MSBuild. exe*, programu Visual Studio i wszystkich hostów programu MSBuild.

> [!NOTE]
> Jeśli plik konfiguracji definiuje ustawienia dla `ToolsVersion`, które zostały już zdefiniowane w rejestrze, dwie definicje nie są scalone. Definicja w pliku konfiguracji ma pierwszeństwo, a ustawienia w rejestrze dla tego `ToolsVersion` są ignorowane.

 Następujące właściwości są specyficzne dla wartości `ToolsVersion`, które są używane w projektach:

- **$ (MSBuildBinPath)** jest ustawiona na wartość `ToolsPath` określoną w rejestrze lub w pliku konfiguracyjnym, w którym zdefiniowano `ToolsVersion`. Ustawienie `$(MSBuildToolsPath)` w rejestrze lub pliku konfiguracji określa lokalizację podstawowych zadań i elementów docelowych. W pliku projektu, jest mapowany do właściwości $ (MSBuildBinPath), a także do właściwości $ (MSBuildToolsPath).

- `$(MSBuildToolsPath)` jest właściwością zastrzeżoną, która jest dostarczana przez właściwość MSBuildToolsPath, która jest określona w pliku konfiguracji. (Ta właściwość zastępuje `$(MSBuildBinPath)`. Jednak `$(MSBuildBinPath)` jest przenoszony pod kątem zgodności). Niestandardowy zestaw narzędzi musi definiować `$(MSBuildToolsPath)` lub `$(MSBuildBinPath)`, ale nie oba, chyba że obie te wartości mają tę samą wartość.

  Możesz również dodać niestandardowe właściwości specyficzne dla ToolsVersion do pliku konfiguracji, używając tej samej składni, która jest używana do dodawania właściwości MSBuildToolsPath. Aby udostępnić te właściwości niestandardowe dla pliku projektu, należy użyć tej samej nazwy co nazwa wartości, która jest określona w pliku konfiguracji. Można definiować zestawy narzędzi, ale nie podzestawy narzędzi w pliku konfiguracji.

## <a name="see-also"></a>Zobacz też

- [Zestaw narzędzi (ToolsVersion)](../msbuild/msbuild-toolset-toolsversion.md)
