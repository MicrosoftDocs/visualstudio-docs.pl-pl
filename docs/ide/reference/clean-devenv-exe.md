---
title: -Clean (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia Clean devenv wyczyścić wszystkie pliki pośredniczące i katalogi wyjściowe.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- builds [Team System], cleaning files
- Clean Devenv switch
- /Clean Devenv switch
- Devenv, /Clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d4c3fdc30737a2266241e19ae40f840a41784cc1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99963292"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Czyści wszystkie pliki pośredniczące i katalogi wyjściowe.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

- *Config*

  Opcjonalny. Konfiguracja (na przykład `Debug` lub `Release` ) do czyszczenia plików pośrednich dla rozwiązania o nazwie w *SolutionName*. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32` ). Jeśli ten argument jest nieokreślony lub jest ciągiem pustym ( `""` ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Możesz również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*ProjConfigName*

  Opcjonalny. Nazwa konfiguracji kompilacji projektu ( `Debug` na przykład lub), `Release` która ma być używana podczas czyszczenia `/Project` nazwy. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32` ). Jeśli ten przełącznik jest określony, zastępuje argument *konfiguracji* .

- `/Out`*OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

Ten przełącznik ma taką samą funkcję jak polecenie menu **Wyczyść rozwiązanie** w środowisku IDE.

Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

Informacje podsumowujące podczas czyszczenia i kompilowania, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika [/out](out-devenv-exe.md) .

Jeśli `/Project` przełącznik nie zostanie określony, Akcja czyszczenia jest wykonywana we wszystkich projektach w rozwiązaniu, nawet jeśli *Nazwa* pliku została określona jako plik projektu.

## <a name="example"></a>Przykład

Pierwszy przykład czyści `MySolution` rozwiązanie przy użyciu domyślnej konfiguracji określonej w pliku rozwiązania.

Drugi przykład czyści projekt `CSharpWinApp` przy użyciu `Debug` konfiguracji kompilacji projektu w programie `MySolution` .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
