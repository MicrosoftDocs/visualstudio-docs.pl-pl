---
title: -Kompilacja (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
 `SolutionName` Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

 `SolnConfigName` Wymagane. Nazwa konfiguracji rozwiązania, która zostanie użyta do skompilowania rozwiązania o nazwie w `SolutionName` .

 /Project `ProjName` opcjonalne. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwę wyświetlaną projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalne. Nazwa konfiguracji kompilacji projektu, która ma być używana podczas kompilowania `/project` nazwanego.

## <a name="remarks"></a>Uwagi
 Ten przełącznik wykonuje tę samą funkcję co polecenie menu **rozwiązania kompilacji** w ramach zintegrowanego środowiska programistycznego (IDE).

 Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

 Informacje podsumowujące dla kompilacji, w tym błędy, można wyświetlić w oknie **polecenia** lub w dowolnym pliku dziennika określonym za pomocą `/out` przełącznika.

 To polecenie kompiluje tylko projekty, które uległy zmianie od czasu ostatniej kompilacji. Aby skompilować wszystkie projekty w rozwiązaniu, użyj [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md).

## <a name="example"></a>Przykład
 Ten przykład kompiluje projekt `CSharpConsoleApp` przy użyciu `Debug` konfiguracji kompilacji projektu w ramach `Debug` konfiguracji rozwiązania `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też
 [Kompilowanie i czyszczenie projektów i rozwiązań w programie Visual Studio](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
