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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 620e55938a9c96393d8cd7de6f238d3f98715d29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596687"
---
# <a name="replace-command"></a>Zastąp — Polecenie
Zastępuje tekst w plikach przy użyciu podzbioru opcji dostępnych na karcie **Zamień w oknie Zamień** w oknie **Znajdź i zamień.**

## <a name="syntax"></a>Składnia

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`

Wymagany. Tekst do dopasowania.

`replacewith`

Wymagany. Tekst, który ma zastąpić dopasowany tekst.

## <a name="switches"></a>Przełączniki
/wszystko lub /a

Element opcjonalny. Zastępuje wszystkie wystąpienia wyszukiwanego tekstu tekstem zastępczym.

/case lub /c

Element opcjonalny. Dopasowania występują tylko wtedy, gdy wielkie i małe litery dokładnie `findwhat` odpowiadają tym określonym w argumie.

/doc lub /d

Element opcjonalny. Przeszukuje tylko bieżący dokument. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/ukryte lub /h

Element opcjonalny. Wyszukuje ukryty i zwinięty tekst, taki jak metadane formantu czasu projektowania, ukryty obszar zarysowanego dokumentu lub zwiniętej klasy lub metody.

/open lub /o

Element opcjonalny. Przeszukuje wszystkie otwarte dokumenty tak, jakby były jednym dokumentem. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/opcje lub /t

Element opcjonalny. Wyświetla listę bieżących ustawień opcji wyszukiwania i nie przeprowadza wyszukiwania.

/proc lub /p

Element opcjonalny. Przeszukuje tylko bieżącą procedurę. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/regex lub /r

Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argurze jako notacji, które reprezentują wzorce tekstu, a nie znaki dosłowne. Aby uzyskać pełną listę znaków wyrażeń regularnych, zobacz [Wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/reset lub /e

Element opcjonalny. Zwraca opcje wyszukiwania do ustawień domyślnych i nie wykonuje wyszukiwania.

/sel lub /s

Element opcjonalny. Przeszukuje tylko bieżące zaznaczenie. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/up lub /u

Element opcjonalny. Wyszukuje z bieżącej lokalizacji w pliku w kierunku górnej części pliku. Domyślnie wyszukiwania rozpoczynają się w bieżącej lokalizacji w pliku i przesuwają się w kierunku dolnej części pliku.

/wild lub /l

Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argumie jako notacji do reprezentowania znaku lub sekwencji znaków.

/słowo lub /w

Element opcjonalny. Wyszukuje tylko całe słowa.

## <a name="example"></a>Przykład
W tym `btnSend` przykładzie zastępuje `btnSubmit` się we wszystkich otwartych dokumentów.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
