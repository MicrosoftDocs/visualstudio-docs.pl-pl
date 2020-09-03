---
title: -Deploy (devenv.exe) | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
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
 `SolnConfigName` Wymagane. Nazwa konfiguracji rozwiązania, która zostanie użyta do skompilowania rozwiązania o nazwie w `SolutionName` .

 `SolutionName` Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

 /Project `ProjName` opcjonalne. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwę wyświetlaną projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalne. Nazwa konfiguracji kompilacji projektu, która ma być używana podczas kompilowania `/project` nazwanego.

## <a name="remarks"></a>Uwagi
 Określony projekt musi być projektem wdrożenia. Jeśli określony projekt nie jest projektem wdrożenia, w przypadku przekazanie skompilowanego projektu do wdrożenia nie powiedzie się z powodu błędu.

 Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

 Informacje podsumowujące dla kompilacji, w tym błędy, można wyświetlić w oknie **polecenia** lub w dowolnym pliku dziennika określonym za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 Ten przykład wdraża projekt `CSharpConsoleApp` przy użyciu `Release` konfiguracji kompilacji projektu w ramach `Release` konfiguracji rozwiązania `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /deploy Release /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Release
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Project (devenv.exe)](../../ide/reference/project-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
