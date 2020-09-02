---
title: Kody komunikatów | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c09245056bf7e947985bfa55dc9cc4a3a96b8cf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "62846277"
---
# <a name="message-codes"></a>Kody komunikatów
Każdy wiersz komunikatu wyświetlany w [widoku komunikatów](../debugger/messages-view.md) zawiera kod "P", "," lub "R". Kody te mają następujące znaczenie:

|Kod|Znaczenie|
|----------|-------------|
|P|Wiadomość została opublikowana w kolejce przy użyciu funkcji **PostMessage** . Brak dostępnych informacji dotyczących ostatecznej dyspozycji wiadomości.|
|S|Komunikat został wysłany przy użyciu funkcji **SendMessage** . Oznacza to, że nadawca nie odzyska kontroli do momentu, gdy odbiornik nie przetwarza i nie zwróci komunikatu. W związku z tym odbiornik może przekazać wartość zwrotną z powrotem do nadawcy.|
|s|Wiadomość została wysłana, ale zabezpieczenia uniemożliwiają dostęp do wartości zwracanej.|
|R|Każdy element "line" ma odpowiadający wiersz "R" (Return), który wyświetla wartość zwracaną przez komunikat. Czasami wywołania komunikatów są zagnieżdżane, co oznacza, że jeden program obsługi komunikatów wysyła kolejny komunikat.|