---
title: Stan | Microsoft Docs
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
ms.sourcegitcommit: 00b71889bd72b6a566586885bdb982cfe807cf54
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74778248"
---
# <a name="status"></a>Stan
Opcja **stanu** *VSPerfCmd. exe* wyświetla informacje na temat stanu profilera i procesów, które są aktualnie profilowane.

 Opcja **stanu** musi być jedyną opcją określoną w wierszu polecenia. Aby można było wyświetlić dowolny stan, profiler musi być zainicjowany przy użyciu opcji **Start** *VSPerfCmd. exe* .

## <a name="syntax"></a>Składnia

```cmd
VSPerfCmd.exe /Status
```

#### <a name="parameters"></a>Parametry
 Brak

## <a name="remarks"></a>Uwagi
 Opcja **stan** wyświetla następujące informacje o stanie profilera.

 **Nazwa pliku wyjściowego** Ścieżka i nazwa pliku bieżącego pliku danych profilera.

 **Tryb kolekcji** PRÓBKowanie lub śledzenie

 **Maksymalna liczba procesów** Maksymalna liczba procesów, które mogą być profilowane jednocześnie, oraz liczba aktualnie aktywnych procesów.

 **Maksymalna liczba wątków** Maksymalna liczba wątków, które mogą być profilowane jednocześnie.

 **Liczba buforów** Liczba buforów pamięci, które są przeznaczone do zapisywania danych profilowania.

 **Rozmiar buforów** Rozmiar w bajtach bufora pamięci.

 Opcja **stan** wyświetla następujące informacje o stanie dla każdego procesu, który jest obecnie profilowany.

 **Proces** Nazwa profilowanego procesu.

 **Identyfikator procesu** Identyfikator systemowy procesu.

 **Liczba wątków** Liczba aktualnie wykonywanych wątków.

 **Liczba uruchomień/zatrzymań** Podstawowa wewnętrzna liczba profilera do sterowania zbieraniem danych dla tego procesu. Liczba musi być równa 1, aby zbierać dane. Licznik uruchamiania/zatrzymywania może być manipulowany przez interfejsy API profilera i opcje VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**i **ThreadOff**.

 **Liczba wstrzymań/wznowień** Pomocniczy wewnętrzny Profiler do sterowania zbieraniem danych dla tego procesu. Liczba musi być mniejsza lub równa zero, aby zebrać dane. Liczbę **wstrzymania/wznowienia** można manipulować tylko przez interfejsy API profilera.

 **Użytkownicy z prawami dostępu do monitorowania** Wyświetla listę nazw użytkowników, którzy mają dostęp do profilera. Dodatkowym użytkownikom można udzielić dostępu przy użyciu opcji **administratora** VSPerfCmd. exe

## <a name="see-also"></a>Zobacz także
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
