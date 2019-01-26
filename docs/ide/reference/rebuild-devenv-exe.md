---
title: -Rebuild (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65667245ba8cdcdccc3fe96f2fefe89d2d2b1aba
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54965292"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Czyści, a następnie kompiluje konfigurację określonego rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

- *SolnConfigName*

  Opcjonalna. Nazwa konfiguracji rozwiązania (takie jak `Debug` lub `Release`) ma być używany, aby ponownie skompilować rozwiązanie o nazwie w *SolutionName*. Jeśli więcej niż jedną platformę rozwiązanie jest dostępne, należy także określić platformy (na przykład `Debug|Win32`). Jeśli ten argument jest nieokreślona lub pusty ciąg (`""`), narzędzie użyje aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżką względną z *SolutionName* folderu do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig` *ProjConfigName*

  Opcjonalna. Nazwa konfiguracji kompilacji projektu (takie jak `Debug` lub `Release`) do użycia podczas odbudowywania `/Project` o nazwie. Jeśli więcej niż jedną platformę rozwiązanie jest dostępne, należy także określić platformy (na przykład `Debug|Win32`). Jeśli ten parametr jest określony, zastępuje ona *SolnConfigName* argumentu.

- `/Out` *OutputFilename*

  Opcjonalna. Nazwa pliku, który chcesz wysłać narzędzia danych wyjściowych do. Jeśli plik już istnieje, narzędzie dołączyło dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

- Ta opcja działa tak samo jak **Kompiluj rozwiązanie** polecenia menu w środowisku IDE.

- Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

- Podsumowanie informacji na temat czyszczenia i kompilowania, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą [/Out](out-devenv-exe.md) przełącznika.

## <a name="example"></a>Przykład

W tym przykładzie Czyści i ponownie kompiluje projekt `CSharpWinApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)