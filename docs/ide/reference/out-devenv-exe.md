---
title: -Out (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- errors [Visual Studio], builds
- Devenv, /out switch
- builds [Visual Studio], logs
- error logs [Visual Studio], command-line build errors
- error logs [Visual Studio]
- /out Devenv switch
- out Devenv switch
- builds [Visual Studio], errors
- output files, build errors
ms.assetid: 9002d8c2-36d4-451c-b489-8f01932f31f7
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a5778cb281ca6edcf8045620aee049b0f115a50a
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948247"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
Określa plik do przechowywania i wyświetlania błędów podczas uruchamiania, tworzenia, odbudować lub wdrożyć rozwiązanie.

## <a name="syntax"></a>Składnia

```cmd
devenv /out FileName
```

## <a name="arguments"></a>Argumenty
 `FileName`

 Wymagana. Ścieżka i nazwa pliku, aby otrzymywać komunikaty o błędach podczas kompilowania pliku wykonywalnego.

## <a name="remarks"></a>Uwagi
 Jeśli określono nazwę pliku, który nie istnieje, plik zostanie utworzony automatycznie. Jeśli plik już istnieje, wyniki są dołączane do istniejącej zawartości pliku.

 Błędy kompilacji wiersza polecenia są wyświetlane w **polecenia** okna i konstruktora rozwiązania widoku **dane wyjściowe** okna. Ta opcja jest przydatna, jeśli działają nienadzorowanej kompilacji i chcesz zobaczyć wyniki.

## <a name="example"></a>Przykład
 W tym przykładzie jest uruchamiany `MySolution` i zapisuje błędy do pliku `MyErrorLog.txt`.

```cmd
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
- [/ Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/ Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/ Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/ Wdrażanie (devenv.exe)](../../ide/reference/deploy-devenv-exe.md)