---
title: Zastąp w plikach — polecenie | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d5088366548c9f92d04f1b65a3afc378db29d6a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665616"
---
# <a name="replace-in-files-command"></a>Zastąp w plikach — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych na karcie **Zamień na pliki w** oknie **Znajdź i Zamień** .

## <a name="syntax"></a>Składnia

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argumenty
 Wymagane `findwhat`. Tekst do dopasowania.

 Wymagane `replacewith`. Tekst, który ma zostać zastąpiony dla dopasowanego tekstu.

## <a name="switches"></a>Przełączniki
 /All lub/a Optional. Zamienia wszystkie wystąpienia szukanego tekstu na tekst zastępczy.

 /Case lub/c opcjonalne. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do znaków określonych w argumencie `findwhat`.

 /EXT: `extensions` opcjonalny. Określa rozszerzenia plików, które mają być przeszukiwane.

 /Keep lub/k opcjonalne. Określa, że wszystkie zmodyfikowane pliki są otwarte.

 /lookin: `searchpath` opcjonalny. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, ujmij całą ścieżkę w cudzysłów.

 /Options lub/t opcjonalne. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

 /Regex lub/r Optional. Używa wstępnie zdefiniowanych znaków specjalnych w argumencie `findwhat` jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

 /Reset lub/e opcjonalne. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

 Opcja/Stop jest opcjonalna. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Zastąp ignoruje wszystkie inne argumenty w przypadku określenia `/stop`. Na przykład aby zatrzymać bieżącą zamianę, należy wprowadzić następujące polecenie:

```
>Edit.ReplaceinFiles /stop
```

 /Sub. lub/s opcjonalne. Przeszukuje podfoldery w katalogu określonym w argumencie/lookin: `searchpath`.

 /Text2 lub/2 opcjonalne. Wyświetla wyniki zamiany w oknie **Znajdź wyniki 2** .

 /Wild lub/l Optional. Używa wstępnie zdefiniowanych znaków specjalnych w argumencie `findwhat` jako notacji do reprezentowania znaku lub sekwencji znaków.

 /Word lub/w opcjonalne. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
 Ten przykład wyszukuje `btnCancel` i zastępuje go `btnReset` we wszystkich plikach. CLS znajdujących się w folderze "Moje projekty programu Visual Studio" i wyświetla informacje zastępcze w oknie **Znajdź wyniki 2** .

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Zobacz też
 [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md) [Zamień w plikach](../../ide/replace-in-files.md) [poleceń okno](../../ide/reference/command-window.md) [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio polecenia](../../ide/reference/visual-studio-commands.md) [](../../ide/reference/visual-studio-command-aliases.md)
