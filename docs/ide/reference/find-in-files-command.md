---
title: Znajdź w plikach — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- edit.findinfiles
helpviewer_keywords:
- Edit.FindInFiles command
- find in files command
ms.assetid: 2fc78bfe-b339-4599-97f9-4cafd8a194d9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 87d313c29be1d5fb4f1be1febe9b5b7cd32e7e11
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75569585"
---
# <a name="find-in-files-command"></a>Znajdź w plikach — Polecenie
Wyszukiwanie plików przy użyciu podzbioru opcji dostępnych na karcie **Znajdź w plikach** w oknie **Znajdź i zamień.**

## <a name="syntax"></a>Składnia

```cmd
Edit.FindinFiles findwhat [/case] [/ext:extensions]
[/lookin:searchpath] [/names] [/options] [/reset] [/stop] [/sub]
[/text2] [/wild|/regex] [/word]
```

## <a name="arguments"></a>Argumenty

`findwhat`\
Wymagany. Tekst do dopasowania.

## <a name="switches"></a>Przełączniki
/case lub /c\
Element opcjonalny. Dopasowania występują tylko wtedy, gdy wielkie i małe litery `findwhat` dokładnie odpowiadają tym określonym w argumie.

/ext:`extensions`\
Element opcjonalny. Określa rozszerzenia plików dla przeszukiwanych plików. Jeśli nie zostanie określony, poprzednie rozszerzenie jest używane, jeśli zostało wcześniej wprowadzone.

/lookin:`searchpath`\
Element opcjonalny. Katalog do wyszukania. Jeśli ścieżka zawiera spacje, należy ująć całą ścieżkę w cudzysłów.

/nazwy lub /n\
Element opcjonalny. Wyświetla listę nazw plików zawierających dopasowania.

/options lub /t\
Element opcjonalny. Wyświetla listę bieżących ustawień opcji wyszukiwania i nie przeprowadza wyszukiwania.

/regex lub /r\
Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argurze jako notacji, które reprezentują wzorce tekstu, a nie znaki dosłowne. Aby uzyskać pełną listę znaków wyrażeń regularnych, zobacz [Wyrażenia regularne](../../ide/using-regular-expressions-in-visual-studio.md).

/reset lub /e\
Element opcjonalny. Zwraca opcje wyszukiwania do ustawień domyślnych i nie wykonuje wyszukiwania.

/stop\
Element opcjonalny. Zatrzymuje bieżącą operację wyszukiwania, jeśli jest w toku. Wyszukiwanie ignoruje wszystkie `/stop` inne argumenty, gdy został określony. Na przykład, aby zatrzymać bieżące wyszukiwanie, należy wprowadzić następujące czynności:

```cmd
>Edit.FindinFiles /stop
```

/sub lub /s\
Element opcjonalny. Przeszukuje podfoldery w katalogu określonym w`searchpath` /lookin: argument.

/text2 lub /2\
Element opcjonalny. Wyświetla wyniki wyszukiwania w oknie Znajdź wyniki 2.

/wild lub /l\
Element opcjonalny. Używa wstępnie zdefiniowanych znaków `findwhat` specjalnych w argumie jako notacji do reprezentowania znaku lub sekwencji znaków.

/słowo lub /w\
Element opcjonalny. Wyszukuje tylko całe słowa.

## <a name="example"></a>Przykład
W tym przykładzie wyszukuje btnCancel we wszystkich plikach cls znajdujących się w folderze "Moje projekty programu Visual Studio" i wyświetla informacje o dopasowaniu w oknie Znajdź wyniki 2.

```cmd
>Edit.FindinFiles btnCancel /lookin:"c:/My Visual Studio Projects" /ext:*.cls /text2
```

## <a name="see-also"></a>Zobacz też

- [Znajdź w plikach](../../ide/find-in-files.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
