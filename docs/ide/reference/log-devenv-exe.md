---
title: -Log (devenv.exe)
description: Dowiedz się, jak za pomocą przełącznika wiersza polecenia usługi log devenv rejestrować wszystkie działania w pliku dziennika w celu rozwiązywania problemów.
ms.custom: SEO-VS-2020
ms.date: 12/12/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9dae594df60d75ced4ba6bdda5cb37c8c07a852
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040579"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik jest wyświetlany po wywołaniu `devenv /log` co najmniej raz. Domyślnie plik dziennika znajduje się tutaj:

**% AppData% \\ActivityLog.xml\\ Microsoft \\ VisualStudio** \<Version\> **\\**

gdzie \<Version\> jest wersja programu Visual Studio. Można jednak określić inną ścieżkę i nazwę pliku.

## <a name="syntax"></a>Składnia

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumenty

- *NameOfLogFile*

  Wymagane. Pełna ścieżka i nazwa pliku dziennika, w którym ma zostać zapisany plik.

## <a name="remarks"></a>Uwagi

Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.

Dziennik jest zapisywana tylko dla wszystkich wystąpień programu Visual Studio, które zostały otwarte przy użyciu `/Log` przełącznika.

## <a name="example"></a>Przykład

Ten przykład kieruje rejestrowanie do `MyVSLog.xml` pliku w katalogu macierzystym użytkownika.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
