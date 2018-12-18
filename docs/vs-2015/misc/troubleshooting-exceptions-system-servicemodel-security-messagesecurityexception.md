---
title: 'Rozwiązywanie problemów z wyjątkami: System.ServiceModel.Security.MessageSecurityException | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: e7d13f5cc282026b1590f59180ed7f25312bb926
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51742479"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Rozwiązywanie problemów z wyjątkami: System.ServiceModel.Security.MessageSecurityException
A <xref:System.ServiceModel.Security.MessageSecurityException> wyjątek jest generowany, gdy [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] Określa, że komunikat nie jest poprawnie zabezpieczony lub została naruszona. Ten błąd występuje najczęściej, gdy wszystkie spełnione są następujące warunki:  
  
-   Umożliwia to odwołanie do usługi WCF za pośrednictwem połączenia zdalnego, takich jak połączenia pulpitu zdalnego lub usług terminalowych komunikować się z usługą WCF (SVC) w projekcie aplikacji witryny sieci Web lub sieci Web.  
  
-   Nie masz uprawnienia administratora na zdalnej witrynie.  
  
-   Żądania z hostem lokalnym na zdalnej witrynie są aktualnie obsługiwane przez [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] serwera projektowego.  
  
## <a name="associated-tips"></a>Skojarzone porady  
 **Korzystając z programem ASP.Net Development Server, należy rozwiązać problemy z uwierzytelnianiem NTLM.**  
 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server ma zwykle jest wyłączone, zabezpieczeń typu wezwanie/odpowiedź systemu Windows NT (NTLM), która zezwala na dostęp anonimowy. Domyślnie podczas uruchamiania sesji usług terminalowych lub użycia połączenia zdalnego, zabezpieczenie NTLM jest włączona. Po włączeniu uwierzytelniania NTLM, wszystkie żądania localhost są weryfikowane względem poświadczeń użytych do użytkownika lub procesu, który uruchomił [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] serwera projektowego. Pozwala to ograniczyć zagrożenia bezpieczeństwa. Jednak WCF również swój własny uwierzytelnianie jest wykonywane i nie zezwala na konta użytkowników niebędących administratorami, korzystać z usług WCF.  
  
 Jeśli użytkownik zdalny może uruchomić witryny sieci Web przy użyciu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Development Server oraz pracy z usługą sieci Web lub usługi WCF, możesz utworzyć powiązania usługi niestandardowych lub wyłączyć zabezpieczenie NTLM.  
  
> [!IMPORTANT]
>  Wyłączenie zabezpieczeń NTLM nie jest zalecane i może stanowić zagrożenie bezpieczeństwa.  
  
 Jeśli tworzysz powiązania niestandardowej usługi, nadal są chronione przez uwierzytelnianie NTLM.  
  
 Wykonaj następujące kroki, aby utworzyć powiązanie niestandardowych usług dla usługi WCF.  
  
#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Aby utworzyć usługę niestandardowe powiązanie dla usługi WCF hostowanej w ASP.NET Development Server  
  
1. Otwórz plik Web.config dla usługi WCF, które generuje wyjątek.  
  
2. Wprowadź następujące informacje w pliku Web.config.  
  
   ```  
   <bindings>  
     <customBinding>  
       <binding name="Service1Binding">  
         <transactionFlow />  
         <textMessageEncoding />  
         <httpTransport authenticationScheme="Ntlm" />  
       </binding>  
     </customBinding>  
   </bindings>  
   ```  
  
3. Zapisz i zamknij plik Web.config.  
  
4. W kodzie dla usługi sieci Web lub usługi WCF należy zmienić wartość punktu końcowego do następujących:  
  
   ```  
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />  
   ```  
  
    Daje to gwarancję, że usługa używa niestandardowego powiązania.  
  
5. Dodaj odwołanie do usługi w aplikacji sieci Web, który uzyskuje dostęp do usługi. (W **Dodaj odwołanie do usługi** okna dialogowego Dodaj odwołanie do usługi, jak w przypadku oryginalnej usługi, która generowania wyjątku.)  
  
   Można wykonaj następujące kroki, aby wyłączyć zabezpieczenie NTLM, gdy pracujesz z odwołania do usługi WCF.  
  
> [!IMPORTANT]
>  Wyłączenie zabezpieczeń NTLM nie jest zalecane i może stanowić zagrożenie bezpieczeństwa.  
  
#### <a name="to-turn-off-ntlm-security"></a>Aby wyłączyć zabezpieczenie NTLM  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy nazwę witryny sieci Web, a następnie kliknij przycisk **stron właściwości**.  
  
2.  Wybierz **opcje uruchamiania**, a następnie wyczyść **uwierzytelniania NTLM** pole wyboru.  
  
3.  Kliknij przycisk **OK**.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.Security.MessageSecurityException>   
 [Korzystanie z Asystenta wyjątków](http://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)