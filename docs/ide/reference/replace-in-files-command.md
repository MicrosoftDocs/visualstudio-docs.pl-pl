---
title: Zastąp w plikach — Polecenie
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 96f7d7ae0ea5eaf0de1a6fa4357e2750cdd8c22e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565477"
---
# <a name="replace-in-files-command"></a>Zastąp w plikach — Polecenie
Zastępuje tekst w plikach przy użyciu podzbioru opcji dostępnych na karcie **Zamień w oknie Zamień** w oknie **Znajdź i zamień.**

## <a name="syntax"></a>Składnia

```
Edit.ReplaceinFiles findwhat replacewith [/all] [/case]
[/ext:extensions] [/keep] [/lookin:searchpath] [/options] [/regex]
[/reset] [/stop] [/sub] [/text2] [/wild] [/word]
```

## <a name="arguments"></a>Argumenty
`findwhat`

Wymagany. Tekst do dopasowania.

`replacewith`

Wymagany. Tekst, który ma zastąpić dopasowany tekst.

## <a name="switches"></a>Przełączniki
/wszystko lub /a

Element opcjonalny. Zastępuje wszystkie wystąpienia wyszukiwanego tekstu tekstem zastępczym.

/case lub /c

Element opcjonalny. Dopasowania występują tylko wtedy, gdy wielkie i małe litery dokładnie `findwhat` odpowiadają tym określonym w argumie.

/ext:`extensions`

Element opcjonalny. Określa rozszerzenia plików dla przeszukiwanych plików.

/keep lub /k

Element opcjonalny. Określa, że wszystkie zmodyfikowane pliki pozostają otwarte.

/lookin:`searchpath`

Element opcjonalny. Katalog do wyszukania. Jeśli ścieżka zawiera spacje, należy ująć całą ścieżkę w cudzysłów.

/opcje lub /t

Element opcjonalny. Wyświetla listę bieżących ustawień opcji wyszukiwania i nie przeprowadza wyszukiwania.

/regex lub /r

Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argurze jako notacji, które reprezentują wzorce tekstu, a nie znaki dosłowne. Aby uzyskać pełną listę znaków wyrażeń regularnych, zobacz [Wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/reset lub /e

Element opcjonalny. Zwraca opcje wyszukiwania do ustawień domyślnych i nie wykonuje wyszukiwania.

/stop

Element opcjonalny. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Zamień ignoruje `/stop` wszystkie inne argumenty, gdy został określony. Na przykład, aby zatrzymać bieżącą wymianę, należy wprowadzić następujące czynności:

```
>Edit.ReplaceinFiles /stop
```

/sub lub /s

Element opcjonalny. Przeszukuje podfoldery w katalogu określonym w`searchpath` /lookin: argument.

/text2 lub /2

Element opcjonalny. Wyświetla wyniki wymiany w oknie **Znajdź wyniki 2.**

/wild lub /l

Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argumie jako notacji do reprezentowania znaku lub sekwencji znaków.

/słowo lub /w

Element opcjonalny. Wyszukuje tylko całe słowa.

## <a name="example"></a>Przykład
W tym `btnCancel` przykładzie wyszukuje i zastępuje go `btnReset` we wszystkich plikach cls znajdujących się w folderze "moje projekty programu visual studio" i wyświetla informacje zastępcze w oknie Znajdź wyniki **2.**

```
>Edit.ReplaceinFiles btnCancel btnReset /lookin:"c:/my visual studio projects" /ext:.cls /text2
```

## <a name="see-also"></a>Zobacz też

- [Znajdowanie i zastępowanie tekstu](../../ide/finding-and-replacing-text.md)
- [Zastąp w plikach](../../ide/replace-in-files.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
