---
title: Przypisania portów zdalnego debugera | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2628d8929a0d2b6fd3561f88c81cfaa3b62564f0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85542106"
---
# <a name="remote-debugger-port-assignments"></a>Przypisania portów debugera zdalnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zdalny debuger programu Visual Studio może działać jako aplikacja lub jako usługa w tle. Gdy działa jako aplikacja, używa portu, który jest domyślnie przypisany w następujący sposób:  
  
- Visual Studio 2015:4020  
  
- Visual Studio 2013:4018  
  
- Visual Studio 2012:4016  
  
  Innymi słowy, liczba portów przypisanych do zdalnego debugera jest zwiększana o 2 dla każdej wersji. Możesz ustawić inny numer portu. Wyjaśnimy, jak ustawić numery portów w dalszej części.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port zdalnego debugera w 32-bitowych systemach operacyjnych  
 TCP 4020 (w Visual Studio 2015) jest portem głównym i jest wymagany dla wszystkich scenariuszy. Można to skonfigurować z poziomu wiersza polecenia lub okna zdalnego debugera.  
  
 W oknie Debuger zdalny kliknij pozycję **Narzędzia/Opcje**i ustaw numer portu TCP/IP.  
  
 W wierszu polecenia Uruchom zdalny debuger za pomocą opcji **/port** Switch: **msvsmon/port \<port number> **.  
  
 Wszystkie przełączniki wiersza polecenia debugera zdalnego można znaleźć w pomocy zdalnego debugowania (naciśnij klawisz **F1** lub kliknij przycisk **Pomoc/użycie** w oknie Debuger zdalny).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port zdalnego debugera w 64-bitowych systemach operacyjnych  
 Po uruchomieniu 64-bitowej wersji zdalnego debugera program domyślnie używa portu 4020.  Jeśli debugujesz proces 32-bitowy, wersja 64-bitowa debugera zdalnego uruchamia 32-bitową wersję debugera zdalnego na porcie 4021. Jeśli zostanie uruchomiony zdalny debuger 32-bitowy, używa 4020 i 4021 nie jest używany.  
  
 Ten port można skonfigurować przy użyciu wiersza polecenia: **msvsmon/wow64port \<port number> **.  
  
## <a name="the-discovery-port"></a>Port odnajdowania  
 UDP 3702 służy do znajdowania uruchomionych wystąpień zdalnego debugera w sieci (na przykład okno dialogowe **Znajdowanie** w oknie dialogowym **Dołącz do procesu** ). Jest on używany tylko do odnajdywania maszyny z debugerem zdalnym, więc jest to opcjonalne, jeśli istnieje inny sposób znajomości nazwy komputera lub adresu IP komputera docelowego. Jest to standardowy port do odnajdowania, więc nie można skonfigurować numeru portu.  
  
 Jeśli nie chcesz włączać odnajdowania, możesz uruchomić msvsmon z wiersza polecenia z wyłączonym odnajdywaniem:  **msvsmon/nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Porty zdalnego debugera na platformie Azure  
 Zdalny debuger na platformie Azure używa następujących portów. Porty w usłudze w chmurze są mapowane na porty na poszczególnych maszynach wirtualnych. Wszystkie porty są TCP.  

|**Połączenie**|**Port w usłudze w chmurze**|**Port na maszynie wirtualnej**|  
|-|-|-|
|Microsoft. WindowsAzure. plugins. RemoteDebugger. Connector|30400|30398|  
|Microsoft. WindowsAzure. plugins. RemoteDebugger. Forwarder|31400|31398|  
|Microsoft. WindowsAzure. plugins. RemoteDebugger. FileUpload|32400|32398|  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)
