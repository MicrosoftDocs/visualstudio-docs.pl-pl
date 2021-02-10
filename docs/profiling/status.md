---
title: Stan | Microsoft Docs
description: Dowiedz się, w jaki sposób opcja VSPerfCmd.exe status wyświetla informacje o stanie profilera i procesach, które są aktualnie profilowane.
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
author: mikejo5000
ms.author: mikejo
manager: jmartens
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 894afcbf8827fe0b5d5662a4c20e302f8224263f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960042"
---
# <a name="status"></a>Stan
Opcja *VSPerfCmd.exe* **stan** zawiera informacje dotyczące stanu profilera i procesów, które są aktualnie profilowane.

 Opcja **stanu** musi być jedyną opcją określoną w wierszu polecenia. Aby można było wyświetlić dowolny stan, profiler musi być zainicjowany przy użyciu opcji **Start** *VSPerfCmd.exe* .

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

 **Liczba uruchomień/zatrzymań** Podstawowa wewnętrzna liczba profilera do sterowania zbieraniem danych dla tego procesu. Liczba musi być równa 1, aby zbierać dane. Licznik uruchamiania/zatrzymywania może być manipulowany przez interfejsy API profilera i opcje VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn** i **ThreadOff**.

 **Liczba wstrzymań/wznowień** Pomocniczy wewnętrzny Profiler do sterowania zbieraniem danych dla tego procesu. Liczba musi być mniejsza lub równa zero, aby zebrać dane. Liczbę **wstrzymania/wznowienia** można manipulować tylko przez interfejsy API profilera.

 **Użytkownicy z prawami dostępu do monitorowania** Wyświetla listę nazw użytkowników, którzy mają dostęp do profilera. Dodatkowym użytkownikom można udzielić dostępu przy użyciu opcji **administrator** VSPerfCmd.exe

## <a name="see-also"></a>Zobacz też
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Profile aplikacji autonomicznych](../profiling/command-line-profiling-of-stand-alone-applications.md)
- [Profilowanie aplikacji sieci Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)
- [Usługi profilu](../profiling/command-line-profiling-of-services.md)
