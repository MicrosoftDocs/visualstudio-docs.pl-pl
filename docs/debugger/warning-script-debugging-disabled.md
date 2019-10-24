---
title: 'Ostrzeżenie: debugowanie skryptu wyłączone | Microsoft Docs'
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
ms.openlocfilehash: 91875a370f6d072cf2dd69807f516b8f1a808461
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728196"
---
# <a name="warning-script-debugging-disabled"></a>Ostrzeżenie: debugowanie skryptu wyłączone
Debugowanie skryptów jest obecnie wyłączone w programie Internet Explorer

 To ostrzeżenie występuje podczas próby debugowania skryptu bez włączania debugowania skryptów w programie Internet Explorer. Ze względów bezpieczeństwa program Internet Explorer domyślnie wyłącza debugowanie skryptów.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Aby włączyć debugowanie skryptów w programie Internet Explorer

1. W menu **Narzędzia** programu Internet Explorer wybierz pozycję **Opcje internetowe**.

2. W oknie dialogowym **Opcje internetowe** kliknij kartę **Zaawansowane** .

3. Na karcie **Zaawansowane** poszukaj w oknie **Ustawienia** , **przeglądanie** kategorii.

4. Wyczyść pole **Wyłącz debugowanie skryptów (Internet Explorer)** .

5. Kliknij przycisk **OK**.

6. Zamknij i uruchom ponownie program Internet Explorer.

     Nowe ustawienia będą obowiązywać.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: dołączanie do skryptu](../debugger/how-to-attach-to-script.md)