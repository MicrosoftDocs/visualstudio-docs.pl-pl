---
title: -Out (devenv.exe)
description: Dowiedz się, w jaki sposób używać przełącznika wiersza polecenia devenv out, aby określić plik do przechowywania i wyświetlania błędów podczas uruchamiania, uruchamiania i kończenia, uaktualniania, kompilowania, ponownego kompilowania, czyszczenia lub wdrażania rozwiązania.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: db5a67031d48c55a4bd9c668335360897bcca62b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99932192"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)

Określa plik do przechowywania i wyświetlania błędów podczas [uruchamiania](run-devenv-exe.md), [uruchamiania i kończenia](runexit-devenv-exe.md), [uaktualniania](upgrade-devenv-exe.md), [kompilowania](build-devenv-exe.md), [odbudowy](rebuild-devenv-exe.md), [czyszczenia](clean-devenv-exe.md)lub [wdrażania](deploy-devenv-exe.md) rozwiązania.

## <a name="syntax"></a>Składnia

```shell
devenv /Out FileName
```

## <a name="arguments"></a>Argumenty

- *Nazwa pliku*

  Wymagane. Ścieżka i nazwa pliku do odbierania danych wyjściowych podczas kompilowania pliku wykonywalnego.

## <a name="remarks"></a>Uwagi

Jeśli określono nieistniejącą nazwę pliku, plik zostanie utworzony automatycznie. W przeciwnym razie plik już istnieje, a wyniki są dołączane do istniejącej zawartości pliku.

Błędy kompilacji w wierszu polecenia są wyświetlane w oknie **poleceń** i w widoku konstruktora rozwiązań okna **danych wyjściowych** . Ten przełącznik jest przydatny do wyświetlania wyników nienadzorowanych kompilacji.

## <a name="example"></a>Przykład

Ten przykład uruchamia `MySolution` i zapisuje błędy w pliku `MyErrorLog.txt` .

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
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Deploy (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)
