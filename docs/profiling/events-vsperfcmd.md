---
title: Zdarzenia (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62d4e2431ab2dbc2ca74944ac1717fe6c3169287
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63440094"
---
# <a name="events-vsperfcmd"></a>Zdarzenia (VSPerfCmd)
*VSPerfCmd.exe* **zdarzenia** opcja kontroluje rejestrowanie zdarzeń śledzenia dla Windows (ETW). Dane funkcji ETW są zapisywane w pliku etl, który jest oddzielony od plików danych profilera. Dane mogą być wyświetlane w raporcie przy użyciu [VSPerfReport](../profiling/vsperfreport.md) polecenia/Summary: ETW.

 **Zdarzenia** opcji można wywołać w dowolnym momencie przed VSPerfCmd **zamknięcia** polecenia jest wywoływana, aby zatrzymać profilowanie.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametry
 **Na**&#124;**poza** uruchamia lub zatrzymuje zbieranie danych zdarzeń.

 `Guid` Identyfikator GUID kontrolki dostawcy.

 `ProviderName` Nazwa dostawcy, który jest zarejestrowany za pomocą Instrumentacji zarządzania Windows (WMI).

 `Flags` "0 x" — prefiks wartość szesnastkową znaczników, który jest definiowany przez dostawcę zdarzeń.

 `Level` Określa ilość zebranych danych. `Level` jest definicją Dostawca zdarzeń.

 **Zdarzenia** opcja obsługuje następujące słowa kluczowe jądra jako nazwy dostawcy:

 **Proces** przetwarzania zdarzeń

 **Wątek** zdarzenia wątków

 **Obraz** obrazu ładowanie i zwalnianie zdarzenia

 **Dysk** zdarzenia We/Wy dysku

 **Plik** zdarzenia We/Wy pliku

 **Hardfault** sprzętowe błędy stron

 **Pagefault** błędów słabe strony

 **Sieć** sieci zdarzenia

 **Rejestr** zdarzenia dostępu do rejestru

 Należy pamiętać, że dostawca jądra można włączyć tylko. Nie można wyłączyć, ani jej flag można modyfikować, dopóki nie wyłącza monitor.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Po włączeniu zdarzeń CLR ETW uruchamiania dodatkowe są zbierane również w raporcie widoku śledzenia. Aby wykluczyć zdarzenia uruchamiania były wyświetlane w raporcie, użyj następującego polecenia:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Jeśli nie wykluczysz zdarzenia uruchamiania, następnie ponieważ te zdarzenia nie są wymienione w pliku Managed Object Format (MOF), zostaną one wyświetlone jako identyfikatory GUID w raporcie. Aby uzyskać więcej informacji zobacz tę stronę w witrynie internetowej firmy Microsoft: [Przykładowy plik Managed Object Format (MOF)](http://go.microsoft.com/fwlink/?linkid=37118).

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)