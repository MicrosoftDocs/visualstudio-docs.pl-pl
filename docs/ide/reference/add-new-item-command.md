---
title: Dodaj nowy element — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 38be691ae7c49ffbd6c98c9e4beb25b6ebb021b6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585694"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
Dodaje nowy element rozwiązania, taki jak .htm, css, .txt lub frameset do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Element opcjonalny. Ścieżka i nazwa pliku elementu, który ma być dodawany do rozwiązania.

## <a name="switches"></a>Przełączniki
/t:`templatename`\
Element opcjonalny. Określa typ pliku, który ma zostać utworzony. Jeśli nie podano nazwy szablonu, plik tekstowy jest tworzony domyślnie.

Składnia argumentu /t:`templatename` odzwierciedla informacje znalezione w oknie dialogowym Dodawanie nowego elementu **rozwiązania.** Należy wprowadzić pełną kategorię, po której następuje typ pliku, oddzielając nazwę kategorii`\`od typu pliku ukośnikiem odwrotnym ( ) i otaczając cały ciąg cudzysłowami.

Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić`templatename` następujące dla /t: argument.

```cmd
/t:"General\Style Sheet"
```

/e:`editorname`\
Element opcjonalny. Nazwa edytora, w którym zostanie otwarty plik. Jeśli argument jest określony, ale nie podano nazwy edytora, zostanie wyświetlone okno dialogowe **Otwórz za pomocą.**

Składnia argumentu /e:`editorname` używa nazw edytorów wyświetlanych w oknie **dialogowym Otwórz za pomocą**, ujętych w cudzysłów.

Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego,`editorname` należy wprowadzić następujące dla argumentu /e:.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
W tym przykładzie dodaje nowy element rozwiązania, MyHTMLpg, do bieżącego rozwiązania.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
