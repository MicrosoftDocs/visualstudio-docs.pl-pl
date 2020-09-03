---
title: ClickOnce i Authenticode | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- .pfx files
- ClickOnce deployment, Authenticode
- Authenticode, ClickOnce
- ClickOnce deployment, certificates
- ClickOnce deployment, security
ms.assetid: ab5b6712-f32a-4e33-842f-e88ab4818ccf
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9b0e22f56ab68be521eda7a765a2be7e23bbf92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093951"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce i podpis Authenticode
*Authenticode* to technologia firmy Microsoft, która używa kryptografii standardowej w branży do podpisywania kodu aplikacji za pomocą certyfikatów cyfrowych, które weryfikują autentyczność wydawcy aplikacji. Użycie technologii Authenticode do wdrażania aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zmniejsza ryzyko koń trojański. Koń trojański jest wirusem lub innym szkodliwym programem, który złośliwa osoba trzecia Niemniej reprezentuje jako legalny program pochodzący z ustalonego, wiarygodnego źródła. [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]Aby sprawdzić, czy zestawy i pliki nie zostały naruszone, należy wykonać dodatkowe czynności.

 W poniższych sekcjach opisano różne typy certyfikatów cyfrowych używanych w technologii Authenticode, sposób weryfikowania certyfikatów przy użyciu urzędów certyfikacji, rolę sygnatury czasowej w certyfikatach oraz metody magazynowania dostępne dla certyfikatów.

## <a name="authenticode-and-code-signing"></a>Authenticode i podpisywanie kodu
 *Certyfikat cyfrowy* to plik, który zawiera kryptograficzną parę kluczy publiczny/prywatny wraz z metadanymi opisującymi wydawcy, dla których certyfikat został wystawiony, oraz Agencję, która wystawił certyfikat.

 Istnieją różne typy certyfikatów Authenticode. Każdy z nich jest skonfigurowany do różnych typów podpisywania. W przypadku [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji trzeba mieć certyfikat Authenticode, który jest prawidłowy w przypadku podpisywania kodu. Próba podpisania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu innego typu certyfikatu, na przykład cyfrowego certyfikatu poczty e-mail, nie będzie działała. Aby uzyskać więcej informacji, zobacz [wprowadzenie do podpisywania kodu](/windows/desktop/seccrypto/cryptography-tools).

 Certyfikat do podpisywania kodu można uzyskać na jeden z trzech sposobów:

- Kup dostawcę certyfikatu.

- Odbierz jeden z grup w organizacji odpowiedzialnych za tworzenie certyfikatów cyfrowych.

- Wygeneruj własny certyfikat przy użyciu polecenia cmdlet New-SelfSignedCertificate programu PowerShell lub za pomocą *MakeCert.exe*, który jest dołączony do programu [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] .

### <a name="how-using-certificate-authorities-helps-users"></a>Jak korzystanie z urzędów certyfikacji ułatwia użytkownikom
 Certyfikat wygenerowany przy użyciu polecenia New-SelfSignedCertificate lub narzędzia *MakeCert.exe* jest często nazywany certyfikatem *samodzielnego certyfikatu lub* *testem*. Ten rodzaj certyfikatu działa tak samo, jak plik *. snk* działa w .NET Framework. Składa się ona wyłącznie z publicznej/prywatnej pary kluczy kryptograficznych i nie zawiera informacji o zweryfikowaniu wydawcy. Za pomocą samoobsługi certyfikatów można wdrażać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje z wysokim zaufaniem w intranecie. Jednak po uruchomieniu tych aplikacji na komputerze klienckim program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zidentyfikuje je jako pochodzące od nieznanego wydawcy. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] Aplikacje podpisane przy użyciu samoobsługi certyfikatów i wdrożone za pośrednictwem Internetu nie mogą korzystać z wdrożenia zaufanej aplikacji.

 Z drugiej strony, jeśli otrzymasz certyfikat od urzędu certyfikacji, na przykład dostawcy certyfikatu lub działu w przedsiębiorstwie, certyfikat ten zapewnia większe bezpieczeństwo użytkowników. Nie tylko identyfikuje wydawcę podpisanego oprogramowania, ale weryfikuje tę tożsamość, sprawdzając urząd certyfikacji, który go podpisał. Jeśli urząd certyfikacji nie jest urzędem głównym, w celu sprawdzenia, czy urząd certyfikacji jest autoryzowany do wystawiania certyfikatów, będzie również "łańcuch" z powrotem do urzędu głównego. Aby zwiększyć bezpieczeństwo, należy użyć certyfikatu wystawionego przez urząd certyfikacji, jeśli jest to możliwe.

 Aby uzyskać więcej informacji o generowaniu certyfikatów samoobsługowych, zobacz [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) lub [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Znaczniki czasu
 Certyfikaty używane do podpisywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji wygasają po upływie określonego czasu, zwykle przez dwanaście miesięcy. W celu usunięcia potrzeby ciągłego ponownego podpisywania aplikacji przy użyciu nowych certyfikatów program [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] obsługuje sygnaturę czasową. Gdy aplikacja jest podpisana sygnaturą czasową, jej certyfikat będzie nadal akceptowany nawet po wygaśnięciu, pod warunkiem, że sygnatura czasowa jest prawidłowa. Pozwala to [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacjom z wygasłymi certyfikatami, ale prawidłowymi sygnaturami czasowymi, aby pobierać i uruchamiać. Umożliwia także zainstalowanie aplikacji z wygasłymi certyfikatami, aby kontynuować pobieranie i instalowanie aktualizacji.

 Aby dołączyć sygnaturę czasową na serwerze aplikacji, musi być dostępny serwer sygnatur czasowych. Aby uzyskać informacje o sposobach wybierania serwera znacznika czasu, zobacz [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Aktualizowanie wygasłych certyfikatów
 We wcześniejszych wersjach .NET Framework zaktualizowanie aplikacji, której certyfikat wygasł, może spowodować, że aplikacja przestanie działać. Aby rozwiązać ten problem, należy użyć jednej z następujących metod:

- Zaktualizuj .NET Framework do wersji 2,0 SP1 lub nowszej w systemie Windows XP lub w wersji 3,5 lub nowszej w systemie Windows Vista.

- Odinstaluj aplikację i ponownie zainstaluj nową wersję z prawidłowym certyfikatem.

### <a name="store-certificates"></a>Certyfikaty magazynu

- Certyfikaty można przechowywać jako plik *PFX* w systemie plików lub przechowywać je wewnątrz kontenera kluczy. Użytkownik w domenie systemu Windows może mieć wiele kontenerów kluczy. Domyślnie *MakeCert.exe* będą przechowywać certyfikaty w prywatnym kontenerze kluczy, chyba że zostanie określona, że powinna zapisać ją w pliku *PFX* . *Mage.exe* i *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] Narzędzia do tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń, umożliwiają korzystanie z certyfikatów przechowywanych w jeden sposób.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (Narzędzie tworzenia i edycji manifestów)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
