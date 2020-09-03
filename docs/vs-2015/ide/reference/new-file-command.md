---
title: Nowy plik — polecenie | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.newfile
helpviewer_keywords:
- File.NewFile command
- New File command
ms.assetid: 767868d6-a525-425b-a43b-2198f636ab6b
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8e0d25d585f518c854ad6176ae4ae7a5f27b22ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671964"
---
# <a name="new-file-command"></a>Nowy plik — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tworzy nowy plik i otwiera go. Plik zostanie wyświetlony w folderze różne pliki.

## <a name="syntax"></a>Składnia

```
File.NewFile [filename] [/t:templatename] [/editor:editorname]
```

## <a name="arguments"></a>Argumenty
 `filename` Obowiązkowe. Nazwa pliku. Jeśli nie podano nazwy, zostanie podana nazwa domyślna. Jeśli na liście nie ma nazwy szablonu, tworzony jest plik tekstowy.

## <a name="switches"></a>Przełączniki
 /t: `templatename` opcjonalne. Określa typ pliku, który ma zostać utworzony.

 Składnia/t: `templatename` argument odzwierciedla informacje znajdujące się w oknie dialogowym Nowy plik. Wprowadź nazwę kategorii, a następnie ukośnik odwrotny ( `\` ) i nazwę szablonu, a następnie umieść cały ciąg w cudzysłowie.

 Na przykład, aby utworzyć nowy [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)] plik źródłowy, należy wprowadzić następujące polecenie dla/t: `templatename` argumentu.

```
/t:"Visual C++\C++ File (.cpp)"
```

 Powyższy przykład wskazuje, że szablon pliku C++ znajduje się w kategorii Visual C++ w oknie dialogowym **nowy plik** .

 /e: `editorname` opcjonalne. Nazwa edytora, w którym plik zostanie otwarty. Jeśli argument jest określony, ale nie zostanie podana nazwa edytora, pojawi się okno dialogowe **Otwórz za pomocą** .

 Składnia/e: `editorname` argument używa nazw edytorów, jak pojawiają się w oknie dialogowym Otwórz za pomocą, ujętym w cudzysłów.

 Na przykład, aby otworzyć plik w edytorze kodu źródłowego, należy wprowadzić następujące polecenie/e: `editorname` argument.

```
/e:"Source Code (text) Editor"
```

## <a name="example"></a>Przykład
 Ten przykład tworzy nową stronę sieci Web "test1.htm" i otwiera ją w edytorze kodu źródłowego.

```
>File.NewFile test1 /t:"General\HTML Page" /e:"Source Code (text) Editor"
```

## <a name="see-also"></a>Zobacz też
 Okno poleceń [poleceń programu Visual Studio](../../ide/reference/visual-studio-commands.md) [Command Window](../../ide/reference/command-window.md) okno [bezpośrednie](../../ide/reference/immediate-window.md) [Znajdź/pole polecenia](../../ide/find-command-box.md) [Aliasy poleceń programu Visual Studio](../../ide/reference/visual-studio-command-aliases.md)
