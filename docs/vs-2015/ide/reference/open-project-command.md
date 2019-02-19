---
title: Otwórz projekt — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 916ea8435571efc01f38e408d4fc2d4563c16f1c
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54753488"
---
# <a name="open-project-command"></a>Otwórz projekt — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Otwiera istniejący projekt.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Wymagana. Pełna ścieżka i nazwa projektu, aby otworzyć.  
  
 Składnia `filename` argument wymaga, że ścieżki zawierające spacje, użyj znaków cudzysłowu.  
  
## <a name="remarks"></a>Uwagi  
 Automatyczne uzupełnianie próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.  
  
 To polecenie nie jest dostępne podczas debugowania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie otwiera [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektu Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
