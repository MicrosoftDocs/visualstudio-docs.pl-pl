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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b6ba8fb419726018bd089e217386ab5dbd6a9c33
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568662"
---
# <a name="log-command-window-output-command"></a>Zapisuj dane wyjściowe okna Polecenie — Polecenie

Kopiuje wszystkie dane wejściowe i wyjściowe z okna **Polecenia** do pliku.

## <a name="syntax"></a>Składnia

```cmd
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty

`filename`\
Element opcjonalny. Nazwa pliku dziennika. Domyślnie plik jest tworzony w folderze profilu użytkownika. Jeśli nazwa pliku już istnieje, dziennik jest dołączany na końcu istniejącego pliku. Jeśli nie określono żadnego pliku, używany jest ostatni określony plik. Jeśli nie istnieje żaden poprzedni plik, tworzony jest domyślny plik dziennika o nazwie cmdline.log.

> [!TIP]
> Aby zmienić lokalizację, w której zapisywany jest plik dziennika, wprowadź pełną ścieżkę pliku otoczoną cudzysłowami, jeśli ścieżka zawiera spacje.

## <a name="switches"></a>Przełączniki

/on\
Element opcjonalny. Uruchamia dziennik okna **polecenia** w określonym pliku i dołącza plik z nowymi informacjami.

/off\
Element opcjonalny. Zatrzymuje dziennik okna **polecenia.**

/overwrite\
Element opcjonalny. Jeśli plik określony `filename` w argumie jest zgodny z istniejącym plikiem, plik zostanie zastąpiony.

## <a name="remarks"></a>Uwagi

Jeśli nie określono żadnego pliku, plik cmdline.log jest tworzony domyślnie. Domyślnie aliasem tego polecenia jest Log.

## <a name="examples"></a>Przykłady

W tym przykładzie tworzy nowy plik dziennika, cmdlog i uruchamia dziennik poleceń.

```cmd
>Tools.LogCommandWindowOutput cmdlog
```

W tym przykładzie zatrzymuje rejestrowanie poleceń.

```cmd
>Tools.LogCommandWindowOutput /off
```

W tym przykładzie wznawia rejestrowanie poleceń w wcześniej używanym pliku dziennika.

```cmd
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Zobacz też

- [Polecenia programu Visual Studio](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenie](../../ide/find-command-box.md)
- [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
