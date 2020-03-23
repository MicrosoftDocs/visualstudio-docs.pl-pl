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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d49f0fde7bbf13a1219296420b84970f4350860
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75585707"
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
Dodaje istniejący plik do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Wymagany. Pełna ścieżka i nazwa pliku, z rozszerzeniem, elementu, aby dodać do bieżącego rozwiązania. Jeśli ścieżka pliku lub nazwa pliku zawiera spacje, należy ująć całą ścieżkę w cudzysłów.

## <a name="switches"></a>Przełączniki
/e:`editorname`\
Element opcjonalny. Nazwa edytora, w którym zostanie otwarty plik. Jeśli argument jest określony, ale nie podano nazwy edytora, zostanie wyświetlone okno dialogowe **Otwórz za pomocą.**

Składnia argumentu /e:`editorname` używa nazw edytorów wyświetlanych w oknie **dialogowym Otwórz za pomocą**, ujętych w cudzysłów. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego,`editorname` należy wprowadzić następujące dla argumentu /e:.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
Autouzupełnianie próbuje zlokalizować prawidłową ścieżkę i nazwę pliku podczas pisania.

## <a name="example"></a>Przykład
W tym przykładzie dodaje plik Form1.frm do bieżącego rozwiązania.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Zobacz też

- [Visual Studio — Polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno polecenia](../../ide/reference/command-window.md)
- [Pole Znajdź/Polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
