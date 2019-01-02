---
title: 'Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bfd4e953c0a2ecee17c167fbcdda529d7607b9cd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53882977"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
Za pomocą zaufanego wdrożenia aplikacji można skonfigurować komputery klienckie tak, aby Twoje [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje są uruchamiane na wyższym poziomie zaufania bez monitowania użytkownika. Poniższe procedury pokazują, jak używać narzędzia wiersza polecenia CertMgr.exe można dodać certyfikatu wydawcy do magazynu zaufanych wydawców na komputerze klienckim.  
  
 Polecenia, których można się nieco różnić w zależności od tego, czy urząd certyfikacji (CA), który wystawił certyfikat znajduje się zaufany główny urząd certyfikacji do klienta. Jeśli komputer kliencki Windows jest częścią domeny, będzie zawierać, w postaci listy urzędów certyfikacji, które są traktowane jako zaufanych certyfikatów głównych. Ta lista jest zwykle konfigurowana przez administratora systemu. Jeśli certyfikat został wystawiony przez jedną z tych zaufanych certyfikatów głównych lub przez urząd certyfikacji który tworzy łańcuch do jednej z tych zaufanych certyfikatów głównych, można dodać certyfikatu do magazynu zaufanych certyfikatów głównych firmy klienta. Jeśli z drugiej strony, certyfikat nie został wystawiony przez jeden z tych zaufanych certyfikatów głównych, musisz dodać certyfikat do klienta magazynu zaufanych certyfikatów głównych i magazynie zaufanego wydawcę.  
  
> [!NOTE]
>  Należy dodać certyfikaty w ten sposób na każdym komputerze klienckim, na którym planujesz wdrożyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację, która wymaga podniesionych uprawnień. Należy dodać certyfikaty, ręcznie lub za pośrednictwem aplikacji wdrażanej dla klientów. Należy skonfigurować te komputery raz, po którym można wdrożyć dowolną liczbę [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje podpisane przy użyciu tego samego certyfikatu.  
  
 Możesz też dodać certyfikat do magazynu, programowo przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509Store> klasy.  
  
 Aby uzyskać omówienie wdrażanie zaufanych aplikacji, zobacz [Przegląd wdrażania aplikacji zaufanego](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w obszarze zaufanego głównego  
  
1.  Uzyskaj certyfikat z urzędu certyfikacji.  
  
2.  Wyeksportuj certyfikat w formacie Base64 X.509 (*cer*) format. Aby uzyskać więcej informacji na temat formatów certyfikatów Zobacz [eksportowania certyfikatu](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:  
  
     **certmgr.exe — Dodaj certificate.cer - c -s - r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w ramach różnych głównych  
  
1.  Uzyskaj certyfikat z urzędu certyfikacji.  
  
2.  Wyeksportuj certyfikat w formacie Base64 X.509 (*cer*) format. Aby uzyskać więcej informacji na temat formatów certyfikatów Zobacz [eksportowania certyfikatu](http://go.microsoft.com/fwlink/?LinkId=164793).  
  
3.  W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:  
  
     **certmgr.exe — Dodaj good.cer - c -s - r localMachine głównego**  
  
     **certmgr.exe — Dodaj good.cer - c -s - r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Zobacz także  
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
 [Instrukcje: Ponowne podpisywanie manifestów aplikacji i wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Instrukcje: Konfigurowanie funkcji ClickOnce zaufania monitowania](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)