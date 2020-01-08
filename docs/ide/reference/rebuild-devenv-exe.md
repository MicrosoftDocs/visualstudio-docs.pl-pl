---
title: -Rebuild (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- Rebuild Devenv switch (/Rebuild)
- projects [Visual Studio], rebuilding
- /Rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76fe4bcf3441163604d93e9264ed6f78fcf0224b
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565620"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)

Czyści, a następnie kompiluje określoną konfigurację rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Rebuild [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.

- *SolnConfigName*

  Opcjonalny. Nazwa konfiguracji rozwiązania (na przykład `Debug` lub `Release`), która ma zostać użyta do odbudowania rozwiązania o nazwie w *SolutionName*. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32`). Jeśli ten argument jest nieokreślony lub pusty ciąg (`""`), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project` *ProjName*

  Opcjonalny. Ścieżka i nazwa pliku projektu w ramach rozwiązania. Możesz wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Możesz również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig` *ProjConfigName*

  Opcjonalny. Nazwa konfiguracji kompilacji projektu (na przykład `Debug` lub `Release`), która ma być używana podczas odbudowy `/Project` o nazwie. Jeśli jest dostępna więcej niż jedna platforma rozwiązania, należy również określić platformę (na przykład `Debug|Win32`). Jeśli ten przełącznik jest określony, zastępuje argument *SolnConfigName* .

- `/Out` *OutputFilename*

  Opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe do końca pliku.

## <a name="remarks"></a>Uwagi

- Ten przełącznik działa tak samo jak polecenie menu **Kompiluj rozwiązanie** w środowisku IDE.

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące dla czyszczenia i kompilowania, w tym błędy, można wyświetlić w oknie **polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika [/out](out-devenv-exe.md) .

## <a name="example"></a>Przykład

Ten przykład czyści i rekonstruuje projekt `CSharpWinApp`przy użyciu konfiguracji kompilacji projektu `Debug` w `MySolution`.

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Clean (devenv. exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)
