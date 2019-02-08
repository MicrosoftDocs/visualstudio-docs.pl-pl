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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 588c5e39f8b6b6a89de1636bd45036b21d392d33
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55930535"
---
# <a name="log-command-window-output-command"></a>Zapisuj dane wyjściowe okna Polecenie — Polecenie
Kopiuje wszystkie wejścia i wyjścia z **polecenia** okna w pliku.

## <a name="syntax"></a>Składnia

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty
 `filename`

 Opcjonalna. Nazwa pliku dziennika. Domyślnie plik jest tworzony w folderze profilu użytkownika. Jeśli nazwa pliku już istnieje, dziennik jest dołączany na końcu istniejącego pliku. Jeśli plik nie zostanie określony, ostatni określony plik jest używany. Jeśli nie poprzedni plik istnieje, utworzona jest domyślny plik dziennika o nazwie cmdline.log.

> [!TIP]
> Aby zmienić lokalizację, w której zostanie zapisany plik dziennika, należy wprowadzić pełną ścieżkę pliku ujęta w cudzysłów, jeżeli ścieżka zawiera spacje.


## <a name="switches"></a>Przełączniki
 /on

 Opcjonalna. Rozpoczyna się w dzienniku **polecenia** okna w określonym pliku i dołącza plik o nowe informacje.

 / off

 Opcjonalna. Zatrzymuje się w dzienniku **polecenia** okna.

 /overwrite

 Opcjonalna. Jeżeli plik określony w `filename` argumentów pasuje do istniejącego pliku, plik jest zastępowany.

## <a name="remarks"></a>Uwagi
 Jeśli plik nie zostanie określony, domyślnie jest tworzone cmdline.log pliku. Domyślnie alias dla tego polecenia jest dziennika.

## <a name="examples"></a>Przykłady
 W tym przykładzie tworzy nowy plik dziennika cmdlog i rozpoczyna się w dzienniku polecenia.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

 W tym przykładzie zatrzymuje rejestrowanie poleceń.

```cmd
>Tools.LogCommandWindowOutput /off
```

 W tym przykładzie wznawia rejestrowanie poleceń w pliku dziennika stosowanych wcześniej.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)