---
title: Równoległe kompilowanie wielu projektów za pomocą programu MSBuild | Microsoft Docs
description: Dowiedz się więcej na temat ustawień programu MSBuild, których można użyć do szybszego kompilowania wielu projektów przez uruchamianie ich równolegle.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- parallel project builds
- building multiple projects in parallel
- msbuild, building projects in parallel
ms.assetid: c8c9aadc-33ad-4aa1-b07d-b879e9eabda0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c8e90a649a11933e4281140299bf9ee1b564a212
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939633"
---
# <a name="build-multiple-projects-in-parallel-with-msbuild"></a>Równoległe kompilowanie wielu projektów za pomocą programu MSBuild

Można użyć programu MSBuild do kompilacji wielu projektów przez uruchomienie ich równolegle. Aby uruchomić kompilacje równolegle, należy użyć następujących ustawień na komputerze z wieloma procesorami lub procesorem o wielu rdzeniach:

- Należy użyć przełącznika `-maxcpucount` w wierszu polecenia.

- Parametr zadania <xref:Microsoft.Build.Tasks.MSBuild.BuildInParallel%2A> w zadaniu programu MSBuild.

> [!NOTE]
> Przełącznik **-verbose** (**-v**) w wierszu polecenia może również wpływać na wydajność kompilacji. Wydajność kompilacji może spaść jeśli szczegółowość informacji dziennika kompilacji jest ustawiona na szczegóły lub diagnostyka, które są używane w celu rozwiązania problemów. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie dzienników kompilacji](../msbuild/obtaining-build-logs-with-msbuild.md) i [Dokumentacja wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

## <a name="-maxcpucount-switch"></a>-maxcpucount przełącznik

Jeśli używasz `-maxcpucount` przełącznika lub `-m` krótko, MSBuild może utworzyć określoną liczbę *MSBuild.exe* procesów, które mogą być uruchamiane równolegle. Procesy te są nazywane także „procesami roboczymi”. Każdy proces roboczy używa oddzielnego rdzenia procesora, jeśli jakieś są dostępne, do kompilacji projektu a w tym samym czasie inne dostępne procesory mogą kompilować inne projekty. Na przykład ustawienie tego parametru na wartość „4” spowoduje, że program MSBuild utworzy cztery procesy robocze w celu skompilowania projektu.

Jeśli przełącznik `-maxcpucount` zostanie dołączony, bez określenia wartości, program MSBuild użyje maksymalnie wartości równej liczbie procesorów w komputerze.

Aby uzyskać więcej informacji na temat tego przełącznika, który został wprowadzony w programie MSBuild 3,5, zobacz [informacje dotyczące wiersza polecenia](../msbuild/msbuild-command-line-reference.md).

Poniższy przykład powoduje, że program MSBuild będzie używać trzech procesów roboczych. Jeśli używana jest ta konfiguracja, program MSBuild może kompilować trzy projekty w tym samym czasie.

```cmd
msbuild.exe myproj.proj -maxcpucount:3
```

## <a name="buildinparallel-task-parameter"></a>BuildInParallel — parametr zadania

`BuildInParallel` jest opcjonalnym parametrem logicznym zadania programu MSBuild. Gdy `BuildInParallel` jest ustawiona na `true` (wartość domyślna to `true` ), generowane są wiele procesów roboczych w celu jednoczesnego skompilowania możliwie największej liczby projektów. Do poprawnego działania przełącznik `-maxcpucount` musi być ustawiony na wartość większą niż 1, a system musi posiadać co najmniej dwa procesory lub procesor dwurdzeniowy.

Poniżej znajduje się przykład pochodzący z *Microsoft. Common. targets*, how to Set The `BuildInParallel` Parameter.

```xml
<PropertyGroup>
    <BuildInParallel Condition="'$(BuildInParallel)' ==
        ''">true</BuildInParallel>
</PropertyGroup>
<MSBuild
    Projects="@(_MSBuildProjectReferenceExistent)"
    Targets="GetTargetPath"
    BuildInParallel="$(BuildInParallel)"
    Properties="%(_MSBuildProjectReferenceExistent.SetConfiguration);
        %(_MSBuildProjectReferenceExistent.SetPlatform)"
    Condition="'@(NonVCProjectReference)'!='' and
        ('$(BuildingSolutionFile)' == 'true' or
        '$(BuildingInsideVisualStudio)' == 'true' or
        '$(BuildProjectReferences)' != 'true') and
        '@(_MSBuildProjectReferenceExistent)' != ''"
    ContinueOnError="!$(BuildingProject)">
    <Output TaskParameter="TargetOutputs"
        ItemName="_ResolvedProjectReferencePaths"/>
</MSBuild>
```

## <a name="see-also"></a>Zobacz też

- [Używanie wielu procesorów do kompilowania projektów](../msbuild/using-multiple-processors-to-build-projects.md)
- [Zapisuj rejestratory obsługujące wiele procesorów](../msbuild/writing-multi-processor-aware-loggers.md)
- [Dostrajanie blogu kompilacji w języku C++](https://devblogs.microsoft.com/visualstudio/tuning-c-build-parallelism-in-vs2010/)
