---
title: Zdarzenia (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1b8d6085f21035408b33b229220e4aea10b2b6c5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842086"
---
# <a name="events-vsperfcmd"></a>Zdarzenia (VSPerfCmd)
*VSPerfCmd.exe* **zdarzenia** opcja kontroluje rejestrowanie zdarzeń śledzenia dla Windows (ETW). Dane funkcji ETW są zapisywane w pliku etl, który jest oddzielony od plików danych profilera. Dane mogą być wyświetlane w raporcie przy użyciu [VSPerfReport](../profiling/vsperfreport.md) polecenia/Summary: ETW.  
  
 **Zdarzenia** opcji można wywołać w dowolnym momencie przed VSPerfCmd **zamknięcia** polecenia jest wywoływana, aby zatrzymać profilowanie.  
  
## <a name="syntax"></a>Składnia  
  
```cmd  
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]  
```  
  
#### <a name="parameters"></a>Parametry  
 **Na**&#124;**wyłączone**  
 Uruchamia lub zatrzymuje zbieranie danych zdarzeń.  
  
 `Guid`  
 Identyfikator GUID kontrolki dostawcy.  
  
 `ProviderName`  
 Nazwa dostawcy, który jest zarejestrowany za pomocą Instrumentacji zarządzania Windows (WMI).  
  
 `Flags`  
 "0 x" — prefiks wartość szesnastkową znaczników, który jest definiowany przez dostawcę zdarzeń.  
  
 `Level`  
 Określa ilość zebranych danych. `Level` jest definicją Dostawca zdarzeń.  
  
 **Zdarzenia** opcja obsługuje następujące słowa kluczowe jądra jako nazwy dostawcy:  
  
 **Proces**  
 Przetwarzanie zdarzeń  
  
 **Wątek**  
 Zdarzenia wątków  
  
 **Obraz**  
 Obraz ładowanie i zwalnianie zdarzenia  
  
 **Dysk**  
 Zdarzenia We/Wy dysku  
  
 **Plik**  
 Zdarzenia We/Wy plików  
  
 **Hardfault**  
 Sprzętowe błędy stron  
  
 **Pagefault**  
 Słabe strony błędów  
  
 **Sieci**  
 Zdarzenia sieci  
  
 **Registry**  
 Zdarzenia dostępu do rejestru  
  
 Należy pamiętać, że dostawca jądra można włączyć tylko. Nie można wyłączyć, ani jej flag można modyfikować, dopóki nie wyłącza monitor.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
>  Po włączeniu zdarzeń CLR ETW uruchamiania dodatkowe są zbierane również w raporcie widoku śledzenia. Aby wykluczyć zdarzenia uruchamiania były wyświetlane w raporcie, użyj następującego polecenia:  
  
```cmd  
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5  
```  
  
> [!IMPORTANT]
>  Jeśli nie wykluczysz zdarzenia uruchamiania, następnie ponieważ te zdarzenia nie są wymienione w pliku Managed Object Format (MOF), zostaną one wyświetlone jako identyfikatory GUID w raporcie. Aby uzyskać więcej informacji zobacz tę stronę w witrynie internetowej firmy Microsoft: [Przykładowy plik Managed Object Format (MOF)](http://go.microsoft.com/fwlink/?linkid=37118).  
  
## <a name="see-also"></a>Zobacz także  
 [Narzędzia VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)