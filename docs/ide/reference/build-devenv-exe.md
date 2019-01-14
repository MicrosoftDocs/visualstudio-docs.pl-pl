---
title: -Build (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 30637a797d8c0845bae9548bb6a48e877d44727b
ms.sourcegitcommit: 38db86369af19e174b0aba59ba1918a5c4fe4a61
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2019
ms.locfileid: "54269478"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Kompiluje rozwiązanie lub projekt przy użyciu pliku konfiguracji określonego rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

- *SolnConfigName*

  Opcjonalna. Nazwa konfiguracji rozwiązania (takie jak `Debug` lub `Release`) ma być używany w celu skompilowania rozwiązania o nazwie w *SolutionName*. Jeśli dostępnych jest wiele platform rozwiązania, należy także określić platformy (na przykład `Debug|Win32`). Jeśli ten argument jest nieokreślona lub pusty ciąg (`""`), narzędzie użyje aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z *SolutionName* folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig` *ProjConfigName*

  Opcjonalna. Nazwa projektu Konfiguracja kompilacji (takich jak `Debug` lub `Release`) ma być używany podczas kompilowania projektu o nazwie. Jeśli więcej niż jedną platformę rozwiązanie jest dostępne, należy także określić platformy (na przykład `Debug|Win32`). Jeśli ten parametr jest określony, zastępuje ona *SolnConfigName* argumentu.

- `/Out` *OutputFilename*

  Opcjonalna. Nazwa pliku, który chcesz wysłać narzędzia danych wyjściowych do. Jeśli plik już istnieje, narzędzie dołączyło dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

- `/Build` Przełącznika wykonuje taką samą funkcję jak **Kompiluj rozwiązanie** polecenia menu w ramach zintegrowanego środowiska programistycznego (IDE).

- Należy ująć ciągi zawierające spacje w cudzysłów.

- Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w oknie wiersza polecenia lub pliku dziennika określony za pomocą `/Out` przełącznika.

- `/Build` Przełącznika tylko kompilacje projektów, które uległy zmianie od czasu ostatniej kompilacji. Aby utworzyć wszystkie projekty w rozwiązaniu, użyj [/rebuild](../../ide/reference/rebuild-devenv-exe.md) zamiast tego.

- Jeśli otrzymasz komunikat o błędzie informujący, że **nieprawidłowa konfiguracja projektu**, upewnij się, że został określony platforma rozwiązania lub projektu platformy (na przykład `Debug|Win32`).

## <a name="example"></a>Przykład

Następujące polecenie tworzy projekt `CSharpWinApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Projekty i rozwiązania — kompilowanie i czyszczenie](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)