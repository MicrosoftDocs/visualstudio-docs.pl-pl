---
title: Zapisuj dane wyjściowe okna Polecenie — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2056cf335f2cf6024e6ebb4b5daff72e54dd9d50
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610431"
---
# <a name="log-command-window-output-command"></a>Zapisuj dane wyjściowe okna Polecenie — Polecenie

Kopiuje wszystkie dane wejściowe i wyjściowe z okna **poleceń** do pliku.

## <a name="syntax"></a>Składnia

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty

`filename`\
Opcjonalny. Nazwa pliku dziennika. Domyślnie plik jest tworzony w folderze profilu użytkownika. Jeśli nazwa pliku już istnieje, dziennik jest dołączany na końcu istniejącego pliku. Jeśli plik nie zostanie określony, zostanie użyty ostatni określony plik. Jeśli żaden z powyższych plików nie istnieje, zostanie utworzony domyślny plik dziennika o nazwie Cmdlines. log.

> [!TIP]
> Aby zmienić lokalizację, w której zapisano plik dziennika, wprowadź pełną ścieżkę pliku, ujętą w cudzysłów, jeśli ścieżka zawiera spacje.

## <a name="switches"></a>Przełączniki

situ
Opcjonalny. Uruchamia dziennik dla okna **polecenia** w określonym pliku i dołącza plik do nowych informacji.

/off
Opcjonalny. Kończy dziennik okna **poleceń** .

/overwrite
Opcjonalny. Jeśli plik określony w argumencie `filename` jest zgodny z istniejącym plikiem, plik zostanie nadpisany.

## <a name="remarks"></a>Uwagi

Jeśli plik nie zostanie określony, domyślnie tworzony jest plik Cmdlines. log. Domyślnie alias dla tego polecenia to log.

## <a name="examples"></a>Przykłady

W tym przykładzie tworzony jest nowy plik dziennika, cmdlog i uruchamiany jest dziennik poleceń.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

Ten przykład powoduje zatrzymanie rejestrowania poleceń.

```cmd
>Tools.LogCommandWindowOutput /off
```

Ten przykład wznawia Rejestrowanie poleceń w poprzednio używanym pliku dziennika.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [okno Polecenie](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)