---
title: Replace — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replace
helpviewer_keywords:
- Edit.Replace command
- Replace command
ms.assetid: a15767f1-5a3d-44f5-8c77-7b0f1157f340
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7ba633999925e86b753dbd815babe6e52c75ca53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665628"
---
# <a name="replace-command"></a>Zastąp — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych na karcie **Zamień na pliki w** oknie **Znajdź i Zamień** .

## <a name="syntax"></a>Składnia

```
Edit.Replace findwhat replacewith [/all] [/case]
[/doc|/proc|/open|/sel] [/hidden] [/options] [/reset] [/up]
[/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty
 `findwhat` Wymagane. Tekst do dopasowania.

 `replacewith` Wymagane. Tekst, który ma zostać zastąpiony dla dopasowanego tekstu.

## <a name="switches"></a>Przełączniki
 /All lub/a Optional. Zamienia wszystkie wystąpienia szukanego tekstu na tekst zastępczy.

 /Case lub/c opcjonalne. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do znaków określonych w `findwhat` argumencie.

 /doc lub/d opcjonalne. Przeszukuje tylko bieżący dokument. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

 /Hidden lub/h opcjonalne. Wyszukuje tekst ukryty i zwinięty, taki jak metadane kontrolki czasu projektowania, ukryty region dokumentu konspektu lub zwiniętej klasy lub metody.

 /Open lub/o opcjonalne. Przeszukuje wszystkie otwarte dokumenty, tak jakby były one jednym dokumentem. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

 /Options lub/t opcjonalne. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

 /proc lub/p opcjonalne. Przeszukuje tylko bieżącą procedurę. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

 /Regex lub/r Optional. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset lub/e opcjonalne. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

 /SEL lub/s opcjonalne. Przeszukuje tylko bieżące zaznaczenie. Określ tylko jeden z dostępnych zakresów wyszukiwania, `/doc` , `/proc` , `/open` lub `/sel` .

 /up lub/u opcjonalne. Przeszukuje bieżącą lokalizację w pliku w kierunku początku pliku. Domyślnie wyszukiwania zaczynają się w bieżącej lokalizacji w pliku i są w dolnej części pliku.

 /Wild lub/l Optional. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji do reprezentowania znaku lub sekwencji znaków.

 /Word lub/w opcjonalne. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 Ten przykład zastępuje `btnSend` przy użyciu `btnSubmit` we wszystkich otwartych dokumentach.

```
>Edit.Replace btnSend btnSubmit /open
```

## <a name="see-also"></a>Zobacz też
 [Znajdowanie i zamienianie](../../ide/finding-and-replacing-text.md) [okna poleceń](../../ide/reference/command-window.md) tekstowych [przycisk Znajdź/polecenie](../../ide/find-command-box.md) polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) polecenie Visual Studio — [Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
