---
title: VSPerf | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 00f8543c2fdb204a165292844cb5bf5b925c63e8
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330488"
---
# <a name="vsperf"></a>VSPerf
Użyj narzędzia wiersza polecenia **VsPerf** , aby:

1. Profilowanie aplikacji platformy UWP z poziomu wiersza polecenia, gdy program Visual Studio nie jest zainstalowany na urządzeniu.

2. Profilowanie aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012 przy użyciu metody profilowania próbkowania.

   Aby uzyskać więcej informacji na temat opcji profilowania, zobacz [Narzędzia do oceny wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="uwp-apps-only"></a>Tylko aplikacje platformy UWP
 Te opcje mają zastosowanie tylko do aplikacji platformy UWP.

|||
|-|-|
|**/App: {nazwa_aplikacji}**|Uruchamia Profiler i czeka na uruchomienie określonej aplikacji z menu Start.<br /><br /> Uruchom, `vsperf /listapps` Aby wyświetlić nazwę aplikacji i PackageFullName zainstalowanych aplikacji.|
|**/Package: {PackageFullName}**|Uruchamia Profiler i czeka na uruchomienie określonej aplikacji z menu Start.<br /><br /> Uruchom, `vsperf /listapps` Aby wyświetlić nazwę aplikacji i PackageFullName zainstalowanych aplikacji.|
|**/js**|Wymagane do profilowania aplikacji JavaScript.<br /><br /> Zbieranie danych dotyczących wydajności z aplikacji JavaScript.<br /><br /> Używaj tylko z/Package lub/Attach.|
|**/noclr**|Opcjonalny. Nie Zbieraj danych CLR.<br /><br /> Używaj tylko z/Package lub/Attach.<br /><br /> Optymalizacja nie zostanie rozpoznana przez żadne zarządzane symbole.|
|**/listapps**|Wyświetl listę zainstalowanych nazw aplikacji i PackageFullNames.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Aplikacje klasyczne systemu Windows 8 i aplikacje systemu Windows Server 2012
 Te opcje nie działają w aplikacjach platformy UWP.

|||
|-|-|
|**Przełącznik/Launch: {plik wykonywalny}**|Rozpoczyna i rozpoczyna profilowanie określonego pliku wykonywalnego.|
|**/args: {ExecutableArguments}**|Określa argumenty wiersza polecenia do przekazania elementu docelowego **przełącznik/Launch** .|
|**/Console**|Uruchamia element docelowy **przełącznik/Launch** w nowym oknie poleceń.|

## <a name="all-applications"></a>Wszystkie aplikacje
 Ta opcja ma zastosowanie do dowolnej aplikacji systemu Windows 8 lub Windows Server 2012.

|||
|-|-|
|**/Attach: {PID&#124;ProcessName} [, PID&#124;ProcessName]...**|Zbiera dane z określonych procesów.<br /><br /> Użyj Menedżera zadań, aby wyświetlić identyfikator procesu (PID) i nazwy procesów uruchomionych aplikacji.|
|**/File: {ReportName}**|Opcjonalny. Określa plik wyjściowy (Zastępuje istniejący plik).<br /><br /> Używaj tylko z/Package lub/Attach.|
|**/Pause**|Wstrzymywanie zbierania danych.|
|**/Resume**|Wznów zbieranie danych.|
|**/Stop**|Zatrzymaj zbieranie danych i kończenie procesów docelowych.|
|**/detach**|Zatrzymaj zbieranie danych, ale pozwól, aby procesy docelowe nadal działały.|
|**/status**|Pokaż stan profilera.|

## <a name="see-also"></a>Zobacz też
- [Narzędzia do oceny wydajności w aplikacjach Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
