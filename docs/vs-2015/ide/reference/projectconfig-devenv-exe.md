---
title: -ProjectConfig (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a33c7cbaef473e75631bb4ac6c0d217198cbf250
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662086"
---
# <a name="projectconfig-devenvexe"></a>/ProjectConfig (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa konfigurację kompilacji projektu, która ma zostać zastosowana podczas kompilowania, czyszczenia, odbudowywania lub wdrażania projektu o nazwie w argumencie `/project`.

## <a name="syntax"></a>Składnia

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 /Build kompiluje projekt określony przez `/project` `ProjName`.

 /Clean czyści wszystkie pliki pośredniczące i katalogi wyjściowe utworzone podczas kompilacji.

 /Rebuild czyści, a następnie kompiluje projekt określony przez `/project` `ProjName`.

 /Deploy określa, że projekt zostanie wdrożony po kompilacji lub odbudowy.

 Wymagane `SolnConfigName`. Nazwa konfiguracji rozwiązania, która zostanie zastosowana do rozwiązania o nazwie w `SolutionName`.

 Wymagane `SolutionName`. Pełna ścieżka i nazwa pliku rozwiązania.

 /Project `ProjName` opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z folderu `SolutionName` do pliku projektu lub nazwy wyświetlanej projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalny. Nazwa konfiguracji kompilacji projektu, która ma zostać zastosowana do `/project` o nazwie.

## <a name="remarks"></a>Uwagi

- Musi być używany z przełącznikiem `/project` w ramach polecenia `devenv /build`,/`clean`, `/rebuild` lub `/deploy`.

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika `/out`.

## <a name="example"></a>Przykład
 Ten przykład kompiluje `CSharpConsoleApp` projektu przy użyciu konfiguracji kompilacji projektu `Debug` w `Debug` konfiguracji rozwiązania `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
