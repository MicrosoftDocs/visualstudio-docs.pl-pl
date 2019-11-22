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
ms.openlocfilehash: 06edf9954134a6110f9285fc744c87c2696b19d5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74298268"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce i podpis Authenticode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Authenticode * to technologia firmy Microsoft, która używa kryptografii standardowej w branży do podpisywania kodu aplikacji za pomocą certyfikatów cyfrowych, które weryfikują autentyczność wydawcy aplikacji. Przy użyciu Authenticode na potrzeby wdrażania aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] zmniejsza ryzyko koń trojański. Koń trojański jest wirusem lub innym szkodliwym programem, który złośliwa osoba trzecia Niemniej reprezentuje jako legalny program pochodzący z ustalonego, wiarygodnego źródła. Podpisywanie [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeń z certyfikatem cyfrowym jest opcjonalnym krokiem do sprawdzenia, czy zestawy i pliki nie zostały naruszone.  
  
 W poniższych sekcjach opisano różne typy certyfikatów cyfrowych używanych w technologii Authenticode, sposób weryfikowania certyfikatów przy użyciu urzędów certyfikacji, rolę sygnatury czasowej w certyfikatach oraz metody magazynów dostępne dla programu przystawki.  
  
## <a name="authenticode-and-code-signing"></a>Authenticode i podpisywanie kodu  
 *Certyfikat cyfrowy* to plik, który zawiera kryptograficzną parę kluczy publiczny/prywatny wraz z metadanymi opisującymi wydawcy, dla których certyfikat został wystawiony, oraz Agencję, która wystawił certyfikat.  
  
 Istnieją różne typy certyfikatów Authenticode. Każdy z nich jest skonfigurowany do różnych typów podpisywania. W przypadku aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] należy mieć certyfikat Authenticode, który jest prawidłowy w przypadku podpisywania kodu. Próba podpisania aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] przy użyciu innego typu certyfikatu, na przykład cyfrowego certyfikatu poczty e-mail, nie będzie działała. Aby uzyskać więcej informacji, zobacz [wprowadzenie do podpisywania kodu](https://go.microsoft.com/fwlink/?LinkId=179452).  
  
 Certyfikat do podpisywania kodu można uzyskać na jeden z trzech sposobów:  
  
- Kup dostawcę certyfikatu.  
  
- Odbierz jeden z grup w organizacji odpowiedzialnych za tworzenie certyfikatów cyfrowych.  
  
- Wygeneruj własny certyfikat z MakeCert. exe, który jest dołączony do [!INCLUDE[winsdklong](../includes/winsdklong-md.md)].  
  
### <a name="how-using-certificate-authorities-helps-users"></a>Jak korzystanie z urzędów certyfikacji ułatwia użytkownikom  
 Certyfikat wygenerowany za pomocą narzędzia MakeCert. exe jest zwykle nazywany certyfikatem *samoobsługowym* lub *testowym*. Ten rodzaj certyfikatu działa tak samo, jak plik. snk działa w .NET Framework. Składa się ona wyłącznie z publicznej/prywatnej pary kluczy kryptograficznych i nie zawiera informacji o zweryfikowaniu wydawcy. Za pomocą samoobsługi certyfikatów można wdrażać [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacje z wysokim zaufaniem w intranecie. Jeśli jednak te aplikacje są uruchamiane na komputerze klienckim, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] będą identyfikować je jako pochodzące od nieznanego wydawcy. [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] domyślnie aplikacje podpisane przy użyciu samoobsługi certyfikatów i wdrożone za pośrednictwem Internetu nie mogą korzystać z wdrożenia zaufanej aplikacji.  
  
 Z drugiej strony, jeśli otrzymasz certyfikat od urzędu certyfikacji, na przykład dostawcy certyfikatu lub działu w przedsiębiorstwie, certyfikat ten zapewnia większe bezpieczeństwo użytkowników. Nie tylko identyfikuje wydawcę podpisanego oprogramowania, ale weryfikuje tę tożsamość, sprawdzając urząd certyfikacji, który go podpisał. Jeśli urząd certyfikacji nie jest urzędem głównym, w celu sprawdzenia, czy urząd certyfikacji jest autoryzowany do wystawiania certyfikatów, będzie również "łańcuch" z powrotem do urzędu głównego. Aby zwiększyć bezpieczeństwo, należy użyć certyfikatu wystawionego przez urząd certyfikacji, jeśli jest to możliwe.  
  
 Aby uzyskać więcej informacji na temat generowania certyfikatów samoobsługowych, zobacz [Makecert. exe (narzędzie tworzenia certyfikatów)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d).  
  
### <a name="timestamps"></a>Sygnatury czasowe  
 Certyfikaty używane do podpisywania aplikacji [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wygasają po upływie określonego czasu, zwykle dwanaście miesięcy. Aby usunąć konieczność ciągłego ponownego podpisywania aplikacji przy użyciu nowych certyfikatów, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] obsługuje sygnaturę czasową. Gdy aplikacja jest podpisana sygnaturą czasową, jej certyfikat będzie nadal akceptowany nawet po wygaśnięciu, pod warunkiem, że sygnatura czasowa jest prawidłowa. Pozwala to [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacjom z wygasłymi certyfikatami, ale prawidłowymi sygnaturami czasowymi, aby pobierać i uruchamiać. Umożliwia także zainstalowanie aplikacji z wygasłymi certyfikatami, aby kontynuować pobieranie i instalowanie aktualizacji.  
  
 Aby dołączyć sygnaturę czasową na serwerze aplikacji, musi być dostępny serwer sygnatur czasowych. Aby uzyskać informacje o sposobach wybierania serwera znacznika czasu, zobacz [How to: Signing Application and Deployment Manifests](../ide/how-to-sign-application-and-deployment-manifests.md).  
  
### <a name="updating-expired-certificates"></a>Aktualizowanie wygasłych certyfikatów  
 We wcześniejszych wersjach .NET Framework zaktualizowanie aplikacji, której certyfikat wygasł, może spowodować, że aplikacja przestanie działać. Aby rozwiązać ten problem, należy użyć jednej z następujących metod:  
  
- Zaktualizuj .NET Framework do wersji 2,0 SP1 lub nowszej w systemie Windows XP lub w wersji 3,5 lub nowszej w systemie Windows Vista.  
  
- Odinstaluj aplikację i ponownie zainstaluj nową wersję z prawidłowym certyfikatem.  
  
- Utwórz zestaw wiersza polecenia, który aktualizuje certyfikat. Informacje krok po kroku dotyczące tego procesu można znaleźć w [artykule pomoc techniczna firmy Microsoft artykułu 925521](https://go.microsoft.com/fwlink/?LinkId=179454).  
  
### <a name="storing-certificates"></a>Przechowywanie certyfikatów  
  
- Certyfikaty można przechowywać jako plik PFX w systemie plików lub przechowywać je wewnątrz kontenera kluczy. Użytkownik w domenie systemu Windows może mieć wiele kontenerów kluczy. Domyślnie program MakeCert. exe będzie przechowywał certyfikaty w prywatnym kontenerze kluczy, chyba że określisz, że powinien on zapisać go w pliku PFX. Program Mage. exe i MageUI. exe, [!INCLUDE[winsdkshort](../includes/winsdkshort-md.md)] narzędzia do tworzenia [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] wdrożeń, umożliwiają korzystanie z certyfikatów przechowywanych w obu przypadkach.  
  
## <a name="see-also"></a>Zobacz też  
   [zabezpieczeń i wdrażania technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Mage.exe (narzędzie generowania manifestu i edytowania)](https://msdn.microsoft.com/library/77dfe576-2962-407e-af13-82255df725a1)
