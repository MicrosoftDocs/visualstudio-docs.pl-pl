---
title: 'Błąd: Proces roboczy witryny sieci Web został zakończony przez usługi IIS | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.web_server_process_terminated
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 5707b972-71a6-4cc6-ab99-c7c00ca8628c
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 787785909cd980176fd9220f58198ae6cc272ea8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68185462"
---
# <a name="error-web-site-worker-process-has-been-terminated-by-iis"></a>Błąd: Proces roboczy witryny internetowej został zakończony przez usługi IIS
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Debuger zatrzymana wykonywanie kodu na witrynie sieci Web. Spowodowało to Internet Information Services (IIS) aby założył, że proces roboczy przestał odpowiadać. W związku z tym usługi IIS zakończone procesu roboczego.  
  
 Aby kontynuować debugowanie, należy skonfigurować serwer IIS zezwala na proces roboczy kontynuować. Nie ma tego komunikatu o błędzie z wersjami usług IIS, które są starsze niż IIS 7.  
  
### <a name="to-configure-iis-7-to-allow-the-worker-process-to-continue"></a>Aby skonfigurować usługi IIS 7, aby zezwolić na proces roboczy kontynuować  
  
1. Otwórz **narzędzia administracyjne** okna.  
  
   1. Kliknij przycisk **Start**, a następnie wybierz **Panelu sterowania**.  
  
   2. W **Panelu sterowania**, wybierz **Przełącz na widok klasyczny**, jeśli to konieczne, a następnie kliknij dwukrotnie **narzędzia administracyjne**.  
  
2. W **narzędzia administracyjne** okna, kliknij dwukrotnie **Internet Information Services (IIS) Manager**.  
  
    Zostanie otwarty Menedżer usług IIS.  
  
3. W **połączeń** okienku rozwiń \<nazwa komputera > węzła, jeśli to konieczne.  
  
4. W obszarze \<nazwa komputera > węzła, kliknij przycisk **pul aplikacji**.  
  
5. W **pul aplikacji** listy, kliknij prawym przyciskiem myszy nazwę puli aplikacji działa w, a następnie kliknij **Zaawansowane ustawienia**.  
  
6. W **Zaawansowane ustawienia** dialogowym zlokalizuj **Model procesu** sekcji, a następnie wykonaj jedną z następujących czynności:  
  
   - Ustaw **pingowanie włączone** do **False**.  
  
   - Ustaw **maksymalny czas odpowiedzi polecenia Ping** wartość, która jest większa niż 90 sekund.  
  
     Ustawienie **pingowanie włączone** do **False** zatrzymuje IIS sprawdzanie, czy Proces roboczy jest nadal uruchomione i utrzymuje aktywność procesu roboczego aż do zatrzymania usługi debugowanego procesu. Ustawienie **maksymalny czas odpowiedzi polecenia Ping** na dużą wartość umożliwia usług IIS kontynuować monitorowanie procesu roboczego.  
  
7. Kliknij przycisk **OK** zamknąć **Zaawansowane ustawienia** okno dialogowe.  
  
8. Zamknij Menedżera usług IIS i **narzędzia administracyjne** okna.  
  
## <a name="see-also"></a>Zobacz też  
 [Błędy związane z debugowaniem zdalnym i rozwiązywanie problemów](../debugger/remote-debugging-errors-and-troubleshooting.md)
