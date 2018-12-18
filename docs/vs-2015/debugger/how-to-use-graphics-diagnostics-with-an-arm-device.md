---
title: 'Porady: używanie diagnostyki grafiki z urządzeniem ARM | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 346fd3c0-9e92-4ab8-bb3b-1aa9000a2483
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4c5122cb009b3624388ff8825b34cae8ca44a546
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51728676"
---
# <a name="how-to-use-graphics-diagnostics-with-an-arm-device"></a>Porady: używanie diagnostyki grafiki z urządzeniem ARM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Graphics Diagnostics obsługuje zdalne debugowanie aplikacji Direct3D na urządzeniach z systemem ARM z systemem Windows RT 8.1 lub Windows Phone 8.1. Możesz przechwytywać informacje graficzne z aplikacji Direct3D, po uruchomieniu na urządzeniu lub korzystanie z urządzenia jako maszynę odtwarzającą dla wcześniej przechwycone informacje graficzne.  
  
## <a name="using-graphics-diagnostics-with-an-arm-based-device"></a>Używanie Graphics Diagnostics przy użyciu urządzenia z systemem ARM  
 Ponieważ program Visual Studio nie jest uruchamiany na urządzeniach z systemem ARM, masz umożliwia analizowanie aplikacja, która działa na nich za pomocą zdalnego debugera. Zdalny debuger obsługuje przechwytywanie grafiki i odtwarzanie tak, aby zdiagnozować błędy renderowania i po prostu równie łatwo, jak można debugować aplikację na nich ocenić wydajność grafiki na tych urządzeniach.  
  
 Korzystanie z funkcji diagnostyki grafiki, należy najpierw włączyć, zdalne debugowanie na urządzeniu.  
  
#### <a name="to-enable-remote-debugging-on-your-arm-based-device"></a>Aby włączyć debugowanie zdalne na urządzeniu z systemem ARM  
  
1.  Zainstaluj [zasad dotyczących zestawów ARM](http://msdn.microsoft.com/windows/desktop/dn469188) na urządzeniu z systemem ARM.  
  
2.  Zainstaluj [Remote Debugging Tools](http://go.microsoft.com/fwlink/?LinkId=393086) na urządzeniu z systemem ARM.  
  
> [!IMPORTANT]
>  Urządzeń z systemem Windows Phone 8.1 trzeba zarejestrować telefon do programowania. Aby to zrobić, musi być zarejestrowany dla deweloperów. Aby uzyskać więcej informacji, zobacz [sposób wdrażania i uruchamiania aplikacji dla systemu Windows Phone 8](http://msdn.microsoft.com/library/windowsphone/develop/ff402565.aspx).  
  
 Po włączeniu zdalnego debugowania na urządzeniu z systemem przekształcić ją w docelowych debugowania i uruchom narzędzie Diagnostyka grafiki.  
  
#### <a name="to-configure-and-start-graphics-diagnostics-on-your-device"></a>Aby skonfigurować i uruchomić diagnostyki grafiki na urządzeniu z systemem  
  
1.  Na **platformy rozwiązania** listy rozwijanej wybierz **ARM** tak, aby urządzenia z systemem ARM będą dostępne jako obiekt docelowy debugowania zdalnego.  
  
2.  Na **Debuguj element docelowy** listy rozwijanej wybierz urządzenie ARM.  
  
3.  W menu, wybierz **debugowania**, **grafiki**, **Rozpocznij diagnostykę**. (Klawiatura: Alt + F5)  
  
## <a name="see-also"></a>Zobacz też  
 [Uruchom Windows Store apps na komputerze zdalnym](../debugger/run-windows-store-apps-on-a-remote-machine.md)   
 [Instrukcje: zmiana maszyny odtwarzania diagnostyki grafiki](../debugger/how-to-change-the-graphics-diagnostics-playback-machine.md)



