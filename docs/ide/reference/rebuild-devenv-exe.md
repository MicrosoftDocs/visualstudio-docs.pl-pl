---
title: -Rebuild (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 782a0864c692d8c50932f41077762c994f24eeae
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53985686"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
Czyści, a następnie kompiluje konfigurację określonego rozwiązania.

## <a name="syntax"></a>Składnia

```cmd
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 `SolnConfigName`

 Wymagana. Nazwa konfiguracji rozwiązania, która będzie służyć do ponownie skompiluj rozwiązanie o nazwie w `SolutionName`.

 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 / Project `ProjName`

 Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName`

 Opcjonalna. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas odbudowywania `/project` o nazwie.

## <a name="remarks"></a>Uwagi

-   Ta opcja wykonuje taką samą funkcję jak **Kompiluj rozwiązanie** polecenia menu w ramach zintegrowanego środowiska programistycznego (IDE).

-   Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

-   Podsumowanie informacji na temat Czyści i kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie Czyści i ponownie kompiluje projekt `CSharpWinApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `Debug` Konfiguracja rozwiązania o `MySolution`.

```cmd
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)