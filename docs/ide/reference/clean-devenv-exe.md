---
title: -Clean (devenv.exe)
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ac184f25d79a47814fee52b99bce1cddce247fc5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570469"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)

Czyści wszystkie pliki pośrednie i katalogi wyjściowe.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Clean [Config [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.

- *Config*

  Element opcjonalny. Konfiguracja (na `Debug` `Release`przykład lub ) do czyszczenia plików pośredniczących dla rozwiązania o nazwie w *SolutionName*. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład). Jeśli ten argument jest nieokreślony lub`""`pusty ciąg ( ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project`*Nazwa proj*

  Element opcjonalny. Ścieżka i nazwa pliku projektu w rozwiązaniu. Można wprowadzić nazwę wyświetlaną projektu lub ścieżkę względną z folderu *SolutionName* do pliku projektu. Można również wprowadzić pełną ścieżkę i nazwę pliku projektu.

- `/ProjectConfig`*Nazwa ProjConfigName*

  Element opcjonalny. Nazwa konfiguracji kompilacji projektu (na przykład `Debug` lub `Release`) `/Project` do użycia podczas czyszczenia nazwanego. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład). Jeśli ten przełącznik jest określony, zastępuje *config* argumentu.

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Ten przełącznik wykonuje tę samą funkcję co polecenie menu **Czyste rozwiązanie** w środowisku IDE.

Łącz ciągi, które zawierają spacje w cudzysłowie podwójnym.

Informacje podsumowujące podczas czyszczenia i tworzenia, w tym błędy, mogą być wyświetlane w oknie **Polecenia** lub w dowolnym pliku dziennika określonym za pomocą przełącznika [/Out.](out-devenv-exe.md)

Jeśli `/Project` przełącznik nie jest określony, akcja czyszczenia jest wykonywana na wszystkich projektach w rozwiązaniu, nawet jeśli *FileName* został określony jako plik projektu.

## <a name="example"></a>Przykład

Pierwszy przykład czyści `MySolution` rozwiązanie przy użyciu domyślnej konfiguracji określonej w pliku rozwiązania.

Drugi przykład czyści `CSharpWinApp`projekt, `Debug` przy użyciu `MySolution`konfiguracji kompilacji projektu w ramach .

```shell
devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean

devenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /Clean "Debug" /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
