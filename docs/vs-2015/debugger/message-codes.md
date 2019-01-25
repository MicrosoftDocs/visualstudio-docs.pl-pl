---
title: Kody komunikatów | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54799432"
---
# <a name="message-codes"></a>Kody komunikatów
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Każdy wiersz komunikat wyświetlany w [widoku komunikatów](../debugger/messages-view.md) zawiera "P", użytkownika, "firmy," lub "R" kodu. Te kody mają następujące znaczenie:  
  
|Kod|Znaczenie|  
|----------|-------------|  
|P|Opublikowano wiadomość do kolejki za pomocą **funkcji PostMessage** funkcji. Nie są dostępne informacje dotyczące ultimate dyspozycji wiadomości.|  
|S|Wiadomość została wysłana z **SendMessage** funkcji. Oznacza to, nadawca nie odzyskać kontrolę do momentu Odbiorca przetwarza i zwraca komunikat. Odbiornik w związku z tym, przekazać wartość zwracaną do nadawcy.|  
|s|Komunikat został wysłany, ale zabezpieczeń uniemożliwia dostęp do wartości zwracanej.|  
|R|W każdym "wiersz ma odpowiedni wiersz"R"(zwrot), zawierającego wartość zwracaną wiadomości. Czasami wywołania wiadomości są zagnieżdżone, co oznacza, że ten program obsługi komunikatów co wysyła kolejną wiadomość.|
