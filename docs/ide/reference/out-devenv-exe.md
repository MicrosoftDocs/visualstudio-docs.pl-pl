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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568014"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Określa plik do przechowywania i wyświetlania błędów podczas [uruchamiania](run-devenv-exe.md), [uruchamiania i zamykania](runexit-devenv-exe.md), [uaktualniania,](upgrade-devenv-exe.md) [budowania,](build-devenv-exe.md) [przebudowy,](rebuild-devenv-exe.md) [czyszczenia](clean-devenv-exe.md)lub [wdrażania](deploy-devenv-exe.md) rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumenty

- *Pod nazwą*

  Wymagany. Ścieżka i nazwa pliku do odbierania danych wyjściowych podczas tworzenia pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

Jeśli określono nieistniejącą nazwę pliku, plik jest tworzony automatycznie. W przeciwnym razie plik już istnieje, a wyniki są dołączane do istniejącej zawartości pliku.

Błędy kompilacji wiersza polecenia są wyświetlane w oknie **Polecenia** i w widoku Konstruktora rozwiązań w oknie **Dane wyjściowe.** Ten przełącznik jest przydatny do wyświetlania wyników kompilacji nienadzorowanych.

## <a name="example"></a>Przykład

W tym `MySolution` przykładzie uruchamia się `MyErrorLog.txt`i zapisuje błędy w pliku .

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/RunExit (devenv.exe)](runexit-devenv-exe.md)
- [/Upgrade (devenv.exe)](upgrade-devenv-exe.md)
- [/Clean (devenv.exe)](clean-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Odbuduj (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
