---
title: -Project (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /project Devenv switch
- projects [Visual Studio], rebuilding
- projects [Visual Studio], building
- deployment projects, specifying
- project Devenv switch (/project)
- Devenv, /project switch
- projects [Visual Studio], cleaning
ms.assetid: 8b07859c-3439-436d-9b9a-a8ee744eee30
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3b18e4715eb711160d0adcc95c6a19e4b90bcc94
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948221"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
Umożliwia określenie jednego projektu w ramach konfiguracji określonego rozwiązania do kompilacji, czyszczenia, odbudować lub wdrożenia.

## <a name="syntax"></a>Składnia

```cmd
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 / Build

 Tworzy projekt określony przez `/project` `ProjName`.

 / clean

 Czyści wszystkie pośrednie pliki i katalogi dane wyjściowe utworzone podczas kompilacji.

 / REBUILD

 Czyści, a następnie kompiluje projekt określony przez `/project` `ProjName`.

 / deploy

 Określa, czy wdrożony po kompilacji lub skompiluj ponownie projekt.

 `SolnConfigName`

 Wymagana. Nazwa konfiguracji rozwiązania, które zostaną zastosowane do rozwiązania o nazwie w `SolutionName`.

 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 / Project `ProjName`

 Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName`

 Opcjonalna. Nazwa projektu kompilacji konfiguracji, które mają być stosowane do `/project` o nazwie.

## <a name="remarks"></a>Uwagi

-   Należy użyć wchodzi w skład `devenv /build`, /`clean`, `/rebuild`, lub `/deploy` polecenia.

-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

-   Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie tworzy projekt `CSharpConsoleApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `Debug` Konfiguracja rozwiązania o `MySolution`.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)