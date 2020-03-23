---
title: Find — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 288fb294ab712713d6be116f46ca159ea40a6e67
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595647"
---
# <a name="find-command"></a>Find — Polecenie
Wyszukuje pliki przy użyciu podzbioru opcji dostępnych na karcie **Znajdź w plikach** w oknie **Znajdź i zamień.**

## <a name="syntax"></a>Składnia

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`Wymagane. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
/case lub /c\
Element opcjonalny. Dopasowania występują tylko wtedy, gdy wielkie i małe litery `findwhat` dokładnie odpowiadają tym określonym w argumie.

/doc lub /d\
Element opcjonalny. Przeszukuje tylko bieżący dokument. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/markall lub /m\
Element opcjonalny. Umieszcza grafikę w każdym wierszu zawierającym dopasowanie wyszukiwania w bieżącym dokumencie.

/open lub /o\
Element opcjonalny. Przeszukuje wszystkie otwarte dokumenty tak, jakby były jednym dokumentem. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/options lub /t\
Element opcjonalny. Wyświetla listę bieżących ustawień opcji wyszukiwania i nie przeprowadza wyszukiwania.

/proc lub /p\
Element opcjonalny. Przeszukuje tylko bieżącą procedurę. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/reset lub /e\
Element opcjonalny. Zwraca opcje wyszukiwania do ustawień domyślnych i nie wykonuje wyszukiwania.

/sel lub /s\
Element opcjonalny. Przeszukuje tylko bieżące zaznaczenie. Określ tylko jeden z dostępnych `/doc` `/proc`zakresów wyszukiwania, , , `/open`lub `/sel`.

/up lub /u\
Element opcjonalny. Wyszukuje z bieżącej lokalizacji w pliku na początku pliku. Domyślnie wyszukiwanie rozpoczyna się w bieżącej lokalizacji w pliku i wyszukuje pod koniec pliku.

/regex lub /r\
Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argurze jako notacji, które reprezentują wzorce tekstu, a nie znaki dosłowne. Aby uzyskać pełną listę znaków wyrażeń regularnych, zobacz [Wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/wild lub /l\
Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argumie jako notacji do reprezentowania znaku lub sekwencji znaków.

/słowo lub /w\
Element opcjonalny. Wyszukuje tylko całe słowa.

## <a name="example"></a>Przykład
W tym przykładzie wykonuje wyszukiwanie z uwzględnieniem wielkości liter dla słowa "somestring" w aktualnie wybranej sekcji kodu.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Zobacz też

- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
