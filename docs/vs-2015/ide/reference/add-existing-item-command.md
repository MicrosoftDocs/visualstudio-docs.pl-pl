---
title: Dodaj istniejący element — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addexistingitem
helpviewer_keywords:
- File.AddExistingItem command
- Add Existing Item command
ms.assetid: 41f56131-d4c7-4f81-83b7-bdac713ea870
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2f636c2a0eb2cfdcebf383fdc7eea70f72cb90e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670235"
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dodaje istniejący plik do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```
File.AddExistingItem filename [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Wymagane. Pełna ścieżka i nazwa pliku z rozszerzeniem, elementu, który ma zostać dodany do bieżącego rozwiązania. Jeśli ścieżka pliku lub nazwa pliku zawiera spacje, należy ująć całą ścieżkę w cudzysłów.

## <a name="switches"></a>Przełączniki
 /e: `editorname` opcjonalne. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

 Składnia/e: `editorname` argument używa nazw edytorów, jak pojawiają się w **oknie dialogowym Otwórz za pomocą**, ujętym w cudzysłów. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, dla argumentu/e: należy wprowadzić następujące elementy `editorname` .

```
/e:"Source Code (text) Editor"
```

## <a name="remarks"></a>Uwagi
 Autouzupełnianie próbuje znaleźć poprawną ścieżkę i nazwę pliku podczas wpisywania.

## <a name="example"></a>Przykład
 Ten przykład dodaje plik Form1. frm do bieżącego rozwiązania.

```
>File.AddExistingItem "C:\public\solution files\Form1.frm"
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
