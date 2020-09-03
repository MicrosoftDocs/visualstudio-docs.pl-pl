---
title: Kody komunikatów | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182964"
---
# <a name="message-codes"></a>Kody komunikatów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Każdy wiersz komunikatu wyświetlany w [widoku komunikatów](../debugger/messages-view.md) zawiera kod "P", "," lub "R". Kody te mają następujące znaczenie:  
  
|Kod|Znaczenie|  
|----------|-------------|  
|P|Wiadomość została opublikowana w kolejce przy użyciu funkcji **PostMessage** . Brak dostępnych informacji dotyczących ostatecznej dyspozycji wiadomości.|  
|S|Komunikat został wysłany przy użyciu funkcji **SendMessage** . Oznacza to, że nadawca nie odzyska kontroli do momentu, gdy odbiornik nie przetwarza i nie zwróci komunikatu. W związku z tym odbiornik może przekazać wartość zwrotną z powrotem do nadawcy.|  
|s|Wiadomość została wysłana, ale zabezpieczenia uniemożliwiają dostęp do wartości zwracanej.|  
|R|Każdy element "line" ma odpowiadający wiersz "R" (Return), który wyświetla wartość zwracaną przez komunikat. Czasami wywołania komunikatów są zagnieżdżane, co oznacza, że jeden program obsługi komunikatów wysyła kolejny komunikat.|
