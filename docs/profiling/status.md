---
title: Status | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: bf5e0fdf478e067f61b1d0e259cb1624380e4f02
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778248"
---
# <a name="status"></a>Stan
Opcja **Status** *programu VSPerfCmd.exe* wyświetla informacje o stanie profilera i wszystkich procesach, które są obecnie profilowane.

 Opcja **Stan** musi być jedyną opcją określoną w wierszu polecenia. Profiler musi zostać zainicjowany za pomocą opcji *VSPerfCmd.exe* **Start,** zanim będzie można wyświetlić dowolny stan.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="remarks"></a>Uwagi
 Opcja **Stan** wyświetla następujące informacje o stanie dla profilera.

 **Nazwa pliku wyjściowego** Ścieżka i nazwa pliku bieżącego pliku danych profilera.

 **Tryb zbierania** PRÓBKA lub ŚLEDZENIE

 **Maksymalna liczba procesów** Maksymalna liczba procesów, które mogą być profilowane w tym samym czasie i liczba aktualnie aktywnych procesów.

 **Maksymalna liczba wątków** Maksymalna liczba wątków, które mogą być profilowane w tym samym czasie.

 **Liczba buforów** Liczba buforów pamięci przeznaczonych do zapisywania danych profilowania.

 **Rozmiar buforów** Rozmiar w bajtach buforu pamięci.

 Opcja **Stan** wyświetla następujące informacje o stanie dla każdego procesu, który jest obecnie profilowany.

 **Proces** Nazwa procesu profilowanego.

 **Identyfikator procesu** Identyfikator systemowy procesu.

 **Num wątki** Liczba aktualnie wykonywanych wątków.

 **Liczba start/stop** Podstawowa wewnętrzna liczba profilera do kontrolowania zbierania danych dla tego procesu. Liczba musi być równa jednej do zbierania danych. Licznik start/stop może być manipulowany przez interfejsy API profilera i opcje VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**i **ThreadOff**.

 **Liczba wstrzymań/wznawiania** Pomocnicza wewnętrzna liczba profilerów do kontrolowania zbierania danych dla tego procesu. Liczba musi być mniejsza lub równa zero do zbierania danych. Liczba **wstrzymania/wznawiania** może być manipulowana tylko przez interfejsy API profilera.

 **Użytkownicy z uprawnieniami dostępu do monitorowania** Wyświetla listę nazw użytkowników, którzy mają dostęp do profilera. Dodatkowi użytkownicy mogą uzyskać dostęp za pomocą **opcji** administratora programu VSPerfCmd.exe

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Aplikacje autonomiczne profilu](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profil ASP.NET aplikacji internetowych](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)
