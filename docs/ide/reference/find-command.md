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
ms.openlocfilehash: 9cd4a50ebf4c27213d288cbab33647931c4a399d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55953064"
---
# <a name="find-command"></a>Find — Polecenie
Przeszukuje pliki za pomocą podzestawu opcji dostępnych w **Znajdź w plikach** karcie **Znajdź i Zamień** okna.

## <a name="syntax"></a>Składnia

```cmd
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat` Wymagane. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
 /Case lub /c atrybut opcjonalny. Dopasowuje występują tylko wtedy, gdy wielkich i małych liter dokładnie odpowiadać, określone w `findwhat` argumentu.

 / doc lub /d atrybut opcjonalny. Wyszukuje w bieżącym dokumencie. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 /markall lub /m atrybut opcjonalny. Umieszcza grafiki na każdy wiersz zawiera dopasowanie wyszukiwania w bieżącym dokumencie.

 / Open lub /o atrybut opcjonalny. Przeszukuje wszystkie otwarte dokumenty, jakby pochodziły z jednego dokumentu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 / Options lub/t atrybut opcjonalny. Wyświetla listę bieżących ustawień opcji wyszukiwania, a nie wyszukiwania.

 /proc lub /p atrybut opcjonalny. Wyszukuje bieżącą procedurę. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 / Reset lub /e atrybut opcjonalny. Zwraca opcje wyszukiwania do ustawień domyślnych, a nie wyszukiwania.

 /SEL lub /s atrybut opcjonalny. Wyszukuje w bieżącym zaznaczeniu. Określ tylko jeden zakres wyszukiwania dostępnych `/doc`, `/proc`, `/open`, lub `/sel`.

 /Up lub /u opcjonalne. Wyszukiwanie w bieżącej lokalizacji w pliku w kierunku początku pliku. Domyślnie wyszukiwanie rozpoczyna się w bieżącej lokalizacji w pliku i wyszukiwania na końcu pliku.

 /regex lub /r atrybut opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji, które reprezentują wzorców tekstu, a nie jako znaki literału. Aby uzyskać pełną listę znaki wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).

 /Wild lub/l atrybut opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji do reprezentowania znaku lub sekwencji znaków.

 opcji lub Wn atrybut opcjonalny. Wyszukiwanie tylko całe wyrazy.

## <a name="example"></a>Przykład
 W tym przykładzie przeprowadza wyszukiwanie dla słowa "somestring" w obecnie zaznaczonej sekcji kodu.

```cmd
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Zobacz też

- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)