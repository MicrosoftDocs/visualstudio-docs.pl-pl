---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18ca581c5a8a7f631138e8b3eacff02a031e0931
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593606"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Kompiluje i uruchamia określony projekt lub rozwiązanie, a następnie zamyka zintegrowane środowisko programistyczne (IDE).

## <a name="syntax"></a>Składnia

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Pełna ścieżka i nazwa pliku rozwiązania.

- *Nazwaprojektu*

  Pełna ścieżka i nazwa pliku projektu.

- `/Out`*Plik wyjściowy*

  Element opcjonalny. Nazwa pliku, do którego chcesz wysłać dane wyjściowe narzędzia. Jeśli plik już istnieje, narzędzie dołącza dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Kompiluje i uruchamia określony projekt lub rozwiązanie zgodnie z ustawieniami określonymi dla konfiguracji aktywnego rozwiązania. Ten przełącznik minimalizuje IDE podczas uruchamiania projektu lub rozwiązania. Zamyka IDE po zakończeniu uruchamiania projektu lub rozwiązania.

- Łącz ciągi, które zawierają spacje w cudzysłowie podwójnym.

- Informacje podsumowujące, w tym błędy, **Command** mogą być wyświetlane w oknie polecenia `/Out` lub w dowolnym pliku dziennika określonym za pomocą przełącznika.

## <a name="example"></a>Przykład

W tym przykładzie uruchamia rozwiązanie `MySolution` w zminimalizowanym IDE przy użyciu konfiguracji aktywnego wdrażania, a następnie zamyka IDE.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
