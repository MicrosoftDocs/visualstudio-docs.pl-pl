---
title: CrossSession | Microsoft Docs
description: Dowiedz się, jak używać opcji CrossSession VSPerfCmd.exe, aby Profiler zbierał dane z dowolnych sesji konsoli. Należy również określić opcję uruchamiania.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b9fcb9c3-7903-478c-9b7c-dbd94092fcba
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a52acb80bac511706086c56074eb5bfe450b7674
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955908"
---
# <a name="crosssession"></a>CrossSession
Opcja *VSPerfCmd.exe* **CrossSession** umożliwia programowi Profiler zbieranie danych z dowolnych sesji konsoli. Opcja **CrossSession** musi być używana z opcją **Start** .

 Można użyć skrótu **CS** zamiast **CrossSession**.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Start:Method /CrossSession [Options]
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="valid-options"></a>Prawidłowe opcje
 Aby włączyć profilowanie w innej sesji, należy określić opcję **CrossSession** z opcją **Start** . **CrossSession** należy również określić we wszystkich kolejnych poleceniach **dołączania** i **odłączania** VSPerfCmd.

 **Rozpocznij:** `Method` Opcja **Start** inicjuje profiler do określonej metody profilowania.

 **Dołącz:** _Identyfikator PID_[**,**_PID_] rozpoczyna profilowanie określonych procesów.

 **Odłączenie**[**:**_PID_[,_PID_]] powoduje zatrzymanie profilowania określonych procesów.

## <a name="example"></a>Przykład
 W tym przykładzie opcja **CrossSession** jest używana w celu dołączenia do aplikacji, która została uruchomiona w innej sesji konsoli.

```cmd
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp /CrossSession
VSPerfCmd.exe /Attach:12345 /CS
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
