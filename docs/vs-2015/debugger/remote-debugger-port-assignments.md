---
title: Przypisania portów debugera zdalnego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 238bb4ec-bb00-4c2b-986e-18ac278f3959
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47a2b212ce3e98588a5dcf6ee75a479b01b5b302
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51817861"
---
# <a name="remote-debugger-port-assignments"></a>Przypisania portów debugera zdalnego
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zdalny debuger programu Visual Studio można uruchomić jako aplikację lub usługę w tle. Po jego uruchomieniu jako aplikacja wykorzystuje port, który jest domyślnie przypisane w następujący sposób:  
  
- Program Visual Studio 2015:4020  
  
- Program Visual Studio 2013:4018  
  
- Program Visual Studio 2012:4016  
  
  Innymi słowy numer portu przypisany do zdalnego debugera jest zwiększany przez 2 dla każdej wersji. Możesz ustawić inny numer portu, np. Firma Microsoft wyjaśniono, jak ustawić numery portów w dalszej części tego tematu.  
  
## <a name="the-remote-debugger-port-on-32-bit-operating-systems"></a>Port debugera zdalnego w systemach operacyjnych 32-bitowy  
 4020 TCP (w programie Visual Studio 2015) jest port główny i jest wymagany w przypadku wszystkich scenariuszy. Można to skonfigurować, z poziomu wiersza polecenia lub okna debugera zdalnego.  
  
 Kliknij w oknie debugera zdalnego **narzędzia / Opcje**i Ustaw numer portu TCP/IP.  
  
 W wierszu polecenia, uruchom zdalny debuger za pomocą **/port** przełącznika: **msvsmon/port \<numer portu >**.  
  
 Można znaleźć zdalnego debugera przełączniki wiersza polecenia zdalnego debugowania pomocy (naciśnij klawisz **F1** lub kliknij przycisk **pomocy / użycia** w oknie debugera zdalnego).  
  
## <a name="the-remote-debugger-port-on-64-bit-operating-systems"></a>Port debugera zdalnego na 64-bitowych systemach operacyjnych  
 Po uruchomieniu 64-bitowej wersji zdalnego debugera, używa portu 4020 domyślnie.  Jeśli debugujesz proces 32-bitowy, 64-bitowej wersji zdalnego debugera uruchamia 32-bitowej wersji zdalnego debugera na porcie 4021. Jeśli uruchamiasz 32-bitowy zdalny debuger, używa ona 4020 i 4021 nie jest używany.  
  
 Ten port jest konfigurowane z poziomu wiersza polecenia: **Msvsmon/wow64port \<numer portu >**.  
  
## <a name="the-discovery-port"></a>Port odnajdywania  
 UDP 3702 służy do znajdowania uruchomionych wystąpień zdalnego debugera w sieci (na przykład **znaleźć** okna dialogowego w **dołączyć do procesu** okna dialogowego). Jest on używany tylko w przypadku odnajdywania maszyny z systemem zdalnego debugera, dzięki czemu jest to opcjonalne, jeśli masz inny sposób określenia nazwy komputera lub adres IP komputera docelowego. Jest to port standardowy dla odnajdywania, aby numer portu nie można skonfigurować.  
  
 Czy chcesz włączyć funkcję odnajdywania, można uruchomić polecenia msvsmon z wiersza polecenia, z odnajdywaniem wyłączone: **Msvsmon /nodiscovery**.  
  
## <a name="remote-debugger-ports-on-azure"></a>Portów debugera zdalnego na platformie Azure  
 Następujące porty są używane przez debuger zdalny na platformie Azure. Porty w usłudze w chmurze są mapowane na porty na poszczególnych maszyn wirtualnych. Wszystkie porty są TCP.  
  
||||  
|-|-|-|  
|**połączenia**|**Port w usłudze w chmurze**|**Port na maszynie Wirtualnej**|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Connector|30400|30398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.Forwarder|31400|31398|  
|Microsoft.WindowsAzure.Plugins.RemoteDebugger.FileUpload|32400|32398|  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie zdalne](../debugger/remote-debugging.md)



