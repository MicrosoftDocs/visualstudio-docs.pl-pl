---
title: ClickOnce i podpis Authenticode | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
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
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6057aa437aa4fc0d14bd21f20e3fa657f5c5c15d
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2019
ms.locfileid: "54834771"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce i podpis Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode * jest technologia firmy Microsoft, która używa branżowego standardu kryptografii do podpisania kodu aplikacji przy użyciu certyfikatów cyfrowych, które zweryfikowania autentyczności wydawcy aplikacji. Za pomocą kodu Authenticode dla wdrożenia aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zmniejsza ryzyko konia trojańskiego. Koń trojański jest wirus lub występuje inne szkodliwe program, który złośliwy firm zniesławiającej jako program wiarygodnego źródła ustanowione, godne zaufania. Podpisywanie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożenia za pomocą certyfikatu cyfrowego jest opcjonalny krok, aby sprawdzić, czy zestawów i plików nie były modyfikowane.  
  
 Poniższe sekcje opisują różne typy certyfikatów cyfrowych używanych w Authenticode, w jaki sposób certyfikaty są weryfikowane przy użyciu certyfikatów urzędów certyfikacji, rola Oznaczanie sygnaturą czasową w certyfikatach oraz metody przestrzeń dyskowa dostępna dla certyfikaty.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode i podpisywanie kodu  
 A *certyfikatu cyfrowego* jest plik, który zawiera publicznego i prywatnego klucza kryptograficznego, wraz z metadanych opisujących wydawcy do której certyfikat został wystawiony i agencja, który wystawił certyfikat.  
  
 Istnieją różne typy certyfikatów Authenticode. Każdy z nich jest skonfigurowany dla różnych typów rejestracji. Aby uzyskać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji, konieczne jest posiadanie certyfikatu Authenticode, który jest prawidłowy do podpisywania kodu. Jeśli spróbujesz zarejestrować [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji przy użyciu innego typu certyfikatu, takie jak certyfikat cyfrowy poczty e-mail nie będzie ono działać. Aby uzyskać więcej informacji, zobacz [wprowadzenie do podpisywania kodu](http://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Można uzyskać certyfikat podpisywania w jeden z trzech sposobów kodu:  
  
-   Kupić od dostawcy certyfikatu.  
  
-   Wyświetlany jest jeden z grupy w Twojej organizacji, które są odpowiedzialne za tworzenie certyfikatów cyfrowych.  
  
-   Generowanie certyfikatu z MakeCert.exe, który jest dołączony do [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Jak za pomocą urzędów certyfikacji ułatwia użytkownikom  
 Certyfikat wygenerowany za pomocą narzędzia MakeCert.exe jest popularnie określany mianem *self-cert* lub *certyfikatu testowego*. Tego rodzaju certyfikatu działa znacznie tak samo jak pliku .snk działa w programie .NET Framework. Składa się wyłącznie z pary kluczy kryptograficznych publiczny/prywatny, a nie zawiera możliwe do zweryfikowania informacji o wydawcy. Certyfikaty z własnym można użyć do wdrożenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje z wysokim poziomem zaufania w sieci intranet. Jednak gdy te aplikacje uruchomione na komputerze klienckim [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zidentyfikować je jako pochodzący od nieznanego wydawcy. Domyślnie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje podpisane przy użyciu własnym certyfikatami i wdrożone przez Internet nie może wykorzystać zaufanego wdrożenia aplikacji.  
  
 Z drugiej strony Jeśli zostanie wyświetlony certyfikat od urzędu certyfikacji, takich jak dostawcy certyfikatu lub działu, w przedsiębiorstwie, certyfikat oferuje większe bezpieczeństwo dla użytkowników. Nie tylko identyfikuje wydawcę oprogramowania podpisany, ale tej tożsamości weryfikuje, sprawdzając z urzędem certyfikacji, który podpisał go. Jeśli urząd certyfikacji nie jest główny urząd certyfikacji, Authenticode będą również "połączony" do głównego urzędu, aby sprawdzić, czy urząd certyfikacji jest autoryzowany do wystawiania certyfikatów. Ze względów bezpieczeństwa należy używać certyfikatu wystawionego przez urząd certyfikacji, jeśli to możliwe.  
  
 Aby uzyskać więcej informacji na temat generowania certyfikatów self zobacz [Makecert.exe (narzędzie tworzenia certyfikatów)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Sygnatury czasowe  
 Certyfikaty używane do podpisywania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje wygasają po upływie określonego czasu, zwykle przez dwanaście miesięcy. Aby wyeliminować potrzebę stale ponownego podpisywania aplikacji przy użyciu nowych certyfikatów [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] obsługuje sygnatury czasowej. Gdy aplikacja jest podpisana z sygnaturą czasową, jego certyfikat będzie nadal być akceptowane, nawet po wygaśnięciu, pod warunkiem, że sygnatura czasowa jest nieprawidłowa. Dzięki temu [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji za pomocą wygasłe certyfikaty, ale nieprawidłowy sygnatury czasowe, aby pobrać i uruchomić. Umożliwia także zainstalowanych aplikacji za pomocą wygasłe certyfikaty, aby w dalszym ciągu pobieranie i instalowanie aktualizacji.  
  
 Aby uwzględnić znacznika czasu w serwera aplikacji, musi być dostępny serwera znacznika czasowego. Aby uzyskać informacje o sposobie wybierania serwera znacznika czasowego, zobacz [jak: Podpisywanie aplikacji i manifestów wdrożenia](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Aktualizowanie wygasłych certyfikatów  
 We wcześniejszych wersjach programu .NET Framework aktualizowanie aplikacji wygasło którego certyfikat może spowodować tę aplikację, przestanie działać. Aby rozwiązać ten problem, należy użyć jednej z następujących metod:  
  
-   Zaktualizuj programu .NET Framework w wersji 2.0 z dodatkiem SP1 lub nowszy na Windows XP, lub w wersji 3.5 lub nowszy na Windows Vista.  
  
-   Odinstaluj tę aplikację, a następnie ponownie zainstaluj nową wersję z prawidłowym certyfikatem.  
  
-   Utwórz zestaw wiersza polecenia, który aktualizuje certyfikat. Szczegółowe informacje o tym procesie, można znaleźć w folderze [925521 artykuł pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="storing-certificates"></a>Przechowywanie certyfikatów  
  
-   Jako plik pfx w systemie plików można przechowywać certyfikaty, lub przechowywać je wewnątrz kontenera kluczy. Użytkownik w domenie Windows może mieć wiele kontenerów kluczy. Domyślnie program MakeCert.exe będzie certyfikaty są przechowywane w osobistych kontener kluczy, chyba że określisz, że jej należy zapisywać do pliku PFX zamiast tego. Mage.exe i MageUI.exe, [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] narzędzia służące do tworzenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeń umożliwiają korzystanie z certyfikatów przechowywanych w dowolnym czasie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wdrażania i zabezpieczeń ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (narzędzie generowania manifestu i edytowania)](http://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
