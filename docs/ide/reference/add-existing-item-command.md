---
title: Dodaj istniejący element — Polecenie
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b8ab2ce6e9f1260172bf0ffbf0aede9138a5115f
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951569"
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
Dodaje istniejący plik do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Wymagane. Pełna ścieżka i nazwa pliku, z rozszerzeniem element do dodania do bieżącego rozwiązania. Jeśli ścieżka do pliku lub nazwa pliku zawiera spacje, należy ująć w znaki cudzysłowu pełną ścieżkę.

## <a name="switches"></a>Przełączniki
 /e: `editorname` Opcjonalnie. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument jest określony, ale nazwa edytora nie został podany, **Otwórz za pomocą** pojawi się okno dialogowe.

 / E:`editorname` składnię argumentu używa nazw edytora, w jakiej występują w **Otwórz okno dialogowe za pomocą**, ujęty w znaki cudzysłowu. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
 Automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.

## <a name="example"></a>Przykład
 Ten przykład dodaje plik Form1.frm, do bieżącego rozwiązania.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)