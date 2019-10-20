---
title: 'Rozwiązywanie problemów z wyjątkami: System. ServiceModel. Security. MessageSecurityException — | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: troubleshooting
helpviewer_keywords:
- System.ServiceModel.Security.MessageSecurityException exception
- MessageSecurityException exception
ms.assetid: 61ad69a1-ac50-49de-9a7c-8454a84ec5bd
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9b8ce3f16c1439d62cfa1e2cff344b70e6724c42
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655350"
---
# <a name="troubleshooting-exceptions-systemservicemodelsecuritymessagesecurityexception"></a>Rozwiązywanie problemów z wyjątkami: System.ServiceModel.Security.MessageSecurityException
Wyjątek <xref:System.ServiceModel.Security.MessageSecurityException> jest generowany, gdy [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] określa, że komunikat nie jest prawidłowo zabezpieczony lub został naruszony. Ten błąd występuje najczęściej, gdy spełnione są następujące warunki:

- Aby komunikować się z usługą WCF (SVC) w witrynie sieci Web lub projekcie aplikacji sieci Web, należy użyć odwołania do usługi WCF za pośrednictwem połączenia zdalnego, takiego jak Podłączanie pulpitu zdalnego lub usług terminalowych.

- Nie masz uprawnień administratora w zdalnej witrynie.

- Żądania do hosta lokalnego w zdalnej lokacji są obsługiwane przez [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] Serwer deweloperski.

## <a name="associated-tips"></a>Skojarzone porady
 **Rozwiązywanie problemów z uwierzytelnianiem NTLM podczas korzystania z serwera deweloperskiego ASP.Net.**
Serwer deweloperski [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] ma zwykle wyłączone zabezpieczenia wyzwania/odpowiedzi systemu Windows NT, co umożliwia dostęp anonimowy. Domyślnie podczas uruchamiania sesji usług terminalowych lub korzystania z połączenia zdalnego jest włączone zabezpieczenia NTLM. Po włączeniu protokołu NTLM wszystkie żądania localhost są weryfikowane pod kątem poświadczeń użytkownika lub procesu, który uruchomił Serwer deweloperski [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Powoduje to zmniejszenie zagrożeń bezpieczeństwa. Jednak funkcja WCF wykonuje także własne uwierzytelnianie i nie zezwala na użycie usług WCF przez konto niebędące administratorami.

 Jeśli użytkownik zdalny może uruchomić witrynę sieci Web przy użyciu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] serwera deweloperskiego, a także pracować z usługą sieci Web lub usługą WCF, można utworzyć niestandardowe powiązanie usługi lub wyłączyć zabezpieczenia NTLM.

> [!IMPORTANT]
> Wyłączenie zabezpieczeń NTLM nie jest zalecane i może stanowić zagrożenie bezpieczeństwa.

 W przypadku tworzenia powiązania usługi niestandardowej nadal jest chronione uwierzytelnianie NTLM.

 Wykonaj następujące kroki, aby utworzyć niestandardowe powiązanie usługi dla usługi WCF.

#### <a name="to-create-a-custom-service-binding-for-the-wcf-service-hosted-inside-the-aspnet-development-server"></a>Tworzenie niestandardowego powiązania usługi dla usługi WCF hostowanej wewnątrz serwera ASP.NET Development

1. Otwórz plik Web. config usługi WCF, która generuje wyjątek.

2. Wprowadź następujące informacje w pliku Web. config.

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

3. Zapisz i zamknij plik Web. config.

4. W kodzie usługi WCF lub sieci Web Zmień wartość punktu końcowego na następujący:

   ```
   <endpoint address="" binding="customBinding" bindingConfiguration="Service1Binding" contract="IService1" />
   ```

    Dzięki temu usługa korzysta z niestandardowego powiązania.

5. Dodaj odwołanie do usługi w aplikacji sieci Web, która uzyskuje dostęp do usługi. (W **Dodaj odwołanie do usługi** okno dialogowe, Dodaj odwołanie do usługi w ramach pierwotnej usługi, która wygeneruje wyjątek).

   Możesz wykonać następujące kroki, aby wyłączyć zabezpieczenia NTLM podczas pracy z odwołaniem do usługi WCF.

> [!IMPORTANT]
> Wyłączenie zabezpieczeń NTLM nie jest zalecane i może stanowić zagrożenie bezpieczeństwa.

#### <a name="to-turn-off-ntlm-security"></a>Aby wyłączyć zabezpieczenia NTLM

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy nazwę witryny sieci Web, a następnie kliknij pozycję **strony właściwości**.

2. Wybierz **Opcje Start**, a następnie wyczyść pole wyboru **uwierzytelnianie NTLM** .

3. Kliknij przycisk **OK**.

## <a name="see-also"></a>Zobacz też
 <xref:System.ServiceModel.Security.MessageSecurityException> [Użyj Asystenta wyjątków](https://msdn.microsoft.com/library/e0a78c50-7318-4d54-af51-40c00aea8711)