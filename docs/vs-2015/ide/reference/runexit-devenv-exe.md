---
title: -Runexit (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6d1158a12de8b8adfe20fa6d045b756abf8d7b3c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665501"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kompiluje i uruchamia określony projekt lub rozwiązanie, a następnie zamyka zintegrowane środowisko programistyczne (IDE).

## <a name="syntax"></a>Składnia

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Argumenty
 `SolutionName` Wymagane. Pełna ścieżka i nazwa pliku rozwiązania.

 `ProjectName` Wymagane. Pełna ścieżka i nazwa pliku projektu.

## <a name="remarks"></a>Uwagi
 Kompiluje i uruchamia określony projekt lub rozwiązanie zgodnie z ustawieniami określonymi dla aktywnej konfiguracji rozwiązania. Ten przełącznik minimalizuje środowisko IDE w trakcie działania projektu lub rozwiązania i zamyka środowisko IDE po zakończeniu działania projektu lub rozwiązania.

- Ujmij ciągi, które zawierają spacje w podwójnym cudzysłowie.

- Informacje podsumowujące, w tym błędy, mogą być wyświetlane w oknie **wiersza polecenia** lub w dowolnym pliku dziennika określonym za pomocą `/out` przełącznika.

## <a name="example"></a>Przykład
 Ten przykład uruchamia rozwiązanie `MySolution` w zminimalizowanym środowisku IDE przy użyciu konfiguracji aktywnego wdrażania, a następnie zamyka IDE.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Zobacz też
 [Devenv przełączniki wiersza polecenia](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
