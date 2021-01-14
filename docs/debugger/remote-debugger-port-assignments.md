---
title: Przypisania portów zdalnego debugera | Microsoft Docs
description: Informacje o przypisywaniu portów zdalnego debugera programu Visual Studio na 32-bitowych systemach operacyjnych, 64-bitowych systemach operacyjnych i na platformie Azure. Dowiedz się więcej o porcie odnajdowania.
ms.custom: SEO-VS-2020
ms.date: 05/18/2018
ms.topic: reference
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40081f276dc9649cf448bf00e80d11fc80f58f47
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2021
ms.locfileid: "98204829"
---
# <a name="remote-debugger-port-assignments"></a>Przypisania portów debugera zdalnego
Zdalny debuger programu Visual Studio może działać jako aplikacja lub jako usługa w tle. Gdy działa jako aplikacja, używa portu, który jest domyślnie przypisany w następujący sposób:
::: moniker range=">=vs-2019"
- Visual Studio 2019:4024
::: moniker-end
- Visual Studio 2017:4022

- Visual Studio 2015:4020

- Visual Studio 2013:4018

- Visual Studio 2012:4016

Innymi słowy, liczba portów przypisanych do zdalnego debugera jest zwiększana o 2 dla każdej wersji. Jeśli chcesz, możesz ustawić inny numer portu. Wyjaśnimy, jak ustawić numery portów w dalszej części.

## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port zdalnego debugera w 32-bitowych systemach operacyjnych

::: moniker range=">=vs-2019"
 TCP 4024 (w Visual Studio 2019) jest portem głównym i jest wymagany dla wszystkich scenariuszy. Można to skonfigurować z poziomu wiersza polecenia lub okna zdalnego debugera.
::: moniker-end
::: moniker range="vs-2017"
 TCP 4022 (w Visual Studio 2017) jest portem głównym i jest wymagany dla wszystkich scenariuszy. Można to skonfigurować z poziomu wiersza polecenia lub okna zdalnego debugera.
::: moniker-end

 W oknie Debuger zdalny kliknij pozycję **narzędzia > opcje** i ustaw numer portu TCP/IP.

 W wierszu polecenia Uruchom zdalny debuger za pomocą opcji **/port** Switch: **msvsmon/port \<port number>**.

 Wszystkie przełączniki wiersza polecenia debugera zdalnego można znaleźć w pomocy zdalnego debugowania (naciśnij klawisz **F1** lub kliknij przycisk **Pomoc > użycie** w oknie Debuger zdalny).

## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port zdalnego debugera w 64-bitowych systemach operacyjnych
::: moniker range=">=vs-2019"
 Po uruchomieniu 64-bitowej wersji zdalnego debugera program domyślnie używa portu głównego (4024).  Jeśli debugujesz proces 32-bitowy, wersja 64-bitowa debugera zdalnego uruchamia 32-bitową wersję debugera zdalnego na porcie 4025 (numer portu głównego zwiększany o 1). Jeśli zostanie uruchomiony zdalny debuger 32-bitowy, używa 4024 i 4025 nie jest używany.
::: moniker-end
::: moniker range="vs-2017"
 Po uruchomieniu 64-bitowej wersji zdalnego debugera program domyślnie używa portu głównego (4022).  Jeśli debugujesz proces 32-bitowy, wersja 64-bitowa debugera zdalnego uruchamia 32-bitową wersję debugera zdalnego na porcie 4023 (numer portu głównego zwiększany o 1). Jeśli zostanie uruchomiony zdalny debuger 32-bitowy, używa 4022 i 4023 nie jest używany.
:::moniker-end

 Ten port można skonfigurować przy użyciu wiersza polecenia: **msvsmon/wow64port \<port number>**.

## <a name="the-discovery-port"></a>Port odnajdowania
 UDP 3702 służy do znajdowania uruchomionych wystąpień zdalnego debugera w sieci (na przykład okno dialogowe **Znajdowanie** w oknie dialogowym **Dołącz do procesu** ). Jest on używany tylko do odnajdywania maszyny z debugerem zdalnym, więc jest to opcjonalne, jeśli istnieje inny sposób znajomości nazwy komputera lub adresu IP komputera docelowego. Jest to standardowy port do odnajdowania, więc nie można skonfigurować numeru portu.

 Jeśli nie chcesz włączać odnajdowania, możesz uruchomić msvsmon z wiersza polecenia z wyłączonym odnajdywaniem:  **msvsmon/nodiscovery**.

## <a name="remote-debugger-ports-on-azure"></a>Porty zdalnego debugera na platformie Azure
 Zdalny debuger na platformie Azure używa następujących portów. Porty w usłudze w chmurze są mapowane na porty na poszczególnych maszynach wirtualnych. Wszystkie porty są TCP.

|Połączenie|Port w usłudze w chmurze|Port na maszynie wirtualnej|
|-|-|-|
|Microsoft. WindowsAzure. plugins. RemoteDebugger. Connector|30400|30398|
|Microsoft. WindowsAzure. plugins. RemoteDebugger. Forwarder|31400|31398|
|Microsoft. WindowsAzure. plugins. RemoteDebugger. Forwarderx86|31401|31399|
|Microsoft. WindowsAzure. plugins. RemoteDebugger. FileUpload|32400|32398|

## <a name="see-also"></a>Zobacz też
- [Debugowanie zdalne](../debugger/remote-debugging.md)
