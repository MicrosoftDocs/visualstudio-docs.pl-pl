---
title: 'Ostrzeżenie: Debugowanie skryptów wyłączone | Dokumenty firmy Microsoft'
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
ms.openlocfilehash: 15de1a1e516cb3d84c24428ef04dd87baedaed9e
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81648506"
---
# <a name="warning-script-debugging-disabled"></a>Ostrzeżenie: debugowanie skryptu wyłączone
Debugowanie skryptów jest obecnie wyłączone w programie Internet Explorer

 To ostrzeżenie występuje podczas próby debugowania skryptu bez włączania debugowania skryptów w programie Internet Explorer. Ze względów bezpieczeństwa program Internet Explorer domyślnie wyłącza debugowanie skryptów.

### <a name="to-enable-script-debugging-in-internet-explorer"></a>Aby włączyć debugowanie skryptów w programie Internet Explorer

1. W menu **Narzędzia** programu Internet Explorer wybierz polecenie **Opcje internetowe**.

2. W oknie dialogowym **Opcje internetowe** kliknij kartę **Zaawansowane** .

3. Na karcie **Zaawansowane** poszukaj w polu **Ustawienia** kategorii **Przeglądanie.**

4. **Wyczyść funkcję Wyłącz debugowanie skryptów (Internet Explorer).**

5. Kliknij przycisk **OK**.

6. Zamknij i uruchom ponownie program Internet Explorer.

     Nowe ustawienia będą teraz obowiązywać.

## <a name="see-also"></a>Zobacz też
- [Jak: Dołącz do skryptu](attach-to-running-processes-with-the-visual-studio-debugger.md)