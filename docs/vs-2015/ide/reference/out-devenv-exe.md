---
title: -Out (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
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
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 075746353440462a66133cd83ed9158470d8de5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662212"
---
# <a name="out-devenvexe"></a>/Out (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Określa plik do przechowywania i wyświetlania błędów podczas uruchamiania, kompilowania, odbudowywania lub wdrażania rozwiązania.

## <a name="syntax"></a>Składnia

```
devenv /out FileName
```

## <a name="arguments"></a>Argumenty
 Wymagane `FileName`. Ścieżka i nazwa pliku, do którego mają być wysyłane błędy podczas kompilowania pliku wykonywalnego.

## <a name="remarks"></a>Uwagi
 Jeśli określona nazwa pliku nie istnieje, plik zostanie utworzony automatycznie. Jeśli plik już istnieje, wyniki są dołączane do istniejącej zawartości pliku.

 Błędy kompilacji wiersza polecenia są wyświetlane w oknie **poleceń** i w widoku konstruktora rozwiązań okna **dane wyjściowe** . Ta opcja jest przydatna, jeśli używasz kompilacji nienadzorowanych i chcesz zobaczyć wyniki.

## <a name="example"></a>Przykład
 W tym przykładzie uruchomiono `MySolution` i zapisuje błędy w `MyErrorLog.txt` pliku.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /out "C:\MyErrorLog.txt"
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv. exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv. exe)](../../ide/reference/rebuild-devenv-exe.md) [/Deploy (devenv. exe)](../../ide/reference/deploy-devenv-exe.md)
