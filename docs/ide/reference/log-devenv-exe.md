---
title: -Log (devenv.exe)
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
ms.openlocfilehash: 008e7ca15595db249c05485f0d9e8f8b1277993e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595465"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)

Loguje wszelką aktywność do pliku dziennika w celu rozwiązywania problemów. Ten plik pojawia się `devenv /log` po wywołaniu co najmniej raz. Domyślnie plik dziennika znajduje się tutaj:

**%APPDATA%\\\\Witryna\\**aktywności w wersji\<\>**\\** programu Microsoft VisualStudio.xml

gdzie \<\> wersja jest wersją programu Visual Studio. Można jednak określić inną ścieżkę i nazwę pliku.

## <a name="syntax"></a>Składnia

```shell
devenv /Log NameOfLogFile
```

## <a name="arguments"></a>Argumenty

- *NazwaOfLogFile*

  Wymagany. Pełna ścieżka i nazwa pliku dziennika do zapisania.

## <a name="remarks"></a>Uwagi

Ten przełącznik musi być umieszczony na końcu wiersza polecenia po innych przełącznikach.

Dziennik jest napisany tylko dla wszystkich wystąpień programu Visual Studio, które zostały otwarte za pomocą przełącznika. `/Log`

## <a name="example"></a>Przykład

W tym przykładzie kieruje `MyVSLog.xml` rejestrowanie do pliku w katalogu macierzystym użytkownika.

```shell
devenv /log "%USERPROFILE%\MyVSLog.xml"
```

## <a name="see-also"></a>Zobacz też

- [Przełączniki wiersza polecenia Devenv](../../ide/reference/devenv-command-line-switches.md)
