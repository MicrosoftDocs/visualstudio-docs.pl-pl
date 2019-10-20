---
title: Find — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.find
helpviewer_keywords:
- Find command
- Edit.Find command
ms.assetid: f0c705dc-2b97-423d-abbf-5584d4827208
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6ce0e4a3aaca752cbdeda0a83e469977306c3404
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657681"
---
# <a name="find-command"></a>Find — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przeszukuje pliki za pomocą podzestawu opcji dostępnych na karcie **Znajdź w plikach** okna **Znajdź i Zamień** .

## <a name="syntax"></a>Składnia

```
Edit.Find findwhat [/case] [/doc | /proc | /open | /sel]
[/markall] [/options] [/reset] [/up] [/wild | /regex] [/word]
```

## <a name="arguments"></a>Argumenty
 Wymagane `findwhat`. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
 /Case lub/c opcjonalne. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do znaków określonych w argumencie `findwhat`.

 /doc lub/d opcjonalne. Przeszukuje tylko bieżący dokument. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc`, `/proc`, `/open` lub `/sel`.

 /markall lub/m opcjonalne. Umieszcza grafikę w każdym wierszu, który zawiera dopasowanie wyszukiwania w bieżącym dokumencie.

 /Open lub/o opcjonalne. Przeszukuje wszystkie otwarte dokumenty, tak jakby były one jednym dokumentem. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc`, `/proc`, `/open` lub `/sel`.

 /Options lub/t opcjonalne. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

 /proc lub/p opcjonalne. Przeszukuje tylko bieżącą procedurę. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc`, `/proc`, `/open` lub `/sel`.

 /Reset lub/e opcjonalne. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

 /SEL lub/s opcjonalne. Przeszukuje tylko bieżące zaznaczenie. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc`, `/proc`, `/open` lub `/sel`.

 /up lub/u opcjonalne. Wyszukuje z bieżącej lokalizacji pliku w kierunku początku pliku. Domyślnie wyszukiwania zaczynają się w bieżącej lokalizacji w pliku i wyszukuje na końcu pliku.

 /Regex lub/r Optional. Używa wstępnie zdefiniowanych znaków specjalnych w argumencie `findwhat` jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

 /Wild lub/l Optional. Używa wstępnie zdefiniowanych znaków specjalnych w argumencie `findwhat` jako notacji do reprezentowania znaku lub sekwencji znaków.

 /Word lub/w opcjonalne. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 W tym przykładzie jest wykonywane wyszukiwanie z uwzględnieniem wielkości liter dla słowa "someString" w aktualnie zaznaczonej sekcji kodu.

```
>Edit.Find somestring /sel /case
```

## <a name="see-also"></a>Zobacz też
 [Okno polecenia](../../ide/reference/command-window.md) [Znajdź/polecenie](../../ide/find-command-box.md) polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) — [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
