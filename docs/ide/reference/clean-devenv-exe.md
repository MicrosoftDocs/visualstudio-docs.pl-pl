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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 823f79169b655bd12222a7debedab820017257f6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003022"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Czyści wszystkie pośrednie pliki i katalogi wyjściowe.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

- *config*

  Opcjonalna. Konfiguracja (takie jak `Debug` lub `Release`) można wyczyścić pośrednie pliki dla rozwiązania o nazwie w *SolutionName*. Jeśli więcej niż jedną platformę rozwiązanie jest dostępne, należy także określić platformy (na przykład `Debug|Win32`). Jeśli ten argument jest nieokreślona lub pusty ciąg (`""`), narzędzie użyje aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżką względną z *SolutionName* folderu do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig` *ProjConfigName*

  Opcjonalna. Nazwa konfiguracji kompilacji projektu (takie jak `Debug` lub `Release`) ma być używany podczas czyszczenia `/Project` o nazwie. Jeśli więcej niż jedną platformę rozwiązanie jest dostępne, należy także określić platformy (na przykład `Debug|Win32`). Jeśli ten parametr jest określony, zastępuje ona *Config* argumentu.

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