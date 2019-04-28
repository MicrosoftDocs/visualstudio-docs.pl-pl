---
title: Stan | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25f452dcb473abf87d8992f36f5326973937e85e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62967875"
---
# <a name="status"></a>Stan
*VSPerfCmd.exe* **stan** opcji wyświetla informacje o stanie programu profilującego i wszystkie procesy, które są obecnie poddawany profilowaniu.

 **Stan** opcja musi być jedyną opcją, określone w wierszu polecenia. Program profilujący musi zostać zainicjowany z *VSPerfCmd.exe* **Start** opcji, przed wyświetleniem dowolny stan.

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="remarks"></a>Uwagi
 **Stan** opcja wyświetla następujące informacje o stanie programu Profiler.

 **Nazwa pliku wyjściowego** ścieżkę i nazwę bieżącego pliku danych profilera.

 **Tryb kolekcji** przykład lub śledzenia

 **Maksymalna liczba procesów** maksymalną liczbę procesów, które mogą być profilowane, w tym samym czasie i Liczba obecnie aktywnych procesów.

 **Maksymalna liczba wątków** maksymalną liczbę wątków, które mogą być profilowane, w tym samym czasie.

 **Liczba buforów** liczba buforów pamięci przeznaczone do zapisywania danych profilowania.

 **Rozmiar buforów** rozmiar w bajtach bufora pamięci.

 **Stan** opcja wyświetla następujące informacje o stanie dla każdego procesu, który jest obecnie poddawany profilowaniu.

 **Proces** nazwę PROFILOWANEGO procesu.

 **Identyfikator procesu** systemowy identyfikator procesu.

 **Liczba wątków** liczbę wątków w trakcie wykonywania.

 **Liczba uruchomień/zatrzymań** głównej wewnętrzny profilera za pomocą licznika kontrolować zbieranie danych dla tego procesu. Liczba musi być równa jeden do zbierania danych. Liczba uruchomień/zatrzymań może być manipulowane przez profiler interfejsów API i opcji VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**, i **ThreadOff**.

 **Liczba wstrzymań/wznowień** dodatkowej wewnętrzny profilera za pomocą licznika kontrolować zbieranie danych dla tego procesu. Liczba musi być mniejsza lub równa zero do zbierania danych. **Wstrzymań/wznowień** liczba może używać tylko interfejsów API profilera.

 **Użytkownicy z prawami dostępu w celu monitorowania** Wyświetla nazwy użytkowników, którzy mają dostęp do programu profilującego. Dodatkowym użytkownikom można udzielić dostępu przy użyciu VSPerfCmd.exe **administratora** opcji

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilowania](../profiling/command-line-profiling-of-services.md)