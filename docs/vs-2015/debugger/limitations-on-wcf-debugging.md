---
title: Ograniczenia debugowania WCF | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, WCF
- WCF, debugging limitations
ms.assetid: 8e0333c4-1ddc-4abe-8f1c-d19bf6a2a07a
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3faa57a0a2ca413898364c2d4ad1891df85f1ce8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68176797"
---
# <a name="limitations-on-wcf-debugging"></a>Ograniczenia debugowania WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Istnieją trzy sposoby, aby można było rozpocząć debugowanie usługi WCF:  
  
- Debugowany proces klienta, który wywołuje usługę. Debuger nie wchodzi do usługi. Usługa nie ma znajdować się w tym samym rozwiązaniu jako aplikację kliencką.  
  
- Debugowany proces klienta, który wysyła żądanie do usługi. Usługa musi być częścią rozwiązania.  
  
- Możesz użyć **dołączyć do procesu** do dołączenia do usługi, które jest aktualnie uruchomione. Debugowanie rozpoczyna się w usłudze.  
  
  W tym temacie opisano ograniczenia dotyczące tych scenariuszy.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Ograniczenia dotyczące Wkraczanie do usługi  
 Aby wkraczać do usługi z aplikacji klienckich, które jest debugowany, muszą być spełnione następujące warunki:  
  
- Klient musi wywołać usługę za pomocą obiektu klienta synchroniczne.  
  
- Operacja Umowy nie może być jednokierunkowe.  
  
- Jeśli serwer jest asynchroniczne, nie można wyświetlić pełny stos wywołania, gdy są wykonywane kod wewnątrz usługi.  
  
- Debugowanie musi być włączone w pliku Web.config lub app.config następującym kodem:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Ten kod ma tylko do dodania jeden raz. Ten kod można dodawać, edytując plik .config lub dołączanie do usługi przy użyciu **dołączyć do procesu**. Kiedy używasz **dołączyć do procesu** w usłudze kod debugowania jest automatycznie dodawany do pliku Config. Po tym można debugować i przejść do usługi bez konieczności edytowania pliku Config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Ograniczenia dotyczące przechodzenie krok po kroku, poza eksploatacją  
 Przechodzenie z usługi z powrotem do klienta ma te same ograniczenia opisane do przechodzenia do usługi. Ponadto debuger musi być dołączony do klienta. Jeśli debugujesz, klient i usługa krok po kroku, debuger nadal jest dołączony do usługi. Jest to istotne, czy klient jest uruchomiony przy użyciu **Rozpocznij debugowanie** lub dołączone do klienta przy użyciu **dołączyć do procesu**. Jeśli zostało uruchomione, debugowanie, dołączając do usługi, debuger nie jest jeszcze dołączony do klienta. W takiej sytuacji, mając do kroku poza usługi i do klienta, należy najpierw użyć **dołączyć do procesu** ręcznie Dołącz do klienta.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Ograniczenia dotyczące automatyczne dołączanie do usługi  
 Automatyczne dołączanie do usługi ma następujące ograniczenia:  
  
- Usługa musi być częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania debugowania.  
  
- Usługa musi być obsługiwana. Może być częścią projektu witryny sieci Web (System plików i HTTP), projekt aplikacji sieci Web (System plików i HTTP) lub projektu biblioteki usługi WCF. Projekty biblioteki usługi WCF może być Usługa biblioteki lub biblioteki usługi przepływu pracy.  
  
- Usługa musi być wywoływane z klienta programu WCF.  
  
- Debugowanie musi być włączone w pliku Web.config lub app.config następującym kodem:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Hostingu samodzielnego  
 A *usługi hosta samodzielnego* to usługa WCF, która nie jest uruchamiane w usługach IIS, Host usługi WCF, lub [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] serwera projektowego. Aby uzyskać informacje o tym, jak można debugować samodzielnie hostowanej usługi, zobacz [jak: Debugowanie hostowania samoobsługowego WCF usługi](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Hostingu samodzielnego  
 Aby włączyć debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji w wersji 3.0 lub 3.5, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 lub 3.5 musi zostać zainstalowany przed [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] jest zainstalowany. Jeśli [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] została zainstalowana przed [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3.0 lub 3.5, wystąpi błąd podczas próby debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji w wersji 3.0 lub 3.5. Jest komunikat o błędzie, "nie można automatycznie wkroczyć do serwera." Aby rozwiązać ten problem, należy użyć Windows **Panelu sterowania**, **programy i funkcje** naprawić swoje [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] instalacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Instrukcje: Debugowanie samodzielnie hostowanej usługi WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
