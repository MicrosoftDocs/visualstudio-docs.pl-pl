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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d7a71a6d313ce12a40cd5c30470f53b1e2a1b69e
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919126"
---
# <a name="new-file-command"></a>Nowy plik — Polecenie
Tworzy nowy plik i otwiera go. Plik zostanie wyświetlony w folderze różne pliki.

## <a name="syntax"></a>Składnia

```cmd
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`

Opcjonalna. Nazwa pliku. Jeśli nie podano nazwy, zostanie podana nazwa domyślna. Jeśli na liście nie ma nazwy szablonu, tworzony jest plik tekstowy.

## <a name="switches"></a>Przełączniki
/t`templatename`\
Opcjonalna. Określa typ pliku, który ma zostać utworzony.

Składnia/t:`templatename` argument odzwierciedla informacje znajdujące się w oknie dialogowym Nowy plik. Wprowadź nazwę kategorii, a następnie ukośnik odwrotny (`\`) i nazwę szablonu, a następnie umieść cały ciąg w cudzysłowie.

Na przykład, aby utworzyć nowy [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] plik źródłowy, należy wprowadzić następujące polecenie dla/t:`templatename` argumentu.

```cmd
/t:"Visual C++\C++ File (.cpp)"
```

Powyższy przykład wskazuje, że C++ szablon pliku znajduje się w kategorii wizualizacji C++ w oknie dialogowym **nowy plik** .

/e`editorname`\
Opcjonalny. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

Składnia/e:`editorname` argument używa nazw edytorów, jak pojawiają się w oknie dialogowym Otwórz za pomocą, ujętym w cudzysłów.

Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące polecenie/e:`editorname` argument.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
Ten przykład tworzy nową stronę sieci Web "test1. htm" i otwiera ją w edytorze kodu źródłowego.

```cmd
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Okno bezpośrednie](../../ide/reference/immediate-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)