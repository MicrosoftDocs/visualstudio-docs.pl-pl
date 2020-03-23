---
title: -Build (devenv.exe)
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
ms.openlocfilehash: 1766fe22573554b41ebfaa38fbd9e8d6c90c5790
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595764"
---
# <a name="build-devenvexe"></a>/Build (devenv.exe)

Tworzy rozwiązanie lub projekt przy użyciu pliku konfiguracji określonego rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv SolutionName /Build [SolnConfigName [/Project ProjName [/ProjectConfig ProjConfigName]] [/Out OutputFilename]]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Wymagany. Pełna ścieżka i nazwa pliku rozwiązania.

- *Nazwa SolnConfigName*

  Element opcjonalny. Nazwa konfiguracji rozwiązania (na `Debug` przykład `Release`lub ) do utworzenia rozwiązania o nazwie w *SolutionName*. Jeśli dostępnych jest wiele platform rozwiązań, należy również `Debug|Win32`określić platformę (na przykład ). Jeśli ten argument jest nieokreślony lub`""`pusty ciąg ( ), narzędzie używa aktywnej konfiguracji rozwiązania.

- `/Project`*Nazwa proj*

  Element opcjonalny. Ścieżka i nazwa pliku projektu w rozwiązaniu. Ścieżkę względną można wprowadzić z folderu *SolutionName* do pliku projektu, nazwy wyświetlanej projektu lub pełnej ścieżki i nazwy pliku projektu.

- `/ProjectConfig`*Nazwa ProjConfigName*

  Element opcjonalny. Nazwa konfiguracji kompilacji projektu (na przykład `Debug` lub `Release`) do użycia podczas tworzenia nazwanego projektu. Jeśli dostępna jest więcej niż jedna platforma rozwiązania, należy `Debug|Win32`również określić platformę (na przykład). Jeśli ten przełącznik jest określony, zastępuje *SolnConfigName* argument.

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

- Przełącznik `/Build` wykonuje tę samą funkcję co polecenie menu **Rozwiązanie kompilacji** w zintegrowanym środowisku programistycznym (IDE).

- Łącz ciągi, które zawierają spacje w cudzysłowach.

- Informacje podsumowujące dla kompilacji, w tym błędy, mogą być wyświetlane w oknie `/Out` polecenia lub w dowolnym pliku dziennika określonym za pomocą przełącznika.

- Przełącznik `/Build` tworzy tylko projekty, które uległy zmianie od czasu ostatniej kompilacji. Aby utworzyć wszystkie projekty w rozwiązaniu, należy użyć [/rebuild](../../ide/reference/rebuild-devenv-exe.md) zamiast.

- Jeśli zostanie wyświetlony komunikat o błędzie z informacją **Nieprawidłowa konfiguracja projektu,** upewnij się, `Debug|Win32`że określono platformę rozwiązania lub platformę projektu (na przykład).

## <a name="example"></a>Przykład

Następujące polecenie tworzy projekt, `CSharpWinApp`przy `Debug` użyciu konfiguracji `MySolution`kompilacji projektu w ramach .

```shell
devenv "%USERPROFILE%\source\repos\MySolution.sln" /build Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug
```

## <a name="see-also"></a>Zobacz też

- [Projekty i rozwiązania — kompilowanie i czyszczenie](../../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
