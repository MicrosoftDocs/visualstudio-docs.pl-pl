---
title: GC (VSPerfCmd) | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: e14fef1cfdc2dfc5f0d737ac09a08d90ab1de309
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74776982"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
Opcja **GC** umożliwia zbieranie danych alokacji pamięci .NET Framework i okresu istnienia obiektu. Opcja **GC** może być używana tylko z metodą profilowania próbkowania i tylko z opcją **Uruchom.**

 Podczas korzystania z opcji **GC,** VSPerfClrEnv **/sampleon** polecenie nie jest wymagane.

 Jeśli nie określono żadnych parametrów lub jeśli określono parametr **Alokacja,** zbierane są tylko dane alokacji pamięci programu .NET Framework. Jeśli określono parametr **Lifetime,** zbierane są zarówno alokacje pamięci .NET Framework, jak i dane okresu istnienia obiektu .NET Framework.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametry
 **Alokacja** Domyślny. Zbiera dane alokacji pamięci programu .NET Framework.

 **Okres istnienia** Zbiera dane alokacji pamięci programu .NET Framework i dane okresu istnienia obiektu programu .NET Framework.

## <a name="required-options"></a>Wymagane opcje
 Opcji **GC** można używać tylko z opcją **Uruchom.**

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna profilowanie za pomocą metody próbkowania.

## <a name="example"></a>Przykład
 Poniższy przykład uruchamia aplikację i zbiera dane alokacji pamięci .NET Framework.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
