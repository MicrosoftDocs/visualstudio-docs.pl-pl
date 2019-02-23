---
title: 'Ostrzeżenie: Debugowanie skryptu wyłączone | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.scriptdisabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: 323d2b1d-52a4-42f7-b4ad-96b4b0c23b8d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2543ad00b2065f7659a89e165c2d4df990403667
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56687045"
---
# <a name="warning-script-debugging-disabled"></a>Ostrzeżenie: Debugowanie skryptów wyłączone
Debugowanie skryptów jest obecnie wyłączone w programie Internet Explorer

 Ostrzeżenie to pojawia się podczas próby debugowania skryptu bez włączania debugowania skryptu w programie Internet Explorer. Ze względów bezpieczeństwa program Internet Explorer wyłącza debugowanie skryptu domyślnie.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Aby włączyć debugowanie skryptów w programie Internet Explorer

1.  W programie Internet Explorer **narzędzia** menu, wybierz **Opcje internetowe**.

2.  W oknie dialogowym **Opcje internetowe** kliknij kartę **Zaawansowane** .

3.  Na **zaawansowane** kartę, Szukaj w **ustawienia** polu **przeglądania** kategorii.

4.  Wyczyść **Wyłącz debugowanie skryptu (Internet Explorer)**.

5.  Kliknij przycisk **OK**.

6.  Zamknij i ponownie uruchom program Internet Explorer.

     Teraz będzie obowiązywać do nowych ustawień.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Dołączanie do skryptu](../debugger/how-to-attach-to-script.md)