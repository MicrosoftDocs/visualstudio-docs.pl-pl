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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c08ae19ee6e1238d412e2df2f3a4ebe544bca851
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658791"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
Dodaje nowy element rozwiązania, taki jak. htm, CSS, txt lub FRAMESET do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Opcjonalny. Ścieżka i nazwa pliku elementu, który ma zostać dodany do rozwiązania.

## <a name="switches"></a>Przełączniki
/t: `templatename` \
Opcjonalny. Określa typ pliku, który ma zostać utworzony. Jeśli nie podano nazwy szablonu, plik tekstowy jest tworzony domyślnie.

Składnia argumentów/t: `templatename` odzwierciedla informacje znajdujące się w oknie dialogowym **Dodaj nowy element rozwiązania** . Należy wprowadzić kompletną kategorię, a następnie typ pliku, oddzielając nazwę kategorii od typu pliku przez ukośnik odwrotny (`\`) i otaczając cały ciąg w cudzysłowie.

Na przykład, aby utworzyć nowy plik tekstowy, dla argumentu/t: `templatename` wprowadź następujące polecenie.

```cmd
/t:"General\Style Sheet"
```

/e: `editorname` \
Opcjonalny. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

Składnia argumentów/e: `editorname` używa nazw edytorów, które są wyświetlane w **oknie dialogowym Otwórz za pomocą**, ujęte w cudzysłów.

Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące polecenie dla argumentu/e: `editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
W tym przykładzie dodano nowy element rozwiązania MyHTMLpg do bieżącego rozwiązania.

```cmd
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)