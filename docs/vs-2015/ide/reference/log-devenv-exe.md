---
title: -Log (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666844"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik jest wyświetlany po wywołaniu `devenv /log` co najmniej raz. Domyślnie plik dziennika to:

 *% AppData%* \Microsoft\VisualStudio \\*wersja*\ActivityLog.XML

 gdzie *wersja* jest wersją programu Visual Studio. Można jednak określić inną ścieżkę i nazwę pliku.

## <a name="syntax"></a>Składnia

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Uwagi
 Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.

 Dziennik jest zapisywana dla wszystkich wystąpień programu Visual Studio, które zostały wywołane za pomocą przełącznika/log. Nie rejestruje wystąpienia programu Visual Studio, który został wywołany bez przełącznika.

## <a name="see-also"></a>Zobacz też
 [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
