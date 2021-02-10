---
title: Zastąp — Polecenie
description: Dowiedz się więcej na temat polecenia Replace i sposobu zamieniania tekstu w plikach za pomocą podzestawu opcji dostępnych na karcie Zamień na pliki okna Znajdź i Zamień.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6c3149b55c2b5b3a5ca666fbd780e4efbd03ef22
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958066"
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

Wymagane. Tekst do dopasowania.

`replacewith`

Wymagane. Tekst, który ma zostać zastąpiony dla dopasowanego tekstu.

## <a name="switches"></a>Przełączniki
/All lub/a

Opcjonalny. Zamienia wszystkie wystąpienia szukanego tekstu na tekst zastępczy.

/Case lub/c

Opcjonalny. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do znaków określonych w `findwhat` argumencie.

/doc lub/d

Opcjonalny. Przeszukuje tylko bieżący dokument. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

/Hidden lub/h

Opcjonalny. Wyszukuje tekst ukryty i zwinięty, taki jak metadane kontrolki czasu projektowania, ukryty region dokumentu konspektu lub zwiniętej klasy lub metody.

/Open lub/o

Opcjonalny. Przeszukuje wszystkie otwarte dokumenty, tak jakby były one jednym dokumentem. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

/Options lub/t

Opcjonalny. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

/proc lub/p

Opcjonalny. Przeszukuje tylko bieżącą procedurę. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

/Regex lub/r

Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset lub/e

Opcjonalny. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

/SEL lub/s

Opcjonalny. Przeszukuje tylko bieżące zaznaczenie. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

/up lub/u

Opcjonalny. Przeszukuje bieżącą lokalizację w pliku w kierunku początku pliku. Domyślnie wyszukiwania zaczynają się w bieżącej lokalizacji w pliku i są w dolnej części pliku.

/Wild lub/l

Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji do reprezentowania znaku lub sekwencji znaków.

/Word lub/w

Opcjonalny. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
Ten przykład zastępuje `btnSend` przy użyciu `btnSubmit` we wszystkich otwartych dokumentach.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
