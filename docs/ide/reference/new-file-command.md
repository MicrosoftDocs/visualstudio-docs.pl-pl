---
title: Nowy plik — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5fe8a99ee59a347fdcb7cff601b75139760630f7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75595959"
---
# <a name="new-file-command"></a>Nowy plik — Polecenie
Tworzy nowy plik i otwiera go. Plik pojawi się w folderze Różne pliki.

## <a name="syntax"></a>Składnia

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`

Element opcjonalny. Nazwa pliku. Jeśli nie podano nazwy, podana jest nazwa domyślna. Jeśli nie ma na liście nazwy szablonu, tworzony jest plik tekstowy.

## <a name="switches"></a>Przełączniki
/t:`templatename`\
Element opcjonalny. Określa typ pliku, który ma zostać utworzony.

Składnia argumentu /t:`templatename` odzwierciedla informacje znalezione w oknie dialogowym Nowy plik. Wprowadź nazwę kategorii, po której następuje ukośnik odwrotny (`\`) i nazwa szablonu, a cały ciąg należy ująć w cudzysłów.

Na przykład, aby [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] utworzyć nowy plik źródłowy, należy wprowadzić`templatename` następujące dla argumentu /t:.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Powyższy przykład wskazuje, że szablon pliku języka C++ znajduje się w kategorii Visual C++ w oknie dialogowym **Nowy plik.**

/e:`editorname`\
Element opcjonalny. Nazwa edytora, w którym zostanie otwarty plik. Jeśli argument jest określony, ale nie podano nazwy edytora, zostanie wyświetlone okno dialogowe **Otwórz za pomocą.**

Składnia argumentu /e:`editorname` używa nazw edytorów wyświetlanych w oknie dialogowym Otwórz za pomocą, ujętych w cudzysłów.

Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy`editorname` wprowadzić następujące dla /e: argument.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
W tym przykładzie tworzy nową stronę sieci web "test1.htm" i otwiera ją w edytorze kodu źródłowego.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
