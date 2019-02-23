---
title: Kody komunikatów | Dokumentacja firmy Microsoft
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
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681195"
---
# <a name="message-codes"></a>Kody komunikatów
Każdy wiersz komunikat wyświetlany w [widoku komunikatów](../debugger/messages-view.md) zawiera "P", użytkownika, "firmy," lub "R" kodu. Te kody mają następujące znaczenie:

|Kod|Znaczenie|
|----------|-------------|
|P|Opublikowano wiadomość do kolejki za pomocą **funkcji PostMessage** funkcji. Nie są dostępne informacje dotyczące ultimate dyspozycji wiadomości.|
|S|Wiadomość została wysłana z **SendMessage** funkcji. Oznacza to, nadawca nie odzyskać kontrolę do momentu Odbiorca przetwarza i zwraca komunikat. Odbiornik w związku z tym, przekazać wartość zwracaną do nadawcy.|
|s|Komunikat został wysłany, ale zabezpieczeń uniemożliwia dostęp do wartości zwracanej.|
|R|W każdym "wiersz ma odpowiedni wiersz"R"(zwrot), zawierającego wartość zwracaną wiadomości. Czasami wywołania wiadomości są zagnieżdżone, co oznacza, że ten program obsługi komunikatów co wysyła kolejną wiadomość.|