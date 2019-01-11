---
title: -Clean (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6ba03deab04fa3660d48de84803e4fc974965c0b
ms.sourcegitcommit: 01185dadd2fa1f9a040d2a366869f1a5e1d18e0f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54227151"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Czyści wszystkie pośrednie pliki i katalogi wyjściowe.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *Nazwa rozwiązania*

  Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

- *config*

  Opcjonalna. Konfigurację, aby wyczyścić pośrednie pliki (takie jak `Debug` lub `Release`). Jeśli ten argument jest wykluczony, narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżką względną z *SolutionName* folderu do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig` *ProjConfigName*

  Opcjonalna. Nazwa konfiguracji kompilacji projektu który będzie używany podczas czyszczenia `/Project` o nazwie. Jeśli ten parametr jest określony, zastępuje ona *Config* argumentu.

- `/Out` *OutputFilename*

  Opcjonalna. Nazwa pliku, który chcesz wysłać narzędzia danych wyjściowych do. Jeśli plik już istnieje, narzędzie dołączyło dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Ten przełącznik jest taką samą funkcję jak **czyste rozwiązanie** polecenia menu w środowisku IDE.

Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

Informacje podsumowujące podczas czyszczenia i kompilowania, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą [/Out](out-devenv-exe.md) przełącznika.

Jeśli `/Project` przełącznika nie jest określona, akcja czyszczenia odbywa się na wszystkie projekty w rozwiązaniu, nawet jeśli *FileName* został określony jako pliku projektu.

## <a name="example"></a>Przykład

Pierwszy przykład czyści `MySolution` rozwiązania przy użyciu domyślnej konfiguracji określone w pliku rozwiązania.

Drugi przykład czyści projektu `CSharpWinApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)