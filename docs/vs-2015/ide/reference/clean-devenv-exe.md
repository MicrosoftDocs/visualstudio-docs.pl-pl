---
title: -Clean (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 043e9373f242523b7925a9ae775be6789f7cfc20
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660882"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Czyści wszystkie pliki pośredniczące i katalogi wyjściowe.

## <a name="syntax"></a>Składnia

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>Argumenty
 Wymagane `FileName`. Pełna ścieżka i nazwa pliku rozwiązania lub pliku projektu.

 /Project `ProjName` opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić ścieżkę względną z folderu `SolutionName` do pliku projektu lub nazwy wyświetlanej projektu lub pełną ścieżkę i nazwę pliku projektu.

 /projectconfig `ProjConfigName` opcjonalny. Nazwa konfiguracji kompilacji projektu, która ma być używana podczas czyszczenia `/project` o nazwie.

## <a name="remarks"></a>Uwagi
 Ten przełącznik wykonuje tę samą funkcję jak polecenie menu **Wyczyść rozwiązanie** w ramach zintegrowanego środowiska programistycznego (IDE).

 Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

 Informacje podsumowujące dla czyszczenia i kompilacji, w tym błędy, można wyświetlić w oknie **polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika `/out`.

## <a name="example"></a>Przykład
 Pierwszy przykład czyści rozwiązanie `MySolution` przy użyciu konfiguracji domyślnej określonej w pliku rozwiązania.

 Drugi przykład czyści projekt `CSharpConsoleApp` przy użyciu konfiguracji kompilacji projektu `Debug` w `Debug` konfiguracji rozwiązania `MySolution`.

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
