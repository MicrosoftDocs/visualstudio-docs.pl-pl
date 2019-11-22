---
title: 'Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 9b535737860b846aadecb6b73b4bd26659db37b1
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74289716"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Porady: dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dzięki wdrożeniu zaufanej aplikacji można skonfigurować komputery klienckie w taki sposób, aby aplikacje [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] działały z wyższym poziomem zaufania bez monitowania użytkownika. W poniższych procedurach pokazano, jak za pomocą narzędzia wiersza polecenia CertMgr. exe dodać certyfikat wydawcy do magazynu zaufanych wydawców na komputerze klienckim.  
  
 Używane polecenia różnią się nieco w zależności od tego, czy urząd certyfikacji (CA), który wystawił certyfikat, jest częścią zaufanego katalogu głównego klienta. Jeśli komputer kliencki z systemem Windows jest częścią domeny, będzie zawierać listę urzędów certyfikacji, które są uznawane za zaufane certyfikaty główne. Ta lista jest zazwyczaj konfigurowana przez administratora systemu. Jeśli certyfikat został wystawiony przez jeden z zaufanych katalogów głównych lub przez urząd certyfikacji, który tworzy łańcuch do jednego z tych zaufanych katalogów głównych, można dodać certyfikat do zaufanego magazynu głównego klienta. Jeśli z drugiej strony certyfikat nie został wystawiony przez jeden z tych zaufanych katalogów głównych, należy dodać ten certyfikat zarówno do zaufanego magazynu głównego klienta, jak i do magazynu zaufanych wydawców.  
  
> [!NOTE]
> W ten sposób należy dodać certyfikaty na każdym komputerze klienckim, na którym planujesz wdrożyć aplikację [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], która wymaga podniesionych uprawnień. Certyfikaty można dodać ręcznie lub za pomocą wdrażanej aplikacji na klientach. Wystarczy tylko skonfigurować te komputery, aby można było wdrożyć dowolną liczbę [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji podpisanych za pomocą tego samego certyfikatu.  
  
 Certyfikat można także dodać do magazynu programowo przy użyciu klasy <xref:System.Security.Cryptography.X509Certificates.X509Store>.  
  
 Omówienie wdrażania zaufanych aplikacji można znaleźć w temacie [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w zaufanym katalogu głównym  
  
1. Uzyskaj certyfikat cyfrowy od urzędu certyfikacji.  
  
2. Wyeksportuj certyfikat do formatu Base64 X. 509 (. cer). Aby uzyskać więcej informacji na temat formatów certyfikatów, zobacz [Eksportowanie certyfikatu](https://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. W wierszu polecenia na komputerach klienckich Uruchom następujące polecenie:  
  
     **certmgr. exe-Add Certificate. cer-c-s-r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w innym katalogu głównym  
  
1. Uzyskaj certyfikat cyfrowy od urzędu certyfikacji.  
  
2. Wyeksportuj certyfikat do formatu Base64 X. 509 (. cer). Aby uzyskać więcej informacji na temat formatów certyfikatów, zobacz [Eksportowanie certyfikatu](https://go.microsoft.com/fwlink/?LinkId=164793).  
  
3. W wierszu polecenia na komputerach klienckich Uruchom następujące polecenie:  
  
     **certmgr. exe-Add dobry. cer-c-s-r localMachine root**  
  
     **certmgr. exe-Add dobry. cer-c-s-r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 Technologia [ClickOnce i  Authenticode](../deployment/clickonce-and-authenticode.md)  
 [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Instrukcje: Włączanie ustawień zabezpieczeń ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Instrukcje: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Instrukcje: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Instrukcje: ponowne podpisywanie manifestów aplikacji i wdrażania](../deployment/how-to-re-sign-application-and-deployment-manifests.md)   
 [Instrukcje: konfigurowanie funkcji zaufanego monitowania technologii ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
