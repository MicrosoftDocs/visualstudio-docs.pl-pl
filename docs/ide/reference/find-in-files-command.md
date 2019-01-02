---
title: Znajdź w plikach — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9aab2251f8859cb8e6a5699ba3cd2d4828bd32a4
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53831209"
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
Wyszukiwanie plików za pomocą podzestawu opcji dostępnych w **Znajdź w plikach** karcie **Znajdź i Zamień** okna.

## <a name="syntax"></a>Składnia

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat` Wymagane. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
 /Case lub /c atrybut opcjonalny. Dopasowuje występują tylko wtedy, gdy wielkich i małych liter dokładnie odpowiadać, określone w `findwhat` argumentu.

 /ext: `extensions` Opcjonalnie. Określa rozszerzenia plików dla plików do przeszukania. Jeśli nie zostanie określony, poprzednie rozszerzenie jest używana, jeśli wcześniej zostało wprowadzone.

 /lookin: `searchpath` Opcjonalnie. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, należy ująć w znaki cudzysłowu pełną ścieżkę.

 /names lub /n atrybut opcjonalny. Wyświetla listę nazw plików, które zawierają dopasowania.

 / Options lub/t atrybut opcjonalny. Wyświetla listę bieżących ustawień opcji wyszukiwania, a nie wyszukiwania.

 /regex lub /r atrybut opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji, które reprezentują wzorców tekstu, a nie jako znaki literału. Aby uzyskać pełną listę znaki wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).

 / Reset lub /e atrybut opcjonalny. Zwraca opcje wyszukiwania do ustawień domyślnych, a nie wyszukiwania.

 / stop atrybut opcjonalny. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwania ignoruje wszystkie inne argumenty po `/stop` została określona. Na przykład można zatrzymać bieżące wyszukiwanie możesz wprowadzić następujące czynności:

```cmd
>Edit.FindinFiles /stop
```

 / Sub lub /s atrybut opcjonalny. Wyszukuje podfoldery znajdujące się w katalogu wskazanym na /lookin:`searchpath` argumentu.

 /text2 lub /2 atrybut opcjonalny. Wyświetla wyniki wyszukiwania w oknie Znajdź wyniki 2.

 /Wild lub/l atrybut opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji do reprezentowania znaku lub sekwencji znaków.

 opcji lub Wn atrybut opcjonalny. Wyszukiwanie tylko całe wyrazy.

## <a name="example"></a>Przykład
 W tym przykładzie wyszukuje btnCancel we wszystkich plikach .cls znajduje się w folderze "Moje projektów programu Visual Studio" i wyświetla informacje o dopasowania w oknie Znajdź wyniki 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Zobacz też

- [Znajdź w plikach](../../ide/find-in-files.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)