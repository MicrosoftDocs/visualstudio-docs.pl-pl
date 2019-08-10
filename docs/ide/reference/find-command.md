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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9e94f8aa823fc7665144f1d774339d1c41f37edc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68926244"
---
# <a name="find-command"></a>Find — Polecenie
Przeszukuje pliki za pomocą podzestawu opcji dostępnych na karcie **Znajdź w plikach** okna **Znajdź i Zamień** .

## <a name="syntax"></a>Składnia

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`Wymagane. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
/Case lub/c\
Opcjonalny. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do `findwhat` znaków określonych w argumencie.

/doc lub/d\
Opcjonalny. Przeszukuje tylko bieżący dokument. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/markall lub/m\
Opcjonalna. Umieszcza grafikę w każdym wierszu, który zawiera dopasowanie wyszukiwania w bieżącym dokumencie.

/Open lub/O\
Opcjonalna. Przeszukuje wszystkie otwarte dokumenty, tak jakby były one jednym dokumentem. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/Options lub/t\
Opcjonalna. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

/proc lub/p\
Opcjonalny. Przeszukuje tylko bieżącą procedurę. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/Reset lub/e\
Opcjonalny. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

/SEL lub/s\
Opcjonalny. Przeszukuje tylko bieżące zaznaczenie. Określ tylko jeden z dostępnych zakresów wyszukiwania `/doc`,, `/proc`, `/open`lub `/sel`.

/up lub/U\
Opcjonalny. Wyszukuje z bieżącej lokalizacji pliku w kierunku początku pliku. Domyślnie wyszukiwania zaczynają się w bieżącej lokalizacji w pliku i wyszukuje na końcu pliku.

/Regex lub/r\
Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/Wild lub/l\
Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji do reprezentowania znaku lub sekwencji znaków.

/Word lub/w\
Opcjonalny. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
W tym przykładzie jest wykonywane wyszukiwanie z uwzględnieniem wielkości liter dla słowa "someString" w aktualnie zaznaczonej sekcji kodu.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)