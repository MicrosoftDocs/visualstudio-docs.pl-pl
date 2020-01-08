---
title: -Out (devenv.exe)
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /Out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /Out Devenv switch
- Out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cda81d37be0246c1181b4d82cbd17c3119b94437
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/01/2020
ms.locfileid: "75568014"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Określa plik do przechowywania i wyświetlania błędów podczas [uruchamiania](run-devenv-exe.md), [uruchamiania i kończenia](runexit-devenv-exe.md), [uaktualniania](upgrade-devenv-exe.md), [kompilowania](build-devenv-exe.md), [odbudowy](rebuild-devenv-exe.md), [czyszczenia](clean-devenv-exe.md)lub [wdrażania](deploy-devenv-exe.md) rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumenty

- *FileName*

  Wymagany. Ścieżka i nazwa pliku do odbierania danych wyjściowych podczas kompilowania pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

Jeśli określono nieistniejącą nazwę pliku, plik zostanie utworzony automatycznie. W przeciwnym razie plik już istnieje, a wyniki są dołączane do istniejącej zawartości pliku.

Błędy kompilacji w wierszu polecenia są wyświetlane w oknie **poleceń** i w widoku konstruktora rozwiązań okna **danych wyjściowych** . Ten przełącznik jest przydatny do wyświetlania wyników nienadzorowanych kompilacji.

## <a name="example"></a>Przykład

W tym przykładzie uruchomiono `MySolution` i zapisuje błędy w `MyErrorLog.txt`pliku.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv. exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv. exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv. exe)](upgrade-devenv-exe.md)
- [/Clean (devenv. exe)](clean-devenv-exe.md)
- [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)
