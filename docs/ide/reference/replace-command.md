---
title: Zastąp — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: edcff51428451b50dc149b7b55cee11cb9ede853
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919047"
---
# <a name="replace-command"></a>Zastąp — Polecenie
Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych na karcie **Zamień na pliki w** oknie **Znajdź i Zamień** .

## <a name="syntax"></a>Składnia

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`

Wymagana. Tekst do dopasowania.

`replacewith`

Wymagana. Tekst, który ma zostać zastąpiony dla dopasowanego tekstu.

## <a name="switches"></a>Przełączniki
/All lub/a

Opcjonalny. Zamienia wszystkie wystąpienia szukanego tekstu na tekst zastępczy.

/Case lub/c

Opcjonalny. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do znaków `findwhat` określonych w argumencie.

/doc lub/d

Opcjonalna. Przeszukuje tylko bieżący dokument. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/Hidden lub/h

Opcjonalny. Wyszukuje tekst ukryty i zwinięty, taki jak metadane kontrolki czasu projektowania, ukryty region dokumentu konspektu lub zwiniętej klasy lub metody.

/Open lub/o

Opcjonalny. Przeszukuje wszystkie otwarte dokumenty, tak jakby były one jednym dokumentem. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/Options lub/t

Opcjonalny. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

/proc lub/p

Opcjonalny. Przeszukuje tylko bieżącą procedurę. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/Regex lub/r

Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset lub/e

Opcjonalna. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

/SEL lub/s

Opcjonalna. Przeszukuje tylko bieżące zaznaczenie. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/up lub/u

Opcjonalny. Przeszukuje bieżącą lokalizację w pliku w kierunku początku pliku. Domyślnie wyszukiwania zaczynają się w bieżącej lokalizacji w pliku i są w dolnej części pliku.

/Wild lub/l

Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji do reprezentowania znaku lub sekwencji znaków.

/Word lub/w

Opcjonalna. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
Ten przykład zastępuje `btnSend` przy `btnSubmit` użyciu we wszystkich otwartych dokumentach.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)