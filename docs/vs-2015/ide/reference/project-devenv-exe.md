---
title: -Projekt (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9c54691ed343493ef1e43798faf4d2ab6f60fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662113"
---
# <a name="project-devenvexe"></a>/Project (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Identyfikuje pojedynczy projekt w ramach określonej konfiguracji rozwiązania do kompilowania, czyszczenia, odbudowy lub wdrożenia.

## <a name="syntax"></a>Składnia

```
devenv SolutionName {/build|/clean|/rebuild|/deploy} SolnConfigName
[/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 /Build kompiluje projekt określony przez `/project` `ProjName` .

 /Clean czyści wszystkie pliki pośredniczące i katalogi wyjściowe utworzone podczas kompilacji.

 /Rebuild czyści następnie kompiluje projekt określony przez `/project` `ProjName` .

 /Deploy określa, że projekt zostanie wdrożony po kompilacji lub odbudowy.

 `SolnConfigName` Wymagane. Nazwa konfiguracji rozwiązania, która zostanie zastosowana do rozwiązania o nazwie w `SolutionName` .

 `SolutionName` Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

 /Project `ProjName` opcjonalne. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwę wyświetlaną projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalne. Nazwa konfiguracji kompilacji projektu, która ma zostać zastosowana do `/project` nazwanego.

## <a name="remarks"></a>Uwagi

- Musi być użyta część `devenv /build` polecenia,/ `clean` , `/rebuild` lub `/deploy` .

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące dla kompilacji, w tym błędy, można wyświetlić w oknie **polecenia** lub w dowolnym pliku dziennika określonym za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 Ten przykład kompiluje projekt `CSharpConsoleApp` przy użyciu `Debug` konfiguracji kompilacji projektu w ramach `Debug` konfiguracji rozwiązania `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/ProjectConfig (devenv.exe)](../../ide/reference/projectconfig-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
