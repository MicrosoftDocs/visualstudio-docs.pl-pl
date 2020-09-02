---
title: Ograniczenia dotyczące debugowania WCF | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "68176797"
---
# <a name="limitations-on-wcf-debugging"></a>Ograniczenia debugowania WCF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Istnieją trzy sposoby rozpoczęcia debugowania usługi WCF:  
  
- Debugujesz proces klienta wywołujący usługę. Debuger prowadzi do usługi. Usługa nie musi znajdować się w tym samym rozwiązaniu co aplikacja kliencka.  
  
- Debugujesz proces klienta, który wysyła żądanie do usługi. Usługa musi być częścią rozwiązania.  
  
- W celu dołączenia do usługi, która jest aktualnie uruchomiona, należy użyć **dołączania do procesu** . Debugowanie zaczyna się wewnątrz usługi.  
  
  W tym temacie opisano ograniczenia dotyczące tych scenariuszy.  
  
## <a name="limitations-on-stepping-into-a-service"></a>Ograniczenia dotyczące przechodzenia do usługi  
 Aby przejść do usługi z aplikacji klienckich, które są debugowane, muszą zostać spełnione następujące warunki:  
  
- Klient musi wywoływać usługę za pomocą synchronicznego obiektu klienckiego.  
  
- Operacja kontraktu nie może być jednokierunkowa.  
  
- Jeśli serwer jest asynchroniczny, nie można wyświetlić pełnego stosu wywołań podczas wykonywania kodu w ramach usługi.  
  
- Debugowanie musi być włączone przy użyciu następującego kodu w pliku app.config lub Web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    </system.web>  
    ```  
  
     Ten kod należy dodać tylko jeden raz. Możesz dodać ten kod, edytując plik. config lub dołączając do usługi za pomocą **dołączania do procesu**. W przypadku korzystania **z dołączania do procesu** w usłudze kod debugowania jest automatycznie dodawany do pliku. config. Następnie można debugować i przechodzenie do usługi bez konieczności edytowania pliku. config.  
  
## <a name="limitations-on-stepping-out-of-a-service"></a>Ograniczenia dotyczące stopniowego działania usługi  
 Przechodzenie do usługi i powrót do klienta ma takie same ograniczenia, jak w przypadku przechodzenia do usługi. Ponadto debuger musi być dołączony do klienta programu. Jeśli debugujesz klienta i przechodzenie do usługi, debuger pozostanie dołączony do usługi. Jest to prawdziwe, niezależnie od tego, czy klient został uruchomiony przy użyciu polecenia **Rozpocznij debugowanie** , czy dołączone do klienta przy użyciu funkcji **Dołącz do procesu**. Po rozpoczęciu debugowania przez dołączenie do usługi debuger nie jest jeszcze dołączony do klienta programu. W takim przypadku, jeśli konieczne jest przechodzenie do usługi i powrót do klienta programu, należy najpierw użyć **Dołącz do procesu** , aby dołączyć do klienta ręcznie.  
  
## <a name="limitations-on-automatic-attach-to-a-service"></a>Ograniczenia dotyczące automatycznego dołączania do usługi  
 Automatyczne dołączanie do usługi ma następujące ograniczenia:  
  
- Usługa musi być częścią [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] debugowanego rozwiązania.  
  
- Usługa musi być hostowana. Może być częścią projektu witryny sieci Web (systemu plików i HTTP), projektu aplikacji sieci Web (systemu plików i HTTP) lub projektu biblioteki usług WCF. Projekty biblioteki usług WCF mogą być bibliotekami usług lub bibliotekami usługi przepływu pracy.  
  
- Usługa musi być wywołana z poziomu klienta WCF.  
  
- Debugowanie musi być włączone przy użyciu następującego kodu w pliku app.config lub Web.config:  
  
    ```  
    <system.web>  
      <compilation debug="true" />  
    <system.web>  
    ```  
  
## <a name="self-hosting"></a>Samoobsługowe hosting  
 *Samoobsługowa usługa* to usługa WCF, która nie działa w ramach usług IIS, hosta usługi WCF ani [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] serwera deweloperskiego. Informacje o sposobie debugowania usługi samodzielnej można znaleźć w temacie [How to: Debug a The Inhosteding WCF Service](../debugger/how-to-debug-a-self-hosted-wcf-service.md).  
  
## <a name="self-hosting"></a>Samoobsługowe hosting  
 Aby włączyć debugowanie [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji 3,0 lub 3,5, [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] przed zainstalowaniem programu należy zainstalować program 3,0 lub 3,5 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] . Jeśli program [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] został zainstalowany przed [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] 3,0 lub 3,5, wystąpi błąd podczas próby debugowania [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikacji 3,0 lub 3,5. Komunikat o błędzie to "nie można automatycznie wkroczyć do serwera". Aby rozwiązać ten problem, użyj **Panelu sterowania**systemu Windows, **programów i funkcji** do naprawy [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] instalacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie usług WCF](../debugger/debugging-wcf-services.md)   
 [Instrukcje: debugowanie hostowanej samodzielnie usługi WCF](../debugger/how-to-debug-a-self-hosted-wcf-service.md)
