---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4b2e11cb36176aec94528019cdd19bb5fa86c92b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946807"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik pojawia się, gdy została wywołana `devenv /log` co najmniej raz. Domyślnie plik dziennika znajduje się tutaj:

**%APPDATA%\\Microsoft\\VisualStudio\\**\<Version\>**\\ActivityLog.xml**

gdzie \<wersji\> jest wersja programu Visual Studio. Można jednak określić inną ścieżkę i nazwę pliku.

## <a name="syntax"></a>Składnia

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumenty

- *NameOfLogFile*

  Wymagana. Pełna ścieżka i nazwa pliku dziennika, aby zapisać.

## <a name="remarks"></a>Uwagi

Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.

Dziennik jest zapisywany tylko w przypadku wszystkich wystąpień programu Visual Studio, które zostało otwarte z `/Log` przełącznika.

## <a name="example"></a>Przykład

W tym przykładzie kieruje rejestrowania `MyVSLog.xml` pliku w katalogu macierzystym użytkownika.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)