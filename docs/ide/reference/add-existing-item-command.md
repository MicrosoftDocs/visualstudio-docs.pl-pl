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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89910a9504f587f97b0555f7f0d5ef7257ab4ae4
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748839"
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
Dodaje istniejący plik do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Wymagany. Pełna ścieżka i nazwa pliku z rozszerzeniem, elementu, który ma zostać dodany do bieżącego rozwiązania. Jeśli ścieżka pliku lub nazwa pliku zawiera spacje, należy ująć całą ścieżkę w cudzysłów.

## <a name="switches"></a>Przełączniki
/e: `editorname` \
Opcjonalny. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

Składnia argumentów/e: `editorname` używa nazw edytorów, które są wyświetlane w **oknie dialogowym Otwórz za pomocą**, ujęte w cudzysłów. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące polecenie dla argumentu/e: `editorname`.

```cmd
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
Autouzupełnianie próbuje znaleźć poprawną ścieżkę i nazwę pliku podczas wpisywania.

## <a name="example"></a>Przykład
Ten przykład dodaje plik Form1. frm do bieżącego rozwiązania.

```cmd
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Zobacz także

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)