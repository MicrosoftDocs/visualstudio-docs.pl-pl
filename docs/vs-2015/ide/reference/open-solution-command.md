---
title: Otwórz rozwiązanie — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.opensolution
helpviewer_keywords:
- Open Solution command
- File.OpenSolution command
ms.assetid: 61de76c8-69d7-4cdb-b605-e132f45d05d9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 298609aa37557eebc52dce7ca6eada2f98f2096d
ms.sourcegitcommit: a83c60bb00bf95e6bea037f0e1b9696c64deda3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2019
ms.locfileid: "54759989"
---
# <a name="open-solution-command"></a>Otwórz rozwiązanie — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Powoduje otwarcie istniejącego rozwiązania, zamyka wszystkie otwarte rozwiązania.  
  
## <a name="syntax"></a>Składnia  
  
```  
File.OpenSolution filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `Filename`  
 Wymagana. Pełna ścieżka i nazwa pliku rozwiązania, aby otworzyć.  
  
 Składnia `filename` argument wymaga, że ścieżki zawierające spacje, użyj znaków cudzysłowu.  
  
## <a name="remarks"></a>Uwagi  
 Automatyczne uzupełnianie próbuje zlokalizować poprawną ścieżkę i nazwę pliku podczas wpisywania.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie otwiera rozwiązanie Test1.sln.  
  
```  
>File.OpenSolution "c:\MySolutions\Test1\Test1.sln"  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
