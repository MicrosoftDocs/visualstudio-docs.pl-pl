---
title: Przejdź do polecenia | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- edit.goto
helpviewer_keywords:
- Debug.Goto command
- Go To command
ms.assetid: 201e1dd2-6701-467d-8cc1-faec2ef20511
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 010d2c395d77be590b3d8d3bc26fc83aaa63adfa
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68199261"
---
# <a name="go-to-command"></a>Przejdź do — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Przenosi kursor do określonego wiersza.  
  
## <a name="syntax"></a>Składnia  
  
```  
Edit.GoTo [linenumber]  
```  
  
## <a name="arguments"></a>Argumenty  
 `linenumber`  
 Opcjonalny. Liczba całkowita reprezentująca numer wiersza, aby przejść do.  
  
## <a name="remarks"></a>Uwagi  
 Numerowanie wierszy rozpoczyna się od jednego. Jeśli wartość `linenumber` jest mniejsza niż jeden, pierwszy wyświetla wiersz. Jeśli wartość `linenumber` jest większa niż liczba ostatnim wierszu ostatniej wyświetla wiersz.  
  
 Jeśli wartość `linenumber` nie zostanie określony, **przejdź do wiersza** Wyświetla okno dialogowe.  
  
 Alias dla tego polecenia jest GoToLn.  
  
## <a name="example"></a>Przykład  
  
```  
>Edit.GoTo 125  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
