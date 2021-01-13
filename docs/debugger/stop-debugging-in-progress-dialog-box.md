---
title: Okno dialogowe Zatrzymaj debugowanie w toku | Microsoft Docs
description: Przejrzyj okno dialogowe Zatrzymaj debugowanie w toku, które jest wyświetlane, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywanie sesji trwa.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.stopnow
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
- SQL
helpviewer_keywords:
- Stop Debugging in Progress dialog box
ms.assetid: ed7ef49d-e25f-4a4d-9396-9bc7b4143117
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c3ff46a8cd9b8e5a4ab80b0af1296348ca788d9
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150226"
---
# <a name="stop-debugging-in-progress-dialog-box"></a>Zatrzymanie trwającego debugowania — Okno dialogowe
To okno dialogowe pojawia się, gdy debuger próbuje zatrzymać sesję debugowania, ale zatrzymywanie sesji może zająć trochę czasu. Zatrzymywanie sesji debugowania jest zwykle bardzo szybkie i to okno dialogowe nie pojawia się. Czasami jednak odłączenie od wszystkich debugowanych procesów trwa dłużej. Jeśli zatrzymywanie sesji trwa dłużej niż kilka sekund (lub jeśli wystąpi błąd odłączenia), pojawi się to okno dialogowe. Jeśli taka sytuacja występuje często, może to być spowodowane problemem wewnętrznym i warto skontaktować się z pomocą techniczną.

 Możesz poczekać, aż procesy zostaną odłączone, a to okno dialogowe zniknie lub użyj przycisku **Zatrzymaj teraz** , aby wymusić natychmiastowe zakończenie.

 **Zatrzymaj teraz** Kliknij ten przycisk, aby natychmiast zakończyć sesję debugowania. Użycie polecenia **Zatrzymaj teraz** zakończy się zamiast odłączania debugowanych procesów. Jeśli debugujesz procesy systemowe, zakończenie tych procesów z opcją **Zatrzymaj teraz** może mieć nieoczekiwane i niepożądane skutki.

## <a name="see-also"></a>Zobacz także
- [Zabezpieczenia debugera](../debugger/debugger-security.md)
- [Odłączanie programów](/previous-versions/visualstudio/visual-studio-2010/x1thkxez(v=vs.100))