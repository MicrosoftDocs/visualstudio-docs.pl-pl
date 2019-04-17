---
title: Uruchom polecenie | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- debug.start
helpviewer_keywords:
- Start command
- Debug.Start command
ms.assetid: dc4e4aa2-b0ab-4e00-92db-6dc3058ddc21
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: c334f52ba080329ef5cbd6dfde1e3e3beed1dc70
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2019
ms.locfileid: "59658165"
---
# <a name="start-command"></a>Uruchomienie — Polecenie
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Rozpoczyna się debugowanie projektu startowego.  
  
## <a name="syntax"></a>Składnia  
  
```  
Debug.Start [address]  
```  
  
## <a name="arguments"></a>Argumenty  
 `address`  
 Opcjonalna. Adres, w którym program zawiesza wykonywanie, podobnie jak punkt przerwania w kodzie źródłowym. Ten argument jest prawidłowy tylko w trybie debugowania.  
  
## <a name="remarks"></a>Uwagi  
 **Start** polecenia po wykonaniu wykonuje operację RunToCursor do określonego adresu.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie Uruchamia debuger i ignoruje wszelkie wyjątki, które występują.  
  
```  
>Debug.Start  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)   
 [Okno polecenia](../../ide/reference/command-window.md)   
 [Znajdź/Command — pole](../../ide/find-command-box.md)   
 [Visual Studio — aliasy poleceń](../../ide/reference/visual-studio-command-aliases.md)
