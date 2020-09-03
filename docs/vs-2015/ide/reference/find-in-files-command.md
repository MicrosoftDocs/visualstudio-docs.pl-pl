---
title: Znajdź w plikach — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 831a67fe567c2e6ae1e288d1bc7ee91026ff2273
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651035"
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wyszukiwanie plików przy użyciu podzestawu opcji dostępnych na karcie **Znajdź w plikach** okna **Znajdowanie i zamienianie** .

## <a name="syntax"></a>Składnia

```
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat` Wymagane. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
 /Case lub/c opcjonalne. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do znaków określonych w `findwhat` argumencie.

 /EXT: `extensions` opcjonalne. Określa rozszerzenia plików, które mają być przeszukiwane. Jeśli nie zostanie określony, używane jest poprzednie rozszerzenie, jeśli zostało wcześniej wprowadzone.

 /lookin: `searchpath` opcjonalne. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, ujmij całą ścieżkę w cudzysłów.

 /Names lub/n opcjonalne. Wyświetla listę nazw plików, które zawierają dopasowania.

 /Options lub/t opcjonalne. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

 /Regex lub/r Optional. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset lub/e opcjonalne. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

 Opcja/Stop jest opcjonalna. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwanie ignoruje wszystkie inne argumenty, gdy `/stop` zostały określone. Na przykład aby zatrzymać bieżące wyszukiwanie, należy wpisać następujące polecenie:

```
>Edit.FindinFiles /stop
```

 /Sub. lub/s opcjonalne. Przeszukuje podfoldery w katalogu określonym w argumencie/lookin: `searchpath` .

 /Text2 lub/2 opcjonalne. Wyświetla wyniki wyszukiwania w oknie Znajdź wyniki 2.

 /Wild lub/l Optional. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji do reprezentowania znaku lub sekwencji znaków.

 /Word lub/w opcjonalne. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 Ten przykład wyszukuje btnCancel we wszystkich plikach. CLS znajdujących się w folderze "Moje projekty programu Visual Studio" i wyświetla informacje o dopasowaniach w oknie Znajdź wyniki 2.

```
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Zobacz też
 [Znajdź w plikach —](../../ide/find-in-files.md) [okno polecenia](../../ide/reference/command-window.md) [Znajdź/](../../ide/find-command-box.md) okno polecenia [Visual Studio polecenia](../../ide/reference/visual-studio-commands.md) programu Visual Studio — [Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
