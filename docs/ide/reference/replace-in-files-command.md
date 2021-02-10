---
title: Zastąp w plikach — Polecenie
description: Dowiedz się więcej na temat polecenia Zamień w plikach i sposobu zamieniania tekstu w plikach przy użyciu niektórych opcji dostępnych na karcie Zamień na pliki okna Znajdź i Zamień.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.replaceinfiles
helpviewer_keywords:
- Edit.ReplaceInFiles command
- Replace In Files command
- ReplaceInFiles command
ms.assetid: f116066a-4f65-4f2c-94ef-12cbd8cfb598
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 32980161281cf36c54ad15d536870a96694a461a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99958014"
---
# <a name="replace-in-files-command"></a>Zastąp w plikach — Polecenie
Zamienia tekst w plikach za pomocą podzestawu opcji dostępnych na karcie **Zamień na pliki w** oknie **Znajdź i Zamień** .

## <a name="syntax"></a>Składnia

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`

Wymagane. Tekst do dopasowania.

`replacewith`

Wymagane. Tekst, który ma zostać zastąpiony dla dopasowanego tekstu.

## <a name="switches"></a>Przełączniki
/All lub/a

Opcjonalny. Zamienia wszystkie wystąpienia szukanego tekstu na tekst zastępczy.

/Case lub/c

Opcjonalny. Dopasowań występuje tylko wtedy, gdy wielkie i małe litery dokładnie pasują do znaków określonych w `findwhat` argumencie.

EXT `extensions`

Opcjonalny. Określa rozszerzenia plików, które mają być przeszukiwane.

/Keep lub/k

Opcjonalny. Określa, że wszystkie zmodyfikowane pliki są otwarte.

/lookin: `searchpath`

Opcjonalny. Katalog do przeszukania. Jeśli ścieżka zawiera spacje, ujmij całą ścieżkę w cudzysłów.

/Options lub/t

Opcjonalny. Wyświetla listę bieżących ustawień opcji Znajdź i nie wykonuje wyszukiwania.

/Regex lub/r

Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji, które reprezentują wzorce tekstu, a nie znaki literału. Aby uzyskać pełną listę znaków wyrażenia regularnego, zobacz [wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/Reset lub/e

Opcjonalny. Zwraca ustawienia domyślne opcji Znajdź i nie wykonuje wyszukiwania.

/Stop

Opcjonalny. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Zastąp ignoruje wszystkie inne argumenty, gdy `/stop` zostały określone. Na przykład aby zatrzymać bieżącą zamianę, należy wprowadzić następujące polecenie:

```
>Edit.ReplaceinFiles /stop
```

/Sub. lub/s

Opcjonalny. Przeszukuje podfoldery w katalogu określonym w argumencie/lookin: `searchpath` .

/Text2 lub/2

Opcjonalny. Wyświetla wyniki zamiany w oknie **Znajdź wyniki 2** .

/Wild lub/l

Opcjonalny. Używa wstępnie zdefiniowanych znaków specjalnych w `findwhat` argumencie jako notacji do reprezentowania znaku lub sekwencji znaków.

/Word lub/w

Opcjonalny. Wyszukuje tylko całe wyrazy.

## <a name="example"></a>Przykład
Ten przykład wyszukuje `btnCancel` i zastępuje je `btnReset` we wszystkich plikach. CLS znajdujących się w folderze "Moje projekty programu Visual Studio" i wyświetla informacje zastępcze w oknie **Znajdź wyniki 2** .

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
- [Zastąp w plikach](../../ide/replace-in-files.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
