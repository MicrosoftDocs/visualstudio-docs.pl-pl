---
title: 'Instrukcje: korzystanie z Diagnostyka grafiki z urządzeniem ARM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5bbe12449849b656af2658c5bab667b0e611515e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685876"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Instrukcje: używanie diagnostyki grafiki z urządzeniem ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diagnostyka grafiki obsługuje debugowanie zdalne aplikacji Direct3D na urządzeniach opartych na architekturze ARM z systemem Windows RT 8,1 lub Windows Phone 8,1. Możesz przechwytywać informacje graficzne z aplikacji Direct3D uruchomione na urządzeniu lub użyć urządzenia jako maszyny odtwarzania do wcześniej przechwyconych informacji graficznych.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Używanie Diagnostyka grafiki z urządzeniem ARM  
 Ponieważ program Visual Studio nie działa na urządzeniach opartych na architekturze ARM, należy używać zdalnego debugera do analizowania aplikacji, które są na nich uruchamiane. Zdalny debuger obsługuje przechwytywanie i odtwarzanie grafiki, dzięki czemu można zdiagnozować błędy renderowania i oszacować wydajność grafiki na tych urządzeniach równie łatwo, jak można debugować aplikację.  
  
 Aby korzystać z funkcji diagnostyki grafiki, należy najpierw włączyć debugowanie zdalne na urządzeniu.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Aby włączyć debugowanie zdalne na urządzeniu ARM  
  
1. Zainstaluj [zasady zestawów ARM](https://msdn.microsoft.com/windows/desktop/dn469188) na urządzeniu opartym na architekturze ARM.  
  
2. Zainstaluj [narzędzia zdalnego debugowania](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) na urządzeniu opartym na architekturze ARM.  
  
> [!IMPORTANT]
> W przypadku urządzeń z Windows Phone 8,1 może zajść konieczność zarejestrowania telefonu na potrzeby programowania. Aby to zrobić, musisz być zarejestrowanym deweloperem. Aby uzyskać więcej informacji, zobacz [jak wdrożyć i uruchomić aplikację dla Windows Phone 8](https://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Po włączeniu debugowania zdalnego na urządzeniu należy je określić jako miejsce docelowe debugowania i rozpocząć Diagnostyka grafiki.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Aby skonfigurować i uruchomić Diagnostyka grafiki na urządzeniu  
  
1. Na liście rozwijanej **platformy rozwiązań** wybierz pozycję **ARM** , aby urządzenie oparte na architekturze ARM było dostępne jako miejsce docelowe zdalnego debugowania.  
  
2. Z listy rozwijanej **element docelowy debugowania** wybierz urządzenie ARM.  
  
3. W menu wybierz kolejno opcje **Debuguj**, **grafika**i **Uruchom diagnostykę**. (Klawiatura: Alt + F5)  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchamianie aplikacji ze sklepu Windows na maszynie zdalnej](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Instrukcje: zmiana maszyny odtwarzania diagnostyki grafiki](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)
