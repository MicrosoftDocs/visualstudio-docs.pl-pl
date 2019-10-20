---
title: -Deploy (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /deploy switch
- deploy Devenv switch
- deploying applications [Visual Studio], after build
- /deploy Devenv switch
ms.assetid: e47c8723-df08-4645-aa2d-0c956e7ccca2
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 620be9ea458d55a8c9610079b357cc9466a03f56
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660770"
---
# <a name="deploy-devenvexe"></a>/Deploy (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wdraża rozwiązanie po kompilacji lub odbudowywaniu. Dotyczy tylko projektów kodu zarządzanego.

## <a name="syntax"></a>Składnia

```
devenv SolutionName /deploy SolnConfigName [/project ProjName] [/projectconfig ProjConfigName] [/out LogFileName]
```

## <a name="arguments"></a>Argumenty
 Wymagane `SolnConfigName`. Nazwa konfiguracji rozwiązania, która zostanie użyta do skompilowania rozwiązania o nazwie w `SolutionName`.

 Wymagane `SolutionName`. Pełna ścieżka i nazwa pliku rozwiązania.

 /Project `ProjName` opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z folderu `SolutionName` do pliku projektu lub nazwy wyświetlanej projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalny. Nazwa konfiguracji kompilacji projektu, która ma być używana podczas kompilowania `/project` o nazwie.

## <a name="remarks"></a>Uwagi
 Określony projekt musi być projektem wdrożenia. Jeśli określony projekt nie jest projektem wdrożenia, w przypadku przekazanie skompilowanego projektu do wdrożenia nie powiedzie się z powodu błędu.

 Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

 Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika `/out`.

## <a name="example"></a>Przykład
 W tym przykładzie wdrożono `CSharpConsoleApp` projektu przy użyciu konfiguracji kompilacji projektu `Release` w `Release` konfiguracji rozwiązania `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv. exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
