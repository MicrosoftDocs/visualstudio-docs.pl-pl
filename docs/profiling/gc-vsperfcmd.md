---
title: GC (VSPerfCmd) | Microsoft Docs
description: Przejrzyj opcję GC w narzędziu VSPerfCmd.exe. Opcja GC umożliwia zbieranie danych .NET Framework alokacji pamięci i okresu istnienia obiektu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bc1c215359f6b891239cd7b39f33d412bbf40dd5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99907347"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
Opcja **GC** umożliwia zbieranie danych .NET Framework alokacji pamięci i okresu istnienia obiektu. Opcji **GC** można używać tylko z metodą profilowania próbkowania i tylko z opcją **uruchomienia** .

 W przypadku korzystania z opcji **GC** polecenie VSPerfCLREnv **/sampleon** nie jest wymagane.

 Jeśli nie określono parametrów lub jeśli określono parametr **alokacji** , zbierane są tylko .NET Framework dane alokacji pamięci. Jeśli określono parametr **okresu istnienia** , zostaną zebrane dane dotyczące alokacji pamięci .NET Framework i .NET Framework okresu istnienia obiektu.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametry
 **Alokacja** Wartooć. Zbiera .NET Framework dane alokacji pamięci.

 **Okres istnienia** Zbiera .NET Framework dane alokacji pamięci i .NET Framework dane okresu istnienia obiektu.

## <a name="required-options"></a>Wymagane opcje
 Opcji **GC** można używać tylko z opcją **uruchamiania** .

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie przy użyciu metody próbkowania.

## <a name="example"></a>Przykład
 Poniższy przykład uruchamia aplikację i zbiera .NET Framework dane alokacji pamięci.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
