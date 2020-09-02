---
title: Dodaj nowy element — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- project.addnewitem
helpviewer_keywords:
- Add New Item command
- File.AddNewItem command
ms.assetid: 63b7df32-db83-463b-bbe7-7ff011fe5298
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e6237ace96799961683b0b0431f5dad3ab679e24
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670209"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dodaje nowy element rozwiązania, taki jak. htm, CSS, txt lub FRAMESET do bieżącego rozwiązania i otwiera go.

## <a name="syntax"></a>Składnia

```
File.AddNewItem [filename] [/t:templatename] [/e:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Obowiązkowe. Ścieżka i nazwa pliku elementu, który ma zostać dodany do rozwiązania.

## <a name="switches"></a>Przełączniki
 /t: `templatename` opcjonalne. Określa typ pliku, który ma zostać utworzony. Jeśli nie podano nazwy szablonu, plik tekstowy jest tworzony domyślnie.

 Składnia/t: `templatename` argument odzwierciedla informacje znajdujące się w oknie dialogowym **Dodaj nowy element rozwiązania** . Należy wprowadzić kompletną kategorię, a następnie typ pliku, oddzielając nazwę kategorii od typu pliku przez ukośnik odwrotny ( `\` ) i otaczając cały ciąg w cudzysłowie.

 Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić następujące polecenie dla/t: `templatename` argumentu.

```
/t:"General\Style Sheet"
```

 /e: `editorname` opcjonalne. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

 Składnia/e: `editorname` argument używa nazw edytorów, jak pojawiają się w **oknie dialogowym Otwórz za pomocą**, ujętym w cudzysłów.

 Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, dla argumentu/e: należy wprowadzić następujące elementy `editorname` .

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
 W tym przykładzie dodano nowy element rozwiązania MyHTMLpg do bieżącego rozwiązania.

```
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"
```

## <a name="see-also"></a>Zobacz też
 Polecenia [programu Visual Studio](../../ide/reference/visual-studio-commands.md) [okno](../../ide/reference/command-window.md) poleceń [Znajdź/polecenie](../../ide/find-command-box.md) [programu Visual Studio — Aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
