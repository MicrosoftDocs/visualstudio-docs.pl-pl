---
title: Przełącz punkt przerwania — polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.togglebreakpoint
helpviewer_keywords:
- ToggleBreakpoint command
- Debug.ToggleBreakPoint command
- Toggle Breakpoint command
ms.assetid: d50dfadb-ce79-4d5e-9c09-1cfddd57876d
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 11f0598fa20a5293d662bdbb23b7f67c6c0c80b2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54793177"
---
# <a name="toggle-breakpoint-command"></a>Przełącz punkt przerwania — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Włącza punkt przerwania lub wyłączyć, w zależności od bieżącego stanu w bieżącej lokalizacji w pliku.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.ToggleBreakpoint [text]  
```  
  
## <a name="arguments"></a>Argumenty  
 `text`  
 Opcjonalna. Jeśli tekst jest określona, wiersz jest oznaczona jako nazwany punkt przerwania. W przeciwnym razie wiersz jest oznaczona jako nienazwane punkt przerwania, który przypomina co się stanie, gdy klawisz F9.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład zmienia bieżący punkt przerwania.  
  
```  
>Debug.ToggleBreakpoint  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
