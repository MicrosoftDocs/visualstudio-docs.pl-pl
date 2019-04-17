---
title: Dodaj nowy element polecenie | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0ba7820bfa6df7273f170b2222d6a55e685e445e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59668135"
---
# <a name="add-new-item-command"></a>Dodaj nowy element — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dodaje nowy element rozwiązania, takie jak .htm, CSS, txt lub zestaw ramek do bieżącego rozwiązania i otwiera go.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.AddNewItem [filename] [/t:templatename] [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Opcjonalna. Ścieżka i nazwa pliku elementu do dodania do rozwiązania.  
  
## <a name="switches"></a>Przełączniki  
 /t: `templatename`  
 Opcjonalna. Określa typ pliku ma zostać utworzony. Jeśli nazwa szablonu nie zostanie określony, domyślnie tworzone jest plikiem tekstowym.  
  
 T:`templatename` składnię argumentu odzwierciedla informacji znajdujących się w **Dodaj nowy element rozwiązania** okno dialogowe. Należy wprowadzić pełną kategorii, typu pliku, oddzielając nazwy kategorii z typu pliku za ukośnik odwrotny, po którym następuje (`\`) i nawiasami cały ciąg w cudzysłowie.  
  
 Na przykład, aby utworzyć nowy plik tekstowy, należy wprowadzić następujące t:`templatename` argumentu.  
  
```  
/t:"General\Style Sheet"  
```  
  
 / e: `editorname`  
 Opcjonalna. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument jest określony, ale nazwa edytora nie został podany, **Otwórz za pomocą** pojawi się okno dialogowe.  
  
 / E:`editorname` składnię argumentu używa nazw edytora, w jakiej występują w **Otwórz okno dialogowe za pomocą**, ujęty w znaki cudzysłowu.  
  
 Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład dodaje nowy element rozwiązania, MyHTMLpg, do bieżącego rozwiązania.  
  
```  
>File.AddNewItem MyHTMLpg /t:"General\HTML Page"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
