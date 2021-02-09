---
title: 'Ostrzeżenie: debugowanie skryptu wyłączone | Microsoft Docs'
description: Ostrzeżenie "debugowanie skryptu wyłączone" występuje podczas próby debugowania skryptu bez włączania debugowania skryptów w programie Internet Explorer. Zapoznaj się z instrukcjami, aby je włączyć.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 052445b1dbb69c433220caf5764413e04f0909fd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884003"
---
# <a name="warning-script-debugging-disabled"></a>Ostrzeżenie: debugowanie skryptu wyłączone
Debugowanie skryptów jest obecnie wyłączone w programie Internet Explorer

 To ostrzeżenie występuje podczas próby debugowania skryptu bez włączania debugowania skryptów w programie Internet Explorer. Ze względów bezpieczeństwa program Internet Explorer domyślnie wyłącza debugowanie skryptów.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Aby włączyć debugowanie skryptów w programie Internet Explorer

1. W menu **Narzędzia** programu Internet Explorer wybierz pozycję **Opcje internetowe**.

2. W oknie dialogowym **Opcje internetowe** kliknij kartę **Zaawansowane** .

3. Na karcie **Zaawansowane** poszukaj w oknie **Ustawienia** , **przeglądanie** kategorii.

4. Wyczyść pole **Wyłącz debugowanie skryptów (Internet Explorer)**.

5. Kliknij przycisk **OK**.

6. Zamknij i uruchom ponownie program Internet Explorer.

     Nowe ustawienia będą obowiązywać.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: dołączanie do skryptu](attach-to-running-processes-with-the-visual-studio-debugger.md)