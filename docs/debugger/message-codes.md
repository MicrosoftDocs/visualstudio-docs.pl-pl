---
title: Kody komunikatów | Microsoft Docs
description: Poznaj znaczenie kodów komunikatów wyświetlanych w poszczególnych wierszach komunikatów widoku komunikatów.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: e4b836a5d4c1faad6b4c0375e2ec51d759816889
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903613"
---
# <a name="message-codes"></a>Kody komunikatów
Każdy wiersz komunikatu wyświetlany w [widoku komunikatów](../debugger/messages-view.md) zawiera kod "P", "," lub "R". Kody te mają następujące znaczenie:

|Kod|Znaczenie|
|----------|-------------|
|P|Wiadomość została opublikowana w kolejce przy użyciu funkcji **PostMessage** . Brak dostępnych informacji dotyczących ostatecznej dyspozycji wiadomości.|
|S|Komunikat został wysłany przy użyciu funkcji **SendMessage** . Oznacza to, że nadawca nie odzyska kontroli do momentu, gdy odbiornik nie przetwarza i nie zwróci komunikatu. W związku z tym odbiornik może przekazać wartość zwrotną z powrotem do nadawcy.|
|s|Wiadomość została wysłana, ale zabezpieczenia uniemożliwiają dostęp do wartości zwracanej.|
|R|Każdy element "line" ma odpowiadający wiersz "R" (Return), który wyświetla wartość zwracaną przez komunikat. Czasami wywołania komunikatów są zagnieżdżane, co oznacza, że jeden program obsługi komunikatów wysyła kolejny komunikat.|