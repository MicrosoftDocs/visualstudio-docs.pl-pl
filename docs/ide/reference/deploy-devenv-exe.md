---
title: -Deploy (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0297058fea98568551f54d8960e62f80bb35ccd7
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948884"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
Wdraża to rozwiązanie po kompilacji lub ponownej kompilacji. Dotyczy tylko projektów kodu zarządzanego.

## <a name="syntax"></a>Składnia

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Argumenty
 `SolnConfigName`

 Wymagana. Nazwa konfiguracji rozwiązania, która będzie służyć do tworzenia rozwiązania o nazwie w `SolutionName`.

 `SolutionName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania.

 / Project `ProjName`

 Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName`

 Opcjonalna. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas tworzenia `/project` o nazwie.

## <a name="remarks"></a>Uwagi
 Określony projekt musi być projektu wdrożenia. Jeśli określony projekt nie jest projektem wdrożenia, gdy projekt, który został utworzony, jest przekazywany do wdrożenia, jego zakończy się niepowodzeniem z powodu błędu.

 Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

 Podsumowanie informacji na temat kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 W tym przykładzie wdroży projekt `CSharpConsoleApp`przy użyciu `Release` konfigurację kompilacji projektu w ramach `Release` Konfiguracja rozwiązania o `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Project (devenv.exe)](../../ide/reference/project-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)