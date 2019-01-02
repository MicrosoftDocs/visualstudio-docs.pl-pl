---
title: Kompilacja Devenv — przełącznik
ms.date: 11/04/2016
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
ms.openlocfilehash: 9caddb066d02366cac7ee9e34f2d55c726a69896
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53824447"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Tworzy to rozwiązanie przy użyciu pliku konfiguracji określonego rozwiązania.

## <a name="syntax"></a>Składnia

```cmd
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumenty

|||
|-|-|
|*Nazwa rozwiązania*|Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.|
|*SolnConfigName*|Wymagana. Nazwa konfiguracji rozwiązania, która będzie służyć do tworzenia rozwiązania o nazwie w *SolutionName*. Jeśli dostępnych jest wiele platform rozwiązania, należy także określić platformy, na przykład **"debugowanie\|Win32"**.|
|/ project *ProjName*|Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z *SolutionName* folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.|
|/ projectconfig *ProjConfigName*|Opcjonalna. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas kompilowania projektu o nazwie. Jeśli dostępnych jest wiele platform projektów, należy także określić platformy, na przykład **"debugowanie\|Win32"**.|

## <a name="remarks"></a>Uwagi

- **/Build** przełącznika wykonuje taką samą funkcję jak **Kompiluj rozwiązanie** polecenia menu w ramach zintegrowanego środowiska programistycznego (IDE).

- Należy ująć ciągi zawierające spacje w cudzysłów.

- Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w oknie wiersza polecenia lub pliku dziennika określony za pomocą **/out** przełącznika.

- **/Build** przełącznika tylko kompilacje projektów, które uległy zmianie od czasu ostatniej kompilacji. Aby utworzyć wszystkie projekty w rozwiązaniu, użyj [/rebuild](../../ide/reference/rebuild-devenv-exe.md) zamiast tego.

- Jeśli otrzymasz komunikat o błędzie informujący, że **nieprawidłowa konfiguracja projektu**, upewnij się, że został określony platforma rozwiązania lub projektu platformy, na przykład **"debugowanie\|Win32"**.

## <a name="example"></a>Przykład

Poniższe polecenie kompiluje projekt "CSharpConsoleApp", przy użyciu konfiguracji kompilacji projektu "Debugowanie" w konfiguracji rozwiązania "Debug" "MySolution".

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Projekty i rozwiązania — kompilowanie i czyszczenie](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)