---
title: Dodaj istniejący projekt polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7523db6598a32c76944c22bfdabe56ee288c6b43
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771085"
---
# <a name="add-existing-project-command"></a>Dodaj istniejący projekt — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Dodaje istniejący projekt do bieżącego rozwiązania.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Opcjonalna. Pełna ścieżka i projektu nazwa, z rozszerzeniem projekt, aby dodać do rozwiązania.  
  
 Jeśli `filename` argument zawiera spacje, muszą być ujęte w znaki cudzysłowu.  
  
 Jeśli nazwa pliku nie zostanie określony, polecenie spowoduje otwarcie okna dialogowego plików, dzięki czemu użytkownik może wybrać projekt.  
  
## <a name="remarks"></a>Uwagi  
 Automatyczne uzupełnianie próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.  
  
## <a name="example"></a>Przykład  
 Ten przykład dodaje [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] projektu TestProject1, do bieżącego rozwiązania.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
