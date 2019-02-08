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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 039456c10993199ec2265042aabc0ed5c475ccd9
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954741"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Określa plik do przechowywania i wyświetlania błędów po użytkownik [Uruchom](run-devenv-exe.md), [Uruchom i Zamknij](runexit-devenv-exe.md), [uaktualnienia](upgrade-devenv-exe.md), [kompilacji](build-devenv-exe.md), [odbudować](rebuild-devenv-exe.md), [czyste](clean-devenv-exe.md), lub [wdrażanie](deploy-devenv-exe.md) rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumenty

- *FileName*

  Wymagana. Ścieżka i nazwa pliku do odbierania danych wyjściowych podczas kompilowania pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

Jeśli określono nazwy nieistniejącego pliku, plik zostanie utworzony automatycznie. W przeciwnym wypadku plik już istnieje, a wyniki są dołączane do istniejącej zawartości pliku.

Błędy kompilacji wiersza polecenia są wyświetlane w **polecenia** okna i konstruktora rozwiązania widoku **dane wyjściowe** okna. Ten przełącznik jest przydatny do wyświetlania wyników nienadzorowanej kompilacji.

## <a name="example"></a>Przykład

W tym przykładzie jest uruchamiany `MySolution` i zapisuje błędy do pliku `MyErrorLog.txt`.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/ Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/ Clean (devenv.exe)](clean-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)