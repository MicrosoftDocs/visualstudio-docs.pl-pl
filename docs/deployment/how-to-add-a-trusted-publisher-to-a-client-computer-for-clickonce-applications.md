---
title: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1423952405a31063ee88ce6fa1dfe0b75d80fe5d
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649216"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>Jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce
Za pomocą zaufanego wdrażania aplikacji można skonfigurować komputery klienckie tak, aby [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje były uruchamiane z wyższym poziomem zaufania bez monitowania użytkownika. Poniższe procedury pokazują, jak dodać certyfikat wydawcy do magazynu Zaufanych wydawców na komputerze klienckim za pomocą narzędzia wiersza polecenia CertMgr.exe.

 Używane polecenia różnią się nieznacznie w zależności od tego, czy urząd certyfikacji, który wystawił certyfikat, jest częścią zaufanego katalogu głównego klienta. Jeśli komputer kliencki systemu Windows jest częścią domeny, będzie zawierać na liście urzędy dostępu, które są uważane za zaufane katalogi główne. Ta lista jest zwykle konfigurowana przez administratora systemu. Jeśli certyfikat został wystawiony przez jeden z tych zaufanych katalogów głównych lub przez urząd certyfikacji, który sieci do jednego z tych zaufanych katalogów głównych, można dodać certyfikat do zaufanego magazynu głównego klienta. Jeśli z drugiej strony certyfikat nie został wystawiony przez jeden z tych zaufanych katalogów głównych, należy dodać certyfikat zarówno do magazynu zaufanego katalogu głównego klienta, jak i do magazynu Zaufanego wydawcy.

> [!NOTE]
> Certyfikaty należy dodać w ten sposób na każdym [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] komputerze klienckim, na którym planujesz wdrożyć aplikację, która wymaga podwyższonych uprawnień. Certyfikaty można dodać ręcznie lub za pośrednictwem aplikacji wdrażanej dla klientów. Te komputery należy skonfigurować tylko raz, po czym [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] można wdrożyć dowolną liczbę aplikacji podpisanych przy tym samym certyfikacie.

 Można również dodać certyfikat do magazynu programowo <xref:System.Security.Cryptography.X509Certificates.X509Store> przy użyciu klasy.

 Aby zapoznać się z omówieniem wdrażania zaufanych aplikacji, zobacz [Omówienie wdrażania zaufanych aplikacji.](../deployment/trusted-application-deployment-overview.md)

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>Aby dodać certyfikat do magazynu Zaufani wydawcy w zaufanym katalogu głównym

1. Uzyskaj certyfikat cyfrowy od urzędu certyfikacji.

2. Wyeksportuj certyfikat do formatu Base64 X.509 (*.cer*). Aby uzyskać więcej informacji o formatach certyfikatów, zobacz [Eksportowanie certyfikatu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:

     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**

### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>Aby dodać certyfikat do magazynu Zaufani wydawcy w innym katalogu głównym

1. Uzyskaj certyfikat cyfrowy od urzędu certyfikacji.

2. Wyeksportuj certyfikat do formatu Base64 X.509 (*.cer*). Aby uzyskać więcej informacji o formatach certyfikatów, zobacz [Eksportowanie certyfikatu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc730988(v=ws.10)).

3. W wierszu polecenia na komputerach klienckich uruchom następujące polecenie:

     **certmgr.exe -add good.cer -c -s -r localKorzeń nasyczyni**

     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**

## <a name="see-also"></a>Zobacz też
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Jak: Włącz ustawienia zabezpieczeń ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Jak: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Jak: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md)
- [Jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Jak: Ponowne podpisywanie manifestów aplikacji i wdrażania](../deployment/how-to-re-sign-application-and-deployment-manifests.md)
- [Jak: Konfigurowanie zachowania monitu zaufania ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)