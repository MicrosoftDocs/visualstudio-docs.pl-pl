---
title: VSPerf | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b5854e62-279e-4850-bfeb-0c6ef82f4805
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 051c983920ddc80909d721e569c5efb5ecd33a7c
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "74779938"
---
# <a name="vsperf"></a>VSPerf
Użyj narzędzia wiersza polecenia **VsPerf,** aby:

1. Aplikacje platformy uniwersalnej systemu Windows profilu z wiersza polecenia, gdy program Visual Studio nie jest zainstalowany na urządzeniu.

2. Profilowanie aplikacji klasycznych systemu Windows 8 i aplikacji systemu Windows Server 2012 przy użyciu metody profilowania próbkowania.

   Aby uzyskać więcej informacji na temat opcji profilowania, zobacz [Narzędzia wydajności w aplikacjach systemu Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md).

## <a name="uwp-apps-only"></a>Tylko aplikacje platformy uniwersalnej systemu Windows
 Te opcje dotyczą tylko aplikacji platformy uniwersalnej systemu Windows.

|||
|-|-|
|**/app:{AppName}**|Uruchamia profiler i czeka na określoną aplikację, która ma zostać uruchomiona z menu Start.<br /><br /> Uruchom, `vsperf /listapps` aby wyświetlić nazwę aplikacji i PackageFullName zainstalowanych aplikacji.|
|**/package:{PackageFullName}**|Uruchamia profiler i czeka na określoną aplikację, która ma zostać uruchomiona z menu Start.<br /><br /> Uruchom, `vsperf /listapps` aby wyświetlić nazwę aplikacji i PackageFullName zainstalowanych aplikacji.|
|**/js**|Wymagane do profilowania aplikacji JavaScript.<br /><br /> Zbieranie danych dotyczących wydajności z aplikacji JavaScript.<br /><br /> Używaj tylko z /package lub /attach.|
|**/noclr**|Element opcjonalny. Nie zbieraj danych CLR.<br /><br /> Używaj tylko z /package lub /attach.<br /><br /> Optymalizacja, żadne zarządzane symbole nie zostaną rozwiązane.|
|**/listapps**|Lista zainstalowanych nazw aplikacji i PackageFullNames.|

## <a name="windows-8-desktop-applications-and-windows-server-2012-applications-only"></a>Tylko aplikacje klasyczne systemu Windows 8 i windows server 2012
 Te opcje nie działają w aplikacjach platformy uniwersalnej systemu Windows.

|||
|-|-|
|**/launch:{Plik wykonywalny}**|Rozpoczyna i rozpoczyna profilowanie określonego pliku wykonywalnego.|
|**/args:{Argumenty przed wykonywalne}**|Określa argumenty wiersza polecenia, aby przekazać obiekt docelowy **/launch.**|
|**/konsola**|Uruchamia obiekt docelowy **/launch** w nowym oknie polecenia.|

## <a name="all-applications"></a>Wszystkie aplikacje
 Te te zastosowania opcję dotyczą dowolnej aplikacji systemu Windows 8 lub Windows Server 2012.

|||
|-|-|
|**/attach:{PID&#124;ProcessName}[,PID&#124;ProcessName]...**|Zbiera dane z określonych procesów.<br /><br /> Menedżer zadań służy do wyświetlania identyfikatora procesu (PID) i nazw procesów uruchomionych aplikacji.|
|**/file:{Nazwa raportu}**|Element opcjonalny. Określa plik wyjściowy (zastępuje istniejący plik).<br /><br /> Używaj tylko z /package lub /attach.|
|**/pauza**|Wstrzymaj zbieranie danych.|
|**/życiorys**|Wznów zbieranie danych.|
|**/stop**|Zatrzymaj zbieranie danych i zakończ procesy docelowe.|
|**/odłączyć**|Zatrzymaj zbieranie danych, ale pozwól procesom docelowym nadal działać.|
|**/status**|Pokaż stan profilera.|

## <a name="see-also"></a>Zobacz też
- [Narzędzia do oceny wydajności w aplikacjach Windows 8 i Windows Server 2012](../profiling/performance-tools-on-windows-8-and-windows-server-2012-applications.md)
- [Profil z wiersza polecenia](../profiling/using-the-profiling-tools-from-the-command-line.md)
