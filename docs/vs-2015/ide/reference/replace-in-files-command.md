---
title: Zastąp w plikach — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 919e3ed3f372a2f6614553974f5f47cfba24e3ff
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54798535"
---
# <a name="replace-in-files-command"></a>Zastąp w plikach — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Zastępuje tekst w plikach za pomocą podzestawu opcji dostępnych w **Zamień w plikach** karcie **Znajdź i Zamień** okna.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]  
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]  
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]  
```  
  
## <a name="arguments"></a>Argumenty  
 `findwhat`  
 Wymagana. Tekst do dopasowania.  
  
 `replacewith`  
 Wymagana. Tekst do podstawienia w dopasowany tekst.  
  
## <a name="switches"></a>Przełączniki  
 / all lub /a  
 Opcjonalna. Zamienia wszystkie wystąpienia tekstu wyszukiwania tekst zastępczy.  
  
 /Case lub /c  
 Opcjonalna. Dopasowuje występują tylko wtedy, gdy po wielkich i małych liter dokładnie odpowiadać określone w `findwhat` argumentu.  
  
 /ext: `extensions`  
 Opcjonalna. Określa rozszerzenia plików dla plików do przeszukania.  
  
 /Keep lub /k  
 Opcjonalna. Określa, że wszystkie zmodyfikowane pliki są pozostawione otwarte.  
  
 /lookin: `searchpath`  
 Opcjonalna. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, należy ująć w znaki cudzysłowu pełną ścieżkę.  
  
 / Options lub/t  
 Opcjonalna. Wyświetla listę bieżących ustawień opcji wyszukiwania, a nie wyszukiwania.  
  
 /regex lub/r  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji, które reprezentują wzorców tekstu, a nie jako znaki literału. Aby uzyskać pełną listę znaki wyrażenia regularnego, zobacz [wyrażeń regularnych](../../ide/using-regular-expressions-in-visual-studio.md).  
  
 / Reset i/e  
 Opcjonalna. Zwraca opcje wyszukiwania do ustawień domyślnych, a nie wyszukiwania.  
  
 /stop  
 Opcjonalna. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Zastąp ignoruje wszystkie inne argumenty po `/stop` została określona. Na przykład aby zatrzymać zastąpienie bieżącego wprowadziłbyś następujące czynności:  
  
```  
>Edit.ReplaceinFiles /stop  
```  
  
 / Sub lub /s  
 Opcjonalna. Wyszukuje podfoldery znajdujące się w katalogu wskazanym na /lookin:`searchpath` argumentu.  
  
 /text2 lub /2  
 Opcjonalna. Wyświetla wyniki zastąpienia w **Znajdź wyniki 2** okna.  
  
 /Wild lub/l  
 Opcjonalna. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argument jako notacji do reprezentowania znaku lub sekwencji znaków.  
  
 opcji lub Wn  
 Opcjonalna. Wyszukiwanie tylko całe wyrazy.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie wyszukuje `btnCancel` i zastępuje go tekstem `btnReset` w .cls wszystkie pliki znajdujące się w folderze "Moje projekty programu visual studio" i wyświetla informacje dotyczące zastępowania w **Znajdź wyniki 2** okna.  
  
```  
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)   
 [Zastąp w plikach](../../ide/replace-in-files.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
