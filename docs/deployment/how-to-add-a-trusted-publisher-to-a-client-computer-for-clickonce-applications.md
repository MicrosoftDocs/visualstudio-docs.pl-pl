---
title: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
ms.date: 11/04/2016
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 594c012aaa49a5b62e9f254f924a71f4934d1ebe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "85382617"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
Dzięki wdrożeniu zaufanej aplikacji można skonfigurować komputery klienckie w taki sposób, aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje były uruchamiane z wyższym poziomem zaufania bez monitowania użytkownika. W poniższych procedurach pokazano, jak za pomocą narzędzia wiersza polecenia CertMgr.exe dodać certyfikat wydawcy do magazynu zaufanych wydawców na komputerze klienckim.

 Używane polecenia różnią się nieco w zależności od tego, czy urząd certyfikacji (CA), który wystawił certyfikat, jest częścią zaufanego katalogu głównego klienta. Jeśli komputer kliencki z systemem Windows jest częścią domeny, będzie zawierać listę urzędów certyfikacji, które są uznawane za zaufane certyfikaty główne. Ta lista jest zazwyczaj konfigurowana przez administratora systemu. Jeśli certyfikat został wystawiony przez jeden z zaufanych katalogów głównych lub przez urząd certyfikacji, który tworzy łańcuch do jednego z tych zaufanych katalogów głównych, można dodać certyfikat do zaufanego magazynu głównego klienta. Jeśli z drugiej strony certyfikat nie został wystawiony przez jeden z tych zaufanych katalogów głównych, należy dodać ten certyfikat zarówno do zaufanego magazynu głównego klienta, jak i do magazynu zaufanych wydawców.

> [!NOTE]
> W ten sposób należy dodać certyfikaty na każdym komputerze klienckim, na którym planujesz wdrożyć [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikację wymagającą podwyższonego poziomu uprawnień. Certyfikaty można dodać ręcznie lub za pomocą wdrażanej aplikacji na klientach. Wystarczy tylko skonfigurować te komputery, aby można było wdrożyć dowolną liczbę [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji podpisanych za pomocą tego samego certyfikatu.

 Certyfikat można także dodać do magazynu programowo przy użyciu <xref:System.Security.Cryptography.X509Certificates.X509Store> klasy.

 Omówienie wdrażania zaufanych aplikacji można znaleźć w temacie [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w zaufanym katalogu głównym

1. Uzyskaj certyfikat cyfrowy od urzędu certyfikacji.

2. Wyeksportuj certyfikat do formatu Base64 X. 509 (*. cer*). Aby uzyskać więcej informacji na temat formatów certyfikatów, zobacz [Eksportowanie certyfikatu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. W wierszu polecenia na komputerach klienckich Uruchom następujące polecenie:

     **certmgr.exe-Add Certificate. cer-c-s-r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Aby dodać certyfikat do magazynu zaufanych wydawców w innym katalogu głównym

1. Uzyskaj certyfikat cyfrowy od urzędu certyfikacji.

2. Wyeksportuj certyfikat do formatu Base64 X. 509 (*. cer*). Aby uzyskać więcej informacji na temat formatów certyfikatów, zobacz [Eksportowanie certyfikatu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. W wierszu polecenia na komputerach klienckich Uruchom następujące polecenie:

     **certmgr.exe-Add dobry. cer-c-s-r localMachine root**

     **certmgr.exe-Add dobry. cer-c-s-r localMachine TrustedPublisher**

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Instrukcje: Włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Instrukcje: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Instrukcje: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md)
- [Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Instrukcje: ponowne podpisywanie aplikacji i manifestów wdrożenia](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Instrukcje: Konfigurowanie zachowania monitowania zaufania ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)