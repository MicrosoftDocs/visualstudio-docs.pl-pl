---
title: -Kompiluj ponownie (devenv. exe) | Microsoft Docs
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
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
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
 Wymagane `SolnConfigName`. Nazwa konfiguracji rozwiązania, która zostanie użyta w celu odbudowania rozwiązania o nazwie w `SolutionName`.

 Wymagane `SolutionName`. Pełna ścieżka i nazwa pliku rozwiązania.

 /Project `ProjName` opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z folderu `SolutionName` do pliku projektu lub nazwy wyświetlanej projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalny. Nazwa konfiguracji kompilacji projektu, która ma być używana podczas odbudowywania `/project` o nazwie.

## <a name="remarks"></a>Uwagi

- Ten przełącznik wykonuje tę samą funkcję co polecenie menu **Kompiluj rozwiązanie** w zintegrowanym środowisku programistycznym (IDE).

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące dla czyszczenia i kompilacji, w tym błędy, można wyświetlić w oknie **polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika `/out`.

## <a name="example"></a>Przykład
 Ten przykład czyści i rekonstruuje projekt `CSharpWinApp` przy użyciu konfiguracji kompilacji projektu `Debug` w `Debug` konfiguracji rozwiązania `MySolution`.

```
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
