---
title: -Log (devenv.exe)
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bc37f4cd7441fc7945ca1762d16300c18d9ecbfe
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610371"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik jest wyświetlany po wywołaniu `devenv /log` co najmniej raz. Domyślnie plik dziennika znajduje się tutaj:

**% AppData% \\Microsoft \\VisualStudio \\** \<Version \> **\\ActivityLog. XML**

gdzie \<Version \> jest wersją programu Visual Studio. Można jednak określić inną ścieżkę i nazwę pliku.

## <a name="syntax"></a>Składnia

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumenty

- *NameOfLogFile*

  Wymagany. Pełna ścieżka i nazwa pliku dziennika, w którym ma zostać zapisany plik.

## <a name="remarks"></a>Uwagi

Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.

Dziennik jest zapisywana tylko dla wszystkich wystąpień programu Visual Studio, które zostały otwarte przy użyciu przełącznika `/Log`.

## <a name="example"></a>Przykład

Ten przykład kieruje rejestrowanie do pliku `MyVSLog.xml` w katalogu macierzystym użytkownika.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Zobacz także

- [Przełączniki wiersza polecenia devenv](../../ide/reference/devenv-command-line-switches.md)