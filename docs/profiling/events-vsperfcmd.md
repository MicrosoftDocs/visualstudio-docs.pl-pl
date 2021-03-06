---
title: Zdarzenia (VSPerfCmd) | Microsoft Docs
description: Kontrolowanie rejestrowania śledzenia zdarzeń systemu Windows (ETW) przy użyciu opcji zdarzenia w narzędziu wiersza polecenia VSPerfCmd.exe. Przejrzyj parametry składni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: eb139327-4783-4f2a-874c-efad377a7be4
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1ec92cae275d9f73f24f983905bc0013950e9d37
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99899563"
---
# <a name="events-vsperfcmd"></a>Zdarzenia (VSPerfCmd)
Opcja  **zdarzenia** VSPerfCmd.exesteruje rejestrowaniem śledzenia zdarzeń systemu Windows (ETW). Dane ETW są zapisywane w pliku ETL, który jest oddzielony od pliku danych profilera. Dane można wyświetlić w raporcie za pomocą polecenia [VSPerfReport](../profiling/vsperfreport.md) /Summary: ETW.

 Opcję **zdarzenia** można wywołać w dowolnym momencie przed wywołaniem polecenia VSPerfCmd **Shutdown** w celu zatrzymania profilowania.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /events {On|Off} {Guid|ProviderName} [,Flags[,Level]
```

#### <a name="parameters"></a>Parametry
 **Na**&#124;**off startuje** lub kończy zbieranie danych zdarzeń.

 `Guid` Identyfikator GUID kontrolki dostawcy.

 `ProviderName` Nazwa dostawcy, który jest zarejestrowany w Instrumentacja zarządzania Windows (WMI).

 `Flags` Wartość "0x" — wstępnie ustalonych flag szesnastkowych, które są definiowane przez dostawcę zdarzeń.

 `Level` Określa ilość zbieranych danych. `Level` jest definiowana przez dostawcę zdarzeń.

 Opcja **Events** umożliwia zrozumienie następujących słów kluczowych jądra jako nazw dostawców:

 **Proces** Zdarzenia procesu

 **Wątek** Zdarzenia wątku

 **Obraz** Ładowanie i zwalnianie obrazów

 **Dysk** Zdarzenia we/wy dysku

 **Plik** Zdarzenia we/wy pliku

 **Hardfault** Błędy stron twardych

 **Pagefault** Słabe błędy stron

 **Sieć** Zdarzenia sieciowe

 **Rejestr** Zdarzenia dostępu do rejestru

 Należy pamiętać, że dostawca jądra może być tylko włączony. Nie można go wyłączyć ani zmienić jego flag, dopóki monitor nie zostanie zamknięty.

## <a name="remarks"></a>Uwagi

> [!NOTE]
> Po włączeniu zdarzeń ETW CLR dodatkowe dane uruchamiania są również zbierane w raporcie widoku śledzenia. Aby wykluczyć zdarzenia uruchamiania z wyświetlania w raporcie, użyj następującego polecenia:

```cmd
C:\<path>VSPerfCmd -events on, \".NET Common Language Runtime\", 0x7fffffff, 5
```

> [!IMPORTANT]
> Jeśli zdarzenia uruchamiania nie zostaną wykluczone, ponieważ te zdarzenia nie są wymienione w pliku Managed Object Format (MOF), są one wyświetlane jako identyfikatory GUID w raporcie. Aby uzyskać więcej informacji, zobacz Tę stronę w witrynie sieci Web firmy Microsoft: [przykładowy plik Managed Object Format (MOF)](https://msdn.microsoft.com/library/default.aspx).

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
