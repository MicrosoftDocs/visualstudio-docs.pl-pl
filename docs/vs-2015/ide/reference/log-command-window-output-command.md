---
title: Polecenie dziennika danych wyjściowych okna polecenia | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- tools.logcommandwindowoutput
helpviewer_keywords:
- log Command window output command
- View.LogCommandWindowOutput command
ms.assetid: d4ecec35-5af4-4954-8d60-2cd24583fbb4
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d9a5a29cd63f9d51f86d41d2f0f5986a77666318
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666867"
---
# <a name="log-command-window-output-command"></a>Zapisuj dane wyjściowe okna Polecenie — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Kopiuje wszystkie dane wejściowe i wyjściowe z okna **poleceń** do pliku.

## <a name="syntax"></a>Składnia

```
Tools.LogCommandWindowOutput [filename] [/on|/off] [/overwrite]
```

## <a name="arguments"></a>Argumenty
 `filename` opcjonalny. Nazwa pliku dziennika. Domyślnie plik jest tworzony w folderze profilu użytkownika. Jeśli nazwa pliku już istnieje, dziennik jest dołączany na końcu istniejącego pliku. Jeśli plik nie zostanie określony, zostanie użyty ostatni określony plik. Jeśli żaden z powyższych plików nie istnieje, zostanie utworzony domyślny plik dziennika o nazwie Cmdlines. log.

> [!TIP]
> Aby zmienić lokalizację, w której zapisano plik dziennika, wprowadź pełną ścieżkę pliku, ujętą w cudzysłów, jeśli ścieżka zawiera spacje.

## <a name="switches"></a>Przełączniki
 Opcja/on opcjonalna. Uruchamia dziennik dla okna **polecenia** w określonym pliku i dołącza plik do nowych informacji.

 /off opcjonalne. Kończy dziennik okna **poleceń** .

 zastępowania opcjonalne. Jeśli plik określony w argumencie `filename` jest zgodny z istniejącym plikiem, plik zostanie nadpisany.

## <a name="remarks"></a>Uwagi
 Jeśli plik nie zostanie określony, domyślnie tworzony jest plik Cmdlines. log. Domyślnie alias dla tego polecenia to log.

## <a name="examples"></a>Przykłady
 W tym przykładzie tworzony jest nowy plik dziennika, cmdlog i uruchamiany jest dziennik poleceń.

```
>Tools.LogCommandWindowOutput cmdlog
```

 Ten przykład powoduje zatrzymanie rejestrowania poleceń.

```
>Tools.LogCommandWindowOutput /off
```

 Ten przykład wznawia Rejestrowanie poleceń w poprzednio używanym pliku dziennika.

```
>Tools.LogCommandWindowOutput /on
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
