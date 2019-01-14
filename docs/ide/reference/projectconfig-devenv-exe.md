---
title: -ProjectConfig (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /ProjectConfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /ProjectConfig switch
- ProjectConfig Devenv switch (/ProjectConfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a199fb7656e36720a6787557e2e0746b79795fd3
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269933"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Określa konfigurację kompilacji projektu mają być stosowane podczas kompilacji, czyszczenia, odbudować lub wdrożyć projekt o nazwie w `/Project` argumentu.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName {/Build|/Clean|/Deploy|/Rebuild} [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

- {`/Build`|`/Clean`|`/Deploy`|`/Rebuild`}

  Wymagana. [Kompilacje](build-devenv-exe.md), [czyści](clean-devenv-exe.md), [wdraża](deploy-devenv-exe.md), lub [odbudowuje](rebuild-devenv-exe.md) projektu.

- *SolnConfigName*

  Opcjonalna. Nazwa konfiguracji rozwiązania (takie jak `Debug` lub `Release`) mają być stosowane do rozwiązania o nazwie w *SolutionName*. Jeśli więcej niż jedną platformę rozwiązanie jest dostępne, należy także określić platformy (na przykład `Debug|Win32`). Jeśli ten argument jest nieokreślona lub pusty ciąg (`""`), narzędzie użyje aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżką względną z *SolutionName* folderu do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig` *ProjConfigName*

  Opcjonalna. Nazwa konfiguracji kompilacji projektu (takie jak `Debug` lub `Release`) mają być stosowane do `/Project` o nazwie. Jeśli więcej niż jedną platformę rozwiązanie jest dostępne, należy także określić platformy (na przykład `Debug|Win32`).

- `/Out` *OutputFilename*

  Opcjonalna. Nazwa pliku, który chcesz wysłać narzędzia danych wyjściowych do. Jeśli plik już istnieje, narzędzie dołączyło dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

`/ProjectConfig` Przełącznik musi być używany z `/Project` przełącznika jako część `/Build`, /`Clean`, `/Deploy`, lub `/Rebuild` polecenia.

Należy ująć ciągi zawierające spacje w cudzysłów.

Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w oknie wiersza polecenia lub pliku dziennika określony za pomocą `/Out` przełącznika.

## <a name="example"></a>Przykład

Następujące polecenie tworzy projekt `CSharpWinApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `MySolution`:

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)