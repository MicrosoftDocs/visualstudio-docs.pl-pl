---
title: -Run (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7468fbd6422248f2f15bf74e70cdf9c5bee849c3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593632"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Kompiluje i uruchamia określony projekt lub rozwiązanie.

## <a name="syntax"></a>Składnia

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Pełna ścieżka i nazwa pliku rozwiązania.

- *Nazwaprojektu*

  Pełna ścieżka i nazwa pliku projektu.

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Kompiluje i uruchamia określony projekt lub rozwiązanie zgodnie z ustawieniami określonymi dla konfiguracji aktywnego rozwiązania. Ten przełącznik uruchamia IDE i pozostawia go aktywny po zakończeniu uruchamiania projektu lub rozwiązania.

- Łącz ciągi, które zawierają spacje w cudzysłowie podwójnym.

- Informacje podsumowujące, w tym błędy, **Command** mogą być wyświetlane w oknie polecenia `/Out` lub w dowolnym pliku dziennika określonym za pomocą przełącznika.

## <a name="example"></a>Przykład

W tym przykładzie uruchamia rozwiązanie `MySolution` przy użyciu aktywnej konfiguracji wdrażania.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
