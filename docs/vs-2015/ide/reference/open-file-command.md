---
title: Otwórz plik — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openfile
helpviewer_keywords:
- Open File command
- File.OpenFile command
- of command
ms.assetid: a51a83fc-e3c6-4fa2-8882-8b7b6c0a6406
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c8dcf35e4c045db0d9acd45e2eb307a31ba39f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671934"
---
# <a name="open-file-command"></a>Otwórz plik — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Otwiera istniejący plik i umożliwia określenie edytora.

## <a name="syntax"></a>Składnia

```
File.OpenFile filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Wymagane. Pełna lub częściowa ścieżka i nazwa pliku do otwarcia. Ścieżki zawierające spacje muszą być ujęte w cudzysłów.

## <a name="switches"></a>Przełączniki
 /e: `editorname` opcjonalne. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

 Składnia/e: `editorname` argument używa nazw edytorów, jak pojawiają się w oknie dialogowym Otwórz za pomocą, ujętym w cudzysłów.

 Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące polecenie/e: `editorname` argument.

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
 Podczas wprowadzania ścieżki funkcja automatycznego uzupełniania próbuje znaleźć poprawną ścieżkę i nazwę pliku.

## <a name="example"></a>Przykład
 Ten przykład otwiera plik stylu "test1. css" w edytorze kodu źródłowego.

```
>File.OpenFile "C:\My Projects\project1\Test1.css" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też
 Okno poleceń [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) [Command Window](../../ide/reference/command-window.md) okno [bezpośrednie](../../ide/reference/immediate-window.md) [Znajdź/pole polecenia](../../ide/find-command-box.md) [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
