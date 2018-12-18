---
title: -Log (devenv.exe)
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fb33eedf322009cfd5602c481bce36beb4126a9b
ms.sourcegitcommit: 54c65f81a138fc1e8ff1826f7bd9dcec710618cc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/19/2018
ms.locfileid: "51948403"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik pojawia się, gdy została wywołana `devenv /log` co najmniej raz. Domyślnie plik dziennika to:

 *% APPDATA %* \Microsoft\VisualStudio\\*wersji*\ActivityLog.XML

 gdzie *wersji* jest wersja programu Visual Studio. Można jednak określić inną ścieżkę i nazwę pliku.

## <a name="syntax"></a>Składnia

```cmd
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Uwagi
 Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.

 Dziennik jest zapisywany dla wszystkich wystąpień programu Visual Studio, która została wywołana z przełącznikiem/log. Go nie logowania wystąpienia programu Visual Studio, który został wywołany bez przełącznika.

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)