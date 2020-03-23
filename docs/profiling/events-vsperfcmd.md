---
title: Zdarzenia (VSPerfCmd) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 46b47f9b615c824d25e931cd3d05f5d2a04257ba
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74777324"
---
# <a name="events-vsperfcmd"></a>Zdarzenia (VSPerfCmd)
Opcja *VSPerfCmd.exe* **Events** kontroluje rejestrowanie śledzenia zdarzeń dla systemu Windows (ETW). Dane ETW są zapisywane w pliku .etl, który jest oddzielony od pliku danych profilera. Dane można przeglądać w raporcie za pomocą polecenia [VSPerfReport](../profiling/vsperfreport.md) /summary:etw.

 Zdarzenia **Events** opcja może być wywoływana w dowolnym momencie przed VSPerfCmd **shutdown** polecenie jest wywoływana, aby zatrzymać profilowania.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametry
 **Na**&#124;**Off** Rozpoczyna lub zatrzymuje zbieranie danych zdarzeń.

 `Guid`Identyfikator GUID formantu dostawcy.

 `ProviderName`Nazwa dostawcy zarejestrowanego w usłudze Instrumentacja zarządzania windowsem (WMI).

 `Flags`Wartość szesnastkowych flag z prefiksem "0x", która jest zdefiniowana przez dostawcę zdarzeń.

 `Level`Określa ilość zebranych danych. `Level`jest zdefiniowany przez dostawcę zdarzeń.

 Opcja **Zdarzenia** rozumie następujące słowa kluczowe jądra jako nazwy dostawców:

 **Proces** Zdarzenia przetwarzania

 **Wątek** Zdarzenia wątku

 **Fot.** Obraz ładuj i zwalniaj zdarzenia

 **Dysk** Zdarzenia we/wy dysku

 **Plik** Zdarzenia we/wy pliku

 **Hardfault (właśc.** Błędy twardej strony

 **Pagefault (stronicow)** Miękkie błędy strony

 **Sieć** Zdarzenia sieciowe

 **Rejestr** Zdarzenia dostępu do rejestru

 Należy zauważyć, że dostawca jądra można włączyć tylko. Nie można go wyłączyć, ani jego flagi mogą być modyfikowane, dopóki monitor zostanie zamknięty.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Gdy zdarzenia CLR ETW są włączone, dodatkowe dane uruchamiania są również zbierane w raporcie widok śledzenia. Aby wykluczyć zdarzenia uruchamiania z pojawiania się w raporcie, użyj następującego polecenia:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Jeśli zdarzenia uruchamiania nie zostaną wykluczone, ponieważ zdarzenia te nie są wymienione w pliku formatu obiektów zarządzanych (MOF), są one wyświetlane jako identyfikatory GUID w raporcie. Aby uzyskać więcej informacji, zobacz tę stronę w witrynie firmy Microsoft w sieci Web: [Przykładowy plik formatu obiektów zarządzanych (MOF).](https://msdn.microsoft.com/library/default.aspx)

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
