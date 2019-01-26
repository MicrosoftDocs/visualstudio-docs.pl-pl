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
ms.openlocfilehash: 49c06b6820de1ef921cd9c10a2a7d0a9c8b46fb9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070529"
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
  
 **Nazwa pliku wyjściowego**  
 Ścieżka i nazwa bieżącego pliku danych profilera.  
  
 **Tryb kolekcji**  
 PRZYKŁAD lub śledzenia  
  
 **Maksymalna liczba procesów**  
 Maksymalna liczba procesów, które mogą być profilowane, w tym samym czasie i Liczba obecnie aktywnych procesów.  
  
 **Maksymalna liczba wątków**  
 Maksymalna liczba wątków, które mogą być profilowane, w tym samym czasie.  
  
 **Liczba buforów**  
 Liczba buforów pamięci przeznaczone do zapisywania danych profilowania.  
  
 **Rozmiar buforów**  
 Rozmiar w bajtach bufora pamięci.  
  
 **Stan** opcja wyświetla następujące informacje o stanie dla każdego procesu, który jest obecnie poddawany profilowaniu.  
  
 **Proces**  
 Nazwa PROFILOWANEGO procesu.  
  
 **Identyfikator procesu**  
 Identyfikator systemu procesu.  
  
 **Liczba wątków**  
 Liczba wątków w trakcie wykonywania.  
  
 **Liczba uruchomień/zatrzymań**  
 Licznik podstawowy wewnętrzny profilera można kontrolować zbieranie danych dla tego procesu. Liczba musi być równa jeden do zbierania danych. Liczba uruchomień/zatrzymań może być manipulowane przez profiler interfejsów API i opcji VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**, i **ThreadOff**.  
  
 **Liczba wstrzymań/wznowień**  
 Liczba pomocniczych wewnętrzny profilera można kontrolować zbieranie danych dla tego procesu. Liczba musi być mniejsza lub równa zero do zbierania danych. **Wstrzymań/wznowień** liczba może używać tylko interfejsów API profilera.  
  
 **Użytkownicy z prawami dostępu w celu monitorowania**  
 Wyświetla listę nazw użytkowników, którzy mają dostęp do programu profilującego. Dodatkowym użytkownikom można udzielić dostępu przy użyciu VSPerfCmd.exe **administratora** opcji  
  
## <a name="see-also"></a>Zobacz także  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profil aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Aplikacje sieci web ASP.NET profilu](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Usługi profilowania](../profiling/command-line-profiling-of-services.md)