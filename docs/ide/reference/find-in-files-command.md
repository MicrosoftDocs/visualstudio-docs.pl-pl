---
title: Znajdź w plikach — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2877057f32ba6553a2cdcefbbc1bb7a8bf2884da
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919252"
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
Wyszukiwanie plików przy użyciu podzestawu opcji dostępnych na karcie **Znajdź w plikach** okna **Znajdowanie i zamienianie** .

## <a name="syntax"></a>Składnia

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty

`findwhat`\
Wymagana. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
/Case lub/c\
Opcjonalny. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do `findwhat` znaków określonych w argumencie.

EXT`extensions`\
Opcjonalna. Określa rozszerzenia plików, które mają być przeszukiwane. Jeśli nie zostanie określony, używane jest poprzednie rozszerzenie, jeśli zostało wcześniej wprowadzone.

/lookin:`searchpath`\
Opcjonalna. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, ujmij całą ścieżkę w cudzysłów.

/Names lub/n\
Opcjonalny. Wyświetla listę nazw plików, które zawierają dopasowania.

/Options lub/t\
Opcjonalny. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

/Regex lub/r\
Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset lub/e\
Opcjonalny. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

/Stop
Opcjonalna. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwanie ignoruje wszystkie inne argumenty `/stop` , gdy zostały określone. Na przykład aby zatrzymać bieżące wyszukiwanie, należy wpisać następujące polecenie:

```cmd
>Edit.FindinFiles /stop
```

/Sub. lub/s\
Opcjonalny. Przeszukuje podfoldery w katalogu określonym w argumencie/lookin`searchpath` :.

/Text2 lub/2 \
Opcjonalny. Wyświetla wyniki wyszukiwania w oknie Znajdź wyniki 2.

/Wild lub/l\
Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji do reprezentowania znaku lub sekwencji znaków.

/Word lub/w\
Opcjonalna. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
Ten przykład wyszukuje btnCancel we wszystkich plikach. CLS znajdujących się w folderze "Moje projekty programu Visual Studio" i wyświetla informacje o dopasowaniach w oknie Znajdź wyniki 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Zobacz też

- [Znajdź w plikach](../../ide/find-in-files.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)