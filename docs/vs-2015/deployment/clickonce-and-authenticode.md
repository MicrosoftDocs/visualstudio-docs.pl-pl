---
title: ClickOnce i Authenticode | Microsoft Docs
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
ms.openlocfilehash: a8f7fd108250a406339d5be08b5a6e9aaf67d039
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917562"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce i podpis Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode * to technologia firmy Microsoft, która używa kryptografii standardowej w branży do podpisywania kodu aplikacji za pomocą certyfikatów cyfrowych, które weryfikują autentyczność wydawcy aplikacji. Użycie technologii Authenticode do wdrażania aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zmniejsza ryzyko koń trojański. Koń trojański jest wirusem lub innym szkodliwym programem, który złośliwa osoba trzecia Niemniej reprezentuje jako legalny program pochodzący z ustalonego, wiarygodnego źródła. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)]Aby sprawdzić, czy zestawy i pliki nie zostały naruszone, należy wykonać dodatkowe czynności.  
  
 W poniższych sekcjach opisano różne typy certyfikatów cyfrowych używanych w technologii Authenticode, sposób weryfikowania certyfikatów przy użyciu urzędów certyfikacji, rolę sygnatury czasowej w certyfikatach oraz metody magazynowania dostępne dla certyfikatów.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode i podpisywanie kodu  
 *Certyfikat cyfrowy* to plik, który zawiera kryptograficzną parę kluczy publiczny/prywatny wraz z metadanymi opisującymi wydawcy, dla których certyfikat został wystawiony, oraz Agencję, która wystawił certyfikat.  
  
 Istnieją różne typy certyfikatów Authenticode. Każdy z nich jest skonfigurowany do różnych typów podpisywania. W przypadku [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji trzeba mieć certyfikat Authenticode, który jest prawidłowy w przypadku podpisywania kodu. Próba podpisania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji przy użyciu innego typu certyfikatu, na przykład cyfrowego certyfikatu poczty e-mail, nie będzie działała. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do podpisywania kodu](https://msdn.microsoft.com/library/ms537361.aspx).  
  
 Certyfikat do podpisywania kodu można uzyskać na jeden z trzech sposobów:  
  
- Kup dostawcę certyfikatu.  
  
- Odbierz jeden z grup w organizacji odpowiedzialnych za tworzenie certyfikatów cyfrowych.  
  
- Wygeneruj własny certyfikat z MakeCert.exe, który jest dołączony do programu [!INCLUDE[winsdklong](../includes/winsdklong-md.md)] .  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Jak korzystanie z urzędów certyfikacji ułatwia użytkownikom  
 Certyfikat wygenerowany przy użyciu narzędzia MakeCert.exe jest często nazywany certyfikatem *samoobsługowym lub* *testowym*. Ten rodzaj certyfikatu działa tak samo, jak plik. snk działa w .NET Framework. Składa się ona wyłącznie z publicznej/prywatnej pary kluczy kryptograficznych i nie zawiera informacji o zweryfikowaniu wydawcy. Za pomocą samoobsługi certyfikatów można wdrażać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje z wysokim zaufaniem w intranecie. Jednak po uruchomieniu tych aplikacji na komputerze klienckim program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zidentyfikuje je jako pochodzące od nieznanego wydawcy. Domyślnie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] Aplikacje podpisane przy użyciu samoobsługi certyfikatów i wdrożone za pośrednictwem Internetu nie mogą korzystać z wdrożenia zaufanej aplikacji.  
  
 Z drugiej strony, jeśli otrzymasz certyfikat od urzędu certyfikacji, na przykład dostawcy certyfikatu lub działu w przedsiębiorstwie, certyfikat ten zapewnia większe bezpieczeństwo użytkowników. Nie tylko identyfikuje wydawcę podpisanego oprogramowania, ale weryfikuje tę tożsamość, sprawdzając urząd certyfikacji, który go podpisał. Jeśli urząd certyfikacji nie jest urzędem głównym, w celu sprawdzenia, czy urząd certyfikacji jest autoryzowany do wystawiania certyfikatów, będzie również "łańcuch" z powrotem do urzędu głównego. Aby zwiększyć bezpieczeństwo, należy użyć certyfikatu wystawionego przez urząd certyfikacji, jeśli jest to możliwe.  
  
 Aby uzyskać więcej informacji na temat generowania certyfikatów samoobsługi, zobacz [Makecert.exe (narzędzie tworzenia certyfikatów)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Znaczniki czasu  
 Certyfikaty używane do podpisywania [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji wygasają po upływie określonego czasu, zwykle przez dwanaście miesięcy. W celu usunięcia potrzeby ciągłego ponownego podpisywania aplikacji przy użyciu nowych certyfikatów program [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] obsługuje sygnaturę czasową. Gdy aplikacja jest podpisana sygnaturą czasową, jej certyfikat będzie nadal akceptowany nawet po wygaśnięciu, pod warunkiem, że sygnatura czasowa jest prawidłowa. Pozwala to [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacjom z wygasłymi certyfikatami, ale prawidłowymi sygnaturami czasowymi, aby pobierać i uruchamiać. Umożliwia także zainstalowanie aplikacji z wygasłymi certyfikatami, aby kontynuować pobieranie i instalowanie aktualizacji.  
  
 Aby dołączyć sygnaturę czasową na serwerze aplikacji, musi być dostępny serwer sygnatur czasowych. Aby uzyskać informacje o sposobach wybierania serwera znacznika czasu, zobacz [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Aktualizowanie wygasłych certyfikatów  
 We wcześniejszych wersjach .NET Framework zaktualizowanie aplikacji, której certyfikat wygasł, może spowodować, że aplikacja przestanie działać. Aby rozwiązać ten problem, należy użyć jednej z następujących metod:  
  
- Zaktualizuj .NET Framework do wersji 2,0 SP1 lub nowszej w systemie Windows XP lub w wersji 3,5 lub nowszej w systemie Windows Vista.  
  
- Odinstaluj aplikację i ponownie zainstaluj nową wersję z prawidłowym certyfikatem.  
  
- Utwórz zestaw wiersza polecenia, który aktualizuje certyfikat.  
  
### <a name="storing-certificates"></a>Przechowywanie certyfikatów  
  
- Certyfikaty można przechowywać jako plik PFX w systemie plików lub przechowywać je wewnątrz kontenera kluczy. Użytkownik w domenie systemu Windows może mieć wiele kontenerów kluczy. Domyślnie MakeCert.exe będą przechowywać certyfikaty w prywatnym kontenerze kluczy, chyba że zostanie określona, że powinna zapisać ją w pliku PFX. Mage.exe i MageUI.exe, [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] Narzędzia do tworzenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeń, umożliwiają korzystanie z certyfikatów przechowywanych w jeden sposób.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)   
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (Narzędzie tworzenia i edycji manifestów)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
