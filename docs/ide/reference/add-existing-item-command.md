---
title: Dodaj istniejący element — Polecenie
description: Dowiedz się więcej na temat polecenia Dodaj istniejący element i sposobu dodawania istniejącego pliku do bieżącego rozwiązania i otwierania go.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43c9e7d5947796bb1598bf9dc02420b31e43d167
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933833"
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
/e `editorname`\
Opcjonalny. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

Składnia/e: `editorname` argument używa nazw edytorów, jak pojawiają się w **oknie dialogowym Otwórz za pomocą**, ujętym w cudzysłów. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, dla argumentu/e: należy wprowadzić następujące elementy `editorname` .

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
- [Okno polecenia](../../ide/reference/command-window.md)
- [Znajdź/pole polecenia](../../ide/find-command-box.md)
- [Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
