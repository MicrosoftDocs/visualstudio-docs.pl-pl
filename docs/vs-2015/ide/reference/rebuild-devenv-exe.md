---
title: -Kompiluj ponownie (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 008169829a6cf76e959d00f010959239a5f390b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665645"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Czyści, a następnie kompiluje określoną konfigurację rozwiązania.

## <a name="syntax"></a>Składnia

```
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]
```

## <a name="arguments"></a>Argumenty
 `SolnConfigName` Wymagane. Nazwa konfiguracji rozwiązania, która zostanie użyta w celu odbudowania rozwiązania o nazwie w `SolutionName` .

 `SolutionName` Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

 /Project `ProjName` opcjonalne. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić ścieżkę względną z `SolutionName` folderu do pliku projektu lub nazwę wyświetlaną projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalne. Nazwa konfiguracji kompilacji projektu, która ma być używana podczas odbudowywania `/project` nazwanego.

## <a name="remarks"></a>Uwagi

- Ten przełącznik wykonuje tę samą funkcję co polecenie menu **Kompiluj rozwiązanie** w zintegrowanym środowisku programistycznym (IDE).

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące dla czyszczenia i kompilacji, w tym błędy, można wyświetlić w oknie **polecenia** lub w dowolnym pliku dziennika określonym za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 Ten przykład czyści i rekonstruuje projekt `CSharpWinApp` przy użyciu `Debug` konfiguracji kompilacji projektu w ramach `Debug` konfiguracji rozwiązania `MySolution` .

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
