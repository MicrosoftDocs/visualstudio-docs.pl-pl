---
title: ClickOnce i Authenticode | Dokumenty firmy Microsoft
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
ms.sourcegitcommit: 6c3aa85ff17916936018d121e7a0d1b486f6c7eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2020
ms.locfileid: "79093951"
---
# <a name="clickonce-and-authenticode"></a>ClickOnce i podpis Authenticode
*Authenticode* to technologia firmy Microsoft, która używa kryptografii standardowej w branży do podpisywania kodu aplikacji za pomocą certyfikatów cyfrowych, które weryfikują autentyczność wydawcy aplikacji. Za pomocą Authenticode do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożenia aplikacji, zmniejsza ryzyko konia trojańskiego. Koń trojański jest wirusem lub innym szkodliwym programem, który złośliwa strona trzecia błędnie przedstawia jako legalny program pochodzący z ustalonego, godnego zaufania źródła. Podpisywanie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] wdrożeń za pomocą certyfikatu cyfrowego jest opcjonalnym krokiem, aby sprawdzić, czy zestawy i pliki nie są modyfikowane.

 W poniższych sekcjach opisano różne typy certyfikatów cyfrowych używanych w Authenticode, sposób sprawdzania poprawności certyfikatów przy użyciu urzędów certyfikacji, rolę sygnaturowania czasowego w certyfikatach oraz metody przechowywania dostępne dla Certyfikaty.

## <a name="authenticode-and-code-signing"></a>Authenticode i podpisywanie kodu
 *Certyfikat cyfrowy* to plik zawierający kryptograficzną parę kluczy publicznych/prywatnych wraz z metadanymi opisującymi wydawcę, któremu wystawiono certyfikat, oraz agencję, która wystawiła certyfikat.

 Istnieją różne typy certyfikatów Authenticode. Każdy z nich jest skonfigurowany do różnych typów podpisywania. W [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] przypadku aplikacji musisz mieć certyfikat Authenticode, który jest prawidłowy do podpisywania kodu. Jeśli spróbujesz [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] podpisać aplikację za pomocą innego typu certyfikatu, takiego jak cyfrowy certyfikat poczty e-mail, nie będzie działać. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do podpisywania kodu](/windows/desktop/seccrypto/cryptography-tools).

 Certyfikat do podpisywania kodu można uzyskać na jeden z trzech sposobów:

- Kup jeden od dostawcy certyfikatu.

- Odbierz go od grupy w organizacji odpowiedzialnej za tworzenie certyfikatów cyfrowych.

- Generowanie własnego certyfikatu przy użyciu polecenia cmdlet programu PowerShell new-SelfSignedCertificate lub za pomocą [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] *pliku MakeCert.exe,* który jest dołączony do pliku .

### <a name="how-using-certificate-authorities-helps-users"></a>Jak korzystanie z urzędów certyfikacji pomaga użytkownikom
 Certyfikat wygenerowany przy użyciu narzędzia New-SelfSignedCertificate lub *MakeCert.exe* jest powszechnie nazywany *certyfikatem samoadjowym* lub *testowym.* Ten rodzaj certyfikatu działa podobnie, jak plik *.snk* działa w .NET Framework. Składa się wyłącznie z pary kluczy kryptograficznych publicznych/prywatnych i nie zawiera weryfikowalnych informacji o wydawcy. Certyfikatów samoadłów [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] służy do wdrażania aplikacji o wysokim zaufaniu w intranecie. Jednak gdy te aplikacje są [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] uruchamiane na komputerze klienckim, zidentyfikuje je jako pochodzące z nieznanego wydawcy. Domyślnie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje podpisane za pomocą certyfikatów i wdrożone przez Internet nie mogą korzystać z wdrażania zaufanych aplikacji.

 Natomiast jeśli otrzymasz certyfikat od urzędu certyfikacji, takiego jak dostawca certyfikatów lub dział w przedsiębiorstwie, certyfikat oferuje użytkownikom większe bezpieczeństwo. Nie tylko identyfikuje wydawcę podpisanego oprogramowania, ale weryfikuje tę tożsamość, sprawdzając ją w ukaszowym uka, który go podpisał. Jeśli urząd certyfikacji nie jest głównym urzędem certyfikacji, Authenticode będzie również "łańcuch" z powrotem do głównego urzędu, aby sprawdzić, czy urząd certyfikacji jest upoważniony do wystawiania certyfikatów. Aby zwiększyć bezpieczeństwo, należy używać certyfikatu wystawionego przez urząd certyfikacji, gdy tylko jest to możliwe.

 Aby uzyskać więcej informacji na temat generowania certyfikatów samokonfetów, zobacz [New-SelfSignedCertificate](https://technet.microsoft.com/itpro/powershell/windows/pkiclient/new-selfsignedcertificate) lub [MakeCert](/windows/desktop/SecCrypto/makecert).

### <a name="timestamps"></a>Znaczniki czasu
 Certyfikaty używane [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do podpisywania aplikacji wygasają po określonym czasie, zazwyczaj dwanaście miesięcy. Aby usunąć konieczność ciągłego ponownego podpisywania aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] za pomocą nowych certyfikatów, obsługuje sygnaturę czasową. Gdy aplikacja jest podpisana za pomocą sygnatury czasowej, jego certyfikat będzie nadal akceptowany nawet po wygaśnięciu, pod warunkiem, że sygnatura czasowa jest prawidłowa. Dzięki [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] temu aplikacje z wygasłymi certyfikatami, ale prawidłowymi sygnaturami czasowymi, mogą pobierać i uruchamiać. Umożliwia również zainstalowanym aplikacjom z wygasłymi certyfikatami dalsze pobieranie i instalowanie aktualizacji.

 Aby uwzględnić sygnaturę czasową na serwerze aplikacji, serwer sygnatury czasowej musi być dostępny. Aby uzyskać informacje dotyczące wybierania serwera sygnatury czasowej, zobacz [Jak: Podpisywać manifesty aplikacji i wdrażania](../ide/how-to-sign-application-and-deployment-manifests.md).

### <a name="update-expired-certificates"></a>Aktualizacja wygasłych certyfikatów
 We wcześniejszych wersjach programu .NET Framework aktualizowanie aplikacji, której certyfikat wygasł, może spowodować, że aplikacja przestanie działać. Aby rozwiązać ten problem, należy użyć jednej z następujących metod:

- Zaktualizuj program .NET Framework do dodatku SP1 w wersji 2.0 lub nowszej w systemie Windows XP lub w wersji 3.5 lub nowszej w systemie Windows Vista.

- Odinstaluj aplikację i zainstaluj ponownie nową wersję z prawidłowym certyfikatem.

### <a name="store-certificates"></a>Przechowywanie certyfikatów

- Certyfikaty można przechowywać jako plik *pfx* w systemie plików lub przechowywać je wewnątrz kontenera kluczy. Użytkownik w domenie systemu Windows może mieć wiele kontenerów kluczy. Domyślnie *plik MakeCert.exe* będzie przechowywać certyfikaty w kontenerze kluczy osobistych, chyba że określisz, że zamiast tego należy zapisać je w *pliku .pfx.* *Mage.exe* i *MageUI.exe*, [!INCLUDE[winsdkshort](../debugger/debug-interface-access/includes/winsdkshort_md.md)] narzędzia [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] do tworzenia wdrożeń, umożliwiają korzystanie z certyfikatów przechowywanych w obu sposób.

## <a name="see-also"></a>Zobacz też
- [Zabezpieczenia i wdrażanie technologii ClickOnce](../deployment/clickonce-security-and-deployment.md)
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Mage.exe (narzędzie generowania manifestu i edytowania)](/dotnet/framework/tools/mage-exe-manifest-generation-and-editing-tool)
