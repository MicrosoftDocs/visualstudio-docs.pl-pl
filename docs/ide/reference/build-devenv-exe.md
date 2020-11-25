---
title: -Build (devenv.exe)
description: Dowiedz się więcej o przełączniku wiersza polecenia devenv kompilacji i sposobach ich użycia w celu skompilowania rozwiązania lub projektu z określonym plikiem konfiguracji rozwiązania.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds, command-line
- /build Devenv switch
- Devenv, /build switch
- build Devenv switch
- command-line builds
ms.assetid: ced21627-7653-455b-8821-3e31c6a448cf
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b23a15984c4ded6ca77b1660e14c53be9fd42e3
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871434"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Kompiluje rozwiązanie lub projekt przy użyciu określonego pliku konfiguracji rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

- *SolnConfigName*

  Opcjonalny. Nazwa konfiguracji rozwiązania ( `Debug` na przykład lub `Release` ), która ma zostać użyta do skompilowania rozwiązania o nazwie w *SolutionName*. Jeśli dostępnych jest wiele platform rozwiązań, należy również określić platformę (na przykład `Debug|Win32` ). Jeśli ten argument jest nieokreślony lub jest ciągiem pustym ( `""` ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Można wprowadzić ścieżkę względną z folderu *SolutionName* do pliku projektu lub nazwę wyświetlaną projektu lub pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*ProjConfigName*

  Opcjonalny. Nazwa konfiguracji kompilacji projektu ( `Debug` na przykład lub `Release` ), która ma być używana podczas kompilowania nazwanego projektu. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32` ). Jeśli ten przełącznik jest określony, zastępuje argument *SolnConfigName* .

- `/Out`*OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

- `/Build`Przełącznik wykonuje tę samą funkcję, co polecenie menu **Kompiluj rozwiązanie** w ramach zintegrowanego środowiska programistycznego (IDE).

- Ujmij ciągi, które zawierają spacje w podwójnych cudzysłowach.

- Informacje podsumowujące dla kompilacji, w tym błędy, można wyświetlić w oknie polecenia lub w dowolnym pliku dziennika określonym za pomocą `/Out` przełącznika.

- `/Build`Przełącznik kompiluje tylko projekty, które uległy zmianie od czasu ostatniej kompilacji. Aby skompilować wszystkie projekty w rozwiązaniu, należy zamiast tego użyć [/Rebuild](../../ide/reference/rebuild-devenv-exe.md) .

- Jeśli zostanie wyświetlony komunikat o błędzie z informacją o **nieprawidłowej konfiguracji projektu**, upewnij się, że została określona platforma rozwiązania lub platforma projektu (na przykład `Debug|Win32` ).

## <a name="example"></a>Przykład

Następujące polecenie kompiluje projekt `CSharpWinApp` przy użyciu `Debug` konfiguracji kompilacji projektu w programie `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Projekty i rozwiązania — kompilowanie i czyszczenie](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
