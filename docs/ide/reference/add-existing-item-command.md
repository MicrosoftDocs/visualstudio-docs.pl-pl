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
ms.openlocfilehash: d91e84a817b7b68f56c053d11d69facf753c6efc
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68919383"
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
Dodaje istniejący plik do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```cmd
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
`filename`\
Wymagane. Pełna ścieżka i nazwa pliku z rozszerzeniem, elementu, który ma zostać dodany do bieżącego rozwiązania. Jeśli ścieżka pliku lub nazwa pliku zawiera spacje, należy ująć całą ścieżkę w cudzysłów.

## <a name="switches"></a>Przełączniki
/e`editorname`\
Opcjonalny. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

Składnia/e:`editorname` argument używa nazw edytorów, jak pojawiają się w **oknie dialogowym Otwórz za pomocą**, ujętym w cudzysłów. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, dla argumentu/e:`editorname` należy wprowadzić następujące elementy.

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

## <a name="see-also"></a>Zobacz też

- [Visual Studio — polecenia](../../ide/reference/visual-studio-commands.md)
- [Okno Polecenie](../../ide/reference/command-window.md)
- [Pole znajdowania i polecenia](../../ide/find-command-box.md)
- [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)