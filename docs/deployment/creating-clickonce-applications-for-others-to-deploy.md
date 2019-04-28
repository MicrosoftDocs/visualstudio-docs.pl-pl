---
title: Tworzenie aplikacji ClickOnce do wdrażania przez inne osoby | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- preserved branding information
- useManifestForTrust element
- customer deployments [ClickOnce]
- multiple ClickOnce deployment and branding
- ClickOnce applications, previous .NET Framework versions
- application manifests [ClickOnce]
- <useManifestForTrust> element
- manifests [ClickOnce]
- trust applications, ClickOnce
- ClickOnce applications, deployed by others
- ClickOnce applications, previous .NET Framework
ms.assetid: d20766c7-4ef3-45ab-8aa0-3f15b61eccaa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 01e85c0257d372fa9b27ec5f031aae61132f7edc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62928907"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Tworzenie aplikacji ClickOnce do wdrażania przez innych
Nie wszyscy deweloperzy, którzy tworzą wdrożeń technologii ClickOnce firma zamierza same aplikacje. Wiele z nich po prostu spakuj swoje aplikacji przy użyciu technologii ClickOnce, a następnie przekazać pliki do klienta, takich jak dużych przedsiębiorstw. Klient staje się odpowiedzialne za hostowanie aplikacji w jego sieci. W tym temacie omówiono niektóre problemy związane z takich wdrożeń w wersjach programu .NET Framework wcześniejszych niż wersja 3.5. Zawiera opis następnie nowe rozwiązanie zawartym w .NET Framework 3.5 przy użyciu nowej funkcji "przy użyciu manifest dla zaufania". Na koniec zawiera z zalecanych strategii tworzenia wdrożeń technologii ClickOnce dla klientów, którzy nadal używają starszej wersji programu .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemy związane z tworzeniem wdrożenia dla klientów
 Kilka problemów wystąpić, gdy planujesz dostarczać wdrożenia klienta. Pierwszy problem dotyczy, podpisywanie kodu. Aby można było wdrożyć w sieci, manifest wdrożenia i manifest aplikacji ClickOnce wdrożenia muszą zarówno być podpisane za pomocą certyfikatu cyfrowego. Wywołuje to pytanie, czy ma być używany certyfikat dewelopera lub certyfikat klienta podczas podpisywania manifestów.

 Pytanie o certyfikacie używanym ma krytyczne znaczenie, ponieważ tożsamość aplikacji ClickOnce opiera się na podpis cyfrowy manifestu wdrażania. Jeśli Deweloper podpisuje manifest wdrożenia, jeśli klient jest w dużej firmie, a więcej niż jednego oddziału firmy wdraża dostosowaną wersję aplikacji może prowadzić do konfliktów.

 Na przykład załóżmy, że firma Adventure Works ma działu finansowego i działu kadr. Zarówno działów licencji aplikacji ClickOnce z firmy Microsoft Corporation, który generuje raporty z danych przechowywanych w bazie danych SQL. Firma Microsoft dostarcza każdy dział przy użyciu wersji aplikacji, która jest dostosowany do swoich danych. Jeśli aplikacje są podpisane za pomocą tego samego certyfikatu Authenticode, użytkownik, który próbuje użyć obu aplikacji będzie wystąpi błąd, jak ClickOnce będzie uznawać drugiej aplikacji jako pochodzącej identyczny z pierwszym. W takim przypadku klient mogą wystąpić nieprzewidywalne i niepożądane skutki uboczne, obejmujących utratę wszystkich danych przechowywanych lokalnie przez aplikację.

 Dodatkowe problem związany, podpisywanie kodu jest `deploymentProvider` elementu w manifeście wdrożenia ClickOnce informuje, gdzie szukać aktualizacji aplikacji. Ten element, należy dodać do pliku manifestu wdrożenia przed podpisaniem go. Jeśli ten element zostanie dodany później, manifest wdrażania musi zostać ponownie podpisany.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Użytkownik musi podpisać manifest wdrażania
 Jedno rozwiązanie tego problemu nie jest unikatowa wdrożenia jest zapewnienie logowania dla deweloperów w manifeście aplikacji, a klient podpisać manifest wdrożenia. Chociaż to podejście pozwala skutecznie, wprowadza inne problemy. Ponieważ certyfikatu Authenticode musi pozostać chronionych zasobów, klient nie tylko oferowanie certyfikat dla deweloperów do podpisania wdrożenia. Gdy klienta może podpisać manifest wdrożenia samodzielnie za pomocą bezpłatnych narzędzi z zestawu SDK programu .NET Framework, może to wymagać wiedzy technicznej niż klienta jest chęć i możliwość zapewnienia. W takich przypadkach deweloper zazwyczaj tworzy aplikację, witryny sieci Web lub inny mechanizm, za pośrednictwem którego klient może przesłać swoją wersję aplikacji do podpisywania.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Wpływ klienta logowania zabezpieczeń aplikacji ClickOnce
 Nawet wtedy, gdy deweloper i klienta zgadzasz się, że klient powinien zarejestrować manifest aplikacji, szczególnie, ponieważ dotyczy on zaufane wdrożenie aplikacji to wywołuje inne problemy, które otaczają tożsamości aplikacji. (Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Przegląd wdrażania aplikacji zaufanego](../deployment/trusted-application-deployment-overview.md).) Załóżmy, że firma Adventure Works chce skonfigurować jej komputery klienckie, tak aby był uruchamiany z pełnym zaufaniem dowolnej aplikacji udostępnionych im przez firmę Microsoft Corporation. Jeśli firma Adventure Works podpisuje manifest wdrożenia, technologia ClickOnce będzie używała Adventure pracy zabezpieczeń podpisu do określenia poziomu zaufania aplikacja.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Tworzenie wdrożenia klienta przy użyciu manifest aplikacji dla relacji zaufania
 ClickOnce w .NET Framework 3.5 zawiera nową funkcję, która umożliwia deweloperom i klientom nowego rozwiązania do scenariusza, jak powinny być podpisane manifesty. Manifest aplikacji ClickOnce obsługuje nowy element o nazwie `<useManifestForTrust>` , który umożliwia deweloperom oznaczają, że jest podpis cyfrowy manifestu aplikacji, co powinno być używane do podejmowania decyzji dotyczących zaufania. Programistka używa narzędzi pakowania ClickOnce — takich jak *Mage.exe*, *MageUI.exe*i Visual Studio — umieść ten element w manifeście aplikacji, a także osadzić nazwy wydawcy i Nazwa aplikacji w manifeście.

 Korzystając z `<useManifestForTrust>`, manifest wdrożenia nie musi być podpisany za pomocą certyfikatu Authenticode wystawiony przez urząd certyfikacji. Zamiast tego może być podpisana za pomocą co to jest znany jako certyfikat z podpisem własnym. Certyfikat z podpisem własnym wygenerowany przez klienta lub dewelopera przy użyciu standardowych narzędzi zestawu SDK programu .NET Framework, a następnie stosowane do manifestu wdrażania przy użyciu standardowych narzędzi wdrażania ClickOnce. Aby uzyskać więcej informacji, zobacz [MakeCert](/windows/desktop/SecCrypto/makecert).

 Przy użyciu certyfikatu z podpisem własnym do manifestu wdrażania przedstawia kilka zalet. Dzięki wyeliminowaniu konieczności dla klienta uzyskać lub utworzyć własne certyfikatu Authenticode `<useManifestForTrust>` upraszcza wdrażanie klienta, zapewniając dla deweloperów do obsługi własnej marki tożsamości w aplikacji. Wynik jest zestaw podpisem wdrożeń, które są bardziej bezpieczne i korzystają z tożsamości aplikacji unikatowy. Pozwala to wyeliminować potencjalnych konfliktów, które mogą wystąpić z wdrażanie tej samej aplikacji dla wielu klientów.

 Aby uzyskać szczegółowe informacje o sposobie tworzenia składników wdrożenia ClickOnce za pomocą `<useManifestForTrust>` włączone, zobacz [instruktażu: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-runtime"></a>Jak działa manifest aplikacji, aby uzyskać zaufania w czasie wykonywania
 Aby uzyskać lepsze zrozumienie sposobu działania dla zaufania przy użyciu manifest aplikacji w czasie wykonywania, rozważmy następujący przykład. Aplikacji ClickOnce, który jest przeznaczony dla .NET Framework 3.5 jest tworzone przez firmę Microsoft. Manifest aplikacji używa `<useManifestForTrust>` elementu i jest podpisany przez firmę Microsoft. Firma Adventure Works podpisuje manifest wdrożenia przy użyciu certyfikatu z podpisem własnym. Adventure Works, klienci są skonfigurowani do zaufania dowolnej aplikacji podpisane przez firmę Microsoft.

 Po kliknięciu łącza do manifestu wdrażania ClickOnce instaluje aplikację na komputerze użytkownika. Informacje na temat certyfikatów i wdrożenie zidentyfikować jednoznacznie aplikacji ClickOnce, na komputerze klienckim. Jeśli użytkownik spróbuje ponownie zainstalować tę samą aplikację z innej lokalizacji, ClickOnce, można użyć tej tożsamości do określenia, czy aplikacja już istnieje na komputerze klienckim.

 Następnie ClickOnce sprawdza, czy certyfikat Authenticode, który jest używany do podpisywania manifestu aplikacji, który określa poziom zaufania, który udzieli ClickOnce. Od firmy Adventure Works skonfigurował klientom zaufania dowolnej aplikacji podpisane przez firmę Microsoft, ta aplikacja ClickOnce ma udzielone pełne zaufanie. Aby uzyskać więcej informacji, zobacz [Przegląd wdrażania aplikacji zaufanego](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Tworzenie wdrożenia klienta dla starszych wersji
 Co zrobić, jeśli deweloper jest wdrażanie technologii ClickOnce do klientów, którzy używają starszych wersji programu .NET Framework? W poniższych sekcjach opisano kilka zalecanych rozwiązań razem z zalety i wady każdego z nich.

### <a name="sign-deployments-on-behalf-of-customer"></a>Znak wdrożeń w imieniu klientów
 Jest jedną ze strategii wdrażania dla deweloperów utworzyć mechanizm do podpisywania wdrożeń w imieniu swoich klientów przy użyciu klucza prywatnego przez klienta. Zapobiega to konieczności zarządzania kluczami prywatnymi lub wielu pakietów wdrażania dla deweloperów. Deweloper po prostu zapewnia tego samego wdrożenia do każdego klienta. Jest klientem dostosować go do środowiska. za pomocą usługi podpisywania.

 Jedną z wad do tej metody jest czas i pieniądze, które są wymagane do jej wdrożenia. Gdy usługa może być kompilowana za pomocą narzędzi dostępnych w zestawie SDK programu .NET Framework, doda więcej czasu projektowania do cyklu życia produktu.

 Jak wspomniano we wcześniejszej części tego tematu, inną wadą jest to, że każdy klient w wersji aplikacji będą miały tej samej tożsamości aplikacji, co może prowadzić do konfliktów. Jeśli jest to niepożądane, deweloper można zmienić nazwę pola używanego podczas generowania manifestu wdrażania można nadać unikatową nazwę każdej aplikacji. Spowoduje to utworzenie oddzielnych tożsamości dla każdej wersji aplikacji i wyeliminować potencjalne konflikty tożsamości. Odpowiada to pole `-Name` argument dla Mage.exe i **nazwa** na **nazwa** karty w MageUI.exe.

 Na przykład załóżmy, że deweloper utworzył aplikację o nazwie Application1. Zamiast tworzyć pojedyncze wdrożenie z pola Nazwa równa Application1, deweloper może tworzenie wielu wdrożeń z odmianą właściwe dla klienta na tej nazwy, takie jak CustomerA Application1, CustomerB Application1 i tak dalej.

### <a name="deploy-using-a-setup-package"></a>Wdrażanie przy użyciu pakietu instalacyjnego
 Druga strategia możliwe wdrożenie rozwiązania polega na generowaniu projektu Microsoft Setup przeprowadzić początkowym wdrożeniu aplikacji ClickOnce. To można podać w jednym z kilku różnych formatach: jako wdrożenia MSI Instalatora wykonywalnego (. Z rozszerzeniem EXE), lub jako plik cabinet (cab) wraz z skryptu wsadowego.

 Korzystając z tej techniki, deweloper zapewni klienta wdrożenia, który zawiera pliki aplikacji, manifest aplikacji i manifest wdrożenia, która służy jako szablon. Klient może uruchomić program instalacyjny, który będzie monit o ich podanie adres URL wdrożenia (serwer lub lokalizację, z którego użytkownicy będą instalować aplikację ClickOnce udział plików), a także certyfikat cyfrowy. Instalator aplikacji może też monit o podanie dodatkowych opcji konfiguracji technologii ClickOnce, takie jak interwał sprawdzania aktualizacji. Po zebraniu tych informacji, Instalator będzie Generowanie manifestu wdrażania rzeczywistych, podpisać go i publikowanie aplikacji ClickOnce do lokalizacji wyznaczonym serwerze.

 Istnieją trzy sposoby, że klient może zarejestrować manifest wdrożenia w tej sytuacji:

1. Odbiorca może używać prawidłowy certyfikat wystawiony przez urząd certyfikacji (CA).

2. Zmiany na temat tego podejścia klient może zdecydować się ich manifest wdrożenia przy użyciu certyfikatu z podpisem własnym. To wadą jest to, że spowoduje aplikację w celu wyświetlania słowa "Nieznany wydawca", gdy użytkownik jest pytany, czy zainstalować aplikację. Korzyścią jest jednak uniemożliwia klientom mniejszych, od konieczności poświęcania czasu i pieniędzy wymaganego certyfikatu wystawionego przez urząd certyfikacji.

3. Na koniec deweloper może zawierać własne certyfikatu z podpisem własnym w pakiet instalacyjny. Wprowadza potencjalnych problemów za pomocą tożsamości aplikacji z omówionych wcześniej w tym temacie.

   Metoda projektu wdrożenia konfiguracji wadą jest to czas i pieniądze, wymagane do kompilowania aplikacji wdrożenia niestandardowego.

### <a name="have-customer-generate-deployment-manifest"></a>Masz Generuj manifest wdrożenia klienta
 Trzecia strategia wdrażania jest ręcznie wyłączyć tylko aplikację plików i aplikacji manifestu do klienta. W tym scenariuszu klient jest odpowiedzialny za pomocą zestawu SDK programu .NET Framework do generowania i podpisać manifest wdrożenia.

 Wadą tego rozwiązania jest wymaga klienta, aby zainstalować narzędzia .NET Framework SDK i deweloperów lub administratorem systemu, będącego doświadczenie w ich używania. Niektórzy klienci mogą wymagać rozwiązania, które wymaga niewielkiego lub żadnego nakładu pracy Pomoc w ich strony.

## <a name="see-also"></a>Zobacz także
- [Wdrażanie aplikacji ClickOnce do testowania i produkcji serwerów bez ponownego podpisywania](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Przewodnik: Ręczne wdrażanie aplikacji ClickOnce, które nie wymagają ponownego podpisywania i zachowują informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)