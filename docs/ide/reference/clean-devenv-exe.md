---
title: -Clean (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 051485646b7ff19ddae40518215c410d05fa4849
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53906894"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
Czyści wszystkie pośrednie pliki i katalogi wyjściowe.

## <a name="syntax"></a>Składnia

```
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]
```

## <a name="arguments"></a>Argumenty
 `FileName`

 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania lub pliku projektu.

 / Project `ProjName`

 Opcjonalna. Ścieżka i nazwa pliku projektu w rozwiązaniu. Możesz wprowadzić ścieżkę względną z `SolutionName` folderu pliku projektu lub nazwy wyświetlanej projektu, lub pełną ścieżkę i nazwę pliku projektu.

 / projectconfig `ProjConfigName`

 Opcjonalna. Nazwa projektu kompilacji konfiguracji, który będzie używany podczas czyszczenia `/project` o nazwie.

## <a name="remarks"></a>Uwagi
 Ta opcja wykonuje taką samą funkcję jak **czyste rozwiązanie** polecenia menu w ramach zintegrowanego środowiska programistycznego (IDE).

 Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

 Podsumowanie informacji na temat Czyści i kompilacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 Pierwszy przykład czyści `MySolution` rozwiązania przy użyciu domyślnej konfiguracji określone w pliku rozwiązania.

 Drugi przykład czyści projektu `CSharpConsoleApp`przy użyciu `Debug` konfigurację kompilacji projektu w ramach `Debug` Konfiguracja rozwiązania o `MySolution`.

```
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean

devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)