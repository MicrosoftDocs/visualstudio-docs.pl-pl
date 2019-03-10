---
title: Przypisania portów debugera zdalnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 672d54b29e6de9302e88b1b95b4117783b8a0113
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699619"
---
# <a name="remote-debugger-port-assignments"></a>Przypisania portów debugera zdalnego
Zdalny debuger programu Visual Studio można uruchomić jako aplikację lub usługę w tle. Po jego uruchomieniu jako aplikacja wykorzystuje port, który jest domyślnie przypisane w następujący sposób:
::: moniker range=">=vs-2019"
- Visual Studio 2019: 4024
::: moniker-end
- Visual Studio 2017: 4022

- Visual Studio 2015: 4020

- Visual Studio 2013: 4018

- Visual Studio 2012: 4016

  Innymi słowy numer portu przypisany do zdalnego debugera jest zwiększany przez 2 dla każdej wersji. Możesz ustawić inny numer portu, np. Firma Microsoft wyjaśniono, jak ustawić numery portów w dalszej części tego tematu.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port debugera zdalnego w systemach operacyjnych 32-bitowy

::: moniker range=">=vs-2019"
 4024 TCP (w Visual Studio 2019 r.) jest port główny i jest wymagany w przypadku wszystkich scenariuszy. Można to skonfigurować, z poziomu wiersza polecenia lub okna debugera zdalnego.
::: moniker-end
::: moniker range="vs-2017"
 4022 TCP (w programie Visual Studio 2017) jest port główny i jest wymagany w przypadku wszystkich scenariuszy. Można to skonfigurować, z poziomu wiersza polecenia lub okna debugera zdalnego.
::: moniker-end

 Kliknij w oknie debugera zdalnego **Narzędzia > Opcje**i Ustaw numer portu TCP/IP.

 W wierszu polecenia, uruchom zdalny debuger za pomocą **/port** przełącznika: **msvsmon/port \<numer portu >**.

 Można znaleźć zdalnego debugera przełączniki wiersza polecenia zdalnego debugowania pomocy (naciśnij klawisz **F1** lub kliknij przycisk **Pomoc > użycie** w oknie debugera zdalnego).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port debugera zdalnego na 64-bitowych systemach operacyjnych
::: moniker range=">=vs-2019"
 Po uruchomieniu 64-bitowej wersji zdalnego debugera, używa ona głównym portu (4024) domyślnie.  Jeśli debugujesz proces 32-bitowy, 64-bitowej wersji zdalnego debugera uruchamia 32-bitowej wersji zdalnego debugera na porcie 4025 (numer portu głównego zwiększane o 1). Jeśli uruchamiasz 32-bitowy zdalny debuger, używa ona 4024 i 4025 nie jest używany.
::: moniker-end
::: moniker range="vs-2017"
 Po uruchomieniu 64-bitowej wersji zdalnego debugera, używa ona głównym portu (4022) domyślnie.  Jeśli debugujesz proces 32-bitowy, 64-bitowej wersji zdalnego debugera uruchamia 32-bitowej wersji zdalnego debugera na port 4023 (numer portu głównego zwiększane o 1). Jeśli uruchamiasz 32-bitowy zdalny debuger, używa ona 4022 i 4023 nie jest używany.
:::moniker-end

 Ten port jest można skonfigurować z poziomu wiersza polecenia: **Polecenie Msvsmon/wow64port \<numer portu >**.

## <a name="the-discovery-port"></a>Port odnajdywania
 UDP 3702 służy do znajdowania uruchomionych wystąpień zdalnego debugera w sieci (na przykład **znaleźć** okna dialogowego w **dołączyć do procesu** okna dialogowego). Jest on używany tylko w przypadku odnajdywania maszyny z systemem zdalnego debugera, dzięki czemu jest to opcjonalne, jeśli masz inny sposób określenia nazwy komputera lub adres IP komputera docelowego. Jest to port standardowy dla odnajdywania, aby numer portu nie można skonfigurować.

 Jeśli chcesz włączyć odnajdywanie, można uruchomić polecenia msvsmon z wiersza polecenia z odnajdywaniem wyłączone:  **Polecenie Msvsmon /nodiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Portów debugera zdalnego na platformie Azure
 Następujące porty są używane przez debuger zdalny na platformie Azure. Porty w usłudze w chmurze są mapowane na porty na poszczególnych maszyn wirtualnych. Wszystkie porty są TCP.

|Połączenie|Port w usłudze w chmurze|Port na maszynie Wirtualnej|
|-|-|-|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarderx86|31401|31399|
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)