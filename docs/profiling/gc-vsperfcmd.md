---
title: GC (VSPerfCmd) | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 50b2e269ec292aaf37b8d0c707fa27ff8268a1f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62969711"
---
# <a name="gc-vsperfcmd"></a>GC (VSPerfCmd)
**GC** opcja umożliwia zbieranie danych pamięci .NET Framework alokacji i obiekt okresu istnienia. **GC** opcji należy używać tylko z metoda profilowania próbkowanie i tylko **Uruchom** opcji.

 Kiedy używasz **GC** opcji polecenia VSPerfClrEnv **/sampleon** polecenia nie jest wymagana.

 Jeśli nie określono żadnych parametrów lub **alokacji** parametr jest określony, są zbierane tylko .NET Framework dane alokacji pamięci. Jeśli **okres istnienia** parametr jest określony, alokacji pamięci .NET Framework i .NET Framework obiektu zbieranych danych o okresie istnienia.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]
```

#### <a name="parameters"></a>Parametry
 **Alokacja** domyślne. Zbiera dane alokacji pamięci .NET Framework.

 **Okres istnienia** zbiera dane alokacji pamięci .NET Framework i .NET Framework danych o okresie istnienia obiektu.

## <a name="required-options"></a>Wymagane opcje
 **GC** opcja może być używana tylko z **Uruchom** opcji.

 **Uruchom:** `AppName` Uruchamia określoną aplikację i rozpoczyna się profilowanie przy użyciu metody pobierania próbek.

## <a name="example"></a>Przykład
 Poniższy przykład spowoduje uruchomienie aplikacji i zbiera dane alokacji pamięci .NET Framework.

```cmd
VSPerfCmd.exe /Launch:TestApp.exe /gc
```

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)