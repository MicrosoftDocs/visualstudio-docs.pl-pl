---
title: ClickOnce i podpis Authenticode | Dokumentacja firmy Microsoft
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2fe73ba2ef02ecf6f9eb75663650862fd78fea1c
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "53859152"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce i podpis Authenticode
*Authenticode* to technologia firmy Microsoft, która używa branżowego standardu kryptografii do podpisywania kodu aplikacji przy użyciu certyfikatów cyfrowych, które zweryfikowania autentyczności wydawcy aplikacji. Za pomocą kodu Authenticode dla wdrożenia aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zmniejsza ryzyko konia trojańskiego. Koń trojański jest wirus lub występuje inne szkodliwe program, który złośliwy firm zniesławiającej jako program wiarygodnego źródła ustanowione, godne zaufania. Podpisywanie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia za pomocą certyfikatu cyfrowego jest opcjonalny krok, aby sprawdzić, czy zestawów i plików nie były modyfikowane.  
  
 Poniższe sekcje opisują różne typy certyfikatów cyfrowych używanych w Authenticode, w jaki sposób certyfikaty są weryfikowane przy użyciu certyfikatów urzędów certyfikacji, rola Oznaczanie sygnaturą czasową w certyfikatach oraz metody przestrzeń dyskowa dostępna dla certyfikaty.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode i podpisywanie kodu  
 A *certyfikatu cyfrowego* jest plik, który zawiera publicznego i prywatnego klucza kryptograficznego, wraz z metadanych opisujących wydawcy do której certyfikat został wystawiony i agencja, który wystawił certyfikat.  
  
 Istnieją różne typy certyfikatów Authenticode. Każdy z nich jest skonfigurowany dla różnych typów rejestracji. Aby uzyskać [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, konieczne jest posiadanie certyfikatu Authenticode, który jest prawidłowy do podpisywania kodu. Jeśli spróbujesz zarejestrować [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji przy użyciu innego typu certyfikatu, takie jak certyfikat cyfrowy poczty e-mail nie będzie ono działać. Aby uzyskać więcej informacji, zobacz [wprowadzenie do podpisywania kodu](http://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Można uzyskać certyfikat podpisywania w jeden z trzech sposobów kodu:  
  
- Kupić od dostawcy certyfikatu.  
  
- Wyświetlany jest jeden z grupy w Twojej organizacji, które są odpowiedzialne za tworzenie certyfikatów cyfrowych.  
  
- Generowanie własnego certyfikatu za pomocą polecenia cmdlet New-SelfSignedCertificate programu PowerShell lub za pomocą *MakeCert.exe*, który jest dołączony do [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Jak za pomocą urzędów certyfikacji ułatwia użytkownikom  
 Certyfikat wygenerowany za pomocą New-SelfSignedCertificate lub *MakeCert.exe* narzędzie jest popularnie określany mianem *self-cert* lub *certyfikatu testowego*. Tego rodzaju certyfikatu znacznie działa tak samo jak *.snk* pliku działa w programie .NET Framework. Składa się wyłącznie z pary kluczy kryptograficznych publiczny/prywatny, a nie zawiera możliwe do zweryfikowania informacji o wydawcy. Certyfikaty z własnym można użyć do wdrożenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje z wysokim poziomem zaufania w sieci intranet. Jednak gdy te aplikacje uruchomione na komputerze klienckim [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] zidentyfikować je jako pochodzący od nieznanego wydawcy. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje podpisane przy użyciu własnym certyfikatami i wdrożone przez Internet nie może wykorzystać zaufanego wdrożenia aplikacji.  
  
 Z drugiej strony Jeśli zostanie wyświetlony certyfikat od urzędu certyfikacji, takich jak dostawcy certyfikatu lub działu, w przedsiębiorstwie, certyfikat oferuje większe bezpieczeństwo dla użytkowników. Nie tylko identyfikuje wydawcę oprogramowania podpisany, ale tej tożsamości weryfikuje, sprawdzając z urzędem certyfikacji, który podpisał go. Jeśli urząd certyfikacji nie jest główny urząd certyfikacji, Authenticode będą również "połączony" do głównego urzędu, aby sprawdzić, czy urząd certyfikacji jest autoryzowany do wystawiania certyfikatów. Ze względów bezpieczeństwa należy używać certyfikatu wystawionego przez urząd certyfikacji, jeśli to możliwe.  
  
 Aby uzyskać więcej informacji na temat generowania certyfikatów self zobacz [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) lub [MakeCert](/windows/desktop/SecCrypto/makecert).  
  
### <a name="timestamps"></a>Sygnatury czasowe  
 Certyfikaty używane do podpisywania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje wygasają po upływie określonego czasu, zwykle przez dwanaście miesięcy. Aby wyeliminować potrzebę stale ponownego podpisywania aplikacji przy użyciu nowych certyfikatów [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] obsługuje sygnatury czasowej. Gdy aplikacja jest podpisana z sygnaturą czasową, jego certyfikat będzie nadal być akceptowane, nawet po wygaśnięciu, pod warunkiem, że sygnatura czasowa jest nieprawidłowa. Dzięki temu [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji za pomocą wygasłe certyfikaty, ale nieprawidłowy sygnatury czasowe, aby pobrać i uruchomić. Umożliwia także zainstalowanych aplikacji za pomocą wygasłe certyfikaty, aby w dalszym ciągu pobieranie i instalowanie aktualizacji.  
  
 Aby uwzględnić znacznika czasu w serwera aplikacji, musi być dostępny serwera znacznika czasowego. Aby uzyskać informacje o sposobie wybierania serwera znacznika czasowego, zobacz [jak: Podpisywanie aplikacji i manifestów wdrożenia](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="update-expired-certificates"></a>Aktualizuj certyfikaty wygasłe  
 We wcześniejszych wersjach programu .NET Framework aktualizowanie aplikacji wygasło którego certyfikat może spowodować tę aplikację, przestanie działać. Aby rozwiązać ten problem, należy użyć jednej z następujących metod:  
  
-   Zaktualizuj programu .NET Framework w wersji 2.0 z dodatkiem SP1 lub nowszy na Windows XP, lub w wersji 3.5 lub nowszy na Windows Vista.  
  
-   Odinstaluj tę aplikację, a następnie ponownie zainstaluj nową wersję z prawidłowym certyfikatem.  
  
-   Utwórz zestaw wiersza polecenia, który aktualizuje certyfikat. Szczegółowe informacje o tym procesie, można znaleźć w folderze [925521 artykuł pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="store-certificates"></a>Certyfikaty Store  
  
- Można przechowywać certyfikaty jako *PFX* pliku w systemie plików, lub przechowywać je wewnątrz kontenera kluczy. Użytkownik w domenie Windows może mieć wiele kontenerów kluczy. Domyślnie *MakeCert.exe* będą przechowywane certyfikaty w Twoje osobiste kontenera kluczy, chyba że określisz, że jej należy zapisać go w celu *PFX* zamiast tego. *Mage.exe* i *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] narzędzia służące do tworzenia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń umożliwiają korzystanie z certyfikatów przechowywanych w dowolnym czasie.  
  
## <a name="see-also"></a>Zobacz także  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)