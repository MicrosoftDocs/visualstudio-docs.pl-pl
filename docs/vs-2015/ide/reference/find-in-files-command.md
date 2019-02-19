---
title: Znajdź w plikach — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 9cc8218bafd4a6a0a6ce5622b9aff0e28dda8673
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54753322"
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Wyszukiwanie plików za pomocą podzestawu opcji dostępnych w **Znajdź w plikach** karcie **Znajdź i Zamień** okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.FindinFiles findwhat [/case] [/ext:extensions]  
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]  
[/text2] [/wild|/regex] [/word]  
```  
  
## <a name="arguments"></a>Argumenty  
 `findwhat`  
 Wymagana. Tekst do dopasowania.  
  
## <a name="switches"></a>Przełączniki  
 /Case lub /c  
 Opcjonalna. Dopasowuje występują tylko wtedy, gdy wielkich i małych liter dokładnie odpowiadać, określone w `findwhat` argumentu.  
  
 /ext: `extensions`  
 Opcjonalna. Określa rozszerzenia plików dla plików do przeszukania. Jeśli nie zostanie określony, poprzednie rozszerzenie jest używana, jeśli wcześniej zostało wprowadzone.  
  
 /lookin: `searchpath`  
 Opcjonalna. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, należy ująć w znaki cudzysłowu pełną ścieżkę.  
  
 /names lub /n  
 Opcjonalna. Wyświetla listę nazw plików, które zawierają dopasowania.  
  
 / Options lub/t  
 Opcjonalna. Wyświetla listę bieżących ustawień opcji wyszukiwania, a nie wyszukiwania.  
  
 /regex lub/r  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji, które reprezentują wzorców tekstu, a nie jako znaki literału. Aby uzyskać pełną listę znaki wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 / Reset i/e  
 Opcjonalna. Zwraca opcje wyszukiwania do ustawień domyślnych, a nie wyszukiwania.  
  
 /stop  
 Opcjonalna. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwania ignoruje wszystkie inne argumenty po `/stop` została określona. Na przykład można zatrzymać bieżące wyszukiwanie możesz wprowadzić następujące czynności:  
  
```  
>Edit.FindinFiles /stop  
```  
  
 / Sub lub /s  
 Opcjonalna. Wyszukuje podfoldery znajdujące się w katalogu wskazanym na /lookin:`searchpath` argumentu.  
  
 /text2 lub /2  
 Opcjonalna. Wyświetla wyniki wyszukiwania w oknie Znajdź wyniki 2.  
  
 /Wild lub/l  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji do reprezentowania znaku lub sekwencji znaków.  
  
 opcji lub Wn  
 Opcjonalna. Wyszukiwanie tylko całe wyrazy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje btnCancel we wszystkich plikach .cls znajduje się w folderze "Moje projektów programu Visual Studio" i wyświetla informacje o dopasowania w oknie Znajdź wyniki 2.  
  
```  
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdź w plikach](../../ide/find-in-files.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
