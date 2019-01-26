---
title: -RunExit (devenv.exe)
ms.date: 12/10/2018
ms.prod: visual-studio-dev15
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3d426ec4737d2024a4dd24e74753fc216181536
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55069816"
---
# <a name="runexit-devenvexe"></a>/ RunExit (devenv.exe)

Kompiluje i uruchamia określony projekt lub rozwiązanie, a następnie zamyka zintegrowanego środowiska programistycznego (IDE).

## <a name="syntax"></a>Składnia

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Argumenty

- *SolutionName*

  Pełna ścieżka i nazwa pliku rozwiązania.

- *ProjectName*

  Pełna ścieżka i nazwa pliku projektu.

- `/Out` *OutputFilename*

  Opcjonalna. Nazwa pliku, który chcesz wysłać narzędzia danych wyjściowych do. Jeśli plik już istnieje, narzędzie dołączyło dane wyjściowe na końcu pliku.

## <a name="remarks"></a>Uwagi

Kompiluje i uruchamia określony projekt lub rozwiązanie, zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik minimalizuje IDE, podczas projektu lub rozwiązania jest uruchamiany. Zamknięcie IDE po projekt lub rozwiązanie zakończy działanie.

- Należy ująć ciągi zawierające spacje w podwójny cudzysłów.

- Podsumowanie informacji, w tym błędy, mogą być wyświetlane w **polecenia** okno lub pliku dziennika określony za pomocą `/Out` przełącznika.

## <a name="example"></a>Przykład

W tym przykładzie uruchamia rozwiązanie `MySolution` w trybie zminimalizowanym IDE przy użyciu konfiguracji aktywnego wdrożenia, a następnie zamyka IDE.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)