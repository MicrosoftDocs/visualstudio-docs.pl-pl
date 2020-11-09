---
title: Tworzenie aplikacji ClickOnce do wdrażania przez inne osoby | Microsoft Docs
description: Dowiedz się więcej o aplikacjach ClickOnce hostowanych przez klienta opracowanych w .NET Framework 3,5 i poprzednich wersjach .NET Framework.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 7379038d1c2bf203f7787e69408ddd9b2e30f372
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383004"
---
# <a name="create-clickonce-applications-for-others-to-deploy"></a>Tworzenie aplikacji ClickOnce do wdrażania przez inne osoby
Nie wszyscy deweloperzy, którzy tworzą plan wdrożeń ClickOnce do wdrażania samych aplikacji. Wiele z nich po prostu pakuje swoją aplikację za pomocą technologii ClickOnce, a następnie Wycofaj pliki do klienta, na przykład duże firmy. Klient jest odpowiedzialny za hostowanie aplikacji w sieci. W tym temacie omówiono niektóre problemy związane z wdrażaniem w wersjach .NET Framework wcześniejszych niż wersja 3,5. Następnie opisano nowe rozwiązanie dostarczone przy użyciu nowej funkcji "Użyj manifestu dla zaufania" w .NET Framework 3,5. Na koniec zawiera ona zalecane strategie tworzenia wdrożeń ClickOnce dla klientów, którzy nadal korzystają ze starszych wersji .NET Framework.

## <a name="issues-involved-in-creating-deployments-for-customers"></a>Problemy związane z tworzeniem wdrożeń dla klientów
 Podczas planowania wdrożenia dla klienta występuje kilka problemów. Pierwszy problem dotyczy podpisywania kodu. Aby można było wdrożyć w sieci, manifest wdrożenia i manifest aplikacji wdrożenia ClickOnce muszą być podpisane przy użyciu certyfikatu cyfrowego. W ten sposób zostanie zgłoszone pytanie, czy podczas podpisywania manifestów ma być używany certyfikat dewelopera, czy certyfikat klienta.

 Pytanie, którego certyfikatu użyć, ma kluczowe znaczenie, ponieważ tożsamość aplikacji ClickOnce jest oparta na podpisie cyfrowym manifestu wdrożenia. Jeśli deweloper podpisuje Manifest wdrożenia, może to prowadzić do konfliktów, jeśli klient jest w dużej firmie i więcej niż jeden dział firmy wdraża dostosowaną wersję aplikacji.

 Załóżmy na przykład, że firma Adventure Works ma dział finansowy i Dział kadr. Obie usługi dzielą licencję na aplikację ClickOnce od firmy Microsoft Corporation, która generuje raporty z danych przechowywanych w bazie danych SQL. Firma Microsoft dostarcza każdemu działowi wersję aplikacji dostosowaną do swoich danych. Jeśli aplikacje są podpisane przy użyciu tego samego certyfikatu Authenticode, użytkownik próbujący użyć obu aplikacji napotka błąd, ponieważ ClickOnce będzie traktować drugą aplikację jako identyczną z pierwszą. W takim przypadku klient może napotkać nieprzewidywalne i niepożądane skutki uboczne, które obejmują utratę wszelkich danych przechowywanych lokalnie przez aplikację.

 Dodatkowy problem związany z podpisywaniem kodu jest `deploymentProvider` elementem w manifeście wdrożenia, który informuje ClickOnce, gdzie mają być wyszukiwane aktualizacje aplikacji. Przed podpisaniem tego elementu należy dodać go do manifestu wdrażania. Jeśli ten element zostanie dodany później, manifest wdrożenia musi być podpisany.

### <a name="require-the-customer-to-sign-the-deployment-manifest"></a>Wymagaj podpisania manifestu wdrożenia przez klienta
 Jednym z rozwiązań tego problemu w przypadku nieunikatowych wdrożeń jest podpisywanie manifestu aplikacji przez dewelopera i podpisywanie manifestu wdrożenia przez klienta. Chociaż to podejście zadziała, wprowadza inne problemy. Ponieważ certyfikat Authenticode musi pozostać chronionym zasobem, klient nie może po prostu przekazać do dewelopera certyfikatu w celu podpisania wdrożenia. Klient może podpisać manifest wdrożenia przy użyciu narzędzi dostępnych bezpłatnie z zestawem SDK .NET Framework, ale może to wymagać większej wiedzy technicznej niż klient jest skłonny lub może zapewnić. W takich przypadkach Deweloper zazwyczaj tworzy aplikację, witrynę sieci Web lub inny mechanizm, za pomocą którego klient może przesłać swoją wersję aplikacji do podpisywania.

### <a name="the-impact-of-customer-signing-on-clickonce-application-security"></a>Wpływ podpisywania klienta na zabezpieczenia aplikacji ClickOnce
 Nawet jeśli deweloper i klient zgadzają się, że klient powinien podpisać manifest aplikacji, wywołuje inne problemy, które ponoszą tożsamość aplikacji, szczególnie w odniesieniu do wdrożenia zaufanej aplikacji. Aby uzyskać więcej informacji na temat tej funkcji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md). Załóżmy, że firma Adventure Works chce skonfigurować swoje komputery klienckie w taki sposób, aby każda aplikacja udostępniona przez firmę Microsoft Corporation była uruchomiona z pełnym zaufaniem. Jeśli firma Adventure Works podpisuje Manifest wdrożenia, ClickOnce będzie używać sygnatury zabezpieczeń firmy Adventure Work, aby określić poziom zaufania aplikacji.

## <a name="create-customer-deployments-by-using-application-manifest-for-trust"></a>Tworzenie wdrożeń klientów przy użyciu manifestu aplikacji dla zaufania
 Technologia ClickOnce w .NET Framework 3,5 zawiera nową funkcję zapewniającą deweloperom i klientom nowe rozwiązanie do scenariusza, w jaki sposób mają być podpisane manifesty. Manifest aplikacji ClickOnce obsługuje nowy element o nazwie `<useManifestForTrust>` , który umożliwia deweloperom oznaczanie, że podpis cyfrowy manifestu aplikacji jest używany do podejmowania decyzji dotyczących zaufania. Deweloper używa narzędzi do pakowania ClickOnce, takich jak *Mage.exe* , *MageUI.exe* i Visual Studio — do uwzględnienia tego elementu w manifeście aplikacji, a także do osadzania zarówno nazwy wydawcy, jak i nazwy aplikacji w manifeście.

 W przypadku korzystania `<useManifestForTrust>` z programu manifest wdrożenia nie musi być podpisany przy użyciu certyfikatu Authenticode wystawionego przez urząd certyfikacji. Zamiast tego może być podpisany przy użyciu co jest znane jako certyfikat z podpisem własnym. Certyfikat z podpisem własnym jest generowany przez klienta lub dewelopera przy użyciu standardowych narzędzi zestawu SDK .NET Framework, a następnie stosowane do manifestu wdrożenia przy użyciu standardowych narzędzi wdrażania ClickOnce. Aby uzyskać więcej informacji, zobacz [MakeCert](/windows/desktop/SecCrypto/makecert).

 Korzystanie z certyfikatu z podpisem własnym dla manifestu wdrożenia ma kilka zalet. Eliminując konieczność, aby klient uzyskał lub utworzył własny certyfikat Authenticode, `<useManifestForTrust>` upraszcza wdrożenie klienta, a jednocześnie pozwala deweloperom na zachowanie własnej tożsamości oznakowania w aplikacji. Wynikiem jest zestaw podpisanych wdrożeń, które są bardziej bezpieczne i mają unikatowe tożsamości aplikacji. Eliminuje to potencjalne konflikty, które mogą wystąpić podczas wdrażania tej samej aplikacji na wielu klientach.

 Aby uzyskać szczegółowe informacje na temat sposobu tworzenia wdrożenia ClickOnce z `<useManifestForTrust>` włączonym, zobacz [Przewodnik: ręczne wdrażanie aplikacji ClickOnce, która nie wymaga ponownego podpisywania i zachowuje informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md).

### <a name="how-application-manifest-for-trust-works-at-run-time"></a>Jak manifest aplikacji dla zaufania działa w czasie wykonywania
 Aby lepiej zrozumieć sposób używania manifestu aplikacji do zaufania w czasie wykonywania, należy wziąć pod uwagę Poniższy przykład. Aplikacja ClickOnce, która jest przeznaczona dla .NET Framework 3,5, jest tworzona przez firmę Microsoft. Manifest aplikacji używa `<useManifestForTrust>` elementu i jest podpisany przez firmę Microsoft. Firma Adventure Works podpisuje Manifest wdrożenia przy użyciu certyfikatu z podpisem własnym. Klienci firmy Adventure Works są skonfigurowani do ufania wszelkim aplikacji podpisanym przez firmę Microsoft.

 Gdy użytkownik kliknie link do manifestu wdrożenia, ClickOnce zainstaluje aplikację na komputerze użytkownika. Informacje o certyfikacie i wdrożeniu identyfikują aplikację na komputerze klienckim w sposób unikatowy dla technologii ClickOnce. Jeśli użytkownik spróbuje zainstalować tę samą aplikację z innej lokalizacji, ClickOnce może użyć tej tożsamości w celu ustalenia, czy aplikacja już istnieje na kliencie.

 Następnie Technologia ClickOnce sprawdza certyfikat Authenticode, który jest używany do podpisywania manifestu aplikacji, co określa poziom zaufania, który zostanie udzielony przez technologię ClickOnce. Ponieważ firma Adventure Works skonfigurował swoich klientów do zaufania dowolnej aplikacji podpisanej przez firmę Microsoft, ta aplikacja ClickOnce ma przyznane pełne zaufanie. Aby uzyskać więcej informacji, zobacz [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md).

## <a name="create-customer-deployments-for-earlier-versions"></a>Tworzenie wdrożeń klientów dla wcześniejszych wersji
 Co zrobić, jeśli deweloper wdraża aplikacje ClickOnce dla klientów korzystających ze starszych wersji .NET Framework? Poniższe sekcje zawierają podsumowanie kilku zalecanych rozwiązań wraz z zaletami i wadą każdego z nich.

### <a name="sign-deployments-on-behalf-of-customer"></a>Podpisz wdrożenia w imieniu klienta
 Jedną z możliwych strategii wdrażania jest to, aby deweloper mógł utworzyć mechanizm podpisywania wdrożeń w imieniu swoich klientów przy użyciu własnego klucza prywatnego klienta. Zapobiega to konieczności zarządzania kluczami prywatnymi lub wieloma pakietami wdrożeniowymi przez dewelopera. Deweloper udostępnia to samo wdrożenie każdemu klientowi. Klient może dostosować go do swoich środowisk za pomocą usługi podpisywania.

 Jedną z wad tej metody jest czas i koszt, które są wymagane do jego wdrożenia. Taka usługa może być skompilowana przy użyciu narzędzi dostępnych w zestawie .NET Framework SDK, co spowoduje zwiększenie czasu projektowania do cyklu życia produktu.

 Jak wspomniano wcześniej w tym temacie, kolejną wadą jest to, że każda wersja aplikacji klienta będzie miała taką samą tożsamość aplikacji, co może prowadzić do konfliktów. Jeśli jest to problem, deweloper może zmienić pole nazwy, które jest używane podczas generowania manifestu wdrożenia, aby nadać każdej aplikacji unikatową nazwę. Spowoduje to utworzenie oddzielnej tożsamości dla każdej wersji aplikacji i wyeliminowanie potencjalnych konfliktów tożsamości. To pole odnosi się do `-Name` argumentu Mage.exe i do pola **Nazwa** na karcie **Nazwa** w MageUI.exe.

 Załóżmy na przykład, że deweloper utworzył aplikację o nazwie Application1. Zamiast tworzenia jednego wdrożenia z polem nazwa ustawionym na Application1, deweloper może utworzyć kilka wdrożeń z odmianą specyficzną dla klienta, na przykład Application1-Customer, Application1-CustomerB i tak dalej.

### <a name="deploy-using-a-setup-package"></a>Wdrażanie przy użyciu pakietu instalacyjnego
 Druga możliwa strategia wdrażania polega na wygenerowaniu projektu Instalatora firmy Microsoft w celu wykonania początkowego wdrożenia aplikacji ClickOnce. Można to zrobić w jednym z kilku różnych formatów: jako wdrożenie MSI, jako plik wykonywalny Instalatora (. EXE) lub plik Cabinet (CAB) wraz z skryptem wsadowym.

 Korzystając z tej techniki, deweloper dostarczy klientowi wdrożenie obejmujące pliki aplikacji, manifest aplikacji i manifest wdrożenia, który służy jako szablon. Klient uruchomi program instalacyjny, który wyświetli monit o podanie adresu URL wdrożenia (serwera lub lokalizacji udziału plików, z których użytkownicy będą instalować aplikację ClickOnce), a także certyfikat cyfrowy. Aplikacja instalatora może również wybrać monit o podanie dodatkowych opcji konfiguracji ClickOnce, takich jak interwał sprawdzania aktualizacji. Po zebraniu tych informacji program instalacyjny wygeneruje rzeczywisty manifest wdrażania, podpisuje go i opublikuje aplikację ClickOnce w wyznaczeniej lokalizacji serwera.

 Istnieją trzy sposoby podpisywania manifestu wdrożenia w tej sytuacji przez klienta:

1. Klient może korzystać z ważnego certyfikatu wystawionego przez urząd certyfikacji (CA).

2. Jako odmiana tego podejścia klient może zdecydować się na podpisanie manifestu wdrożenia przy użyciu certyfikatu z podpisem własnym. Wadą tego jest to, że spowoduje to wyświetlenie w aplikacji wyrazów "Nieznany wydawca", gdy użytkownik zostanie poproszony o jego zainstalowanie. Korzyścią jest jednak, że uniemożliwiają mniejszym klientom poświęcanie czasu i pieniędzy wymaganych dla certyfikatu wystawionego przez urząd certyfikacji.

3. Na koniec deweloper może uwzględnić własny certyfikat z podpisem własnym w pakiecie instalacyjnym. W tym temacie wprowadzono potencjalne problemy związane z tożsamością aplikacji omówioną wcześniej.

   Wadą metody projektu wdrożenia Instalatora jest czas i wydatki wymagane do utworzenia niestandardowej aplikacji wdrożenia.

### <a name="have-customer-generate-deployment-manifest"></a>Generowanie manifestu wdrażania przez klienta
 Trzecia możliwa strategia wdrażania polega na przekazaniu klientom tylko plików aplikacji i manifestu aplikacji. W tym scenariuszu klient jest odpowiedzialny za używanie zestawu SDK .NET Framework do generowania i podpisywania manifestu wdrożenia.

 Wadą tej metody jest to, że wymaga od klienta zainstalowania narzędzi zestawu SDK .NET Framework i posiadania dewelopera lub administratora systemu, który jest wykwalifikowany do korzystania z nich. Niektórzy klienci mogą wymagać rozwiązania, które wymaga niewielkiego lub żadnego nakładu technicznego na ich część.

## <a name="see-also"></a>Zobacz też
- [Wdrażaj aplikacje ClickOnce do testowania i serwerów produkcyjnych bez ponownego podpisywania](../deployment/deploying-clickonce-applications-for-testing-and-production-without-resigning.md)
- [Przewodnik: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)
- [Przewodnik: ręczne wdrażanie aplikacji ClickOnce, która nie wymaga ponownego podpisywania i zachowuje informacje o znakowaniu](../deployment/walkthrough-manually-deploying-a-clickonce-app-no-re-signing-required.md)