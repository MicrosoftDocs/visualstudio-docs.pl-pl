---
title: 'VsgDbg:: ~ VsgDbg (destruktor) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c0ae3dd206953e728175f4479920861295feae00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200302"
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (Destruktor)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Niszczy wystąpienie `VsgDbg` klasy. Jeśli informacje o grafice są aktywnie rejestrowane, plik dziennika grafiki zostanie sfinalizowany i zamknięty, a zasoby, które były używane podczas aktywnie przechwytywania informacji graficznych, są uwalniane.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Zobacz też  
 [VsgDbg::VsgDbg (Konstruktor)](../debugger/vsgdbg-vsgdbg-constructor.md)
