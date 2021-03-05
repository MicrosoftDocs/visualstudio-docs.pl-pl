---
description: Debuger zatrzymał wykonywanie kodu w witrynie sieci Web.
title: Proces roboczy witryny sieci Web został zakończony przez usługi IIS | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ca2b873a4d4b04362298d2d96b9d037cc80addd4
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146278"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Błąd: proces roboczy witryny sieci Web został zakończony przez usługę IIS
Debuger zatrzymał wykonywanie kodu w witrynie sieci Web. Spowodowało to założenie, że proces roboczy przestanie odpowiadać na Internet Information Services (IIS). W związku z tym usługi IIS zakończyły proces roboczy.

 Aby kontynuować debugowanie, musisz skonfigurować usługi IIS, aby umożliwić kontynuowanie procesu roboczego. Ten komunikat o błędzie nie jest wyświetlany wraz z wersjami usług IIS, które są starsze niż usługi IIS 7.

### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Aby skonfigurować usługi IIS 7, aby umożliwić kontynuowanie procesu roboczego

1. Otwórz okno **Narzędzia administracyjne** .

   1. Kliknij przycisk **Start**, a następnie wybierz pozycję **Panel sterowania**.

   2. W **Panelu sterowania** wybierz opcję **Przełącz do widoku klasycznego**, w razie potrzeby, a następnie kliknij dwukrotnie ikonę **Narzędzia administracyjne**.

2. W oknie **Narzędzia administracyjne** kliknij dwukrotnie pozycję **Menedżer Internet Information Services (IIS)**.

    Zostanie otwarty Menedżer usług IIS.

3. W okienku **połączenia** rozwiń \<computer name> węzeł w razie potrzeby.

4. W \<computer name> węźle kliknij węzeł **Pule aplikacji**.

5. Na liście **Pule aplikacji** kliknij prawym przyciskiem myszy nazwę puli, w której aplikacja jest uruchamiana, a następnie kliknij pozycję **Ustawienia zaawansowane**.

6. W oknie dialogowym **Ustawienia zaawansowane** Znajdź sekcję **model procesu** i wykonaj jedną z następujących czynności:

   - Dla opcji **ping** Ustaw **wartość false**.

   - Ustaw **Maksymalny czas odpowiedzi polecenia ping** na wartość, która jest większa niż 90 sekund.

     Ustawienie opcji **ping włączone** na **wartość false** uniemożliwia usłudze IIS sprawdzenie, czy proces roboczy nadal działa i utrzymuje proces roboczy, dopóki nie zostanie zatrzymany proces. Ustawienie **maksymalnego czasu odpowiedzi polecenia ping** na dużą wartość pozwala usługom IIS kontynuować monitorowanie procesu roboczego.

7. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Ustawienia zaawansowane** .

8. Zamknij Menedżera usług IIS i okno **Narzędzia administracyjne** .

## <a name="see-also"></a>Zobacz też
- [Błędy debugowania zdalnego i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
