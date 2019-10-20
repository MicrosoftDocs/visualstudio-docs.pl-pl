---
title: -Build (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 419716d750771908a43318d051cb0b4681d35149
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660985"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kompiluje rozwiązanie przy użyciu określonego pliku konfiguracji rozwiązania.

## <a name="syntax"></a>Składnia

```
Devenv SolutionName /build SolnConfigName [/project ProjName [/projectconfig ProjConfigName]]
```

## <a name="arguments"></a>Argumenty
 Wymagane `SolutionName`. Pełna ścieżka i nazwa pliku rozwiązania.

 Wymagane `SolnConfigName`. Nazwa konfiguracji rozwiązania, która zostanie użyta do skompilowania rozwiązania o nazwie w `SolutionName`.

 /Project `ProjName` opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z folderu `SolutionName` do pliku projektu lub nazwy wyświetlanej projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalny. Nazwa konfiguracji kompilacji projektu, która ma być używana podczas kompilowania `/project` o nazwie.

## <a name="remarks"></a>Uwagi
 Ten przełącznik wykonuje tę samą funkcję co polecenie menu **rozwiązania kompilacji** w ramach zintegrowanego środowiska programistycznego (IDE).

 Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

 Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika `/out`.

 To polecenie kompiluje tylko projekty, które uległy zmianie od czasu ostatniej kompilacji. Aby skompilować wszystkie projekty w rozwiązaniu, użyj [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md).

## <a name="example"></a>Przykład
 Ten przykład kompiluje `CSharpConsoleApp` projektu przy użyciu konfiguracji kompilacji projektu `Debug` w `Debug` konfiguracji rozwiązania `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też
 [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
