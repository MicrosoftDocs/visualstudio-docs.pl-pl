---
title: ProjectConfig Devenv — przełącznik
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- /projectconfig Devenv switch
- configurations, rebuilding
- deployment projects, creating
- configurations, cleaning
- deployment projects, specifying
- deployment projects, adding
- build configurations, specifying
- Devenv, /projectconfig switch
- projectconfig Devenv switch (/projectconfig)
- projects [Visual Studio], build configuration
- projects [Visual Studio], cleaning
ms.assetid: 6b54ef59-ffed-4f62-a645-1279ede97ebf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7ca481d23757cc9022042db42a6d4be477880367
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53967920"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)

Określa konfigurację kompilacji projektu mają być stosowane podczas kompilacji, czyszczenia, odbudować lub wdrożyć projekt o nazwie w **/project** argumentu.

## <a name="syntax"></a>Składnia

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty

|||
|-|-|
|/ Build|Tworzy projekt określony przez **/project** argumentu.|
|/ clean|Czyści wszystkie pośrednie pliki i katalogi dane wyjściowe utworzone podczas kompilacji.|
|/ REBUILD|Czyści, a następnie kompiluje projekt określony przez **/project** argumentu.|
|/ deploy|Określa, czy wdrożony po kompilacji lub skompiluj ponownie projekt.|
|*SolnConfigName*|Wymagana. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w *SolutionName*. Jeśli dostępnych jest wiele platform rozwiązania, należy także określić platformy, na przykład **"debugowanie\|Win32"**.|
|*Nazwa rozwiązania*|Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.|
|/ project *ProjName*|Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z *SolutionName* folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.|
|/ projectconfig *ProjConfigName*|Opcjonalna. Nazwa projektu kompilacji konfiguracji, które mają być stosowane do projekt określony przez **/project** argumentu. Jeśli dostępnych jest wiele platform rozwiązania, należy także określić platformy, na przykład **"debugowanie\|Win32"**.|

## <a name="remarks"></a>Uwagi

**/Projectconfig** przełącznik musi być używany z **/project** przełącznika jako część **/build**, **/ clean**,  **/rebuild**, lub **/ deploy** polecenia.

Należy ująć ciągi zawierające spacje w cudzysłów.

Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w oknie wiersza polecenia lub pliku dziennika określony za pomocą **/out** przełącznika.

## <a name="example"></a>Przykład

Następujące polecenie tworzy projekt "CSharpConsoleApp", przy użyciu konfiguracji kompilacji projektu "Debugowanie" w konfiguracji rozwiązania "Debug" "MySolution":

```cmd
devenv "C:\Visual Studio Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)