---
title: Dodaj istniejący element — polecenie | Dokumentacja firmy Microsoft
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7686c4db4984188a4f8c4a52343f1386e9edd909
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54797840"
---
# <a name="add-existing-item-command"></a>Dodaj istniejący element — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Dodaje istniejący plik do bieżącego rozwiązania i otwiera go.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.AddExistingItem filename [/e:editorname]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagana. Pełna ścieżka i nazwa pliku, z rozszerzeniem element do dodania do bieżącego rozwiązania. Jeśli ścieżka do pliku lub nazwa pliku zawiera spacje, należy ująć w znaki cudzysłowu pełną ścieżkę.  
  
## <a name="switches"></a>Przełączniki  
 / e: `editorname`  
 Opcjonalna. Nazwa edytora, w którym będzie można otworzyć pliku. Jeśli argument jest określony, ale nazwa edytora nie został podany, **Otwórz za pomocą** pojawi się okno dialogowe.  
  
 / E:`editorname` składnię argumentu używa nazw edytora, w jakiej występują w **Otwórz okno dialogowe za pomocą**, ujęty w znaki cudzysłowu. Na przykład, aby otworzyć arkusz stylów w edytorze kodu źródłowego, należy wprowadzić następujące / e:`editorname` argumentu.  
  
```  
/e:"Source Code (text) Editor"  
```  
  
## <a name="remarks"></a>Uwagi  
 Automatycznego uzupełniania próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.  
  
## <a name="example"></a>Przykład  
 Ten przykład dodaje plik Form1.frm, do bieżącego rozwiązania.  
  
```  
>File.AddExistingItem "C:\public\solution files\Form1.frm"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
