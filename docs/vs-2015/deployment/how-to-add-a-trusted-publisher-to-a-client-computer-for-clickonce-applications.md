---
title: 'Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8c2bc30814af9cdc6181d08b313df20146f855e
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080959"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Za pomocą zaufanego wdrożenia aplikacji można skonfigurować komputery klienckie tak, aby Twoje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje są uruchamiane na wyższym poziomie zaufania bez monitowania użytkownika. Poniższe procedury pokazują, jak używać narzędzia wiersza polecenia CertMgr.exe można dodać certyfikatu wydawcy do magazynu zaufanych wydawców na komputerze klienckim.  
  
 Polecenia, których można się nieco różnić w zależności od tego, czy urząd certyfikacji (CA), który wystawił certyfikat znajduje się zaufany główny urząd certyfikacji do klienta. Jeśli komputer kliencki Windows jest częścią domeny, będzie zawierać, w postaci listy urzędów certyfikacji, które są traktowane jako zaufanych certyfikatów głównych. Ta lista jest zwykle konfigurowana przez administratora systemu. Jeśli certyfikat został wystawiony przez jedną z tych zaufanych certyfikatów głównych lub przez urząd certyfikacji który tworzy łańcuch do jednej z tych zaufanych certyfikatów głównych, można dodać certyfikatu do magazynu zaufanych certyfikatów głównych firmy klienta. Jeśli z drugiej strony, certyfikat nie został wystawiony przez jeden z tych zaufanych certyfikatów głównych, musisz dodać certyfikat do klienta magazynu zaufanych certyfikatów głównych i magazynie zaufanego wydawcę.  
  
> [!NOTE]
>  Należy dodać certyfikaty w ten sposób na każdym komputerze klienckim, na którym planujesz wdrożyć [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikację, która wymaga podniesionych uprawnień. Należy dodać certyfikaty, ręcznie lub za pośrednictwem aplikacji wdrażanej dla klientów. Należy skonfigurować te komputery raz, po którym można wdrożyć dowolną liczbę [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje podpisane przy użyciu tego samego certyfikatu.  
  
 Możesz też dodać certyfikat do magazynu, programowo przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509Store> klasy.  
  
 Aby uzyskać omówienie wdrażanie zaufanych aplikacji, zobacz [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w obszarze zaufanego głównego  
  
1. Uzyskaj certyfikat z urzędu certyfikacji.  
  
2. Wyeksportuj certyfikat w formacie Base64 X.509 (.cer). Aby uzyskać więcej informacji na temat formatów certyfikatów Zobacz [eksportowania certyfikatu](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:  
  
     **certmgr.exe — Dodaj certificate.cer - c -s - r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w ramach różnych głównych  
  
1. Uzyskaj certyfikat z urzędu certyfikacji.  
  
2. Wyeksportuj certyfikat w formacie Base64 X.509 (.cer). Aby uzyskać więcej informacji na temat formatów certyfikatów Zobacz [eksportowania certyfikatu](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:  
  
     **certmgr.exe — Dodaj good.cer - c -s - r localMachine głównego**  
  
     **certmgr.exe — Dodaj good.cer - c -s - r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Instrukcje: Włączenie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Instrukcje: Ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Instrukcje: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Instrukcje: Ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Instrukcje: Konfigurowanie zachowania zaufanego monitowania technologii ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
