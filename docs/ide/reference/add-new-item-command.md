---
title: Dodaj nowy element — Polecenie
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0568e4c03e53896b21dc725c415bda82da69f487
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54956912"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
Dodaje nowy element rozwiązania, takie jak .htm, CSS, txt lub zestaw ramek do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Opcjonalnie. Ścieżka i nazwa pliku elementu do dodania do rozwiązania.

## <a name="switches"></a>Przełączniki
 /t: `templatename` Opcjonalnie. Określa typ pliku ma zostać utworzony. Jeśli nazwa szablonu nie zostanie określony, domyślnie tworzone jest plikiem tekstowym.

 T:`templatename` składnię argumentu odzwierciedla informacji znajdujących się w **Dodaj nowy element rozwiązania** okno dialogowe. Należy wprowadzić pełną kategorii, typu pliku, oddzielając nazwy kategorii z typu pliku za ukośnik odwrotny, po którym następuje (`\`) i nawiasami cały ciąg w cudzysłowie.

 Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić następujące t:`templatename` argumentu.

```cmd
/t:"General\Style Sheet"
```

 /e: `editorname` Opcjonalnie. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument jest określony, ale nazwa edytora nie został podany, **Otwórz za pomocą** pojawi się okno dialogowe.

 / E:`editorname` składnię argumentu używa nazw edytora, w jakiej występują w **Otwórz okno dialogowe za pomocą**, ujęty w znaki cudzysłowu.

 Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
 Ten przykład dodaje nowy element rozwiązania, MyHTMLpg, do bieżącego rozwiązania.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)